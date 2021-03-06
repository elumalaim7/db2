## ./db2_deinstall -r ../db2un.rsp -b /opt/ibm/db2/V11.1/

# https://www.ibm.com/docs/en/db2/11.1?topic=file-sample-response-files-linux-unix-windows

# https://www.ibm.com/docs/en/db2/11.1?topic=SSEPGG_11.1.0/com.ibm.db2.luw.apdv.sample.doc/doc/ese_UNIX/s-db2un.html 

** ============================================================================
**
** Sample response file for db2 uninstall
** ----------------------------------
**
** To select features to uninstall, uncomment the corresponding keywords.
** Comments are made by placing either an asterisk (*) or a number sign (#) at
** the start of a line, or by placing ** or ## after the start of a line to
** comment out the rest of that line.
**
** Refer to the DB2 Information Center at:
** https://www-01.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.db2.luw.kc.doc/welcome.html.
**
** ============================================================================


** Select product(s) to uninstall
** ------------------------------
*REMOVE_PROD              = ALL                                 ** Warning: All DB2 products in the current DB2 copy will be removed. The DB2 products in other copies are not affected
*REMOVE_PROD              = CLIENT
*REMOVE_PROD              = CONNECT_SERVER
*REMOVE_PROD              = DB2_SERVER_EDITION
*REMOVE_PROD              = EXPRESS_C
*REMOVE_PROD              = EXPRESS_EDITION
*REMOVE_PROD              = II_NONRELATIONAL_WRAPPERS
*REMOVE_PROD              = II_RELATIONAL_WRAPPERS
*REMOVE_PROD              = RUNTIME_CLIENT

** Select component(s) to uninstall
** --------------------------------

** DB2 Advanced Copy Services help protect mission-critical data that requires
** 24x7 availability. It offers an integrated solution designed to implement
** high-efficiency backup and restore processes and helps eliminate
** backup-related performance issues.
*REMOVE_COMP              = ACS                                 ** Integrated Flash Copy Support

** The base application development tools component contains tools and files
** (including header files, libraries, and a precompiler) that are needed for
** developing applications that work with DB2.
*REMOVE_COMP              = APPLICATION_DEVELOPMENT_TOOLS       ** Base application development tools

** This component allows support for new data sources to be added to your
** installation through product fix packs and point releases.
*REMOVE_COMP              = CUSTOM_DATA_SOURCE_SUPPORT          ** Custom data source support

** Provides federated support required to access DB2 for iSeries and DB2 for
** z/OS and OS/390 data sources.
*REMOVE_COMP              = DB2_DATA_SOURCE_SUPPORT             ** DB2 data source support

** Sample database source provides sample data and metadata that allows you to
** create a sample database using the First Steps application.
*REMOVE_COMP              = DB2_SAMPLE_DATABASE                 ** Sample database source

** DB2 Update Service is a web tool that lists the available DB2 product
** updates, and provides details about product updates.  The DB2 Update Service
** requires an internet connection.
*REMOVE_COMP              = DB2_UPDATE_SERVICE                  ** DB2 Update Service

** First Steps is a graphical tool that will help familiarize you with DB2
** features and functions.
*REMOVE_COMP              = FIRST_STEPS                         ** First Steps

** A scalable, highly-available, high performance file system optimized for
** multi-petabyte storage management.
*REMOVE_COMP              = GPFS                                ** General Parallel File System (GPFS)

** Guardium Installation Manager Client component will place the Guardium
** Installation Manager(GIM) Client under DB2 Install Path.
*REMOVE_COMP              = GUARDIUM_INST_MNGR_CLIENT           ** Guardium Installation Manager Client

** Application data sources use an application to access the underlying
** nonrelational data.	The raw data can be in a number of standard and
** nonstandard formats.
*REMOVE_COMP              = IINR_APPLICATIONS_WRAPPER           ** Application data sources

** Scientific data sources are developed exclusively for the life sciences
** industry, such as those containing genomic, proteomic, bioinformatic, and
** cheminformatic information.
*REMOVE_COMP              = IINR_SCIENTIFIC_WRAPPER             ** Scientific Data Sources

** Structured file data sources contain nonrelational data stored in files with
** a defined, repeatable structure.
*REMOVE_COMP              = IINR_STRUCTURED_FILES_WRAPPER       ** Structured file data sources

** Enables users and applications to submit distributed requests for data
** managed by Informix systems.
*REMOVE_COMP              = INFORMIX_DATA_SOURCE_SUPPORT        ** Informix data source support

** The DB2 Instance Setup wizard is a Java-based tool you can use to set up
** instances on your computer after installing DB2.
*REMOVE_COMP              = INSTANCE_SETUP_SUPPORT              ** DB2 Instance Setup wizard

** Enables users and applications to submit distributed requests through JDBC
** for data managed by DBMS.
*REMOVE_COMP              = JDBC_DATA_SOURCE_SUPPORT            ** JDBC data source support

** The IBM Software Development Kit (SDK) for Java(TM) provides the support
** required to use Java-based tools, and to create and run Java applications,
** including stored procedures and user-defined functions.
*REMOVE_COMP              = JDK                                 ** IBM Software Development Kit (SDK) for Java(TM)

** LDAP Exploitation allows DB2 to use an LDAP directory to store database
** directory and configuration information.
*REMOVE_COMP              = LDAP_EXPLOITATION                   ** DB2 LDAP support

** Enables users and applications to submit distributed requests for data
** stored in any data source that supports ODBC and X/Open CLI compliant
** drivers.
*REMOVE_COMP              = ODBC_DATA_SOURCE_SUPPORT            ** ODBC data source support

** Enables users and applications to submit distributed requests for data
** managed by Oracle systems.
*REMOVE_COMP              = ORACLE_DATA_SOURCE_SUPPORT          ** Oracle data source support

** The IBM DB2 pureScale Feature provides clustering technology to DB2 products
** on distributed platforms.
*REMOVE_COMP              = PURESCALE                           ** IBM DB2 pureScale Feature

** The Replication tools help you administer, operate, and monitor SQL and Q
** replication.
*REMOVE_COMP              = REPL_CLIENT                         ** Replication tools

** Spatial Extender client contains the support required for communicating with
** a Spatial Extender server.
*REMOVE_COMP              = SPATIAL_EXTENDER_CLIENT_SUPPORT     ** Spatial Extender client

** Provides Spatial Extender support for the DB2 server, providing the storing
** and query of geographical information in DB2 tables.
*REMOVE_COMP              = SPATIAL_EXTENDER_SERVER_SUPPORT     ** Spatial Extender server support

** Enables users and applications to submit distributed requests for data
** managed by Microsoft SQL Server systems.
*REMOVE_COMP              = SQL_SERVER_DATA_SOURCE_SUPPORT      ** SQL Server data source support

** Enables users and applications to submit distributed requests for data
** managed by Sybase systems.
*REMOVE_COMP              = SYBASE_DATA_SOURCE_SUPPORT          ** Sybase data source support

** Enables users and applications to submit distributed requests for data
** managed by Teradata systems.
*REMOVE_COMP              = TERADATA_DATA_SOURCE_SUPPORT        ** Teradata data source support

** The DB2 Text Search component, powered by OmniFind, delivers an integrated,
** high quality and scalable search technology in DB2 databases.
*REMOVE_COMP              = TEXT_SEARCH                         ** DB2 Text Search

** IBM Tivoli System Automation for Multiplatforms provides high availability
** and disaster recovery capabilities for AIX, Linux, Solaris SPARC, and
** Windows.
*REMOVE_COMP              = TSAMP                               ** Tivoli SA MP


** IBM Tivoli System Automation for Multiplatforms Base Component The
** REMOVE_TSAMP keyword will only be looked at when a DB2 copy is removed. To
** remove a DB2 copy, specifiy each product or uncomment REMOVE_PROD=ALL.
** --------------------------------------------------------------------------
*REMOVE_TSAMP             = YES


** Select language(s) to uninstall
** -------------------------------
*REMOVE_LANG              = ALL             ** All non-English languages in the current copy will be removed.
*REMOVE_LANG              = BG              ** Bulgarian (bg_BG)
*REMOVE_LANG              = BR              ** Portuguese - Brazil (pt_BR)
*REMOVE_LANG              = CN              ** Simplified Chinese (zh_CN)
*REMOVE_LANG              = CZ              ** Czech (cs_CZ)
*REMOVE_LANG              = DE              ** German (de_DE)
*REMOVE_LANG              = ES              ** Spanish (es_ES)
*REMOVE_LANG              = FR              ** French (fr_FR)
*REMOVE_LANG              = HR              ** Croatian (hr_HR)
*REMOVE_LANG              = HU              ** Hungarian (hu_HU)
*REMOVE_LANG              = IT              ** Italian (it_IT)
*REMOVE_LANG              = JP              ** Japanese (ja_JP)
*REMOVE_LANG              = KR              ** Korean (ko_KR)
*REMOVE_LANG              = PL              ** Polish (pl_PL)
*REMOVE_LANG              = RO              ** Romanian (ro_RO)
*REMOVE_LANG              = RU              ** Russian (ru_RU)
*REMOVE_LANG              = SK              ** Slovakian (sk_SK)
*REMOVE_LANG              = SL              ** Slovenian (sl_SI)
*REMOVE_LANG              = TW              ** Traditional Chinese (zh_TW)
