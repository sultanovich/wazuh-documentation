.. Copyright (C) 2021 Wazuh, Inc.

.. meta::
      :description: Wazuh 4.3.0 has been released. Check out our release notes to discover the changes and additions of this release.

.. _release_4_3_0:

4.3.0 Release notes
===================

This section lists the changes in version 4.3.0. Every update of the Wazuh solution is cumulative and includes all enhancements and fixes from previous releases.


Highlights
----------

Manager
^^^^^^^

- `#8830 <https://github.com/wazuh/wazuh/pull/8830>`_ `#8178 <https://github.com/wazuh/wazuh/pull/8178>`_ Syscollector and Vulnerability Detector have been extended to support agents running on Amazon Linux and Arch Linux.
- `#7749 <https://github.com/wazuh/wazuh/pull/7749>`_ Vulnerability Detector now manages a vulnerability inventory and produces alerts based on changes on it: when a new vulnerability is either found or solved.


Agent
^^^^^

- `#4983 <https://github.com/wazuh/wazuh/pull/4983>`_ `#7660 <https://github.com/wazuh/wazuh/pull/7660>`_ New integrations to collect auditing logs from Office365 and GitHub have been introduced in the agent.
- `#8632 <https://github.com/wazuh/wazuh/pull/8632>`_ Logcollector can now collect native logs from macOS (Unified Logging System).
- `#8461 <https://github.com/wazuh/wazuh/pull/8461>`_ File Integrity Monitoring has been improved to fully support wilcarded file paths in the configuration.


Wazuh Kibana plugin
^^^^^^^^^^^^^^^^^^^

- `#3424 <https://github.com/wazuh/wazuh-kibana-app/pull/3424>`_ Sample data for Office 365 was added to this new version. Now Wazuh Kibana plugin includes events from Office 365 so that the sample data module covers the cases described in the Office 365 schemas.
- `#3524 <https://github.com/wazuh/wazuh-kibana-app/pull/3524>`_ `#3518 <https://github.com/wazuh/wazuh-kibana-app/pull/3518>`_ Base Module Panel view and a new configuration viewer for the new Office 365 module was added to Wazuh:
   - A base Module Panel view with Office 365 setup was added to this new version. In addition, the Module Panel displays information about the active module. A drill-down table is in charge of doing the drill-down of the parent view, with a search bar and the filtered graphs and table.
   - Configuration viewer for the new Office365 module was added to the Configuration section of the Management menu. This module is only configurable for managers.

.. raw:: html
    
    <div class="images-rn-420-container">
    <div class="images-rn-420">

.. thumbnail::  ../images/release-notes/4.3.0/Management-Configuration.png 
      :align: center
      :title: Management / Configuration

.. thumbnail::  ../images/release-notes/4.3.0/Office-365-General.png
      :align: center
      :title: Office 365 / General

.. raw:: html

    </div>  

- `#3262 <https://github.com/wazuh/wazuh-kibana-app/issues/3262>`_ `#3327 <https://github.com/wazuh/wazuh-kibana-app/pull/3327>`_ `#3321 <https://github.com/wazuh/wazuh-kibana-app/pull/3321>`_ `#3367 <https://github.com/wazuh/wazuh-kibana-app/pull/3367>`_ `#3373 <https://github.com/wazuh/wazuh-kibana-app/pull/3373>`_ Improved the frontend handle errors strategy: UI, Toasts, console log, and log in file:
   - The first attempt to Logger Service (orchestrator) is added, this service is responsible for application logs and for the error orchestration (business rules for errors). Not all errors are sent to the backend, only logs categorized with a certain level or higher.
   - Now the implementation of the ErrorBoundary component and HOC are included to catch components with errors on rendering. In addition, ``loglevel`` dependency to log errors, warnings, etc is also added.
   - The ErrorBoundary HOC to react components were added in his version. It implements error handling HOC in each main react-component (pre-migration).
   - Now try catch strategy is implemented on WzLog by executing Wazuh new error handling strategy on the front-end side. This development was made in order to improve better error handling in the front-end.

- `#3368 <https://github.com/wazuh/wazuh-kibana-app/pull/3368>`_ - `#3344 <https://github.com/wazuh/wazuh-kibana-app/pull/3344>`_ Added Intelligence tab to Mitre Att&ck module:
   - A new Intelligence tab to the Mitre Att&ck module was added with information about the Mitre resources: groups, mitigations, tactics, techniques using the new Wazuh API endpoints. In addition, the Framework tab was adapted to the new Wazuh API endpoints.



What's new
----------

This release includes new features or enhancements.

Manager
^^^^^^^

- `#8178 <https://github.com/wazuh/wazuh/pull/8178>`_ Wazuh adds support for Arch Linux OS in Vulnerability Detector.
- `#8749 <https://github.com/wazuh/wazuh/pull/8749>`_ A log message in the ``cluster.log`` file is added to notify that wazuh-clusterd has been stopped.
- `#9077 <https://github.com/wazuh/wazuh/pull/9077>`_ Wazuh improves API and cluster processes behavior by adding the PID of the ``wazuh-clusterd`` processes and the API when these processes are started in foreground mode.
- `#10492 <https://github.com/wazuh/wazuh/pull/10492>`_ Time calculation is added when extra information is requested to the ``cluster_control`` binary.
- `#9209 <https://github.com/wazuh/wazuh/pull/9209>`_ Wazuh adds a context variable to indicate the origin module in socket communication messages.
- `#9733 <https://github.com/wazuh/wazuh/pull/9733>`_ A unit tests for framework/core files is added to increase coverage.
- `#9204 <https://github.com/wazuh/wazuh/pull/9204>`_ A verbose mode is added in the wazuh-logtest tool.
- `#8830 <https://github.com/wazuh/wazuh/pull/8830>`_ Wazuh adds Vulnerability Detector support for Amazon Linux.
- `#10693 <https://github.com/wazuh/wazuh/pull/10693>`_ The new option ``<force>`` to set the behavior is introduced when Authd finds conflicts on agent enrollment requests.
- `#9099 <https://github.com/wazuh/wazuh/pull/9099>`_ Wazuh adds sanitizers to the unit tests execution.
- `#8237 <https://github.com/wazuh/wazuh/pull/8237>`_ Vulnerability Detector introduces vulnerability inventory.
  - The manager will only deliver alerts when new vulnerabilities are detected in agents or when they stop applying.
