# kafka-mirror-maker-playground

## Topic renaming feature

- clone [this](https://github.com/opencore/mirrormaker_topic_rename) project
- Please, check the `pom.xml` file in order to have a consistent kafka version
- build the downloaded project with `mvn clean package`
- copy `mmchangetopic-1.0-SNAPSHOT.jar` to `jars/mmchangetopic-1.0-SNAPSHOT.jar`
- add this jar to classpath variable

## How to test it

- `docker-compose up -d`
- use your local binaries or acceed to one of the kafka machines

`./bin/kafka-mirror-maker.sh --consumer.config /etc/configs/consumer.s.cfg --producer.config /etc/configs/consumer.s.cfg --whitelist <topicname>`
This command will copy matching regex in whitelist to target cluster preserving the name.

If you want to change names in copy so 
- **--message.handler** 
  give the name of the built class *com.opencore.RenameTopicHandler*
- **--message.handler.args** `topicsourcename1,topictargetname1;topicsourcename2,topictargetname2`


MirrorMaker seems ain't support incluster copy by definition but there are some workaround out there.