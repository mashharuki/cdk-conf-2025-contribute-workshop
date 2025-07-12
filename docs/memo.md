# ワークショップメモ！

## EC２上にVS Codeのサーバーを立ち上げる方法

以下のスタックファイルを使う

https://github.com/jaws-ug-cdk/cdk-conf-2024-contribute-workshop/blob/main/CdkConferenceStack.json

リソース(標準)で作成する。

→ Amazon linux2023でEC2インスタンスをSSMでアクセス可能とする。

**ここで作成されるリソース**
- VPC
- EC2インスタンス
- 接続用のエンドポイント


EC2インスタンスにアクセスして以下のコマンドを実行する

```bash
code tunnel service install
```

これでEC2インスタンスをVS Codeサーバーとすることが可能！！

## 着手できそうなIssueを決める！

以下のリポジトリのIssueをのぞいてみる

https://github.com/aws/aws-cdk/issues

## ダミーリポジトリをクローンしてくる

自分のアカウントにフォークしてもOK!

```bash
git clone https://github.com/jaws-ug-cdk/aws-cdk-for-workshop
```

クローンしたら以下のファイルを除いてみる！

packages/aws-cdk-lib/aws-sqs/lib/queue.ts

依存関係をインストール

```bash
yarn install
```

ビルドを行う

初回は62のプロジェクトをビルドする。

```bash
npx lerna run build --concurrency 4
```

以下のようになればOK!

```bash
lerna notice cli v8.1.2

   ✔  @aws-cdk/script-tests:build (677ms)
   ✔  @aws-cdk/eslint-plugin:build (5s)
   ✔  @aws-cdk/node-bundle:build (5s)
   ✔  @aws-cdk/prlint:build (6s)
   ✔  @aws-cdk/pkglint:build (9s)
   ✔  @aws-cdk/yarn-cling:build (4s)
   ✔  awslint:build (8s)
   ✔  @aws-cdk/cdk-build-tools:build (7s)
   ✔  @aws-cdk/lazify:build (6s)
   ✔  @aws-cdk/aws-custom-resource-sdk-adapter:build (9s)
   ✔  @aws-cdk/spec2cdk:build (11s)
   ✔  @aws-cdk/cloudformation-diff:build (12s)
   ✔  @aws-cdk/cdk-cli-wrapper:build (8s)
   ✔  @aws-cdk/custom-resource-handlers:build (8s)
   ✔  @aws-cdk/cdk-release:build (9s)
   ✔  @aws-cdk/pkgtools:build (8s)
   ✔  @aws-cdk-testing/cli-integ:build (23s)
   ✔  aws-cdk-lib:build (5m)

——————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————

   ✔  @aws-cdk/cloud-assembly-schema:build (4s)

——————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————

   ✔  @aws-cdk/region-info:build (7s)

——————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————————

   ✔  @aws-cdk/cx-api:build (4s)
   ✔  cdk-assets:build (18s)
   ✔  aws-cdk:build (1m)
   ✔  cdk:build (674ms)
   ✔  @aws-cdk/integ-runner:build (14s)
   ✔  @aws-cdk/cli-lib-alpha:build (37s)
   ✔  @aws-cdk/aws-codestar-alpha:build (53s)
   ✔  @aws-cdk/aws-cognito-identitypool-alpha:build (54s)
   ✔  @aws-cdk/integ-tests-alpha:build (1m)
   ✔  @aws-cdk/example-construct-library:build (19s)
   ✔  @aws-cdk/aws-route53resolver-alpha:build (53s)








   ✔  @aws-cdk/aws-s3objectlambda-alpha:build (53s)
   ✔  @aws-cdk/aws-iotevents-alpha:build (53s)
   ✔  @aws-cdk/aws-pipes-alpha:build (1m)
   ✔  @aws-cdk/aws-kinesisfirehose-alpha:build (53s)
   ✔  @aws-cdk/aws-iot-alpha:build (52s)
   ✔  @aws-cdk/aws-kinesisfirehose-destinations-alpha:build (54s)
   ✔  @aws-cdk/aws-scheduler-alpha:build (1m)
   ✔  @aws-cdk-testing/framework-integ:build (1m)
   ✔  @aws-cdk/app-staging-synthesizer-alpha:build (55s)



   ✔  @aws-cdk/aws-amplify-alpha:build (53s)
   ✔  @aws-cdk/aws-appconfig-alpha:build (1m)
   ✔  @aws-cdk/aws-apprunner-alpha:build (53s)
   ✔  @aws-cdk/aws-cloud9-alpha:build (59s)
   ✔  @aws-cdk/aws-gamelift-alpha:build (55s)
   ✔  @aws-cdk/aws-ivs-alpha:build (52s)
   ✔  @aws-cdk/aws-glue-alpha:build (1m)
   ✔  @aws-cdk/aws-kinesisanalytics-flink-alpha:build (52s)
   ✔  @aws-cdk/aws-lambda-go-alpha:build (53s)
   ✔  @aws-cdk/aws-lambda-python-alpha:build (54s)
   ✔  @aws-cdk/aws-location-alpha:build (51s)
   ✔  @aws-cdk/aws-msk-alpha:build (54s)
   ✔  @aws-cdk/aws-neptune-alpha:build (53s)
   ✔  @aws-cdk/aws-redshift-alpha:build (57s)
   ✔  @aws-cdk/aws-sagemaker-alpha:build (56s)
   ✔  @aws-cdk/aws-servicecatalogappregistry-alpha:build (52s)
   ✔  @aws-cdk/aws-iotevents-actions-alpha:build (53s)
   ✔  @aws-cdk/aws-pipes-enrichments-alpha:build (59s)
   ✔  @aws-cdk/aws-pipes-sources-alpha:build (60s)
   ✔  @aws-cdk/aws-pipes-targets-alpha:build (60s)
   ✔  @aws-cdk/aws-iot-actions-alpha:build (1m)

——————————————————————————————————————————————————————————————————————————————————————————————————



   ✔  @aws-cdk/aws-scheduler-targets-alpha:build (59s)

—————————————————————————————————————————————————————————————————————————————————————

 Lerna (powered by Nx)   Successfully ran target build for 62 projects (17m)
```