- `#8083 <https://github.com/wazuh/wazuh/pull/8083>`_ The internal handling of agent keys are changed in Remoted to speed up key reloading.
- `#7885 <https://github.com/wazuh/wazuh/pull/7885>`_ The option ``<server>`` of the Syslog output now supports hostname resolution. 
- `#7763 <https://github.com/wazuh/wazuh/pull/7763>`_ The product's UNIX user and group are renamed to "wazuh".
- `#7865 <https://github.com/wazuh/wazuh/pull/7865>`_ The MITRE database is redesigned to provide full and searchable data.
- `#7358 <https://github.com/wazuh/wazuh/pull/7358>`_ The static fields related to FIM are ported to dynamic fields in Analysisd.
- `#8351 <https://github.com/wazuh/wazuh/pull/8351>`_ All randomly generated IDs used for cluster tasks are changed. Now, uuid4 is used to ensure IDs are not repeated.
- `#8873 <https://github.com/wazuh/wazuh/pull/8873>`_ The sendsync error log is Improved to provide more details of the used parameters.
- `#9708 <https://github.com/wazuh/wazuh/pull/9708>`_ The ``walk_dir`` function is changed to be iterative instead of recursive.
- `#10183 <https://github.com/wazuh/wazuh/pull/10183>`_ The Integrity sync behavior is refactored so that new synchronizations do not start until extra-valid files are processed.
- `#10101 <https://github.com/wazuh/wazuh/pull/10101>`_ Cluster synchronization is changed so that the content of the etc/shared folder is synchronized.
- `#8351 <https://github.com/wazuh/wazuh/pull/8351>`_ All XML file loads are changed. Now, ``defusedxml`` library is used to avoid possible XML-based attacks.
- `#8535 <https://github.com/wazuh/wazuh/pull/8535>`_ Configuration validation from execq socket is changed to com socket.
- `#8392 <https://github.com/wazuh/wazuh/pull/8392>`_ The utils unittest is updated to improve ``process_array`` function coverage.
- `#8885 <https://github.com/wazuh/wazuh/pull/8885>`_ The ``request_slice`` calculation is changed to improve efficiency when accessing wazuh-db data.
- `#9273 <https://github.com/wazuh/wazuh/pull/9273>`_ The retrieval of information from ``wazuh-db`` is improved so it reaches the optimum size in a single iteration.
- `#9234 <https://github.com/wazuh/wazuh/pull/9234>`_ The way framework uses context cached functions and added a note on context_cached docstring is optimized.
- `#9332 <https://github.com/wazuh/wazuh/pull/9332>`_ The framework regexes is improved to be more specific and less vulnerable.
- `#9423 <https://github.com/wazuh/wazuh/pull/9423>`_ The framework exceptions are unified for non-active agents.
- `#9433 <https://github.com/wazuh/wazuh/pull/9433>`_ The RBAC policies are changed to case insensitive.
- `#9548 <https://github.com/wazuh/wazuh/pull/9548>`_ Framework stats module is refactored into SDK and core components to comply with Wazuh framework code standards.
- `#10309 <https://github.com/wazuh/wazuh/pull/10309>`_ The size of the agents' chunks sent to the upgrade socket is changed to make the upgrade endpoints faster.
- `#9408 <https://github.com/wazuh/wazuh/pull/9408>`_ The rootcheck and syscheck SDK code are refactored to make it clearer.
- `#9738 <https://github.com/wazuh/wazuh/pull/9738>`_ The Azure-logs module is adapted to use Microsoft Graph API instead of Active Directory Graph API.
- `#8060 <https://github.com/wazuh/wazuh/pull/8060>`_ Analysisd now reconnects to Active Response if Remoted or Execd get restarted.
- `#10335 <https://github.com/wazuh/wazuh/pull/10335>`_ Agent key polling now supports cluster environments.
- `#10357 <https://github.com/wazuh/wazuh/pull/10357>`_ The support of Vulnerability Detector is extended for Debian 11 (Bullseye).
- `#10326 <https://github.com/wazuh/wazuh/pull/10326>`_ The remoted performance with an agent TCP connection sending queue is improved.
- `#9093 <https://github.com/wazuh/wazuh/pull/9093>`_ Agent DB synchronization has been boosted by caching the last data checksum in Wazuh DB.
- `#8892 <https://github.com/wazuh/wazuh/pull/8892>`_ Logtest now scans new ruleset files when loading a new session.
- `#8237 <https://github.com/wazuh/wazuh/pull/8237>`_ CVE alerts by Vulnerability Detector now include the time of detection, severity, and score.
- `#10849 <https://github.com/wazuh/wazuh/pull/10849>`_ The manager startup is fixed when ``<database_output>`` is enabled.
- `#10767 <https://github.com/wazuh/wazuh/pull/10767>`_ The cluster "local_integrity" task is changed to run in a separate process to improve overall performance.
- `#10807 <https://github.com/wazuh/wazuh/pull/10807>`_ The cluster communication with the database for agent information synchronization runs now in a separate parallel process.
- `#10920 <https://github.com/wazuh/wazuh/pull/10920>`_ Now the cluster processing of the extra-valid files in the master node is carried out in a separate parallel process.
- `#8399 <https://github.com/wazuh/wazuh/pull/8399>`_ The data reporting for Rootcheck scans in the agent_control tool has been deprecated.
- `#8846 <https://github.com/wazuh/wazuh/pull/8846>`_ The old framework functions used to calculate agent status are now removed.


Agent
^^^^^

