# ./db2setup -r responsefile_directory/response_file

# https://www.ibm.com/docs/en/db2/11.1?topic=SSEPGG_11.1.0/com.ibm.db2.luw.apdv.sample.doc/doc/ese_UNIX/s-db2client.html

# https://www.ibm.com/docs/en/db2/11.1?topic=file-sample-response-files-linux-unix-windows

** ============================================================================
**
** Sample response file for IBM DB2
** --------------------------------
** To select features and settings to install, uncomment the corresponding
** keywords and specify values for those keywords.  You do not need to select
** features if you select the TYPICAL or COMPACT installation options.
**
** Comments are made by placing either an asterisk (*) or a hash symbol (#) at
** the start of a line, or by placing ** or ## after the start of a line to
** comment out the rest of that line.
** All keywords that are currently uncommented (not preceded by * or #) are
** mandatory and must be assigned values for the installation to continue.
** All other keywords are optional. If optional keywords are not specified,
** the installation will proceed using default values. Lines that start out
** with two asterisks are documentation and should not be enabled.
** For more information on configuration parameters, see "Configuring the DB2 database manager with 
** configuration parameters" in the DB2 Information Center.
**
** For more information on DB2 registry and environment variables, and configuration 
** parameters, see "DB2 registry and environment variables" in the DB2 Information Center.
**
** For more information on how to perform a response file installation, see 
** "Response file considerations" in the DB2 Information Center.
**
** Refer to the DB2 Information Center at:
** https://www-01.ibm.com/support/knowledgecenter/SSEPGG_11.1.0/com.ibm.db2.luw.kc.doc/welcome.html
**
** ============================================================================
** General Options
** ---------------

** Only one product can be specified for the following PROD keyword. Specifying
** multiple products in an installation is not supported.
PROD                      = CLIENT

** The FILE keyword determines the base installation path. If you specify a
** path that does not yet have this product, this will install a new copy.  If
** you specify a path that has this product, this will be considered an
** existing installation intended to install additional functionality.	This is
** a mandatory keyword for root installation. Remove this keyword for non-root
** installation. If not removed, its value must be $HOME/sqllib where $HOME
** represents the HOME directory of the non-root user ID that owns the non-root
** installation.
FILE                      = /opt/ibm/db2/V11.1

** Modify the value of the following LIC_AGREEMENT keyword to indicate that you
** have read and agreed to the license agreement file in the db2/license
** directory on the CD.
LIC_AGREEMENT             = DECLINE         ** ACCEPT or DECLINE

** If an interactive type is set, db2setup will prompt for CD locations and
** give feedback as to progress, otherwise nothing will be displayed until the
** installation is complete.
*INTERACTIVE              = NONE            ** NONE, YES, MACHINE

** The PACKAGE_LOCATION keyword is used only when the NLPACK is not available
** and any national languages are to be installed. This keyword specifies the
** location of the NLPACK.
*PACKAGE_LOCATION         =                 ** Any valid path

** The CONFIG_ONLY keyword is used to specify that the response file is being
** used for creating or configuring an instance, and nothing is to be
** installed. This keyword must be set to YES if a response file is used with
** db2isetup.
*CONFIG_ONLY              =                 ** YES or NO

** INSTALL_TYPE keyword is used to select the installation type. If you specify
** a TYPICAL or a COMPACT install type, no COMP keywords are required. In this
** case the installer will select the appropriate components for you.  All COMP
** keywords are ignored by the installer unless the INSTALL_TYPE is set  to
** CUSTOM. If you select the CUSTOM install type, then ensure that you enable 
** all of the COMP keywords that are required for your database environment.
** 
** Note: The install type is not related to the language selection.
** ----------------------------------------------------------------------------
INSTALL_TYPE              = TYPICAL         ** TYPICAL, COMPACT, CUSTOM

** The following components are part of all TYPICAL installations. If you
** perform a typical installation, all of these components will be installed on
** your computer.
** ----------------------------------------------------------------------------

** DB2 Update Service is a web tool that lists the available DB2 product
** updates, and provides details about product updates.  The DB2 Update Service
** requires an internet connection.
*COMP                     = DB2_UPDATE_SERVICE                  ** DB2 Update Service

** First Steps is a graphical tool that will help familiarize you with DB2
** features and functions.
*COMP                     = FIRST_STEPS                         ** First Steps

** The DB2 Instance Setup wizard is a Java-based tool you can use to set up
** instances on your computer after installing DB2.
*COMP                     = INSTANCE_SETUP_SUPPORT              ** DB2 Instance Setup wizard

** The IBM Software Development Kit (SDK) for Java(TM) provides the support
** required to use Java-based tools, and to create and run Java applications,
** including stored procedures and user-defined functions.
*COMP                     = JDK                                 ** IBM Software Development Kit (SDK) for Java(TM)

** LDAP Exploitation allows DB2 to use an LDAP directory to store database
** directory and configuration information.
*COMP                     = LDAP_EXPLOITATION                   ** DB2 LDAP support

** The Replication tools help you administer, operate, and monitor SQL and Q
** replication.
*COMP                     = REPL_CLIENT                         ** Replication tools


** The following components are not part of TYPICAL installations, and thus can
** only be installed through CUSTOM installs.
** ----------------------------------------------------------------------------

** The base application development tools component contains tools and files
** (including header files, libraries, and a precompiler) that are needed for
** developing applications that work with DB2.
*COMP                     = APPLICATION_DEVELOPMENT_TOOLS       ** Base application development tools

** Spatial Extender client contains the support required for communicating with
** a Spatial Extender server.
*COMP                     = SPATIAL_EXTENDER_CLIENT_SUPPORT     ** Spatial Extender client

** The following languages apply to all translated components. Enable the
** language(s) you want installed. If you do not enable any language keywords,
** then the English language (EN) will still be installed by default.
** ---------------------------------------------------------------------------
*LANG                     = BR              ** Portuguese - Brazil (pt_BR)
*LANG                     = CN              ** Simplified Chinese (zh_CN)
*LANG                     = DE              ** German (de_DE)
*LANG                     = ES              ** Spanish (es_ES)
*LANG                     = FR              ** French (fr_FR)
*LANG                     = IT              ** Italian (it_IT)
*LANG                     = JP              ** Japanese (ja_JP)
*LANG                     = KR              ** Korean (ko_KR)
*LANG                     = TW              ** Traditional Chinese (zh_TW)


** (Valid for non-root upgrade only) Upgrade Older Release
** -------------------------------------------------------
** Specify whether you want to upgrade any previous versions of the product. 
** Specifying this keyword will remove any previous version and upgrade any
** settings to the new installation.  Be aware that during upgrade of the
** current copy, only the product specified in the response file will be
** installed. Other previously installed products need to be upgraded
** separately following this upgrade.
*UPGRADE_PRIOR_VERSIONS   = FALSE           ** TRUE or FALSE

** Instance Creation Settings
** --------------------------
** User IDs managed by NIS/NIS+ are not supported. If an existing user ID is
** used, make sure it is not locked and its password has not expired.

** Prefix name of one instance set. To create or update an instance, one set of
** instance keywords must be specified. The instance set is comprised of the
** identifying prefix value for the INSTANCE key followed by the keys that are
** prefixed by the specified INSTANCE prefix value.
INSTANCE                  = DB2_INST        ** char(8)  no spaces

** Real name of the instance, and also the user ID of instance owner. It can be
** different from the value of the INSTANCE keyword. If an existing ID is
** specified for the instance's NAME keyword, make sure the user ID exists on
** all the participating hosts with the same UID, GID, corresponding group
** name, user name and user home directory. Ensure that existing user IDs are
** not locked and that the password has not expired. IBM DB2 pureScale Feature
** users must specify a name that is unique across the IBM DB2 pureScale
** implementation.
DB2_INST.NAME             = db2inst1        ** char(8)  no spaces, no upper case letters

** The UID will be generated if the keyword is not specified - highly
** recommended.
*DB2_INST.UID             =                 ** Unsigned integer
DB2_INST.GROUP_NAME       = db2iadm1        ** char(30) no spaces

** Use a generated GID if no value provided - highly recommended.
*DB2_INST.GID             =                 ** Unsigned integer
DB2_INST.HOME_DIRECTORY   =                 ** char(64) no spaces. Valid for root installation only
DB2_INST.PASSWORD         = Replace with your password ** Valid for root installation only
*DB2_INST.TYPE            = CLIENT          ** CLIENT
*DB2_INST.CLIENT_IMPORT_PROFILE =           ** a full path or a file in the same directory as the response file
*DB2_INST.AUTHENTICATION  = SERVER          ** CLIENT, SERVER, or SERVER_ENCRYPT

** Text Search Configuration
** -------------------------

** Instance DBM CFG Settings
** -------------------------
*DB2_INST.CATALOG_NOAUTH  =                 ** 0, 1, YES or NO
*DB2_INST.CLUSTER_MGR     =                 ** TSA, VENDOR:
*DB2_INST.DFT_ACCOUNT_STR =                 ** BLANK or char(25)
*DB2_INST.DIAGLEVEL       =                 ** 0 - 4
*DB2_INST.DIAGPATH        =                 ** BLANK or char(215)
*DB2_INST.DIAGSIZE        =                 ** A value specified in MB and limited by the available disk space in DIAGPATH. Minimum 2 MB must be specified.
*DB2_INST.INSTANCE_MEMORY = AUTOMATIC       ** AUTOMATIC or a number in range [0, 1000000] for 32-bit and [0, 68719476736] for 64-bit
*DB2_INST.HEALTH_MON      =                 ** default is ON; ON or OFF
*DB2_INST.FED_NOAUTH      = NO              ** YES or NO, default is NO
*DB2_INST.DIR_CACHE       =                 ** YES or NO
*DB2_INST.DISCOVER        =                 ** DISABLE, KNOWN or SEARCH
*DB2_INST.DISCOVER_COMM   =                 ** BLANK or TCPIP
*DB2_INST.DISCOVER_INST   =                 ** ENABLE or DISABLE
*DB2_INST.JDK_PATH        =                 ** BLANK or char(255)
*DB2_INST.SSL_SVR_KEYDB   =                 ** BLANK or char(1023)
*DB2_INST.SSL_SVR_STASH   =                 ** BLANK or char(1023)
*DB2_INST.SSL_SVR_LABEL   =                 ** BLANK or char(1023)
*DB2_INST.SSL_SVCENAME    =                 ** BLANK or char(14)
*DB2_INST.SSL_CIPHERSPECS =                 ** BLANK or char(255)
*DB2_INST.SSL_VERSIONS    =                 ** BLANK or char(255)
*DB2_INST.SSL_CLNT_KEYDB  =                 ** BLANK or char(1023)
*DB2_INST.SSL_CLNT_STASH  =                 ** BLANK or char(1023)
*DB2_INST.ALTERNATE_AUTH_ENC =              ** NOT_SPECIFIED, AES_ONLY, AES_CMP
*DB2_INST.ROUTE_OBJ_NAME  =                 ** BLANK or char(255)
*DB2_INST.RQRIOBLK        =                 ** 4096 - 65535
*DB2_INST.SYSADM_GROUP    =                 ** BLANK or char(30)
*DB2_INST.SYSCTRL_GROUP   =                 ** BLANK or char(30)
*DB2_INST.SYSMAINT_GROUP  =                 ** BLANK or char(30)
*DB2_INST.TP_MON_NAME     =                 ** BLANK or char(19)

** Instance Profile Registry Settings
** ----------------------------------
*DB2_INST.DB2ACCOUNT      =                 ** BLANK or char(199)
*DB2_INST.DB2BQTIME       =                 ** BLANK or 1 - MAX
*DB2_INST.DB2BQTRY        =                 ** BLANK or 0 - MAX
*DB2_INST.DB2CHKPTR       =                 ** BLANK, 0, 1, YES, NO, ON, OFF, Y, N, TRUE, FALSE, T or F
*DB2_INST.DB2CLIINIPATH   =                 ** BLANK or char(260)
*DB2_INST.DB2CODEPAGE     =                 ** BLANK or 0 - MAX
*DB2_INST.DB2COUNTRY      =                 ** BLANK or 1 - 999
*DB2_INST.DB2DBDFT        =                 ** BLANK or char(8)
*DB2_INST.DB2DEFPREP      =                 ** BLANK, ALL, 0, 1, YES, NO, ON, OFF, Y, N, TRUE, FALSE, T or F
*DB2_INST.DB2INCLUDE      =                 ** BLANK or char()
*DB2_INST.DB2IQTIME       =                 ** BLANK or 1 - MAX
*DB2_INST.DB2LOCK_TO_RB   =                 ** BLANK or STATEMENT
*DB2_INST.DB2NOEXITLIST   =                 ** BLANK, 0, 1, YES, NO, ON, OFF, Y, N, TRUE, FALSE, T or F
*DB2_INST.DB2OPTIONS      =                 ** BLANK or -/+[a,c,e[c,s],n,o,p,s,t,v,w,x] and/or -[f,l,r,z]filename
*DB2_INST.DB2RQTIME       =                 ** BLANK or 1 - MAX
*DB2_INST.DB2_SET_MAX_CONTAINER_SIZE =      ** -1 (no limit) or any integer greater than 64MB
*DB2_INST.DB2_FORCE_NLS_CACHE =             ** BLANK, 0, 1, YES, NO, ON, OFF, Y, N, TRUE, FALSE, T or F
*DB2_INST.DB2INSTOWNER    =                 ** BLANK or char(30)
*DB2_INST.DB2DBMSADDR     =                 ** BLANK or char(10)
*DB2_INST.DB2_DISABLE_FLUSH_LOG =           ** BLANK or ON, OFF
*DB2_INST.DB2LOCALE       =                 ** BLANK or YES, NO
*DB2_INST.DB2NODE         =                 ** BLANK or YES NO
*DB2_INST.DB2_USE_PAGE_CONTAINER_TAG =      ** BLANK or ON
*DB2_INST.DB2TCPCONNMGRS  =                 ** BLANK or 1 - 8
*DB2_INST.DB2_PARTITIONEDLOAD_DEFAULT =     ** BLANK or YES, NO
*DB2_INST.DB2_INLIST_TO_NLJN =              ** BLANK or YES, NO
*DB2_INST.DB2_XBSA_LIBRARY =                ** BLANK or char()
*DB2_INST.DB2LDAP_SEARCH_SCOPE =            ** BLANK LOCAL DOMAIN GLOBAL
*DB2_INST.DB2ADMINSERVER  =                 ** BLANK or char(64)
*DB2_INST.DB2REMOTEPREG   =                 ** BLANK or char(64)
*DB2_INST.DB2_ANTIJOIN    =                 ** BLANK or YES, NO, EXTEND
*DB2_INST.DB2_COLLECT_TS_REC_INFO =         ** BLANK or YES, NO
*DB2_INST.DB2PROCESSORS   =                 ** BLANK or 1 - MAX
*DB2_INST.DB2ASSUMEUPDATE =                 ** BLANK or ON, OFF
*DB2_INST.DB2_SKIPDELETED =                 ** BLANK or ON, OFF
*DB2_INST.DB2_SQLROUTINE_PREPOPTS =         ** BLANK or char()
*DB2_INST.DB2_INDEX_TYPE2 =                 ** BLANK or ON, OFF
*DB2_INST.DB2_APM_PERFORMANCE =             ** BLANK or ON, OFF
*DB2_INST.DB2_FMP_COMM_HEAPSZ =             ** BLANK or 1 - MAX
*DB2_INST.DB2_EVALUNCOMMITTED =             ** BLANK or YES, NO
*DB2_INST.DB2_NO_FORK_CHECK =               ** BLANK or ON, OFF
*DB2_INST.DB2_KEEPTABLELOCK =               ** BLANK or ON, OFF
*DB2_INST.DB2GRAPHICUNICODESERVER =         ** BLANK or ON, OFF
*DB2_INST.DB2_MINIMIZE_LISTPREFETCH =       ** BLANK or YES, NO
*DB2_INST.DB2_TRUSTED_BINDIN =              ** BLANK or ON, OFF, CHECK
*DB2_INST.DB2_CLPPROMPT   =                 ** BLANK or char(99)
*DB2_INST.DB2_FORCE_APP_ON_MAX_LOG =        ** BLANK or TRUE, FALSE
*DB2_INST.DB2_CLP_EDITOR  =                 ** BLANK or char()
*DB2_INST.DB2_CLP_HISTSIZE =                ** BLANK or 1 - 500
*DB2_INST.DB2_LOAD_COPY_NO_OVERRIDE =       ** BLANK or LOCAL, DOMAIN, GLOBAL
*DB2_INST.DB2_MAX_NON_TABLE_LOCKS =         ** BLANK or 1 - MAX
*DB2_INST.DB2_USE_ALTERNATE_PAGE_CLEANING =  ** BLANK or ON, OFF
*DB2_INST.DB2_SCATTERED_IO =                ** BLANK or ON, OFF
*DB2_INST.DB2_NO_MPFA_FOR_NEW_DB =          ** BLANK or YES, NO
*DB2_INST.DB2_OBJECT_TABLE_ENTRIES =        ** BLANK or 0 - 50000
*DB2_INST.DB2_VIEW_REOPT_VALUES =           ** BLANK or YES, NO
*DB2_INST.DB2_SELUDI_COMM_BUFFER =          ** BLANK or ON, OFF
*DB2_INST.DB2_ENABLE_AUTOCONFIG_DEFAULT =   ** BLANK, YES, NO
*DB2_INST.DB2_OPT_MAX_TEMP_SIZE =           ** BLANK or 0 - MAX
*DB2_INST.DB2RCMD_LEGACY_MODE =             ** YES, ON, TRUE, 1 or NO, OFF, FALSE, 0
*DB2_INST.DB2_LARGE_PAGE_MEM =              ** *, DB
*DB2_INST.DB2_MAX_LOB_BLOCK_SIZE = 0        ** 0 - 21487483647
*DB2_INST.DB2AUTH         =                 ** BLANK or char()
*DB2_INST.DB2CONNECT_DISCONNECT_ON_INTERRUPT = NO ** YES, TRUE, 1 or NO, FALSE, 0
*DB2_INST.DB2CONNECT_ENABLE_EURO_CODEPAGE =  ** BLANK or char()
*DB2_INST.DB2FCMCOMM      = TCPIP4          ** TCPIP4 or TCPIP6
*DB2_INST.DB2FFDC         =                 ** BLANK, ON, CORE:OFF
*DB2_INST.DB2LOADFLAGS    =                 ** BLANK or char()
*DB2_INST.DB2TCP_CLIENT_CONTIMEOUT = 0      ** 0 - 32767
*DB2_INST.DB2TCP_CLIENT_RCVTIMEOUT = 0      ** 0 - 32767
*DB2_INST.DB2TRC_DEF_BUFFSIZE =             ** BLANK or char()
*DB2_INST.DB2YIELD        =                 ** BLANK or char()
*DB2_INST.DB2_ASYNC_IO_MAXFILOP = MAXFILOP  ** MAXFILOP - MAX
*DB2_INST.DB2_BAR_AUTONOMIC_DISABLE =       ** BLANK or char()
*DB2_INST.DB2_CONNRETRIES_INTERVAL =        ** BLANK or char()
*DB2_INST.DB2_DXX_PATHS_ALLOWED_READ =      ** BLANK or char()
*DB2_INST.DB2_DXX_PATHS_ALLOWED_WRITE =     ** BLANK or char()
*DB2_INST.DB2_HADR_BUF_SIZE = 2*LOGBUFSZ    ** BLANK or 0 - MAX
*DB2_INST.DB2_LOGGING_DETAIL =              ** BLANK or char()
*DB2_INST.DB2_MAP_XML_AS_CLOB_FOR_DLC = NO  ** YES, NO
*DB2_INST.DB2_MAX_CLIENT_CONNRETRIES =      ** BLANK or char()
*DB2_INST.DB2_MAX_INACT_STMTS =             ** 0 - 4294967296
*DB2_INST.DB2_MDC_ROLLOUT = IMMEDIATE       ** DEFER, IMMEDIATE or OFF
*DB2_INST.DB2_MINIMUM_CLIENT_LEVEL =        ** BLANK or char()
*DB2_INST.DB2_NUM_CKPW_DAEMONS = 3          ** 0 - 100
*DB2_INST.DB2_RESOURCE_POLICY =             ** valid path to configuration file
*DB2_INST.DB2_SKIPINSERTED = OFF            ** ON, OFF
*DB2_INST.DB2_SMS_TRUNC_TMPTABLE_THRESH =   ** -1, 0-n where n is the number of extents per container that are to be maintained
*DB2_INST.DB2_SNAPSHOT_NOAUTH =             ** BLANK or char()
*DB2_INST.DB2_TAPEMGR_TAPE_EXPIRATION =     ** BLANK or char()
*DB2_INST.DB2_UPDDBCFG_SINGLE_DBPARTITION =  ** YES, 1, TRUE or NO, 0, FALSE
*DB2_INST.DB2_USE_DB2JCCT2_JROUTINE =       ** ON, YES, 1, TRUE or OFF, NO, 0, FALSE
*DB2_INST.DB2_UTIL_MSGPATH = instanceName/tmp directory ** BLANK or char()
*DB2_INST.DB2_WORKLOAD    = Not set         ** BLANK, SAP

** 2nd (non-pureScale) Instance Creation Settings
** ----------------------------------------------
** Multiple (non-pureScale) DB2 instances can be created in the same
** installation. This section shows how to specify the 2nd instance in the rsp
** file. Note: Only a subset of the instance keywords are listed below. You can
** specify other instance related keywords similar as the 1st instance. All
** keywords in this section are commented out. By default, only one instance
** will be created during the install.

** Prefix name of this instance set. Its value is used by all keywords for the
** same instance.
*INSTANCE                 = DB2_INS2        ** char(8) no spaces
*DB2_INS2.NAME            = db2inst2        ** char(8)  no spaces, no upper case letters

** Use a generated UID if no value provided - highly recommended.
*DB2_INS2.UID             =                 ** Unsigned integer
*DB2_INS2.GROUP_NAME      = db2iadm1        ** char(30) no spaces

** Use a generated GID if no value provided - highly recommended.
*DB2_INS2.GID             =                 ** Unsigned integer
*DB2_INS2.HOME_DIRECTORY  =                 ** char(64) no spaces. Valid for root install only
*DB2_INS2.PASSWORD        = Replace with your password ** Valid for root install only

** Global Profile Registry Settings
** --------------------------------
*DB2ACCOUNT               =                 ** BLANK or char(199)
*DB2BQTIME                =                 ** BLANK or 1 - MAX
*DB2BQTRY                 =                 ** BLANK or 0 - MAX
*DB2CHKPTR                =                 ** BLANK, 0, 1, YES, NO, ON, OFF, Y, N, TRUE, FALSE, T or F
*DB2CLIINIPATH            =                 ** BLANK or char(260)
*DB2CODEPAGE              =                 ** BLANK or 0 - MAX
*DB2COUNTRY               =                 ** BLANK or 1 - 999
*DB2DBDFT                 =                 ** BLANK or char(8)
*DB2DEFPREP               =                 ** BLANK, ALL, 0, 1, YES, NO, ON, OFF, Y, N, TRUE, FALSE, T or F
*DB2INCLUDE               =                 ** BLANK or char()
*DB2IQTIME                =                 ** BLANK or 1 - MAX
*DB2LDAPCACHE             =                 ** YES or NO
*DB2LDAPHOST              =                 ** BLANK or char()
*DB2LDAP_BASEDN           =                 ** BLANK or char()
*DB2LDAP_CLIENT_PROVIDER  =                 ** BLANK, MICROSOFT or IBM
*DB2LOCK_TO_RB            =                 ** BLANK or STATEMENT
*DB2NOEXITLIST            =                 ** BLANK, 0, 1, YES, NO, ON, OFF, Y, N, TRUE, FALSE, T or F
*DB2OPTIONS               =                 ** BLANK or -/+[a,c,e[c,s],n,o,p,s,t,v,w,x] and/or -[f,l,r,z]filename
*DB2RQTIME                =                 ** BLANK or 1 - MAX
*DB2_SET_MAX_CONTAINER_SIZE =               ** -1 (no limit) or any integer greater than 64MB
*DB2_ENABLE_LDAP          =                 ** BLANK, 0, 1, YES, NO, ON, OFF, Y, N, TRUE, FALSE, T or F
*DB2_FORCE_NLS_CACHE      =                 ** BLANK, 0, 1, YES, NO, ON, OFF, Y, N, TRUE, FALSE, T or F
*DB2INSTOWNER             =                 ** BLANK or char(30)
*DB2DBMSADDR              =                 ** BLANK or char(10)
*DB2_DISABLE_FLUSH_LOG    =                 ** BLANK or ON, OFF
*DB2LOCALE                =                 ** BLANK or YES, NO
*DB2NODE                  =                 ** BLANK or YES NO
*DB2_USE_PAGE_CONTAINER_TAG =               ** BLANK or ON
*DB2TCPCONNMGRS           =                 ** BLANK or 1 - 8
*DB2_PARTITIONEDLOAD_DEFAULT =              ** BLANK or YES, NO
*DB2_INLIST_TO_NLJN       =                 ** BLANK or YES, NO
*DB2_XBSA_LIBRARY         =                 ** BLANK or char()
*DB2LDAP_SEARCH_SCOPE     =                 ** BLANK LOCAL DOMAIN GLOBAL
*DB2ADMINSERVER           =                 ** BLANK or char(64)
*DB2REMOTEPREG            =                 ** BLANK or char(64)
*DB2_ANTIJOIN             =                 ** BLANK or YES, NO, EXTEND
*DB2_COLLECT_TS_REC_INFO  =                 ** BLANK or YES, NO
*DB2PROCESSORS            =                 ** BLANK or 1 - MAX
*DB2ASSUMEUPDATE          =                 ** BLANK or ON, OFF
*DB2_SKIPDELETED          =                 ** BLANK or ON, OFF
*DB2_SQLROUTINE_PREPOPTS  =                 ** BLANK or char()
*DB2_INDEX_TYPE2          =                 ** BLANK or ON, OFF
*DB2_APM_PERFORMANCE      =                 ** BLANK or ON, OFF
*DB2_FMP_COMM_HEAPSZ      =                 ** BLANK or 1 - MAX
*DB2_EVALUNCOMMITTED      =                 ** BLANK or YES, NO
*DB2_NO_FORK_CHECK        =                 ** BLANK or ON, OFF
*DB2_KEEPTABLELOCK        =                 ** BLANK or ON, OFF
*DB2GRAPHICUNICODESERVER  =                 ** BLANK or ON, OFF
*DB2_MINIMIZE_LISTPREFETCH =                ** BLANK or YES, NO
*DB2_TRUSTED_BINDIN       =                 ** BLANK or ON, OFF, CHECK
*DB2_CLPPROMPT            =                 ** BLANK or char(99)
*DB2_FORCE_APP_ON_MAX_LOG =                 ** BLANK or TRUE, FALSE
*DB2_CLP_EDITOR           =                 ** BLANK or char()
*DB2_CLP_HISTSIZE         =                 ** BLANK or 1 - 500
*DB2_LOAD_COPY_NO_OVERRIDE =                ** BLANK or LOCAL, DOMAIN, GLOBAL
*DB2_MAX_NON_TABLE_LOCKS  =                 ** BLANK or 1 - MAX
*DB2_USE_ALTERNATE_PAGE_CLEANING =          ** BLANK or ON, OFF
*DB2_SCATTERED_IO         =                 ** BLANK or ON, OFF
*DB2_NO_MPFA_FOR_NEW_DB   =                 ** BLANK or YES, NO
*DB2_OBJECT_TABLE_ENTRIES =                 ** BLANK or 0 - 50000
*DB2_VIEW_REOPT_VALUES    =                 ** BLANK or YES, NO
*DB2_SELUDI_COMM_BUFFER   =                 ** BLANK or ON, OFF
*DB2_ENABLE_AUTOCONFIG_DEFAULT =            ** BLANK, YES, NO
*DB2_OPT_MAX_TEMP_SIZE    =                 ** BLANK or 0 - MAX
*DB2RCMD_LEGACY_MODE      =                 ** YES, ON, TRUE, 1 or NO, OFF, FALSE, 0
*DB2_LARGE_PAGE_MEM       =                 ** *, DB
*DB2_MAX_LOB_BLOCK_SIZE   = 0               ** 0 - 21487483647
*DB2AUTH                  =                 ** BLANK or char()
*DB2CONNECT_DISCONNECT_ON_INTERRUPT = NO    ** YES, TRUE, 1 or NO, FALSE, 0
*DB2CONNECT_ENABLE_EURO_CODEPAGE =          ** BLANK or char()
*DB2FCMCOMM               = TCPIP4          ** TCPIP4 or TCPIP6
*DB2FFDC                  =                 ** BLANK, ON, CORE:OFF
*DB2LOADFLAGS             =                 ** BLANK or char()
*DB2TCP_CLIENT_CONTIMEOUT = 0               ** 0 - 32767
*DB2TCP_CLIENT_RCVTIMEOUT = 0               ** 0 - 32767
*DB2TRC_DEF_BUFFSIZE      =                 ** BLANK or char()
*DB2YIELD                 =                 ** BLANK or char()
*DB2_ASYNC_IO_MAXFILOP    = MAXFILOP        ** MAXFILOP - MAX
*DB2_BAR_AUTONOMIC_DISABLE =                ** BLANK or char()
*DB2_CONNRETRIES_INTERVAL =                 ** BLANK or char()
*DB2_DXX_PATHS_ALLOWED_READ =               ** BLANK or char()
*DB2_DXX_PATHS_ALLOWED_WRITE =              ** BLANK or char()
*DB2_HADR_BUF_SIZE        = 2*LOGBUFSZ      ** BLANK or 0 - MAX
*DB2_LOGGING_DETAIL       =                 ** BLANK or char()
*DB2_MAP_XML_AS_CLOB_FOR_DLC = NO           ** YES, NO
*DB2_MAX_CLIENT_CONNRETRIES =               ** BLANK or char()
*DB2_MAX_INACT_STMTS      =                 ** 0 - 4294967296
*DB2_MDC_ROLLOUT          = IMMEDIATE       ** DEFER, IMMEDIATE or OFF
*DB2_MINIMUM_CLIENT_LEVEL =                 ** BLANK or char()
*DB2_NUM_CKPW_DAEMONS     = 3               ** 0 - 100
*DB2_RESOURCE_POLICY      =                 ** valid path to configuration file
*DB2_SKIPINSERTED         = OFF             ** ON, OFF
*DB2_SMS_TRUNC_TMPTABLE_THRESH =            ** -1, 0-n where n is the number of extents per container that are to be maintained
*DB2_SNAPSHOT_NOAUTH      =                 ** BLANK or char()
*DB2_TAPEMGR_TAPE_EXPIRATION =              ** BLANK or char()
*DB2_UPDDBCFG_SINGLE_DBPARTITION =          ** YES, 1, TRUE or NO, 0, FALSE
*DB2_USE_DB2JCCT2_JROUTINE =                ** ON, YES, 1, TRUE or OFF, NO, 0, FALSE
*DB2_UTIL_MSGPATH         = instanceName/tmp directory ** BLANK or char()
*DB2_WORKLOAD             = Not set         ** BLANK, SAP

** Information Center Settings
** ---------------------------
** The default location for accessing the DB2 documentation is the IBM website.
** Only edit this section if you wish to access DB2 documentation from a
** different location, such as your local computer or an intranet server.

** The following DB2_DOCHOST keyword is used to specify where the Information
** Center server is installed. For example, "localhost" for the local computer.
*DB2_DOCHOST              =                 ** Any valid hostname

** The following DB2_DOCPORT keyword is used to specify the port number of the
** Information Center server.
*DB2_DOCPORT              =                 ** 1024-65535

** (Valid for root installation only) Global Secure ToolKit
** --------------------------------------------------------
** The Global Secure ToolKit will be automatically installed for you. If you
** don't want to install it, set the value to NO.
*INSTALL_ENCRYPTION       = YES             ** YES or NO.Valid for root installation only.