テストは以下のコマンドで行う

例えば、SQSのスタックに関するユニットテストを実行する場合は以下の通りとする！

```bash
cd packages/aws-cdk-lib
yarn test aws-sqs/test/sqs.test.ts
```

以下のような感じになるはず

```bash
 PASS  aws-sqs/test/sqs.test.ts (12.165 s)
  ✓ default properties (33 ms)
  ✓ with a dead letter queue (18 ms)
  ✓ message retention period must be between 1 minute to 14 days (21 ms)
  ✓ message retention period can be provided as a parameter (10 ms)
  ✓ addToPolicy will automatically create a policy for this queue (14 ms)
  ✓ test ".fifo" suffixed queues register as fifo (5 ms)
  ✓ test a fifo queue is observed when the "fifo" property is specified (5 ms)
  ✓ test a fifo queue is observed when high throughput properties are specified (5 ms)
  ✓ test a queue throws when fifoThroughputLimit specified on non fifo queue (1 ms)
  ✓ test a queue throws when deduplicationScope specified on non fifo queue (1 ms)
  ✓ test metrics (3 ms)
  ✓ fails if queue policy has no actions (8 ms)
  ✓ fails if queue policy has no IAM principals (2 ms)
  export and import
    ✓ importing works correctly (3 ms)
    ✓ importing fifo and standard queues are detected correctly (1 ms)
    ✓ importing with keyArn and encryptionType is set correctly (1 ms)
    ✓ import queueArn from token, fifo and standard queues can be defined (3 ms)
    ✓ import queueArn from token, check attributes (3 ms)
    ✓ fails if fifo flag is set for non fifo queue name (1 ms)
    ✓ fails if fifo flag is false for fifo queue name (1 ms)
    ✓ importing works correctly for cross region queue (1 ms)
    ✓ sets account for imported queue env by fromQueueAttributes (1 ms)
    ✓ sets region for imported queue env by fromQueueAttributes (1 ms)
    ✓ sets account for imported queue env by fromQueueArn (1 ms)
    ✓ sets region for imported queue env by fromQueueArn (1 ms)
  grants
    ✓ grantConsumeMessages (16 ms)
    ✓ grantSendMessages (12 ms)
    ✓ grantPurge (14 ms)
    ✓ grant() is general purpose (11 ms)
    ✓ grants also work on imported queues (11 ms)
  queue encryption
    ✓ encryptionMasterKey can be set to a custom KMS key (10 ms)
    ✓ a kms key will be allocated if encryption = kms but a master key is not specified (9 ms)
    ✓ it is possible to use a managed kms key (6 ms)
    ✓ grant also affects key on encrypted queue (20 ms)
    ✓ it is possible to use sqs managed server side encryption (6 ms)
    ✓ it is possible to disable encryption (unencrypted) (5 ms)
    ✓ encryptionMasterKey is not supported if encryption type SQS_MANAGED is used (1 ms)
    ✓ encryptionType is always KMS, when an encryptionMasterKey is provided (7 ms)
  encryption in transit
    ✓ enforceSSL can be enabled (8 ms)
  redriveAllowPolicy
    ✓ Default settings for the dead letter source queue permission (5 ms)
    ✓ redrive permission can be set to allowAll (5 ms)
    ✓ redrive permission can be set to denyAll (5 ms)
    ✓ explicit specification of dead letter source queues (8 ms)
    ✓ throw if sourceQueues is not specified when redrivePermission is byQueue (1 ms)
    ✓ throw if dead letter source queues are specified with allowAll permission (1 ms)
    ✓ throw if souceQueues length is greater than 10 (2 ms)
    ✓ throw if sourceQueues is blank array when redrivePermission is byQueue (1 ms)


=============================== Coverage summary ===============================
Statements   : 44.87% ( 4539/10114 )
Branches     : 27.62% ( 1114/4033 )
Functions    : 32.13% ( 758/2359 )
Lines        : 45.73% ( 4440/9708 )
================================================================================
Jest: "global" coverage threshold for statements (55%) not met: 44.87%
Jest: "global" coverage threshold for branches (35%) not met: 27.62%
Test Suites: 1 passed, 1 total
Tests:       47 passed, 47 total
Snapshots:   0 total
Time:        13.217 s
```