- `#8016 <https://github.com/wazuh/wazuh/pull/8016>`_ An option to allow the agent to refresh the connection to the manager is added.
- `#8532 <https://github.com/wazuh/wazuh/pull/8532>`_ A new module to collect audit logs from GitHub is introduced.
- `#8461 <https://github.com/wazuh/wazuh/pull/8461>`_ FIM now expands wildcarded paths in the configuration on Windows agents.
- `#8754 <https://github.com/wazuh/wazuh/pull/8754>`_ FIM reloads wildcarded paths on full scans.
- `#8306 <https://github.com/wazuh/wazuh/pull/8306>`_ Wazuh adds a new ``path_suffix`` option to AWS module configuration.
- `#8331 <https://github.com/wazuh/wazuh/pull/8331>`_ A new ``discard_regex`` option to AWS module configuration is added.
- `#8482 <https://github.com/wazuh/wazuh/pull/8482>`_ Wazuh adds support for the S3 Server Access bucket type in AWS module.
- `#9119 <https://github.com/wazuh/wazuh/pull/9119>`_ Wazuh adds support for Google Cloud Storage buckets using a new GCP module called ``gcp-bucket``.
- `#9119 <https://github.com/wazuh/wazuh/pull/9119>`_ Wazuh adds support for Google Cloud Storage access logs to the ``gcp-bucket`` module.
- `#9420 <https://github.com/wazuh/wazuh/pull/9420>`_ Wazuh adds support for VPC endpoints in AWS module.
- `#9279 <https://github.com/wazuh/wazuh/pull/9279>`_ Wazuh adds support for GCS access logs in the GCP module.
- `#10198 <https://github.com/wazuh/wazuh/pull/10198>`_ An iam role session duration parameter to AWS module is added.
- `#8826 <https://github.com/wazuh/wazuh/pull/8826>`_ Wazuh adds support for variables in SCA policies.
- `#7721 <https://github.com/wazuh/wazuh/pull/7721>`_ FIM now fills an audit rule file to support who-data although Audit is in immutable mode.
- `#8957 <https://github.com/wazuh/wazuh/pull/8957>`_ An integration to collect audit logs from Office365 is introduced.
- `#10168 <https://github.com/wazuh/wazuh/pull/10168>`_ A new field ``DisplayVersion`` to Syscollector to help Vulnerability Detector match vulnerabilities for Windows is added.
- `#10148 <https://github.com/wazuh/wazuh/pull/10148>`_ Wazuh adds support for macOS agent upgrade via WPK.
- `#8632 <https://github.com/wazuh/wazuh/pull/8632>`_ Wazuh adds Logcollector support for macOS logs (Unified Logging System).
- `#8381 <https://github.com/wazuh/wazuh/pull/8381>`_ The agent now reports the version of the running AIX operating system to the manager. 
- `#8604 <https://github.com/wazuh/wazuh/pull/8604>`_ The reliability of the user ID parsing in FIM who-data mode on Linux is improved.
- `#10230 <https://github.com/wazuh/wazuh/pull/10230>`_ AWS ``service_endpoint`` parameter description to suit FIPS endpoints too is reworded.
- `#5047 <https://github.com/wazuh/wazuh/pull/5047>`_ The support of Logcollector for MySQL 4.7 logs is extended.
- `#9887 <https://github.com/wazuh/wazuh/pull/9887>`_ Agents running on FreeBSD and OpenBSD now report their IP addresses.
- `#8202 <https://github.com/wazuh/wazuh/pull/8202>`_ The verbosity of FIM debugging logs is reduced.
- `#9992 <https://github.com/wazuh/wazuh/pull/9992>`_ The agent's IP resolution frequency has been limited to prevent high CPU load.
- `#10236 <https://github.com/wazuh/wazuh/pull/10236>`_ Syscollector is optimized to use less memory.
- `#10337 <https://github.com/wazuh/wazuh/pull/10337>`_ Wazuh adds support of ZscalerOS system information in the agent.
- `#10259 <https://github.com/wazuh/wazuh/pull/10259>`_ Syscollector is extended to collect missing Microsoft product hotfixes.
- `#10396 <https://github.com/wazuh/wazuh/pull/10396>`_ The osquery integration is updated to find the new osqueryd location as of version 5.0.
- `#9123 <https://github.com/wazuh/wazuh/pull/9123>`_ The internal FIM data handling has been simplified to find files by their path instead of their inode.
- `#9764 <https://github.com/wazuh/wazuh/pull/9764>`_  The WPK installer rollback on Windows is reimplemented.
- `#10208 <https://github.com/wazuh/wazuh/pull/10208>`_ Active responses for Windows agents now support native fields from Eventchannel.
- `#10651 <https://github.com/wazuh/wazuh/pull/10651>`_ Error logs by Logcollector when a file is missing have been changed to info logs.
- `#8724 <https://github.com/wazuh/wazuh/pull/8724>`_ The agent MSI installer for Windows now detects the platform version to install the default configuration.
- `#3659 <https://github.com/wazuh/wazuh/pull/3659>`_ Agent logs for inability to resolve the manager hostname now have info level.
- `#10900 <https://github.com/wazuh/wazuh/pull/10900>`_ The oscap module files are removed as it was already deprecated since v4.0.0.


RESTful API
^^^^^^^^^^^

