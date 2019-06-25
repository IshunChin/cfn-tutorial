### create stack vpc

```bash
git clone https://github.com/IshunChin/cfn-tutorial.git
cd cfn-tutorial

git checkout b28966d cfn-tamplate/webservice/web/master.yml

aws cloudformation create-stack \
--stack-name cfn-tutorial-staging-vpc \
--template-body file://`pwd`/cfn-tamplate/network/vpc/master.yml \
--parameters file://`pwd`/cfn-tamplate/network/vpc/parameters/staging.json
```

### create stack security
```bash
aws cloudformation create-stack \
--stack-name cfn-tutorial-staging-security \
--template-body file://`pwd`/cfn-tamplate/network/security/master.yml \
--parameters file://`pwd`/cfn-tamplate/network/security/parameters/staging.json
```

### create stack rds
```bash
aws cloudformation create-stack \
--stack-name cfn-tutorial-staging-rds \
--template-body file://`pwd`/cfn-tamplate/webservice/db/rds/master.yml \
--parameters file://`pwd`/cfn-tamplate/webservice/db/rds/parameters/staging.json
```

### create stack webServer
```bash
aws cloudformation create-stack \
--stack-name cfn-tutorial-staging-webservice \
--template-body file://`pwd`/cfn-tamplate/webservice/web/master.yml \
--parameters file://`pwd`/cfn-tamplate/webservice/web/parameters/staging.json
```

### create change set
```bash
git checkout 8059e26 cfn-tamplate/webservice/web/master.yml

aws cloudformation create-change-set \
--stack-name cfn-tutorial-staging-webservice \
--change-set-name add-loadbalancer \
--template-body file://`pwd`/cfn-tamplate/webservice/web/master.yml \
--parameters file://`pwd`/cfn-tamplate/webservice/web/parameters/staging.json
```

### excute change set
```bash
git checkout 8059e26 cfn-tamplate/webservice/web/master.yml

aws cloudformation create-change-set \
--stack-name cfn-tutorial-staging-webservice \
--change-set-name add-loadbalancer \
--template-body file://`pwd`/cfn-tamplate/webservice/web/master.yml \
--parameters file://`pwd`/cfn-tamplate/webservice/web/parameters/staging.json
```


### Git diff
```bash
git difftool 8059e26 b28966d cfn-tamplate/webservice/web/master.yml
```
