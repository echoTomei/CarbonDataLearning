	create datamap  *** select a as a1 **
	
	should throw error

code:

	  test("test pre agg create table 2") {
	    sql("create datamap preagg2 on table PreAggMain using 'preaggregate' as select a as a1,sum(b) from PreAggMain group by a")
	    checkExistence(sql("DESCRIBE FORMATTED PreAggMain_preagg2"), true, "preaggmain_a")
	    checkExistence(sql("DESCRIBE FORMATTED PreAggMain_preagg2"), true, "preaggmain_b_sum")
	    checkExistence(sql("DESCRIBE FORMATTED PreAggMain_preagg2"), false, "preaggmain_a1")
	    sql("DESCRIBE FORMATTED PreAggMain_preagg2").show()
	    sql("select * from PreAggMain_preagg2").show()
	    sql("select a1 from PreAggMain_preagg2").show()
	
	    sql("DESCRIBE FORMATTED PreAggMain").show()
	    sql("select * from PreAggMain").show()
	    sql("select a as a1,sum(b) from PreAggMain group by a").show()
	
	    sql("drop datamap preagg2 on table PreAggMain")
	  }

error:
	
	/usr/java/jdk1.8.0_131/bin/java -javaagent:/david/idea-IC-171.4424.56/lib/idea_rt.jar=34022:/david/idea-IC-171.4424.56/bin -Dfile.encoding=UTF-8 -classpath /root/.IdeaIC2017.1/config/plugins/Scala/lib/scala-plugin-runners.jar:/usr/java/jdk1.8.0_131/jre/lib/charsets.jar:/usr/java/jdk1.8.0_131/jre/lib/deploy.jar:/usr/java/jdk1.8.0_131/jre/lib/ext/cldrdata.jar:/usr/java/jdk1.8.0_131/jre/lib/ext/dnsns.jar:/usr/java/jdk1.8.0_131/jre/lib/ext/jaccess.jar:/usr/java/jdk1.8.0_131/jre/lib/ext/jfxrt.jar:/usr/java/jdk1.8.0_131/jre/lib/ext/localedata.jar:/usr/java/jdk1.8.0_131/jre/lib/ext/nashorn.jar:/usr/java/jdk1.8.0_131/jre/lib/ext/sunec.jar:/usr/java/jdk1.8.0_131/jre/lib/ext/sunjce_provider.jar:/usr/java/jdk1.8.0_131/jre/lib/ext/sunpkcs11.jar:/usr/java/jdk1.8.0_131/jre/lib/ext/zipfs.jar:/usr/java/jdk1.8.0_131/jre/lib/javaws.jar:/usr/java/jdk1.8.0_131/jre/lib/jce.jar:/usr/java/jdk1.8.0_131/jre/lib/jfr.jar:/usr/java/jdk1.8.0_131/jre/lib/jfxswt.jar:/usr/java/jdk1.8.0_131/jre/lib/jsse.jar:/usr/java/jdk1.8.0_131/jre/lib/management-agent.jar:/usr/java/jdk1.8.0_131/jre/lib/plugin.jar:/usr/java/jdk1.8.0_131/jre/lib/resources.jar:/usr/java/jdk1.8.0_131/jre/lib/rt.jar:/xubo/git/carbondata/integration/spark-common-test/target/test-classes:/xubo/git/carbondata/integration/spark-common-test/target/classes:/xubo/git/carbondata/integration/spark-common/target/classes:/xubo/git/carbondata/processing/target/classes:/xubo/git/carbondata/core/target/classes:/david/repo/org/apache/carbondata/carbondata-format/1.3.0-SNAPSHOT/carbondata-format-1.3.0-SNAPSHOT.jar:/xubo/git/carbondata/common/target/classes:/david/repo/com/google/code/gson/gson/2.3.1/gson-2.3.1.jar:/david/repo/org/xerial/snappy/snappy-java/1.1.2.6/snappy-java-1.1.2.6.jar:/david/repo/org/apache/zookeeper/zookeeper/3.4.7/zookeeper-3.4.7.jar:/david/repo/org/apache/spark/spark-sql_2.11/2.2.1/spark-sql_2.11-2.2.1.jar:/david/repo/org/apache/spark/spark-sketch_2.11/2.2.1/spark-sketch_2.11-2.2.1.jar:/david/repo/org/apache/spark/spark-catalyst_2.11/2.2.1/spark-catalyst_2.11-2.2.1.jar:/david/repo/org/codehaus/janino/janino/3.0.0/janino-3.0.0.jar:/david/repo/org/codehaus/janino/commons-compiler/3.0.0/commons-compiler-3.0.0.jar:/david/repo/org/antlr/antlr4-runtime/4.5.3/antlr4-runtime-4.5.3.jar:/david/repo/org/apache/parquet/parquet-column/1.8.2/parquet-column-1.8.2.jar:/david/repo/org/apache/parquet/parquet-common/1.8.2/parquet-common-1.8.2.jar:/david/repo/org/apache/parquet/parquet-encoding/1.8.2/parquet-encoding-1.8.2.jar:/david/repo/org/apache/parquet/parquet-hadoop/1.8.2/parquet-hadoop-1.8.2.jar:/david/repo/org/apache/parquet/parquet-format/2.3.1/parquet-format-2.3.1.jar:/david/repo/org/apache/parquet/parquet-jackson/1.8.2/parquet-jackson-1.8.2.jar:/david/repo/com/fasterxml/jackson/core/jackson-databind/2.6.5/jackson-databind-2.6.5.jar:/david/repo/com/fasterxml/jackson/core/jackson-annotations/2.6.0/jackson-annotations-2.6.0.jar:/david/repo/com/fasterxml/jackson/core/jackson-core/2.6.5/jackson-core-2.6.5.jar:/david/repo/com/univocity/univocity-parsers/2.2.1/univocity-parsers-2.2.1.jar:/david/repo/org/apache/commons/commons-lang3/3.3.2/commons-lang3-3.3.2.jar:/david/repo/org/apache/hadoop/hadoop-common/2.7.2/hadoop-common-2.7.2.jar:/david/repo/org/apache/hadoop/hadoop-annotations/2.7.2/hadoop-annotations-2.7.2.jar:/usr/java/jdk1.8.0_131/lib/tools.jar:/david/repo/com/google/guava/guava/11.0.2/guava-11.0.2.jar:/david/repo/org/apache/commons/commons-math3/3.1.1/commons-math3-3.1.1.jar:/david/repo/xmlenc/xmlenc/0.52/xmlenc-0.52.jar:/david/repo/commons-net/commons-net/3.1/commons-net-3.1.jar:/david/repo/commons-collections/commons-collections/3.2.2/commons-collections-3.2.2.jar:/david/repo/org/mortbay/jetty/jetty/6.1.26/jetty-6.1.26.jar:/david/repo/org/mortbay/jetty/jetty-util/6.1.26/jetty-util-6.1.26.jar:/david/repo/com/sun/jersey/jersey-core/1.9/jersey-core-1.9.jar:/david/repo/com/sun/jersey/jersey-json/1.9/jersey-json-1.9.jar:/david/repo/org/codehaus/jettison/jettison/1.1/jettison-1.1.jar:/david/repo/com/sun/xml/bind/jaxb-impl/2.2.3-1/jaxb-impl-2.2.3-1.jar:/david/repo/javax/xml/bind/jaxb-api/2.2.2/jaxb-api-2.2.2.jar:/david/repo/javax/xml/stream/stax-api/1.0-2/stax-api-1.0-2.jar:/david/repo/javax/activation/activation/1.1/activation-1.1.jar:/david/repo/org/codehaus/jackson/jackson-jaxrs/1.8.3/jackson-jaxrs-1.8.3.jar:/david/repo/org/codehaus/jackson/jackson-xc/1.8.3/jackson-xc-1.8.3.jar:/david/repo/com/sun/jersey/jersey-server/1.9/jersey-server-1.9.jar:/david/repo/asm/asm/3.1/asm-3.1.jar:/david/repo/log4j/log4j/1.2.17/log4j-1.2.17.jar:/david/repo/net/java/dev/jets3t/jets3t/0.9.0/jets3t-0.9.0.jar:/david/repo/com/jamesmurty/utils/java-xmlbuilder/0.4/java-xmlbuilder-0.4.jar:/david/repo/commons-configuration/commons-configuration/1.6/commons-configuration-1.6.jar:/david/repo/commons-digester/commons-digester/1.8/commons-digester-1.8.jar:/david/repo/commons-beanutils/commons-beanutils/1.7.0/commons-beanutils-1.7.0.jar:/david/repo/commons-beanutils/commons-beanutils-core/1.8.0/commons-beanutils-core-1.8.0.jar:/david/repo/org/slf4j/slf4j-api/1.7.10/slf4j-api-1.7.10.jar:/david/repo/org/slf4j/slf4j-log4j12/1.7.10/slf4j-log4j12-1.7.10.jar:/david/repo/org/codehaus/jackson/jackson-core-asl/1.9.13/jackson-core-asl-1.9.13.jar:/david/repo/com/google/protobuf/protobuf-java/2.5.0/protobuf-java-2.5.0.jar:/david/repo/org/apache/hadoop/hadoop-auth/2.7.2/hadoop-auth-2.7.2.jar:/david/repo/org/apache/directory/server/apacheds-kerberos-codec/2.0.0-M15/apacheds-kerberos-codec-2.0.0-M15.jar:/david/repo/org/apache/directory/server/apacheds-i18n/2.0.0-M15/apacheds-i18n-2.0.0-M15.jar:/david/repo/org/apache/directory/api/api-asn1-api/1.0.0-M20/api-asn1-api-1.0.0-M20.jar:/david/repo/org/apache/directory/api/api-util/1.0.0-M20/api-util-1.0.0-M20.jar:/david/repo/org/apache/curator/curator-framework/2.7.1/curator-framework-2.7.1.jar:/david/repo/com/jcraft/jsch/0.1.42/jsch-0.1.42.jar:/david/repo/org/apache/curator/curator-client/2.7.1/curator-client-2.7.1.jar:/david/repo/org/apache/curator/curator-recipes/2.7.1/curator-recipes-2.7.1.jar:/david/repo/org/apache/htrace/htrace-core/3.1.0-incubating/htrace-core-3.1.0-incubating.jar:/david/repo/org/apache/commons/commons-compress/1.4.1/commons-compress-1.4.1.jar:/david/repo/org/tukaani/xz/1.0/xz-1.0.jar:/david/repo/org/apache/hadoop/hadoop-hdfs/2.7.2/hadoop-hdfs-2.7.2.jar:/david/repo/commons-daemon/commons-daemon/1.0.13/commons-daemon-1.0.13.jar:/david/repo/io/netty/netty/3.6.2.Final/netty-3.6.2.Final.jar:/david/repo/xerces/xercesImpl/2.9.1/xercesImpl-2.9.1.jar:/david/repo/xml-apis/xml-apis/1.3.04/xml-apis-1.3.04.jar:/david/repo/org/fusesource/leveldbjni/leveldbjni-all/1.8/leveldbjni-all-1.8.jar:/xubo/git/carbondata/hadoop/target/classes:/david/repo/org/scala-lang/scala-compiler/2.11.8/scala-compiler-2.11.8.jar:/david/repo/org/scala-lang/modules/scala-parser-combinators_2.11/1.0.4/scala-parser-combinators_2.11-1.0.4.jar:/david/repo/org/scala-lang/scala-reflect/2.11.8/scala-reflect-2.11.8.jar:/david/repo/org/scala-lang/scala-library/2.11.8/scala-library-2.11.8.jar:/xubo/git/carbondata/integration/spark2/target/classes:/xubo/git/carbondata/streaming/target/classes:/david/repo/org/apache/spark/spark-repl_2.11/2.2.1/spark-repl_2.11-2.2.1.jar:/david/repo/org/apache/spark/spark-core_2.11/2.2.1/spark-core_2.11-2.2.1.jar:/david/repo/com/twitter/chill_2.11/0.8.0/chill_2.11-0.8.0.jar:/david/repo/com/esotericsoftware/kryo-shaded/3.0.3/kryo-shaded-3.0.3.jar:/david/repo/com/esotericsoftware/minlog/1.3.0/minlog-1.3.0.jar:/david/repo/org/objenesis/objenesis/2.1/objenesis-2.1.jar:/david/repo/com/twitter/chill-java/0.8.0/chill-java-0.8.0.jar:/david/repo/org/apache/hadoop/hadoop-client/2.6.5/hadoop-client-2.6.5.jar:/david/repo/org/apache/hadoop/hadoop-mapreduce-client-app/2.6.5/hadoop-mapreduce-client-app-2.6.5.jar:/david/repo/org/apache/hadoop/hadoop-mapreduce-client-common/2.6.5/hadoop-mapreduce-client-common-2.6.5.jar:/david/repo/org/apache/hadoop/hadoop-yarn-client/2.6.5/hadoop-yarn-client-2.6.5.jar:/david/repo/org/apache/hadoop/hadoop-yarn-server-common/2.6.5/hadoop-yarn-server-common-2.6.5.jar:/david/repo/org/apache/hadoop/hadoop-mapreduce-client-shuffle/2.6.5/hadoop-mapreduce-client-shuffle-2.6.5.jar:/david/repo/org/apache/hadoop/hadoop-yarn-api/2.6.5/hadoop-yarn-api-2.6.5.jar:/david/repo/org/apache/hadoop/hadoop-mapreduce-client-core/2.7.2/hadoop-mapreduce-client-core-2.7.2.jar:/david/repo/org/apache/hadoop/hadoop-yarn-common/2.7.2/hadoop-yarn-common-2.7.2.jar:/david/repo/org/apache/hadoop/hadoop-mapreduce-client-jobclient/2.6.5/hadoop-mapreduce-client-jobclient-2.6.5.jar:/david/repo/org/apache/spark/spark-launcher_2.11/2.2.1/spark-launcher_2.11-2.2.1.jar:/david/repo/org/apache/spark/spark-network-common_2.11/2.2.1/spark-network-common_2.11-2.2.1.jar:/david/repo/org/apache/spark/spark-network-shuffle_2.11/2.2.1/spark-network-shuffle_2.11-2.2.1.jar:/david/repo/org/apache/spark/spark-unsafe_2.11/2.2.1/spark-unsafe_2.11-2.2.1.jar:/david/repo/javax/servlet/javax.servlet-api/3.1.0/javax.servlet-api-3.1.0.jar:/david/repo/org/slf4j/jcl-over-slf4j/1.7.16/jcl-over-slf4j-1.7.16.jar:/david/repo/com/ning/compress-lzf/1.0.3/compress-lzf-1.0.3.jar:/david/repo/net/jpountz/lz4/lz4/1.3.0/lz4-1.3.0.jar:/david/repo/org/roaringbitmap/RoaringBitmap/0.5.11/RoaringBitmap-0.5.11.jar:/david/repo/org/json4s/json4s-jackson_2.11/3.2.11/json4s-jackson_2.11-3.2.11.jar:/david/repo/org/json4s/json4s-core_2.11/3.2.11/json4s-core_2.11-3.2.11.jar:/david/repo/org/json4s/json4s-ast_2.11/3.2.11/json4s-ast_2.11-3.2.11.jar:/david/repo/org/scala-lang/scalap/2.11.8/scalap-2.11.8.jar:/david/repo/org/glassfish/jersey/core/jersey-client/2.22.2/jersey-client-2.22.2.jar:/david/repo/javax/ws/rs/javax.ws.rs-api/2.0.1/javax.ws.rs-api-2.0.1.jar:/david/repo/org/glassfish/hk2/hk2-api/2.4.0-b34/hk2-api-2.4.0-b34.jar:/david/repo/org/glassfish/hk2/hk2-utils/2.4.0-b34/hk2-utils-2.4.0-b34.jar:/david/repo/org/glassfish/hk2/external/aopalliance-repackaged/2.4.0-b34/aopalliance-repackaged-2.4.0-b34.jar:/david/repo/org/glassfish/hk2/external/javax.inject/2.4.0-b34/javax.inject-2.4.0-b34.jar:/david/repo/org/glassfish/hk2/hk2-locator/2.4.0-b34/hk2-locator-2.4.0-b34.jar:/david/repo/org/javassist/javassist/3.18.1-GA/javassist-3.18.1-GA.jar:/david/repo/org/glassfish/jersey/core/jersey-common/2.22.2/jersey-common-2.22.2.jar:/david/repo/javax/annotation/javax.annotation-api/1.2/javax.annotation-api-1.2.jar:/david/repo/org/glassfish/jersey/bundles/repackaged/jersey-guava/2.22.2/jersey-guava-2.22.2.jar:/david/repo/org/glassfish/hk2/osgi-resource-locator/1.0.1/osgi-resource-locator-1.0.1.jar:/david/repo/org/glassfish/jersey/core/jersey-server/2.22.2/jersey-server-2.22.2.jar:/david/repo/org/glassfish/jersey/media/jersey-media-jaxb/2.22.2/jersey-media-jaxb-2.22.2.jar:/david/repo/javax/validation/validation-api/1.1.0.Final/validation-api-1.1.0.Final.jar:/david/repo/org/glassfish/jersey/containers/jersey-container-servlet/2.22.2/jersey-container-servlet-2.22.2.jar:/david/repo/org/glassfish/jersey/containers/jersey-container-servlet-core/2.22.2/jersey-container-servlet-core-2.22.2.jar:/david/repo/io/netty/netty-all/4.0.43.Final/netty-all-4.0.43.Final.jar:/david/repo/com/clearspring/analytics/stream/2.7.0/stream-2.7.0.jar:/david/repo/io/dropwizard/metrics/metrics-core/3.1.2/metrics-core-3.1.2.jar:/david/repo/io/dropwizard/metrics/metrics-jvm/3.1.2/metrics-jvm-3.1.2.jar:/david/repo/io/dropwizard/metrics/metrics-json/3.1.2/metrics-json-3.1.2.jar:/david/repo/io/dropwizard/metrics/metrics-graphite/3.1.2/metrics-graphite-3.1.2.jar:/david/repo/com/fasterxml/jackson/module/jackson-module-scala_2.11/2.6.5/jackson-module-scala_2.11-2.6.5.jar:/david/repo/com/fasterxml/jackson/module/jackson-module-paranamer/2.6.5/jackson-module-paranamer-2.6.5.jar:/david/repo/org/apache/ivy/ivy/2.4.0/ivy-2.4.0.jar:/david/repo/oro/oro/2.0.8/oro-2.0.8.jar:/david/repo/net/razorvine/pyrolite/4.13/pyrolite-4.13.jar:/david/repo/net/sf/py4j/py4j/0.10.4/py4j-0.10.4.jar:/david/repo/org/apache/commons/commons-crypto/1.0.0/commons-crypto-1.0.0.jar:/david/repo/org/apache/spark/spark-mllib_2.11/2.2.1/spark-mllib_2.11-2.2.1.jar:/david/repo/org/apache/spark/spark-streaming_2.11/2.2.1/spark-streaming_2.11-2.2.1.jar:/david/repo/org/apache/spark/spark-graphx_2.11/2.2.1/spark-graphx_2.11-2.2.1.jar:/david/repo/com/github/fommil/netlib/core/1.1.2/core-1.1.2.jar:/david/repo/net/sourceforge/f2j/arpack_combined_all/0.1/arpack_combined_all-0.1.jar:/david/repo/org/apache/spark/spark-mllib-local_2.11/2.2.1/spark-mllib-local_2.11-2.2.1.jar:/david/repo/org/scalanlp/breeze_2.11/0.13.2/breeze_2.11-0.13.2.jar:/david/repo/org/scalanlp/breeze-macros_2.11/0.13.2/breeze-macros_2.11-0.13.2.jar:/david/repo/com/github/rwl/jtransforms/2.4.0/jtransforms-2.4.0.jar:/david/repo/org/spire-math/spire_2.11/0.13.0/spire_2.11-0.13.0.jar:/david/repo/org/spire-math/spire-macros_2.11/0.13.0/spire-macros_2.11-0.13.0.jar:/david/repo/org/typelevel/machinist_2.11/0.6.1/machinist_2.11-0.6.1.jar:/david/repo/com/chuusai/shapeless_2.11/2.3.2/shapeless_2.11-2.3.2.jar:/david/repo/org/typelevel/macro-compat_2.11/1.1.1/macro-compat_2.11-1.1.1.jar:/david/repo/org/jpmml/pmml-model/1.2.15/pmml-model-1.2.15.jar:/david/repo/org/jpmml/pmml-schema/1.2.15/pmml-schema-1.2.15.jar:/david/repo/jline/jline/2.12.1/jline-2.12.1.jar:/david/repo/org/slf4j/jul-to-slf4j/1.7.16/jul-to-slf4j-1.7.16.jar:/david/repo/org/apache/xbean/xbean-asm5-shaded/4.4/xbean-asm5-shaded-4.4.jar:/david/repo/org/apache/spark/spark-hive-thriftserver_2.11/2.2.1/spark-hive-thriftserver_2.11-2.2.1.jar:/david/repo/org/apache/spark/spark-hive_2.11/2.2.1/spark-hive_2.11-2.2.1.jar:/david/repo/com/twitter/parquet-hadoop-bundle/1.6.0/parquet-hadoop-bundle-1.6.0.jar:/david/repo/org/spark-project/hive/hive-exec/1.2.1.spark2/hive-exec-1.2.1.spark2.jar:/david/repo/javolution/javolution/5.5.1/javolution-5.5.1.jar:/david/repo/log4j/apache-log4j-extras/1.2.17/apache-log4j-extras-1.2.17.jar:/david/repo/org/antlr/antlr-runtime/3.4/antlr-runtime-3.4.jar:/david/repo/org/antlr/stringtemplate/3.2.1/stringtemplate-3.2.1.jar:/david/repo/antlr/antlr/2.7.7/antlr-2.7.7.jar:/david/repo/org/antlr/ST4/4.0.4/ST4-4.0.4.jar:/david/repo/com/googlecode/javaewah/JavaEWAH/0.3.2/JavaEWAH-0.3.2.jar:/david/repo/org/iq80/snappy/snappy/0.2/snappy-0.2.jar:/david/repo/stax/stax-api/1.0.1/stax-api-1.0.1.jar:/david/repo/net/sf/opencsv/opencsv/2.3/opencsv-2.3.jar:/david/repo/org/spark-project/hive/hive-metastore/1.2.1.spark2/hive-metastore-1.2.1.spark2.jar:/david/repo/com/jolbox/bonecp/0.8.0.RELEASE/bonecp-0.8.0.RELEASE.jar:/david/repo/org/datanucleus/datanucleus-api-jdo/3.2.6/datanucleus-api-jdo-3.2.6.jar:/david/repo/org/datanucleus/datanucleus-rdbms/3.2.9/datanucleus-rdbms-3.2.9.jar:/david/repo/commons-pool/commons-pool/1.5.4/commons-pool-1.5.4.jar:/david/repo/commons-dbcp/commons-dbcp/1.4/commons-dbcp-1.4.jar:/david/repo/javax/jdo/jdo-api/3.0.1/jdo-api-3.0.1.jar:/david/repo/javax/transaction/jta/1.1/jta-1.1.jar:/david/repo/org/apache/avro/avro/1.7.7/avro-1.7.7.jar:/david/repo/com/thoughtworks/paranamer/paranamer/2.3/paranamer-2.3.jar:/david/repo/org/apache/avro/avro-mapred/1.7.7/avro-mapred-1.7.7-hadoop2.jar:/david/repo/org/apache/avro/avro-ipc/1.7.7/avro-ipc-1.7.7.jar:/david/repo/org/apache/avro/avro-ipc/1.7.7/avro-ipc-1.7.7-tests.jar:/david/repo/commons-httpclient/commons-httpclient/3.1/commons-httpclient-3.1.jar:/david/repo/org/apache/calcite/calcite-avatica/1.2.0-incubating/calcite-avatica-1.2.0-incubating.jar:/david/repo/org/apache/calcite/calcite-core/1.2.0-incubating/calcite-core-1.2.0-incubating.jar:/david/repo/org/apache/calcite/calcite-linq4j/1.2.0-incubating/calcite-linq4j-1.2.0-incubating.jar:/david/repo/net/hydromatic/eigenbase-properties/1.1.5/eigenbase-properties-1.1.5.jar:/david/repo/org/apache/httpcomponents/httpclient/4.5.2/httpclient-4.5.2.jar:/david/repo/org/codehaus/jackson/jackson-mapper-asl/1.9.13/jackson-mapper-asl-1.9.13.jar:/david/repo/commons-codec/commons-codec/1.10/commons-codec-1.10.jar:/david/repo/joda-time/joda-time/2.9.3/joda-time-2.9.3.jar:/david/repo/org/jodd/jodd-core/3.5.2/jodd-core-3.5.2.jar:/david/repo/com/google/code/findbugs/jsr305/1.3.9/jsr305-1.3.9.jar:/david/repo/org/datanucleus/datanucleus-core/3.2.10/datanucleus-core-3.2.10.jar:/david/repo/org/apache/thrift/libthrift/0.9.3/libthrift-0.9.3.jar:/david/repo/org/apache/thrift/libfb303/0.9.3/libfb303-0.9.3.jar:/david/repo/org/apache/derby/derby/10.12.1.1/derby-10.12.1.1.jar:/david/repo/org/spark-project/hive/hive-cli/1.2.1.spark2/hive-cli-1.2.1.spark2.jar:/david/repo/commons-cli/commons-cli/1.2/commons-cli-1.2.jar:/david/repo/commons-lang/commons-lang/2.6/commons-lang-2.6.jar:/david/repo/org/spark-project/hive/hive-jdbc/1.2.1.spark2/hive-jdbc-1.2.1.spark2.jar:/david/repo/org/apache/httpcomponents/httpcore/4.4/httpcore-4.4.jar:/david/repo/org/spark-project/hive/hive-beeline/1.2.1.spark2/hive-beeline-1.2.1.spark2.jar:/david/repo/commons-io/commons-io/2.4/commons-io-2.4.jar:/david/repo/net/sf/supercsv/super-csv/2.2.0/super-csv-2.2.0.jar:/david/repo/org/apache/spark/spark-tags_2.11/2.2.1/spark-tags_2.11-2.2.1.jar:/david/repo/net/sf/jpam/jpam/1.1/jpam-1.1.jar:/david/repo/commons-logging/commons-logging/1.0.4/commons-logging-1.0.4.jar:/david/repo/org/spark-project/spark/unused/1.0.0/unused-1.0.0.jar:/david/repo/junit/junit/4.11/junit-4.11.jar:/david/repo/org/hamcrest/hamcrest-core/1.3/hamcrest-core-1.3.jar:/david/repo/org/scalatest/scalatest_2.11/2.2.1/scalatest_2.11-2.2.1.jar:/david/repo/org/scala-lang/modules/scala-xml_2.11/1.0.2/scala-xml_2.11-1.0.2.jar:/david/repo/org/jmockit/jmockit/1.10/jmockit-1.10.jar org.jetbrains.plugins.scala.testingSupport.scalaTest.ScalaTestRunner -s org.apache.carbondata.integration.spark.testsuite.preaggregate.TestPreAggCreateCommand -testName "test pre agg create table 2" -C org.jetbrains.plugins.scala.testingSupport.scalaTest.ScalaTestReporter -showProgressMessages true
	Testing started at 11:56 AM ...
	log4j:WARN No appenders could be found for logger (org.apache.spark.sql.test.TestQueryExecutor$).
	log4j:WARN Please initialize the log4j system properly.
	log4j:WARN See http://logging.apache.org/log4j/1.2/faq.html#noconfig for more info.
	Using Spark's default log4j profile: org/apache/spark/log4j-defaults.properties
	18/02/01 19:56:19 INFO SparkContext: Running Spark version 2.2.1
	18/02/01 19:56:19 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
	18/02/01 19:56:20 WARN Utils: Your hostname, hadoop resolves to a loopback address: 127.0.0.1; using 10.229.51.168 instead (on interface eth0)
	18/02/01 19:56:20 WARN Utils: Set SPARK_LOCAL_IP if you need to bind to another address
	18/02/01 19:56:20 INFO SparkContext: Submitted application: Spark2TestQueryExecutor
	18/02/01 19:56:20 INFO SecurityManager: Changing view acls to: root
	18/02/01 19:56:20 INFO SecurityManager: Changing modify acls to: root
	18/02/01 19:56:20 INFO SecurityManager: Changing view acls groups to: 
	18/02/01 19:56:20 INFO SecurityManager: Changing modify acls groups to: 
	18/02/01 19:56:20 INFO SecurityManager: SecurityManager: authentication disabled; ui acls disabled; users  with view permissions: Set(root); groups with view permissions: Set(); users  with modify permissions: Set(root); groups with modify permissions: Set()
	18/02/01 19:56:20 INFO Utils: Successfully started service 'sparkDriver' on port 59637.
	18/02/01 19:56:20 INFO SparkEnv: Registering MapOutputTracker
	18/02/01 19:56:20 INFO SparkEnv: Registering BlockManagerMaster
	18/02/01 19:56:20 INFO BlockManagerMasterEndpoint: Using org.apache.spark.storage.DefaultTopologyMapper for getting topology information
	18/02/01 19:56:20 INFO BlockManagerMasterEndpoint: BlockManagerMasterEndpoint up
	18/02/01 19:56:20 INFO DiskBlockManager: Created local directory at /tmp/blockmgr-8065002d-8022-452b-8b9c-dfa2b6130a67
	18/02/01 19:56:20 INFO MemoryStore: MemoryStore started with capacity 867.6 MB
	18/02/01 19:56:20 INFO SparkEnv: Registering OutputCommitCoordinator
	18/02/01 19:56:21 INFO Utils: Successfully started service 'SparkUI' on port 4040.
	18/02/01 19:56:21 INFO SparkUI: Bound SparkUI to 0.0.0.0, and started at http://10.229.51.168:4040
	18/02/01 19:56:21 INFO Executor: Starting executor ID driver on host localhost
	18/02/01 19:56:21 INFO Utils: Successfully started service 'org.apache.spark.network.netty.NettyBlockTransferService' on port 43279.
	18/02/01 19:56:21 INFO NettyBlockTransferService: Server created on 10.229.51.168:43279
	18/02/01 19:56:21 INFO BlockManager: Using org.apache.spark.storage.RandomBlockReplicationPolicy for block replication policy
	18/02/01 19:56:21 INFO BlockManagerMaster: Registering BlockManager BlockManagerId(driver, 10.229.51.168, 43279, None)
	18/02/01 19:56:21 INFO BlockManagerMasterEndpoint: Registering block manager 10.229.51.168:43279 with 867.6 MB RAM, BlockManagerId(driver, 10.229.51.168, 43279, None)
	18/02/01 19:56:21 INFO BlockManagerMaster: Registered BlockManager BlockManagerId(driver, 10.229.51.168, 43279, None)
	18/02/01 19:56:21 INFO BlockManager: Initialized BlockManager: BlockManagerId(driver, 10.229.51.168, 43279, None)
	18/02/01 19:56:21 INFO SharedState: Setting hive.metastore.warehouse.dir ('null') to the value of spark.sql.warehouse.dir ('/xubo/git/carbondata/integration/spark-common/target/warehouse').
	18/02/01 19:56:21 INFO SharedState: Warehouse path is '/xubo/git/carbondata/integration/spark-common/target/warehouse'.
	18/02/01 19:56:22 INFO HiveUtils: Initializing HiveMetastoreConnection version 1.2.1 using Spark classes.
	18/02/01 19:56:23 INFO HiveMetaStore: 0: Opening raw store with implemenation class:org.apache.hadoop.hive.metastore.ObjectStore
	18/02/01 19:56:23 INFO ObjectStore: ObjectStore, initialize called
	18/02/01 19:56:23 INFO Persistence: Property hive.metastore.integral.jdo.pushdown unknown - will be ignored
	18/02/01 19:56:23 INFO Persistence: Property datanucleus.cache.level2 unknown - will be ignored
	18/02/01 19:56:25 INFO ObjectStore: Setting MetaStore object pin classes with hive.metastore.cache.pinobjtypes="Table,StorageDescriptor,SerDeInfo,Partition,Database,Type,FieldSchema,Order"
	18/02/01 19:56:27 INFO Datastore: The class "org.apache.hadoop.hive.metastore.model.MFieldSchema" is tagged as "embedded-only" so does not have its own datastore table.
	18/02/01 19:56:27 INFO Datastore: The class "org.apache.hadoop.hive.metastore.model.MOrder" is tagged as "embedded-only" so does not have its own datastore table.
	18/02/01 19:56:27 INFO Datastore: The class "org.apache.hadoop.hive.metastore.model.MFieldSchema" is tagged as "embedded-only" so does not have its own datastore table.
	18/02/01 19:56:27 INFO Datastore: The class "org.apache.hadoop.hive.metastore.model.MOrder" is tagged as "embedded-only" so does not have its own datastore table.
	18/02/01 19:56:27 INFO Query: Reading in results for query "org.datanucleus.store.rdbms.query.SQLQuery@0" since the connection used is closing
	18/02/01 19:56:27 INFO MetaStoreDirectSql: Using direct SQL, underlying DB is DERBY
	18/02/01 19:56:27 INFO ObjectStore: Initialized ObjectStore
	18/02/01 19:56:28 INFO HiveMetaStore: Added admin role in metastore
	18/02/01 19:56:28 INFO HiveMetaStore: Added public role in metastore
	18/02/01 19:56:28 INFO HiveMetaStore: No user is added in admin role, since config is empty
	18/02/01 19:56:28 INFO HiveMetaStore: 0: get_all_databases
	18/02/01 19:56:28 INFO audit: ugi=root	ip=unknown-ip-addr	cmd=get_all_databases	
	18/02/01 19:56:28 INFO HiveMetaStore: 0: get_functions: db=default pat=*
	18/02/01 19:56:28 INFO audit: ugi=root	ip=unknown-ip-addr	cmd=get_functions: db=default pat=*	
	18/02/01 19:56:28 INFO Datastore: The class "org.apache.hadoop.hive.metastore.model.MResourceUri" is tagged as "embedded-only" so does not have its own datastore table.
	18/02/01 19:56:28 INFO SessionState: Created local directory: /tmp/20ad95fe-912f-4bcc-8b95-87ade33c438c_resources
	18/02/01 19:56:28 INFO SessionState: Created HDFS directory: /tmp/hive/root/20ad95fe-912f-4bcc-8b95-87ade33c438c
	18/02/01 19:56:28 INFO SessionState: Created local directory: /tmp/root/20ad95fe-912f-4bcc-8b95-87ade33c438c
	18/02/01 19:56:28 INFO SessionState: Created HDFS directory: /tmp/hive/root/20ad95fe-912f-4bcc-8b95-87ade33c438c/_tmp_space.db
	18/02/01 19:56:28 INFO HiveClientImpl: Warehouse location for Hive client (version 1.2.1) is /xubo/git/carbondata/integration/spark-common/target/warehouse
	18/02/01 19:56:28 INFO HiveMetaStore: 0: get_database: default
	18/02/01 19:56:28 INFO audit: ugi=root	ip=unknown-ip-addr	cmd=get_database: default	
	18/02/01 19:56:28 INFO HiveMetaStore: 0: get_database: global_temp
	18/02/01 19:56:28 INFO audit: ugi=root	ip=unknown-ip-addr	cmd=get_database: global_temp	
	18/02/01 19:56:28 WARN ObjectStore: Failed to get database global_temp, returning NoSuchObjectException
	18/02/01 19:56:28 INFO SessionState: Created local directory: /tmp/208a2c8c-9cd2-49e7-a653-942820aefd3a_resources
	18/02/01 19:56:28 INFO SessionState: Created HDFS directory: /tmp/hive/root/208a2c8c-9cd2-49e7-a653-942820aefd3a
	18/02/01 19:56:28 INFO SessionState: Created local directory: /tmp/root/208a2c8c-9cd2-49e7-a653-942820aefd3a
	18/02/01 19:56:28 INFO SessionState: Created HDFS directory: /tmp/hive/root/208a2c8c-9cd2-49e7-a653-942820aefd3a/_tmp_space.db
	18/02/01 19:56:28 INFO HiveClientImpl: Warehouse location for Hive client (version 1.2.1) is /xubo/git/carbondata/integration/spark-common/target/warehouse
	18/02/01 19:56:29 INFO StateStoreCoordinatorRef: Registered StateStoreCoordinator endpoint
	18/02/01 19:56:29 AUDIT CarbonMetaStoreFactory: [hadoop][root][Thread-1]File based carbon metastore is enabled
	18/02/01 19:56:30 AUDIT CarbonCreateTableCommand: [hadoop][root][Thread-1]Creating Table with Database name [default] and Table name [preaggmain]
	18/02/01 19:56:31 AUDIT CarbonCreateTableCommand: [hadoop][root][Thread-1]Table created with Database name [default] and Table name [preaggmain]
	18/02/01 19:56:31 AUDIT CarbonCreateTableCommand: [hadoop][root][Thread-1]Creating Table with Database name [default] and Table name [preaggmain1]
	18/02/01 19:56:31 AUDIT CarbonCreateTableCommand: [hadoop][root][Thread-1]Table created with Database name [default] and Table name [preaggmain1]
	18/02/01 19:56:31 AUDIT CarbonCreateTableCommand: [hadoop][root][Thread-1]Creating Table with Database name [default] and Table name [preaggmain2]
	18/02/01 19:56:32 AUDIT CarbonCreateTableCommand: [hadoop][root][Thread-1]Table created with Database name [default] and Table name [preaggmain2]
	18/02/01 19:56:32 AUDIT CarbonCreateTableCommand: [hadoop][root][Thread-1]Creating Table with Database name [default] and Table name [maintable]
	18/02/01 19:56:32 AUDIT CarbonCreateTableCommand: [hadoop][root][Thread-1]Table created with Database name [default] and Table name [maintable]
	18/02/01 19:56:33 AUDIT CarbonCreateTableCommand: [hadoop][root][Thread-1]Creating Table with Database name [default] and Table name [preaggmain_preagg2]
	18/02/01 19:56:33 AUDIT CarbonCreateTableCommand: [hadoop][root][Thread-1]Table created with Database name [default] and Table name [preaggmain_preagg2]
	18/02/01 19:56:33 AUDIT CarbonCreateDataMapCommand: [hadoop][root][Thread-1]DataMap preagg2 successfully added to Table PreAggMain
	+--------------------+--------------------+--------------------+
	|            col_name|           data_type|             comment|
	+--------------------+--------------------+--------------------+
	|preaggmain_a     ...|string           ...|KEY COLUMN,null  ...|
	|preaggmain_b_sum ...|double           ...|MEASURE,null     ...|
	|                 ...|                 ...|                 ...|
	|##Detailed Table ...|                 ...|                 ...|
	|Database Name    ...|default          ...|                 ...|
	|Table Name       ...|preaggmain_preagg...|                 ...|
	|CARBON Store Path...|/xubo/git/carbond...|                 ...|
	|Comment          ...|                 ...|                 ...|
	|Table Block Size ...|1024 MB          ...|                 ...|
	|Table Data Size  ...|0                ...|                 ...|
	|Table Index Size ...|0                ...|                 ...|
	|Last Update Time ...|0                ...|                 ...|
	|SORT_SCOPE       ...|LOCAL_SORT       ...|LOCAL_SORT       ...|
	|Streaming        ...|false            ...|                 ...|
	|                 ...|                 ...|                 ...|
	|##Detailed Column...|                 ...|                 ...|
	|ADAPTIVE         ...|                 ...|                 ...|
	|SORT_COLUMNS     ...|preaggmain_a     ...|                 ...|
	+--------------------+--------------------+--------------------+
	
	+------------+----------------+
	|preaggmain_a|preaggmain_b_sum|
	+------------+----------------+
	+------------+----------------+
	
	
	cannot resolve '`a1`' given input columns: [preaggmain_a, preaggmain_b_sum]; line 1 pos 7;
	'Project ['a1]
	+- SubqueryAlias preaggmain_preagg2
	   +- Relation[preaggmain_a#101,preaggmain_b_sum#102] CarbonDatasourceHadoopRelation [ Database name :default, Table name :preaggmain_preagg2, Schema :Some(StructType(StructField(preaggmain_a,StringType,true), StructField(preaggmain_b_sum,DoubleType,true))) ]
	
	org.apache.spark.sql.AnalysisException: cannot resolve '`a1`' given input columns: [preaggmain_a, preaggmain_b_sum]; line 1 pos 7;
	'Project ['a1]
	+- SubqueryAlias preaggmain_preagg2
	   +- Relation[preaggmain_a#101,preaggmain_b_sum#102] CarbonDatasourceHadoopRelation [ Database name :default, Table name :preaggmain_preagg2, Schema :Some(StructType(StructField(preaggmain_a,StringType,true), StructField(preaggmain_b_sum,DoubleType,true))) ]
	
		at org.apache.spark.sql.catalyst.analysis.package$AnalysisErrorAt.failAnalysis(package.scala:42)
		at org.apache.spark.sql.catalyst.analysis.CheckAnalysis$$anonfun$checkAnalysis$1$$anonfun$apply$2.applyOrElse(CheckAnalysis.scala:88)
		at org.apache.spark.sql.catalyst.analysis.CheckAnalysis$$anonfun$checkAnalysis$1$$anonfun$apply$2.applyOrElse(CheckAnalysis.scala:85)
		at org.apache.spark.sql.catalyst.trees.TreeNode$$anonfun$transformUp$1.apply(TreeNode.scala:289)
		at org.apache.spark.sql.catalyst.trees.TreeNode$$anonfun$transformUp$1.apply(TreeNode.scala:289)
		at org.apache.spark.sql.catalyst.trees.CurrentOrigin$.withOrigin(TreeNode.scala:70)
		at org.apache.spark.sql.catalyst.trees.TreeNode.transformUp(TreeNode.scala:288)
		at org.apache.spark.sql.catalyst.plans.QueryPlan$$anonfun$transformExpressionsUp$1.apply(QueryPlan.scala:268)
		at org.apache.spark.sql.catalyst.plans.QueryPlan$$anonfun$transformExpressionsUp$1.apply(QueryPlan.scala:268)
		at org.apache.spark.sql.catalyst.plans.QueryPlan.transformExpression$1(QueryPlan.scala:279)
		at org.apache.spark.sql.catalyst.plans.QueryPlan.org$apache$spark$sql$catalyst$plans$QueryPlan$$recursiveTransform$1(QueryPlan.scala:289)
		at org.apache.spark.sql.catalyst.plans.QueryPlan$$anonfun$org$apache$spark$sql$catalyst$plans$QueryPlan$$recursiveTransform$1$1.apply(QueryPlan.scala:293)
		at scala.collection.TraversableLike$$anonfun$map$1.apply(TraversableLike.scala:234)
		at scala.collection.TraversableLike$$anonfun$map$1.apply(TraversableLike.scala:234)
		at scala.collection.immutable.List.foreach(List.scala:381)
		at scala.collection.TraversableLike$class.map(TraversableLike.scala:234)
		at scala.collection.immutable.List.map(List.scala:285)
		at org.apache.spark.sql.catalyst.plans.QueryPlan.org$apache$spark$sql$catalyst$plans$QueryPlan$$recursiveTransform$1(QueryPlan.scala:293)
		at org.apache.spark.sql.catalyst.plans.QueryPlan$$anonfun$6.apply(QueryPlan.scala:298)
		at org.apache.spark.sql.catalyst.trees.TreeNode.mapProductIterator(TreeNode.scala:187)
		at org.apache.spark.sql.catalyst.plans.QueryPlan.mapExpressions(QueryPlan.scala:298)
		at org.apache.spark.sql.catalyst.plans.QueryPlan.transformExpressionsUp(QueryPlan.scala:268)
		at org.apache.spark.sql.catalyst.analysis.CheckAnalysis$$anonfun$checkAnalysis$1.apply(CheckAnalysis.scala:85)
		at org.apache.spark.sql.catalyst.analysis.CheckAnalysis$$anonfun$checkAnalysis$1.apply(CheckAnalysis.scala:78)
		at org.apache.spark.sql.catalyst.trees.TreeNode.foreachUp(TreeNode.scala:127)
		at org.apache.spark.sql.catalyst.analysis.CheckAnalysis$class.checkAnalysis(CheckAnalysis.scala:78)
		at org.apache.spark.sql.catalyst.analysis.Analyzer.checkAnalysis(Analyzer.scala:91)
		at org.apache.spark.sql.execution.QueryExecution.assertAnalyzed(QueryExecution.scala:52)
		at org.apache.spark.sql.Dataset$.ofRows(Dataset.scala:67)
		at org.apache.spark.sql.SparkSession.sql(SparkSession.scala:632)
		at org.apache.spark.sql.test.Spark2TestQueryExecutor.sql(Spark2TestQueryExecutor.scala:35)
		at org.apache.spark.sql.test.util.QueryTest.sql(QueryTest.scala:110)
		at org.apache.carbondata.integration.spark.testsuite.preaggregate.TestPreAggCreateCommand$$anonfun$2.apply$mcV$sp(TestPreAggCreateCommand.scala:63)
		at org.apache.carbondata.integration.spark.testsuite.preaggregate.TestPreAggCreateCommand$$anonfun$2.apply(TestPreAggCreateCommand.scala:56)
		at org.apache.carbondata.integration.spark.testsuite.preaggregate.TestPreAggCreateCommand$$anonfun$2.apply(TestPreAggCreateCommand.scala:56)
		at org.scalatest.Transformer$$anonfun$apply$1.apply$mcV$sp(Transformer.scala:22)
		at org.scalatest.OutcomeOf$class.outcomeOf(OutcomeOf.scala:85)
		at org.scalatest.OutcomeOf$.outcomeOf(OutcomeOf.scala:104)
		at org.scalatest.Transformer.apply(Transformer.scala:22)
		at org.scalatest.Transformer.apply(Transformer.scala:20)
		at org.scalatest.FunSuiteLike$$anon$1.apply(FunSuiteLike.scala:166)
		at org.apache.spark.sql.test.util.CarbonFunSuite.withFixture(CarbonFunSuite.scala:41)
		at org.scalatest.FunSuiteLike$class.invokeWithFixture$1(FunSuiteLike.scala:163)
		at org.scalatest.FunSuiteLike$$anonfun$runTest$1.apply(FunSuiteLike.scala:175)
		at org.scalatest.FunSuiteLike$$anonfun$runTest$1.apply(FunSuiteLike.scala:175)
		at org.scalatest.SuperEngine.runTestImpl(Engine.scala:306)
		at org.scalatest.FunSuiteLike$class.runTest(FunSuiteLike.scala:175)
		at org.scalatest.FunSuite.runTest(FunSuite.scala:1555)
		at org.scalatest.FunSuiteLike$$anonfun$runTests$1.apply(FunSuiteLike.scala:208)
		at org.scalatest.FunSuiteLike$$anonfun$runTests$1.apply(FunSuiteLike.scala:208)
		at org.scalatest.SuperEngine$$anonfun$traverseSubNodes$1$1.apply(Engine.scala:413)
		at org.scalatest.SuperEngine$$anonfun$traverseSubNodes$1$1.apply(Engine.scala:401)
		at scala.collection.immutable.List.foreach(List.scala:381)
		at org.scalatest.SuperEngine.traverseSubNodes$1(Engine.scala:401)
		at org.scalatest.SuperEngine.org$scalatest$SuperEngine$$runTestsInBranch(Engine.scala:396)
		at org.scalatest.SuperEngine.runTestsImpl(Engine.scala:483)
		at org.scalatest.FunSuiteLike$class.runTests(FunSuiteLike.scala:208)
		at org.scalatest.FunSuite.runTests(FunSuite.scala:1555)
		at org.scalatest.Suite$class.run(Suite.scala:1424)
		at org.scalatest.FunSuite.org$scalatest$FunSuiteLike$$super$run(FunSuite.scala:1555)
		at org.scalatest.FunSuiteLike$$anonfun$run$1.apply(FunSuiteLike.scala:212)
		at org.scalatest.FunSuiteLike$$anonfun$run$1.apply(FunSuiteLike.scala:212)
		at org.scalatest.SuperEngine.runImpl(Engine.scala:545)
		at org.scalatest.FunSuiteLike$class.run(FunSuiteLike.scala:212)
		at org.apache.carbondata.integration.spark.testsuite.preaggregate.TestPreAggCreateCommand.org$scalatest$BeforeAndAfterAll$$super$run(TestPreAggCreateCommand.scala:34)
		at org.scalatest.BeforeAndAfterAll$class.liftedTree1$1(BeforeAndAfterAll.scala:257)
		at org.scalatest.BeforeAndAfterAll$class.run(BeforeAndAfterAll.scala:256)
		at org.apache.carbondata.integration.spark.testsuite.preaggregate.TestPreAggCreateCommand.run(TestPreAggCreateCommand.scala:34)
		at org.scalatest.tools.SuiteRunner.run(SuiteRunner.scala:55)
		at org.scalatest.tools.Runner$$anonfun$doRunRunRunDaDoRunRun$3.apply(Runner.scala:2563)
		at org.scalatest.tools.Runner$$anonfun$doRunRunRunDaDoRunRun$3.apply(Runner.scala:2557)
		at scala.collection.immutable.List.foreach(List.scala:381)
		at org.scalatest.tools.Runner$.doRunRunRunDaDoRunRun(Runner.scala:2557)
		at org.scalatest.tools.Runner$$anonfun$runOptionallyWithPassFailReporter$2.apply(Runner.scala:1044)
		at org.scalatest.tools.Runner$$anonfun$runOptionallyWithPassFailReporter$2.apply(Runner.scala:1043)
		at org.scalatest.tools.Runner$.withClassLoaderAndDispatchReporter(Runner.scala:2722)
		at org.scalatest.tools.Runner$.runOptionallyWithPassFailReporter(Runner.scala:1043)
		at org.scalatest.tools.Runner$.run(Runner.scala:883)
		at org.scalatest.tools.Runner.run(Runner.scala)
		at org.jetbrains.plugins.scala.testingSupport.scalaTest.ScalaTestRunner.runScalaTest2(ScalaTestRunner.java:138)
		at org.jetbrains.plugins.scala.testingSupport.scalaTest.ScalaTestRunner.main(ScalaTestRunner.java:28)
	
	18/02/01 19:56:35 AUDIT CarbonDropTableCommand: [hadoop][root][Thread-1]Deleting table [maintable] under database [default]
	18/02/01 19:56:35 ERROR CarbonProperties: ScalaTest-run Configured value for property carbon.number.of.cores.while.loading is wrong. Falling back to the default value 2
	18/02/01 19:56:35 ERROR CarbonProperties: ScalaTest-run Configured value for property carbon.number.of.cores.while.loading is wrong. Falling back to the default value 2
	18/02/01 19:56:36 AUDIT CarbonDropTableCommand: [hadoop][root][Thread-1]Deleted table [maintable] under database [default]
	18/02/01 19:56:36 AUDIT CarbonDropTableCommand: [hadoop][root][Thread-1]Deleting table [preaggmain] under database [default]
	18/02/01 19:56:36 AUDIT CarbonDropTableCommand: [hadoop][root][Thread-1]Deleting table [preaggmain_preagg2] under database [default]
	18/02/01 19:56:36 AUDIT CarbonDropTableCommand: [hadoop][root][Thread-1]Deleted table [preaggmain_preagg2] under database [default]
	18/02/01 19:56:36 AUDIT CarbonDropTableCommand: [hadoop][root][Thread-1]Deleted table [preaggmain] under database [default]
	18/02/01 19:56:36 AUDIT CarbonDropTableCommand: [hadoop][root][Thread-1]Deleting table [preaggmain1] under database [default]
	18/02/01 19:56:36 AUDIT CarbonDropTableCommand: [hadoop][root][Thread-1]Deleted table [preaggmain1] under database [default]
	18/02/01 19:56:36 AUDIT CarbonDropTableCommand: [hadoop][root][Thread-1]Deleting table [preaggmain2] under database [default]
	18/02/01 19:56:36 AUDIT CarbonDropTableCommand: [hadoop][root][Thread-1]Deleted table [preaggmain2] under database [default]
	
	Process finished with exit code 0