- `#7988 <https://github.com/wazuh/wazuh/pull/7988>`_ A new ``PUT /agents/reconnect`` endpoint is added to force agents reconnection to the manager.
- `#6761 <https://github.com/wazuh/wazuh/pull/6761>`_ The ``select`` parameter is added to the ``GET /security/users``, ``GET /security/roles``, ``GET /security/rules`` and ``GET /security/policies`` endpoints.
- `#8100 <https://github.com/wazuh/wazuh/pull/8100>`_ The type and status filters are added to ``GET /vulnerability/{agent_id}`` endpoint.
- `#7490 <https://github.com/wazuh/wazuh/pull/7490>`_ An option is added to configure SSL ciphers.
- `#8919 <https://github.com/wazuh/wazuh/pull/8919>`_ An option is added to configure the maximum response time of the API.
- `#8945 <https://github.com/wazuh/wazuh/pull/8945>`_ A new ``DELETE /rootcheck/{agent_id}`` endpoint is added.
- `#9028 <https://github.com/wazuh/wazuh/pull/9028>`_ A new ``GET /vulnerability/{agent_id}/last_scan`` endpoint is added to check the latest vulnerability scan of an agent.
- `#9028 <https://github.com/wazuh/wazuh/pull/9028>`_ A new ``cvss`` and ``severity`` fields and filters are added to ``GET /vulnerability/{agent_id}`` endpoint.
- `#9100 <https://github.com/wazuh/wazuh/pull/9100>`_ An option  is added to configure the maximum allowed API upload size.
- `#9142 <https://github.com/wazuh/wazuh/pull/9142>`_ A new unit and integration tests for API models are added.
- `#9077 <https://github.com/wazuh/wazuh/pull/9077>`_ A message with the PID of ``wazuh-apid`` process when launched in foreground mode  is added.
- `#9144 <https://github.com/wazuh/wazuh/pull/9144>`_ Wazuh adds ``external id``, ``source``, and ``url`` to the MITRE endpoints responses.
- `#9297 <https://github.com/wazuh/wazuh/pull/9297>`_ A custom healthchecks for legacy agents in API integration tests, improving maintainability is added.
- `#9914 <https://github.com/wazuh/wazuh/pull/9914>`_ A new unit tests for the API python module  is added to increase coverage.
- `#10238 <https://github.com/wazuh/wazuh/pull/10238>`_ A docker logs separately in API integration tests environment are added to get cleaner reports.
- `#10437 <https://github.com/wazuh/wazuh/pull/10437>`_ A new ``disconnection_time`` field is added to ``GET /agents`` response.
- `#10457 <https://github.com/wazuh/wazuh/pull/10457>`_ New filters are added to agents upgrade endpoints.
- `#8288 <https://github.com/wazuh/wazuh/pull/8288>`_ New MITRE API endpoints and framework functions are added to access all the MITRE information.
- `#10947 <https://github.com/wazuh/wazuh/pull/10947>`_ Show agent-info permissions flag is added when using cluster_control and in the ``GET /cluster/healthcheck`` API endpoint.
- `#7490 <https://github.com/wazuh/wazuh/pull/7490>`_ The SSL protocol configuration parameter is renamed.
- `#8827 <https://github.com/wazuh/wazuh/pull/8827>`_ The API spec examples and JSON body examples is reviewed and updated.
- The performance of several API endpoints is improved. This is specially appreciable in environments with a big number of agents:
   - `#8937 <https://github.com/wazuh/wazuh/pull/8937>`_ The endpoint parameter ``PUT /agents/group`` is improved.
   - `#8938 <https://github.com/wazuh/wazuh/pull/8938>`_ The endpoint parameter ``PUT /agents/restart`` is improved.
   - `#8950 <https://github.com/wazuh/wazuh/pull/8950>`_ The endpoint parameter ``DELETE /agents`` is improved.
   - `#8959 <https://github.com/wazuh/wazuh/pull/8959>`_ The endpoint parameter ``PUT /rootcheck`` is improved.
   - `#8966 <https://github.com/wazuh/wazuh/pull/8966>`_ The endpoint parameter ``PUT /syscheck`` is improved.
   - `#9046 <https://github.com/wazuh/wazuh/pull/9046>`_ The endpoint parameter ``DELETE /groups`` is improved and API response is changed to be more consistent.
- `#8945 <https://github.com/wazuh/wazuh/pull/8945>`_ The endpoint parameter ``DELETE /rootcheck`` is changed to ``DELETE /experimental/rootcheck``.
- `#9012 <https://github.com/wazuh/wazuh/pull/9012>`_ The time it takes for ``wazuh-apid`` process is reduced to check its configuration when using the -t parameter.
- `#9019 <https://github.com/wazuh/wazuh/pull/9019>`_ The malfunction in the ``sort`` parameter of syscollector endpoints is fixed.
- `#9113 <https://github.com/wazuh/wazuh/pull/9113>`_ The API integration tests stability when failing in entrypoint is improved.
- `#9228 <https://github.com/wazuh/wazuh/pull/9228>`_ The SCA API integration tests dynamic to validate responses coming from any agent version is fixed.
- `#9227 <https://github.com/wazuh/wazuh/pull/9227>`_ All the date fields in the API responses to use ISO8601 is refactored and standardized.
- `#9263 <https://github.com/wazuh/wazuh/pull/9263>`_ The ``Server`` header from API HTTP responses is removed.
- `#9371 <https://github.com/wazuh/wazuh/pull/9371>`_ The JWT implementation by replacing HS256 signing algorithm with RS256 is improved.
- `#10009 <https://github.com/wazuh/wazuh/pull/10009>`_ The limit of agents to upgrade using the API upgrade endpoints is removed.
- `#10158 <https://github.com/wazuh/wazuh/pull/10158>`_ The Windows agents FIM responses is changed to return permissions as JSON.
- `#10389 <https://github.com/wazuh/wazuh/pull/10389>`_ The API endpoints is adapted to changes in ``wazuh-authd`` daemon ``force`` parameter.
- `#10512 <https://github.com/wazuh/wazuh/pull/10512>`_ The ``use_only_authd`` API configuration option and related functionality is deprecated. ``wazuh-authd`` will always be required for creating and removing agents.
- `#10745 <https://github.com/wazuh/wazuh/pull/10745>`_ The API validators and related unit tests is improved.
- `#10905 <https://github.com/wazuh/wazuh/pull/10905>`_ The specific module healthchecks in API integration tests environment is improved.
- `#10916 <https://github.com/wazuh/wazuh/pull/10916>`_ The thread pool executors for process pool executors to improve API availability is changed.
- `#8599 <https://github.com/wazuh/wazuh/pull/8599>`_ The select parameter from GET /agents/stats/distinct endpoint is removed.
- `#8099 <https://github.com/wazuh/wazuh/pull/8099>`_ The ``GET /mitre`` endpoint is removed.


Ruleset
^^^^^^^