integration テスト(統合テスト)実行方法

```bash
cd packages/@aws-cdk-testing/framework-integ
yarn tsc
# 実際に integration テストを実行する
# jsファイルが生成されていることを確認してから
yarn integ aws-sqs/test/integ.sqs.js 
```

以下のようになればOK!

```bash
Verifying integration test snapshots...

  UNCHANGED  aws-sqs/test/integ.sqs 0.665s

Snapshot Results: 

Tests:    1 passed, 1 total
Done in 1.29s.
```

ビルドが終わったらワークショップ用のブランチを作成する。

```bash
git switch -c workshop-guide-1

git branch
```

今回は以下のファイルを修正する

```bash
aws-cdk/packages/aws-cdk-lib/aws-sns/lib/topic.ts
```

displayNameの説明はCloudFormationのドキュメントからコピーしてくる

https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-sns-topic.html#cfn-sns-topic-displayname

修正が完了したら以下のコマンドでユニットテストを実行する

```bash
yarn test aws-sns/test/sns.test.ts
```

以下の通りになればOK!

```bash
Topic
    ✓ can add a policy to the topic (13 ms)
    ✓ can enforce ssl when creating the topic (9 ms)
    ✓ give publishing permissions (12 ms)
    ✓ TopicPolicy passed document (7 ms)
    ✓ Add statements to policy (7 ms)
    ✓ Create topic policy and enforce ssl (7 ms)
    ✓ topic resource policy includes unique SIDs (8 ms)
    ✓ fromTopicArn (2 ms)
    ✓ fromTopicArn fifo (1 ms)
    ✓ fromTopicAttributes contentBasedDeduplication false (1 ms)
    ✓ fromTopicAttributes contentBasedDeduplication true (1 ms)
    ✓ fromTopicAttributes throws with contentBasedDeduplication on non-fifo topic (1 ms)
    ✓ sets account for imported topic env
    ✓ sets region for imported topic env (1 ms)
    ✓ test metrics (3 ms)
    ✓ subscription is created under the topic scope by default (8 ms)
    ✓ if "scope" is defined, subscription will be created under that scope (14 ms)
    ✓ fails if topic policy has no actions (8 ms)
    ✓ fails if topic policy has no IAM principals (2 ms)
    ✓ topic policy should be set if topic as a notifications rule target (12 ms)
    ✓ specify delivery status logging configuration through construct props (12 ms)
    ✓ add delivery status logging configuration to a topic (8 ms)
    ✓ fails if success feedback sample rate is outside the appropriate range (20 ms)
    ✓ fails if success feedback sample rate is decimal (3 ms)
    ✓ specify displayName (5 ms)
    topic tests
      ✓ all defaults (30 ms)
      ✓ specify topicName (15 ms)
      ✓ specify kmsMasterKey (17 ms)
      ✓ Adds .fifo suffix when no topicName is passed (8 ms)
      ✓ specify fifo without .fifo suffix in topicName (7 ms)
      ✓ specify fifo with .fifo suffix in topicName (6 ms)
      ✓ specify fifo without contentBasedDeduplication (6 ms)
      ✓ specify fifo with contentBasedDeduplication (6 ms)
      ✓ throw with contentBasedDeduplication on non-fifo topic (20 ms)
      ✓ specify signatureVersion (9 ms)
      ✓ throw with incorrect signatureVersion (2 ms)
    message retention period
      ✓ specify message retention period in days (5 ms)
      ✓ throw error if message retention period is invalid value "0" (1 ms)
      ✓ throw error if message retention period is invalid value "366" (1 ms)
      ✓ throw error if message retention period is invalid value "12.3" (1 ms)
      ✓ throw error if message retention period is invalid value "NaN" (1 ms)
      ✓ throw error when specify messageRetentionPeriodInDays to standard topic (1 ms)
    tracingConfig
      ✓ specify tracingConfig (6 ms)


=============================== Coverage summary ===============================
Statements   : 43.77% ( 4469/10208 )
Branches     : 26.61% ( 1073/4031 )
Functions    : 31.12% ( 743/2387 )
Lines        : 44.6% ( 4373/9803 )
================================================================================
Jest: "global" coverage threshold for statements (55%) not met: 43.77%
Jest: "global" coverage threshold for branches (35%) not met: 26.61%
Test Suites: 1 passed, 1 total
Tests:       43 passed, 43 total
Snapshots:   0 total
Time:        3.131 s
```

