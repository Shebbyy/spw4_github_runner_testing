SPW4 - Exercise 3
=================

Name: Gradwohl Sebastian

Effort in hours: 5

## 1. Connect Four Web Application and CI/CD Pipeline

### Task 1.a
Für das lokale Ausführen wurde im IntelliJ aktiviert, dass Terminal Aufgaben direkt durch die IDE ausgeführt wird, 
dadurch kann dann mit STRG+Enter beim Eingeben der Commands dieser durch die IDE ausgeführt werden (so funktioniert 
dann Maven auch korrekt)

Sh.
mvn compile
![local_mvn_build.png](doc/local_mvn_build.png)<br><br>

mvn test
![local_mvn_test.png](doc/local_mvn_test.png)<br><br>

mvn package
![local_mvn_package.png](doc/local_mvn_package.png)<br><br>

Deployment
- Auf http://localhost:8080 verbinden, nachdem ein tomcat Docker Container gestartet wurde
- Manager App öffnen![img.png](doc/local_tomcat_deploy_1.png) 
- Bei WAR file to deploy die .war aus mvn package auswählen und hochladen![local_tomcat_deploy_2.png](doc/local_tomcat_deploy_2.png)
- Projekt öffnen (http://localhost:8080/ConnectFour)![local_tomcat_deploy_3.png](doc/local_tomcat_deploy_3.png)
- Success![local_tomcat_deploy_4.png](doc/local_tomcat_deploy_4.png)


### Task 1.b
Sh. https://gitlab.com/Shebbyy/fh-se-spw4-exercise3-sgradwohl

Die GitlabCI Pipeline wurde gemeinsam im Unterricht erstellt, dabei wurde im WSL der gitlab-runner aufgesetzt,
welcher in Docker Containern die einzelnen Jobs ausführt. Für das Deployment wird dann ein Shell-Runner verwendet, um 
direkt auf der Maschine den Tomcat Docker Container neu zu erstellen
Für das Setup vom Gitlab Runner wurde in der Übung auch die Doku aus SETUP.md verwendet

Hier ein Auszug aus dem Runner Log und Screenshots zu den einzelnen Jobs aus dem Gitlab UI 

![gitlab_ci_worker_cli.png](doc/gitlab_ci_worker_cli.png)
![gitlab_ci_overview.png](doc/gitlab_ci_overview.png)
![gitlab_ci_build.png](doc/gitlab_ci_build.png)
![gitlab_ci_test.png](doc/gitlab_ci_test.png)
![gitlab_ci_analyze.png](doc/gitlab_ci_analyze.png)
![gitlab_ci_package.png](doc/gitlab_ci_package.png)
![gitlab_ci_deploy_test_waiting.png](doc/gitlab_ci_deploy_test_waiting.png)
![gitlab_ci_deploy_test_done.png](doc/gitlab_ci_deploy_test_done.png)
![gitlab_ci_deploy.png](doc/gitlab_ci_deploy.png)
![gitlab_ci_stop_deployment.png](doc/gitlab_ci_stop_deployment.png)

### Task 1.c
Sh. https://github.com/Shebbyy/spw4_github_runner_testing

Docker Container wurde lt. SETUP.md aufgesetzt, für die Pipeline wurde sich an der Umsetzung
aus der Übung zu GitLab orientiert und die Implementation entsprechend umgesetzt.
Nachdem wir hier im Gegensatz zu Gitlab-CI bereits einen Container mit Tomcat für den Runner
verwenden bin ich davon ausgegangen, dass das Deployment eben auch über diesen stattfinden sollte,
eg. im Runner Container das Projekt deployed werden soll.

Hier einige Auszüge aus der CLI des Runners und des Github Action UIs, kann im oberen Repository referenziert werden
![github_worker.png](doc/github_worker.png)
![github_workflow_overview.png](doc/github_workflow_overview.png)
![github_workflow_build.png](doc/github_workflow_build.png)
![github_workflow_test.png](doc/github_workflow_test.png)
![github_workflow_analyze.png](doc/github_workflow_analyze.png)
![github_workflow_package.png](doc/github_workflow_package.png)
![github_workflow_deployment.png](doc/github_workflow_deployment.png)
![github_workflow_deployment_browser.png](doc/github_workflow_deployment_browser.png)