- `#10428 <https://github.com/wazuh/wazuh/pull/10428>`_ The Rules and Decoders for Wazuh API are added.
- `#10458 <https://github.com/wazuh/wazuh/pull/10458>`_ Rules and Decoders for TrendMicro Cloud One are added.
- `#10496 <https://github.com/wazuh/wazuh/pull/10496>`_ Rules for Sophos UTM Firewall are added.
- `#10369 <https://github.com/wazuh/wazuh/pull/10369>`_ SCA policy for Solaris 11.4 is added.
- `#10658 <https://github.com/wazuh/wazuh/pull/10658>`_ Rules for Cloudflare WAF are added.
- `#10667 <https://github.com/wazuh/wazuh/pull/10667>`_ Rules and Decoders for FortiAuth are added.
- `#10315 <https://github.com/wazuh/wazuh/pull/10315>`_ Amazon Linux 2 SCA is updated up to version 2.0.0.
- `#10354 <https://github.com/wazuh/wazuh/pull/10354>`_ RedHat Enterprise Linux 8 SCA is updated up to version 1.0.1.
- `#10507 <https://github.com/wazuh/wazuh/pull/10507>`_ Amazon rules are updated to add more granularity.
- `#10558 <https://github.com/wazuh/wazuh/pull/10558>`_ macOS Big Sur SCA is updated up to version 1.2.0.


Wazuh Kibana plugin
^^^^^^^^^^^^^^^^^^^

- `#3639 <https://github.com/wazuh/wazuh-kibana-app/pull/3639>`_ Wazuh adds the ability to filter the results fo the ``Network Ports`` table in the ``Inventory data`` section.
- `#3324 <https://github.com/wazuh/wazuh-kibana-app/pull/3324>`_ A new endpoint service is added to collect the frontend logs into a file.
- `#3262 <https://github.com/wazuh/wazuh-kibana-app/issues/3262>`_ `#3327 <https://github.com/wazuh/wazuh-kibana-app/pull/3327>`_ `#3321 <https://github.com/wazuh/wazuh-kibana-app/pull/3321>`_ `#3367 <https://github.com/wazuh/wazuh-kibana-app/pull/3367>`_ `#3373 <https://github.com/wazuh/wazuh-kibana-app/pull/3373>`_  The frontend handle errors strategy is improved: UI, Toasts, console log and log in file.
- `#3196 <https://github.com/wazuh/wazuh-kibana-app/pull/3196>`_ Fields status and type are added in vulnerabilities table.
- `#3368 <https://github.com/wazuh/wazuh-kibana-app/pull/3368>`_ `#3344 <https://github.com/wazuh/wazuh-kibana-app/pull/3344>`_ Intelligence tab is added to Mitre Att&ck module.
- `#3424 <https://github.com/wazuh/wazuh-kibana-app/pull/3424>`_ Sample data for office365 events is added.
- `#3475 <https://github.com/wazuh/wazuh-kibana-app/pull/3475>`_ A separate component to check for sample data is created.
- `#3506 <https://github.com/wazuh/wazuh-kibana-app/pull/3506>`_ A new hook for getting value suggestions is added.
- `#3531 <https://github.com/wazuh/wazuh-kibana-app/pull/3531>`_ Dinamic simple filters and simple GitHub filters fields are added.
- `#3524 <https://github.com/wazuh/wazuh-kibana-app/pull/3524>`_ Configuration viewer for Module Office365 is added on the Configuration section of the Management menu.
- `#3518 <https://github.com/wazuh/wazuh-kibana-app/pull/3518>`_ Base Module Panel view with Office365 setup is added.
- `#3533 <https://github.com/wazuh/wazuh-kibana-app/pull/3533>`_ Specifics and custom filters for Office365 search bar are added.
- `#3544 <https://github.com/wazuh/wazuh-kibana-app/pull/3544>`_ Pagination and filter are added to drilldown tables at Office pannel.
- `#3568 <https://github.com/wazuh/wazuh-kibana-app/pull/3568>`_ Simple filters change between panel and drilldown panel.
- `#3525 <https://github.com/wazuh/wazuh-kibana-app/pull/3525>`_ New fields in Inventory table and Flyout Details are added.
- `#3691 <https://github.com/wazuh/wazuh-kibana-app/pull/3691>`_ Columns selector in agents table are added.
- `#3121 <https://github.com/wazuh/wazuh-kibana-app/pull/3121>`_ Ossec to wazuh is changed in all sample-data files.
- `#3279 <https://github.com/wazuh/wazuh-kibana-app/pull/3279>`_ Empty fields are modified in FIM tables and ``syscheck.value_name`` in discovery now show an empty tag for visual clarity.
- `#3346 <https://github.com/wazuh/wazuh-kibana-app/pull/3346>`_ The Mitre tactics and techniques resources are adapted to use the API endpoints.
- `#3517 <https://github.com/wazuh/wazuh-kibana-app/pull/3517>`_ The filterManager subscription are moved to the hook useFilterManager.
- `#3529 <https://github.com/wazuh/wazuh-kibana-app/pull/3529>`_ Filter is changed from "is" to "is one of" in custom searchbar.
- `#3494 <https://github.com/wazuh/wazuh-kibana-app/pull/3494>`_ Refactor ``modules-defaults.js`` to define what buttons and components are rendered in each module tab.
- `#3663 <https://github.com/wazuh/wazuh-kibana-app/pull/3663>`_ Depracated and new references ``authd`` is updated.
- `#3549 <https://github.com/wazuh/wazuh-kibana-app/pull/3549>`_ Time subscription is added to Discover component.
- `#3446 <https://github.com/wazuh/wazuh-kibana-app/pull/3446>`_ Testing logs using the Ruletest Test don't display the rule information if not matching a rule.
- `#3649 <https://github.com/wazuh/wazuh-kibana-app/pull/3649>`_ The format permissions is changed in FIM inventory.
- `#3686 <https://github.com/wazuh/wazuh-kibana-app/pull/3686>`_ Changed of request for one that does not return data that is not necessary to optimize times.


Others
^^^^^^