次に統合テストコードを作成する。

テストコードは `packages/@aws-cdk-testing/framework-integ/test/aws-sns/test` に作成する

```bash
touch packages/@aws-cdk-testing/framework-integ/test/aws-sns/test/integ.sns-display-name.ts
```

今回は以下のようなテストコードを追加する。

```ts
// packages/@aws-cdk-testing/framework-integ/test/aws-sns/test/integ.sns-display-name.ts
import { App, Stack, StackProps } from 'aws-cdk-lib';
import { Topic } from 'aws-cdk-lib/aws-sns';
import * as integ from '@aws-cdk/integ-tests-alpha';

// テスト用のStackを定義
class TestStack extends Stack {
  constructor(scope: App, id: string, props?: StackProps) {
    super(scope, id, props);

    new Topic(this, 'MyTopic', {
      topicName: 'MyTopicName',
      // displayNameを設定
      displayName: 'MyDisplayName',
    });
  }
}

const app = new App();

const stack = new TestStack(app, 'DisplayNameTopicTestStack');

// 統合テストの実行
new integ.IntegTest(app, 'SnsTest', {
  testCases: [stack],
});
```

追加したら再度ビルドして統合テストの実行

```bash
cd /packages/aws-cdk-lib
yarn tsc

cd packages/@aws-cdk-testing/framework-integ
yarn tsc
yarn integ aws-sns/test/integ.sns-display-name.js --update-on-failed
```

以下のようになればOk！

```bash
Verifying integration test snapshots...

  NEW        aws-sns/test/integ.sns-display-name 2.374s

Snapshot Results: 

Tests:    1 failed, 1 total
Failed: /home/ec2-user/aws-cdk-for-workshop/packages/@aws-cdk-testing/framework-integ/test/aws-sns/test/integ.sns-display-name.js

Running integration tests for failed tests...

Running in parallel across regions: us-east-1, us-east-2, us-west-2
Running test /home/ec2-user/aws-cdk-for-workshop/packages/@aws-cdk-testing/framework-integ/test/aws-sns/test/integ.sns-display-name.js in us-east-1
  SUCCESS    aws-sns/test/integ.sns-display-name-SnsTest/DefaultTest 74.573s
       NO ASSERTIONS

Test Results: 

Tests:    1 passed, 1 total
Done in 77.59s.
```
