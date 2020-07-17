## First week summary with question and answers.

### Question- Why OAM users needs GItOps? 

> OAM users needs GitOps because of multiple reasons some of them listed below -
- <b>Deploy Faster More Often</b> When we say “high velocity” we mean that every product team can safely ship updates many times a day — deploy instantly, observe the results in real time, and use this feedback to roll forward or back.
- <b>Easy and Fast Error Recovery</b> — The Git record is then not just an audit log but also a transaction log. You can roll back & forth to any snapshot.
GitOps you have a complete history of how your environment changed over time. This makes error recovery as easy as issuing a git revert and watching your environment being restored.

- <b>Easier Credential Management</b> — GitOps allows you to manage deployments completely from inside your environment. For that, your environment only needs access to your repository and image registry. That’s it. You don’t have to give your developers direct access to the environment.
- <b>Modular architecture</b> -: GitOps has three parts: the Git repo, the deployment process, and possibly a process that automates version updates in the Git repo. All three of these can evolve or be replaced independently of each other.
- <b>Tool-independent architecture</b> -:The modularity mentioned in point No. 4 directly leads to the fact that a GitOps architecture is one where you can assemble the best tools in a flexible way. Any popular Git server will do the Git part of course, and Flux or ArgoCD can take care of syncing the repo to the cluster. JenkinsX is a tool which handles all parts of this process, including creating the Git repos and updating them with new version updates when a new Docker image is built.

### Question- What the additional values provide by Argo or Flux? Why we choose one over other?

We believe both projects, Flux and ArgoCD have very interesting and powerful capabilities to manage deployments in Kubernetes, but each come with pros and cons that should be evaluated for our specific case. These tools aren’t really competing with each other, rather they are aiming to fulfill different use-cases.<br>
ArgoCD feels like the big brother of Flux. It’s a feature-rich tool with a flawless integration to Kubernetes. We really liked the fact that, even though it has a ton of features, its scope is very clear: it synchronises manifests from the Git repositories to the clusters.
- Argo CD follows the GitOps pattern of using Git repositories as the source of truth for defining the desired application state.

> I think we have to choose Argo CD over Flux because-
- Flux allows us to connect only one repository per instance of Flux operator, ArgoCD can connect multiple git repositories to one cluster. This is useful if you have multiple teams that provide manifests for Kubernetes or if you decide to keep application manifests along with the application code.
- ArgoCD is much more powerful – one instance of ArgoCD can manage multiple clusters, so you can create a nice, centralized tool to manage all your clusters from one place, which is very handy.
- ArgoCD comes with a very nice GUI that simplifies monitoring the state of your applications. The GUI also visualizes all relations between the objects in the app manifests.
- ArgoCD is also more ready for enterprise usage – it features SSO as well as builtin support for role-based access control. Flux – as it’s just a controller – is limited to the Kubernetes RBAC for the service account the controller is associated.