- `#10247 <https://github.com/wazuh/wazuh/pull/10247>`_ Upgraded external SQLite library dependency version to 3.36.
- `#10247 <https://github.com/wazuh/wazuh/pull/10247>`_ Upgraded external BerkeleyDB library dependency version to 18.1.40.
- `#10247 <https://github.com/wazuh/wazuh/pull/10247>`_ Upgraded external OpenSSL library dependency version to 1.1.1l.
- `#10927 <https://github.com/wazuh/wazuh/pull/10927>`_ Upgraded external Google Test library dependency version to 1.11.


Resolved issues
---------------

This release resolves known issues. 


Manager
^^^^^^^

==============================================================    =============
Reference                                                         Description
==============================================================    =============
`#8223 <https://github.com/wazuh/wazuh/pull/8223>`_               Fixed a memory defect in Remoted when closing connection handles.
`#7625 <https://github.com/wazuh/wazuh/pull/7625>`_               Fixed a timing problem in the manager that might prevent Analysisd from sending Active responses to agents.
`#8210 <https://github.com/wazuh/wazuh/pull/8210>`_               Fixed a bug in Analysisd that did not apply field lookup in rules that overwrite other ones.
`#8902 <https://github.com/wazuh/wazuh/pull/8902>`_               Prevented the manager from leaving dangling agent database files.
`#8254 <https://github.com/wazuh/wazuh/pull/8254>`_               Corrected remediation message for error code 6004.
`#8157 <https://github.com/wazuh/wazuh/pull/8157>`_               Fixed a bug when deleting non-existing users or roles in the security SDK.
`#8418 <https://github.com/wazuh/wazuh/pull/8418>`_               Fixed a bug with ``agent.conf`` file permissions when creating an agent group.
`#8422 <https://github.com/wazuh/wazuh/pull/8422>`_               Fixed wrong exceptions with wdb pagination mechanism.
`#8747 <https://github.com/wazuh/wazuh/pull/8747>`_               Fixed error when loading some rules with the ``\`` character.
`#9216 <https://github.com/wazuh/wazuh/pull/9216>`_               Changed ``WazuhDBQuery`` class to properly close socket connections and prevent file descriptor leaks.
`#10320 <https://github.com/wazuh/wazuh/pull/10320>`_             Fixed error in the api configuration when using the ``agent_upgrade`` script.
`#10341 <https://github.com/wazuh/wazuh/pull/10341>`_             Handle ``JSONDecodeError`` in Distributed API class methods.
`#9738 <https://github.com/wazuh/wazuh/pull/9738>`_               Fixed an issue with duplicated logs in Azure-logs module and applied several improvements to it.
`#10680 <https://github.com/wazuh/wazuh/pull/10680>`_             Fixed the query parameter validation to allow usage of special chars in Azure module.
`#8394 <https://github.com/wazuh/wazuh/pull/8394>`_               Fix a bug running ``wazuh-clusterd`` process when it was already running.
`#8732 <https://github.com/wazuh/wazuh/pull/8732>`_               Allow cluster to send and receive messages with size higher than request_chunk.
`#9077 <https://github.com/wazuh/wazuh/pull/9077>`_               Fixed a bug that caused ``wazuh-clusterd`` process to not delete its pidfile when running in foreground mode and it is stopped.
`#10376 <https://github.com/wazuh/wazuh/pull/10376>`_             Fixed race condition due to lack of atomicity in the cluster synchronization mechanism.
`#10492 <https://github.com/wazuh/wazuh/pull/10492>`_             Fixed bug when displaying the dates of the cluster tasks that have not finished yet. Now ``n/a`` is displayed in these cases.
`#9196 <https://github.com/wazuh/wazuh/pull/9196>`_               Fixed missing field ``value_type`` in FIM alerts.
`#9292 <https://github.com/wazuh/wazuh/pull/9292>`_               Fixed a typo in the SSH Integrity Check script for Agentless.
`#10421 <https://github.com/wazuh/wazuh/pull/10421>`_             Fixed multiple race conditions in Remoted.
`#10390 <https://github.com/wazuh/wazuh/pull/10390>`_             The manager's agent database has been fixed to prevent dangling entries from removed agents.
`#9765 <https://github.com/wazuh/wazuh/pull/9765>`_               Fixed the alerts generated by FIM when a lookup operation on an SID fails.
`#10866 <https://github.com/wazuh/wazuh/pull/10866>`_             Fixed a bug that caused cluster agent-groups files to be synchronized multiple times unnecessarily.
`#10922 <https://github.com/wazuh/wazuh/pull/10922>`_             Fixed an issue in Wazuh DB that compiled the SQL statements multiple times unnecessarily.
`#10948 <https://github.com/wazuh/wazuh/pull/10948>`_             Fixed a crash in Analysisd when setting Active Response with agent_id = 0.
==============================================================    =============


Agent
^^^^^

