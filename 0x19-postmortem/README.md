Issue Summary:
On August 12, 2023, from 14:30 to 17:45 (UTC), our e-commerce platform experienced a critical outage. During this period, the checkout service was unavailable, causing severe disruptions for users. Approximately 40% of users were impacted, encountering error messages and being unable to complete their purchases.

Root Cause:
The root cause of the outage was traced back to a misconfigured database connection pool. Due to an error in the recent deployment of a code update, the connection pool size was set too low. This resulted in a bottleneck of incoming database requests, overwhelming the database server and leading to timeouts and connection failures.

Timeline:
- Issue detected: August 12, 2023, 14:30 (UTC)
- Detection method: Monitoring alert triggered due to high number of database timeouts and connection errors.
- Actions taken: Initial investigation focused on database server performance and network connectivity. Assumption was made that the database server itself was experiencing issues.
- Misleading paths: Time was spent investigating network configurations and hardware issues on the database server, which yielded no relevant findings.
- Escalation: Incident was escalated to the DevOps and Database Engineering teams for further investigation.
- Resolution: The misconfigured connection pool size was identified as the root cause. The connection pool settings were corrected, and the application code was rolled back to the previous version. The checkout service was gradually restored, and the outage was resolved by 17:45 (UTC).

Root Cause and Resolution:
The misconfiguration of the database connection pool caused an insufficient number of connections to be available for incoming requests. This led to a backlog of requests waiting for database access, causing timeouts and connection failures. To resolve the issue, the connection pool size was increased to accommodate the expected load. The application code was also rolled back to a stable version, ensuring that the previous, functional configuration was reinstated.

Corrective and Preventative Measures:
1. Performance Testing: Implement rigorous performance testing before deploying updates to identify potential bottlenecks or issues.
2. Automated Monitoring: Enhance monitoring by setting up alerts for abnormal database behavior, such as high connection timeouts.
3. Configuration Management: Implement version control for configuration changes to prevent inadvertent misconfigurations.
4. Emergency Rollback Plan: Develop a clear rollback plan that allows for quick reversion to a stable version in case of critical issues.
5. Database Scaling: Evaluate the need for database scaling based on expected traffic to avoid overloading the system during peak periods.

Tasks:
1. Patch database connection pool settings to ensure an adequate number of connections are available.
2. Conduct post-deployment testing to verify code changes before releasing updates.
3. Set up automated monitoring alerts for database performance metrics.
4. Create a documented rollback process for emergency situations.
5. Evaluate options for database scaling and implement if necessary.

In conclusion, the recent e-commerce platform outage was a result of a misconfigured database connection pool. Swift action was taken to identify and rectify the root cause, and measures have been outlined to prevent similar incidents in the future. The incident underscores the importance of thorough testing, monitoring, and configuration management to maintain the reliability of our systems.