==============================================================    =============
Reference                                                         Description
==============================================================    =============
`#8784 <https://github.com/wazuh/wazuh/pull/8784>`_               Fixed a bug in FIM that did not allow monitoring new directories in real-time mode if the limit was reached at some point.
`#8941 <https://github.com/wazuh/wazuh/pull/8941>`_               Fixed a bug in FIM that threw an error when a query to the internal database returned no data.
`#8362 <https://github.com/wazuh/wazuh/pull/8362>`_               Fixed an error where the IP address was being returned along with the port for Amazon NLB service.
`#8372 <https://github.com/wazuh/wazuh/pull/8372>`_               Fixed AWS module to properly handle the exception raised when processing a folder without logs.
`#8433 <https://github.com/wazuh/wazuh/pull/8433>`_               Fixed a bug with AWS module when pagination is needed in the bucket.
`#8672 <https://github.com/wazuh/wazuh/pull/8672>`_               Fixed an error with the ipGeoLocation field in AWS Macie logs.
`#10333 <https://github.com/wazuh/wazuh/pull/10333>`_               Changed an incorrect debug message in the GCloud integration module.
`#7848 <https://github.com/wazuh/wazuh/pull/7848>`_               Data race conditions have been fixed in FIM.
`#10011 <https://github.com/wazuh/wazuh/pull/10011>`_             Fixed wrong command line display in the Syscollector process report on Windows.
`#10249 <https://github.com/wazuh/wazuh/pull/10249>`_             Prevented Modulesd from freezing if Analysisd or Agentd get stopped before it.
`#10405 <https://github.com/wazuh/wazuh/pull/10405>`_             Fixed wrong keepalive message from the agent when file merged.mg is missing.
`#10381 <https://github.com/wazuh/wazuh/pull/10381>`_             Fixed missing logs from the Windows agent when it's getting stopped.
`#10524 <https://github.com/wazuh/wazuh/pull/10524>`_             Fixed missing packages reporting in Syscollector for macOS due to empty architecture data.
`#7506 <https://github.com/wazuh/wazuh/pull/7506>`_               Fixed FIM on Linux to parse audit rules with multiple keys for who-data.
`#10639 <https://github.com/wazuh/wazuh/pull/10639>`_             Fixed Windows 11 version collection in the agent.
`#10602 <https://github.com/wazuh/wazuh/pull/10602>`_             Fixed missing Eventchannel location in Logcollector configuration reporting.
`#10794 <https://github.com/wazuh/wazuh/pull/10794>`_             Updated CloudWatch Logs integration to avoid crashing when AWS raises Throttling errors.
`#10718 <https://github.com/wazuh/wazuh/pull/10718>`_             Fixed AWS modules' log file filtering when there are logs with and without a prefix mixed in a bucket.
`#10884 <https://github.com/wazuh/wazuh/pull/10884>`_             Fixed a bug on the installation script that made upgrades not to update the code of the external integration modules.
`#10921 <https://github.com/wazuh/wazuh/pull/10921>`_             Fixed issue with AWS integration module trying to parse manually created folders as if they were files.
==============================================================    =============


RESTful API
^^^^^^^^^^^

==============================================================    =============
Reference                                                         Description
==============================================================    =============
`#8196 <https://github.com/wazuh/wazuh/pull/8196>`_               Fixed inconsistency in RBAC resources for ``group:create``, ``decoders:update``, and ``rules:update`` actions.
`#8378 <https://github.com/wazuh/wazuh/pull/8378>`_               Fixed the handling of an API error message occurring when Wazuh is started with a wrong ``ossec.conf``. Now the execution continues and raises a warning.
`#8548 <https://github.com/wazuh/wazuh/pull/8548>`_               Fixed a bug with ``sort`` parameter that caused a wrong response when sorting by several fields.
`#8597 <https://github.com/wazuh/wazuh/pull/8597>`_               Fixed the description of ``force_time`` parameter in the API spec reference.
`#8537 <https://github.com/wazuh/wazuh/pull/8537>`_               Fixed API incorrect path in remediation message when maximum number of requests per minute is reached.
`#9071 <https://github.com/wazuh/wazuh/pull/9071>`_               Fixed agents' healthcheck error in the API integration test environment.
`#9077 <https://github.com/wazuh/wazuh/pull/9077>`_               Fixed a bug with ``wazuh-apid`` process handling of pidfiles when running in foreground mode.
`#9192 <https://github.com/wazuh/wazuh/pull/9192>`_               Fixed a bug with RBAC ``group_id`` matching.
`#9147 <https://github.com/wazuh/wazuh/pull/9147>`_               Removed temporal development keys and values from ``GET /cluster/healthcheck`` response.
`#9227 <https://github.com/wazuh/wazuh/pull/9227>`_               Fixed several errors when filtering by dates.
`#9262 <https://github.com/wazuh/wazuh/pull/9262>`_               Fixed limit in some endpoints like ``PUT /agents/group/{group_id}/restart`` and added a pagination method.
`#9320 <https://github.com/wazuh/wazuh/pull/9320>`_               Fixed bug with the ``search`` parameter resulting in invalid results.
`#9368 <https://github.com/wazuh/wazuh/pull/9368>`_               Fixed wrong values of ``external_id`` field in MITRE resources.
`#9399 <https://github.com/wazuh/wazuh/pull/9399>`_               Fixed how the API integration testing environment checks that wazuh-apid daemon is running before starting the tests.
`#9777 <https://github.com/wazuh/wazuh/pull/9777>`_               Add healthcheck to verify that ``logcollector`` stats are ready before starting the API integration test.
`#10159 <https://github.com/wazuh/wazuh/pull/10159>`_             Fixed API integration test healthcheck used in the ``vulnerability`` test cases.
`#10179 <https://github.com/wazuh/wazuh/pull/10179>`_             Fixed an error with ``PUT /agents/node/{node_id}/restart`` endpoint when no agents are present in selected node.
`#10322 <https://github.com/wazuh/wazuh/pull/10322>`_             Fixed RBAC experimental API integration tests expecting a 1760 code in implicit requests.
`#10289 <https://github.com/wazuh/wazuh/pull/10289>`_             Fixed cluster race condition that caused API integration test to randomly fail.
`#10619 <https://github.com/wazuh/wazuh/pull/10619>`_             Fixed ``PUT /agents/node/{node_id}/restart`` endpoint to exclude exception codes properly.
`#10666 <https://github.com/wazuh/wazuh/pull/10666>`_             Fixed ``PUT /agents/group/{group_id}/restart`` endpoint to exclude exception codes properly.
`#10656 <https://github.com/wazuh/wazuh/pull/10656>`_             Fixed agent endpoints q parameter to allow more operators when filtering by groups.
`#10830 <https://github.com/wazuh/wazuh/pull/10830>`_             Fixed API integration tests related to rule, decoder and task endpoints.
==============================================================    =============


Ruleset
^^^^^^^

==============================================================    =============
Reference                                                         Description
==============================================================    =============
`#10315 <https://github.com/wazuh/wazuh/pull/10315>`_             Fixed enabled-like checks for Amazon Linux 2 SCA.
`#10354 <https://github.com/wazuh/wazuh/pull/10354>`_             Fixed enabled-like checks for RedHat Enterprise Linux 8 SCA.
`#10406 <https://github.com/wazuh/wazuh/pull/10406>`_             Fixed typos and not working tests for Centos 7 SCA. Thanks to RonnyMaas (@RonnyMaas).
`#10707 <https://github.com/wazuh/wazuh/pull/10707>`_             Fixed YML syntax problems in Solaris 11.4 SCA.
`#10375 <https://github.com/wazuh/wazuh/pull/10375>`_             Fixed a typo in the Xbox Live Networking Service check for SCA.
==============================================================    =============


Wazuh Kibana plugin
^^^^^^^^^^^^^^^^^^^

==============================================================    =============
Reference                                                         Description
==============================================================    =============
`#3384 <https://github.com/wazuh/wazuh-kibana-app/pull/3384>`_    Fixed creation of log files.
`#3484 <https://github.com/wazuh/wazuh-kibana-app/pull/3484>`_    Fixed double fetching alerts count when pinnin/unpinning the agent in Mitre Att&ck/Framework.
`#3490 <https://github.com/wazuh/wazuh-kibana-app/pull/3490>`_    Query config refactor.
`#3412 <https://github.com/wazuh/wazuh-kibana-app/pull/3412>`_    Fixed rules and decoders test flyout clickout event.
`#3430 <https://github.com/wazuh/wazuh-kibana-app/pull/3430>`_    Notify when you are registering an agent without permissions.
`#3438 <https://github.com/wazuh/wazuh-kibana-app/pull/3438>`_    Remove not used ``redirectRule`` query param when clicking the row table on CDB Lists/Decoders.
`#3439 <https://github.com/wazuh/wazuh-kibana-app/pull/3439>`_    Fixed the code overflows over the line numbers in the API Console editor.
`#3440 <https://github.com/wazuh/wazuh-kibana-app/pull/3440>`_    Don't open the main menu when changing the seleted API or index pattern.
`#3443 <https://github.com/wazuh/wazuh-kibana-app/pull/3443>`_    Fix error message in conf managment.
`#3445 <https://github.com/wazuh/wazuh-kibana-app/pull/3445>`_    Fix size api selector when name is too long.
`#3456 <https://github.com/wazuh/wazuh-kibana-app/pull/3456>`_    Fixed error when edit a rule or decoder.
`#3458 <https://github.com/wazuh/wazuh-kibana-app/pull/3458>`_    Fixed index pattern selector doesn't display the ignored index patterns.
`#3553 <https://github.com/wazuh/wazuh-kibana-app/pull/3553>`_    Fixed error in /Management/Configuration when cluster is disabled.
`#3565 <https://github.com/wazuh/wazuh-kibana-app/pull/3565>`_    Fix the pinned filters were removed when accessing to the ``Panel`` tab of a module.
`#3645 <https://github.com/wazuh/wazuh-kibana-app/pull/3645>`_    Fixed multi-select component searcher handler.
`#3609 <https://github.com/wazuh/wazuh-kibana-app/pull/3609>`_    Fixed order logs properly in Management/Logs.
`#3661 <https://github.com/wazuh/wazuh-kibana-app/pull/3661>`_    Fixed the Wazuh API requests to ``GET //``.
`#3675 <https://github.com/wazuh/wazuh-kibana-app/pull/3675>`_    Fixed missing mitre tactics.
`#3488 <https://github.com/wazuh/wazuh-kibana-app/pull/3488>`_    Fix CDB list view not working with IPv6.
`#3466 <https://github.com/wazuh/wazuh-kibana-app/pull/3466>`_    Fixed the bad requests using Console tool to ``PUT /active-response`` API endpoint.
`#3605 <https://github.com/wazuh/wazuh-kibana-app/pull/3605>`_    Fixed group agent management table does not update on error.
`#3651 <https://github.com/wazuh/wazuh-kibana-app/pull/3651>`_    Fixed not showing packages details in agent inventory for a freeBSD agent SO.
`#3652 <https://github.com/wazuh/wazuh-kibana-app/pull/3652>`_    Fixed wazuh token deleted twice.
`#3687 <https://github.com/wazuh/wazuh-kibana-app/pull/3687>`_    Fixed handler of error on dev-tools.
`#3685 <https://github.com/wazuh/wazuh-kibana-app/pull/3685>`_    Fixed compatibility wazuh 4.3 - kibana 7.13.4.
`#3689 <https://github.com/wazuh/wazuh-kibana-app/pull/3689>`_    Fixed registry values without agent pinned in FIM>Events.
`#3688 <https://github.com/wazuh/wazuh-kibana-app/pull/3688>`_    Fixed breadcrumbs style compatibility for Kibana 7.14.2.
`#3682 <https://github.com/wazuh/wazuh-kibana-app/pull/3682>`_    Fixed security alerts table when filters change.
`#3692 <https://github.com/wazuh/wazuh-kibana-app/pull/3692>`_    Fixed error that shows we're using X-Pack when we have Basic.
`#3700 <https://github.com/wazuh/wazuh-kibana-app/pull/3700>`_    Fixed blank screen in Kibana 7.10.2.
==============================================================    =============


Others
^^^^^^

==============================================================    =============
Reference                                                         Description
==============================================================    =============
`#9168 <https://github.com/wazuh/wazuh/pull/9168>`_               Fixed error detection in the CURL helper library.
`#10899 <https://github.com/wazuh/wazuh/pull/10899>`_             Fixed external BerkeleyDB library support for GCC 11.
==============================================================    =============


Changelogs
----------

More details about these changes are provided in the changelog of each component:

- `wazuh/wazuh <https://github.com/wazuh/wazuh/blob/v4.3.0-rc1/CHANGELOG.md>`_
- `wazuh/wazuh-kibana-app <https://github.com/wazuh/wazuh-kibana-app/blob/4.3-7.10---RC1/CHANGELOG.md>`_
- `wazuh/wazuh-splunk <https://github.com/wazuh/wazuh-splunk/blob/v4.2.5-8.1.4/CHANGELOG.md>`_