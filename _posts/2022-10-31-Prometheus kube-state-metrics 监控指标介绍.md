## Deployment

```cn
kube_deployment_status_replicas  #Gauge类型，每个deployment的副本数。
kube_deployment_status_replicas_available  #Gauge类型，每个deployment的可用副本数
kube_deployment_status_replicas_unavailable  #Gauge类型，每个deployment中不可用副本的数量
kube_deployment_status_replicas_updated  #Gauge类型，每个deployment的更新副本数
kube_deployment_status_observed_generation  #Gauge类型，deployment控制器观察到的生成
kube_deployment_status_condition  #Gauge类型，部署的当前状态condition
kube_deployment_spec_replicas  #Gauge类型，deployment所需的Pod数
kube_deployment_spec_paused  #Gauge类型，deployment是否暂停，并且deployment控制器不会处理。
kube_deployment_spec_strategy_rollingupdate_max_unavailable  #Gauge类型，
kube_deployment_spec_strategy_rollingupdate_max_surge  #Gauge类型，滚动更新deployment期间的最大不可用副本数。
kube_deployment_metadata_generation  #Gauge类型，代表期望状态的特定生成的序列号
kube_deployment_labels  #Gauge类型，Kubernetes标签转换为Prometheus标签
kube_deployment_created  #Gauge类型，Unix创建时间戳
```

## DaemonSet

```cn
kube_daemonset_created  #gauge类型，Unix创建时间戳
kube_daemonset_status_current_number_scheduled  #gauge类型，运行至少一个且应该运行的守护程序容器的节点数。
kube_daemonset_status_desired_number_scheduled  #gauge类型，应该运行守护程序容器的节点数。
kube_daemonset_status_number_available  #gauge类型，应该运行守护程序容器并具有一个或多个守护程序容器正在运行并且可用的节点数
kube_daemonset_status_number_misscheduled  #gauge类型，运行守护程序容器但不应该运行的节点数。
kube_daemonset_status_number_ready  #gauge类型，应该运行守护程序容器并已运行一个或多个守护程序容器并准备就绪的节点数。
kube_daemonset_status_number_unavailable  #gauge类型，应该运行守护程序容器且没有任何守护程序容器正在运行并且可用的节点数
kube_daemonset_updated_number_scheduled  #gauge类型，正在运行更新的守护程序pod的节点总数
kube_daemonset_metadata_generation  #gauge类型，代表所需状态的特定生成的序列号。
kube_daemonset_labels  #gauge类型，Kubernetes标签转换为Prometheus标签。
```

## StatefulSet

```cn
kube_statefulset_status_replicas #Gauge类型，每个StatefulSet的副本数。
kube_statefulset_status_replicas_current #Gauge类型，每个StatefulSet的当前副本数。
kube_statefulset_status_replicas_ready #Gauge类型，每个StatefulSet的就绪副本数。
kube_statefulset_status_replicas_updated #Gauge类型，每个StatefulSet的更新副本数。
kube_statefulset_status_observed_generation #Gauge类型，StatefulSet控制器观察到的生成。
kube_statefulset_replicas #Gauge类型，StatefulSet所需的pod数。
kube_statefulset_metadata_generation #Gauge类型，表示StatefulSet所需状态的特定生成的序列号。
kube_statefulset_created #Gauge类型，Unix创建时间戳。
kube_statefulset_labels #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_statefulset_status_current_revision #Gauge类型，指示用于按顺序[0，currentReplicas）生成Pod的StatefulSet的版本。
kube_statefulset_status_update_revision #Gauge类型，指示用于按顺序[replicas-updatedReplicas，replicas]生成Pod的StatefulSet的版本。
```

## ConfigMap

```cn
kube_configmap_info  #gauge类型，有关configmap的信息
kube_configmap_created  #gauge类型，Unix创建时间戳
kube_configmap_metadata_resource_version  #gauge类型，表示configmap特定版本的资源版本。
```

## CronJob

```cn
kube_cronjob_info   #gauge类型，关于cronjob的信息
kube_cronjob_labels  #gauge类型，Kubernetes标签转换为Prometheus标签。
kube_cronjob_created  #gauge类型，Unix创建时间戳
kube_cronjob_next_schedule_time  #gauge类型，下次应该安排cronjob。 在lastScheduleTime之后的时间，或者在cron作业的创建时间之后（如果从未计划过）。 使用它来确定作业是否延迟。
kube_cronjob_status_active  #gauge类型，活动保持指向当前正在运行的作业的指针。
kube_cronjob_status_last_schedule_time  #gauge类型，LastScheduleTime保留有关上一次成功调度作业的时间的信息。
kube_cronjob_spec_suspend  #gauge类型，挂起标志告诉控制器挂起后续执行。
kube_cronjob_spec_starting_deadline_seconds  #gauge类型，如果由于任何原因错过了计划时间，则开始工作的最后期限（以秒为单位）。
```

## Endpoint

```cn
kube_endpoint_address_not_ready  #Gauge类型，endpoint中not ready的addresses数
kube_endpoint_address_available  #Gauge类型，endpoint中可用的addresses数。
kube_endpoint_info  #Gauge类型，有关endpoint的信息
kube_endpoint_labels  #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_endpoint_created  #Gauge类型，Unix创建时间戳
```

## Horizontal Pod Autoscaler

```cn
kube_horizontalpodautoscaler_labels  #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_horizontalpodautoscaler_metadata_generation  #Gauge类型，通过HorizontalPodAutoscaler控制器观察到的生成。
kube_horizontalpodautoscaler_spec_max_replicas  #Gauge类型，自动定标器可以设置的容器数量上限； 不能小于MinReplicas。
kube_horizontalpodautoscaler_spec_min_replicas  #Gauge类型，自动定标器可以设置的Pod数量下限，默认为1。
kube_horizontalpodautoscaler_spec_target_metric  #Gauge类型，此自动定标器在计算所需副本数时使用的度量标准。
kube_horizontalpodautoscaler_status_condition  #Gauge类型，此自动定标器的条件。
kube_horizontalpodautoscaler_status_current_replicas  #Gauge类型，此自动缩放器管理的Pod的当前副本数。
kube_horizontalpodautoscaler_status_desired_replicas  #Gauge类型，此自动缩放器管理的所需Pod副本数。
```

## Ingress

```cn
kube_ingress_info  #Gauge类型，有关ingress的信息
kube_ingress_labels  #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_ingress_created  #Gauge类型，Unix创建时间戳
kube_ingress_metadata_resource_version  #Gauge类型，代表特定ingress版本的资源版本。
kube_ingress_path  #Gauge类型，ingress host, paths and backend service 信息。
kube_ingress_tls  #Gauge类型，ingress TLS host and secret 信息。
```

## Job

```cn
kube_job_info  #Gauge类型，有关job的信息。
kube_job_labels  #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_job_owner  #Gauge类型，有关job所有者的信息。
kube_job_spec_parallelism  #Gauge类型，在任何给定时间，job应运行的pod的最大期望数量。
kube_job_spec_completions  #Gauge类型，运行job所需的成功完成的Pod数量。
kube_job_spec_active_deadline_seconds  #Gauge类型，在系统尝试终止job之前，作业相对于startTime的活动持续时间（以秒为单位）。
kube_job_status_active  #Gauge类型，正在运行的pod数。
kube_job_status_succeeded  #Gauge类型，成功reached Phase的pod数量。
kube_job_status_failed  #Gauge类型，Failed reached Phase的pod数量。
kube_job_status_start_time  #Gauge类型，StartTime表示作业Job Manager job的时间。
kube_job_status_completion_time  #Gauge类型，CompletionTime表示job完成的时间。
kube_job_complete  #Gauge类型，job已完成执行。
kube_job_failed  #Gauge类型，job执行失败。
kube_job_created  #Gauge类型，Unix创建时间戳。
```

## Lease

```cn
kube_lease_owner #Gauge类型，有关lease所有者的信息。
kube_lease_renew_time #Gauge类型,Kube lease续订时间。
```

## LimitRange

```cn
kube_limitrange #Gauge类型，有关limitrange的信息。
kube_limitrange_created #Gauge类型，Unix创建时间戳
```

## MutatingWebhookConfiguration

```cn
kube_mutatingwebhookconfiguration_info #Gauge类型，有关MutatingWebhookConfiguration的信息。
kube_mutatingwebhookconfiguration_created #Gauge类型，Unix创建时间戳。
kube_mutatingwebhookconfiguration_metadata_resource_version #Gauge类型，资源版本，表示MutatingWebhookConfiguration的特定版本。
```

## Namespace

```cn
kube_namespace_created #Gauge类型，Unix创建时间戳。
kube_namespace_labels #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_namespace_status_condition #Gauge类型，命名空间的状态。
kube_namespace_status_phase #Gauge类型，kubernetes命名空间状态阶段。
```

## Network Policy

```cn
kube_networkpolicy_created #Gauge类型，Unix创建时间戳。
kube_networkpolicy_labels #Gauge类型，
kube_networkpolicy_spec_egress_rules #Gauge类型，规格出口规则
kube_networkpolicy_spec_ingress_rules #Gauge类型，规格入口规则
```

## Node

```cn
kube_node_info #Gauge类型，有关群集节点的信息。
kube_node_labels #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_node_role #Gauge类型，集群节点的角色。
kube_node_spec_unschedulable #Gauge类型，节点是否可以调度新的Pod。
kube_node_spec_taint #Gauge类型，群集节点的污点。
kube_node_status_capacity #Gauge类型，节点不同资源的容量。
kube_node_status_allocatable #Gauge类型，可用于调度的节点的不同资源的可分配资源。
kube_node_status_condition #Gauge类型，群集节点的状况。
kube_node_created #Gauge类型，Unix创建时间戳。
```

## PersistentVolume

```cn
kube_persistentvolume_capacity_bytes #Gauge类型，persistentvolume（持久卷）容量（以字节为单位）。
kube_persistentvolume_status_phase #Gauge类型，该阶段指示某个卷是否可用，绑定到声明或由声明释放。
kube_persistentvolume_labels #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_persistentvolume_info #Gauge类型，有关持久卷的信息。
```

## PersistentVolumeClaim

```cn
kube_persistentvolumeclaim_access_mode #Gauge类型，永久卷声明指定的访问模式。
kube_persistentvolumeclaim_info #Gauge类型，有关持久卷声明的信息。
kube_persistentvolumeclaim_labels #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_persistentvolumeclaim_resource_requests_storage_bytes #Gauge类型，持久卷声明所请求的存储容量。
kube_persistentvolumeclaim_status_condition #Gauge类型，有关持续量索赔的不同条件的状态的信息。
kube_persistentvolumeclaim_status_phase #Gauge类型，永久批量声明当前处于此阶段。
```

## PodDisruptionBudget

```cn
kube_poddisruptionbudget_created #Gauge类型，Unix创建时间戳。
kube_poddisruptionbudget_status_current_healthy #Gauge类型，当前健康pod的数量
kube_poddisruptionbudget_status_desired_healthy #Gauge类型，所需的健康pod的最小数量
kube_poddisruptionbudget_status_pod_disruptions_allowed #Gauge类型，当前允许的pod中断次数
kube_poddisruptionbudget_status_expected_pods #Gauge类型，此中断预算计算的pod总数
kube_poddisruptionbudget_status_observed_generation #Gauge类型，更新此PDB状态时观察到的最新一代
```

## Pod

```cn
kube_pod_info #Gauge类型，有关pod的信息。
kube_pod_start_time #Gauge类型，pod的unix时间戳记中的开始时间。
kube_pod_completion_time #Gauge类型，pod的unix时间戳记中的完成时间。
kube_pod_owner #Gauge类型，有关Pod所有者的信息。
kube_pod_labels #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_pod_status_phase #Gauge类型，Pod当前阶段。
kube_pod_status_ready #Gauge类型，描述容器是否准备好处理请求。
kube_pod_status_scheduled #Gauge类型，描述pod的调度过程的状态。
kube_pod_container_info #Gauge类型，有关容器中container的信息。
kube_pod_container_status_waiting #Gauge类型，描述容器当前是否处于等待状态。
kube_pod_container_status_waiting_reason #Gauge类型，描述容器当前处于等待状态的原因。
kube_pod_container_status_running #Gauge类型，描述容器当前是否处于运行状态。
kube_pod_container_status_terminated #Gauge类型，描述容器当前是否处于终止状态。
kube_pod_container_status_terminated_reason #Gauge类型，描述容器当前处于终止状态的原因。
kube_pod_container_status_last_terminated_reason #Gauge类型，描述容器处于终止状态的最后原因。
kube_pod_container_status_ready #Gauge类型，Describes whether the containers readiness check succeeded.
kube_pod_container_status_restarts_total #Gauge类型，每个容器的容器重新启动次数。
kube_pod_container_resource_requests #Gauge类型，容器请求的请求资源数。
kube_pod_container_resource_limits #Gauge类型，容器请求的限制资源数量。
kube_pod_overhead #Gauge类型
kube_pod_created #Gauge类型，Unix创建时间戳。
kube_pod_deletion_timestamp #Gauge类型，Unix删除时间戳
kube_pod_restart_policy #Gauge类型，描述此pod使用的重新启动策略。
kube_pod_init_container_info #Gauge类型，有关Pod中init容器的信息。
kube_pod_init_container_status_waiting #Gauge类型，描述初始化容器当前是否处于等待状态。
kube_pod_init_container_status_waiting_reason #Gauge类型，Describes the reason the init container is currently in waiting state.
kube_pod_init_container_status_running #Gauge类型，描述初始化容器当前是否处于运行状态。
kube_pod_init_container_status_terminated #Gauge类型，描述初始化容器当前是否处于终止状态。
kube_pod_init_container_status_terminated_reason #Gauge类型，描述初始化容器当前处于终止状态的原因。
kube_pod_init_container_status_last_terminated_reason #Gauge类型，描述初始化容器处于终止状态的最后原因。
kube_pod_init_container_status_ready #Gauge类型，描述初始化容器准备情况检查是否成功。
kube_pod_init_container_status_restarts_total  #Counter类型，初始化容器的重新启动次数。    
kube_pod_init_container_resource_limits #Gauge类型，初始化容器请求的限制资源数。
kube_pod_spec_volumes_persistentvolumeclaims_info #Gauge类型，有关Pod中持久卷声明卷的信息。
kube_pod_spec_volumes_persistentvolumeclaims_readonly #Gauge类型，描述是否以只读方式安装了持久卷声明。
kube_pod_status_reason #Gauge类型，pod状态原因
kube_pod_status_scheduled_time #Gauge类型，Pod移至计划状态时的Unix时间戳
kube_pod_status_unschedulable #Gauge类型，描述pod的unschedulable状态。
```

## ReplicaSet

```cn
kube_replicaset_status_replicas #Gauge类型，每个ReplicaSet的副本数。
kube_replicaset_status_fully_labeled_replicas #Gauge类型，每个ReplicaSet的全标签副本数。
kube_replicaset_status_ready_replicas #Gauge类型，每个ReplicaSet的就绪副本数。
kube_replicaset_status_observed_generation #Gauge类型，ReplicaSet控制器观察到的生成。
kube_replicaset_spec_replicas #Gauge类型，ReplicaSet所需的pods数。
kube_replicaset_metadata_generation #Gauge类型，代表所需状态的特定生成的序列号。
kube_replicaset_labels #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_replicaset_created #Gauge类型，Unix创建时间戳。
kube_replicaset_owner #Gauge类型，有关副本集所有者的信息。
```

## ReplicationController

```cn
kube_replicationcontroller_status_replicas #Gauge类型，每个ReplicationController的副本数。
kube_replicationcontroller_status_fully_labeled_replicas #Gauge类型，每个ReplicationController具有完全标记的副本数。
kube_replicationcontroller_status_ready_replicas #Gauge类型，每个ReplicationController的就绪副本数。
kube_replicationcontroller_status_available_replicas #Gauge类型，每个ReplicationController可用副本的数量。
kube_replicationcontroller_status_observed_generation #Gauge类型，ReplicationController控制器观察到的生成。
kube_replicationcontroller_spec_replicas #Gauge类型，ReplicationController所需的Pod数。
kube_replicationcontroller_metadata_generation #Gauge类型，代表所需状态的特定生成的序列号。
kube_replicationcontroller_created #Gauge类型，Unix创建时间戳。
kube_replicationcontroller_owner #Gauge类型，有关ReplicationController所有者的信息。
```

## ResourceQuota

```cn
kube_resourcequota #Gauge类型，有关资源配额的信息。
kube_resourcequota_created #Gauge类型，Unix创建时间戳。
```

## Secret

```cn
kube_secret_info #Gauge类型，有关secret的信息。
kube_secret_type #Gauge类型，Type about secret.
kube_secret_labels #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_secret_created #Gauge类型，Unix创建时间戳。
kube_secret_metadata_resource_version #Gauge类型，代表secret特定版本的资源版本。
```

## Service

```cn
kube_service_info #Gauge类型，有关service的信息。
kube_service_labels #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_service_created #Gauge类型，Unix创建时间戳。
kube_service_spec_type #Gauge类型，Type about service.
kube_service_spec_external_ip #Gauge类型，服务外部IP。 每个IP一个组。
kube_service_status_load_balancer_ingress #Gauge类型，服务负载均衡器入口状态
```

## StorageClass

```cn
kube_storageclass_info #Gauge类型，有关storageclass的信息。
kube_storageclass_labels #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_storageclass_created #Gauge类型，Unix创建时间戳。
```

## ValidatingWebhookConfiguration

```cn
kube_validatingwebhookconfiguration_info #Gauge类型，有关ValidatingWebhookConfiguration的信息。
kube_validatingwebhookconfiguration_created #Gauge类型，Unix创建时间戳。
kube_validatingwebhookconfiguration_metadata_resource_version #Gauge类型，表示ValidatingWebhookConfiguration特定版本的资源版本。
```

## Vertical Pod Autoscaler

```cn
kube_verticalpodautoscaler_spec_resourcepolicy_container_policies_minallowed #Gauge类型，VerticalPodAutoscaler可以为与名称匹配的容器设置的最小资源。
kube_verticalpodautoscaler_spec_resourcepolicy_container_policies_maxallowed #Gauge类型，VerticalPodAutoscaler可以为与名称匹配的容器设置的最大资源。
kube_verticalpodautoscaler_status_recommendation_containerrecommendations_lowerbound #Gauge类型，在VerticalPodAutoscaler更新程序逐出容器之前，容器可以使用的最少资源。
kube_verticalpodautoscaler_status_recommendation_containerrecommendations_target #Gauge类型，VerticalPodAutoscaler为容器推荐的目标资源。
kube_verticalpodautoscaler_status_recommendation_containerrecommendations_uncappedtarget #Gauge类型，VerticalPodAutoscaler建议的目标资源，用于忽略边界的容器。
kube_verticalpodautoscaler_status_recommendation_containerrecommendations_upperbound #Gauge类型，在VerticalPodAutoscaler更新程序逐出容器之前，容器可以使用的最大资源。
kube_verticalpodautoscaler_labels #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_verticalpodautoscaler_spec_updatepolicy_updatemode #Gauge类型，VerticalPodAutoscaler的更新模式。
```

## Vertical Pod Autoscaler

```cn
kube_verticalpodautoscaler_spec_resourcepolicy_container_policies_minallowed #Gauge类型，VerticalPodAutoscaler可以为与名称匹配的容器设置的最小资源。
kube_verticalpodautoscaler_spec_resourcepolicy_container_policies_maxallowed #Gauge类型，VerticalPodAutoscaler可以为与名称匹配的容器设置的最大资源。
kube_verticalpodautoscaler_status_recommendation_containerrecommendations_lowerbound #Gauge类型，在VerticalPodAutoscaler更新程序逐出容器之前，容器可以使用的最少资源。
kube_verticalpodautoscaler_status_recommendation_containerrecommendations_target #Gauge类型，VerticalPodAutoscaler为容器推荐的目标资源。
kube_verticalpodautoscaler_status_recommendation_containerrecommendations_uncappedtarget #Gauge类型，VerticalPodAutoscaler建议的目标资源，用于忽略边界的容器。
kube_verticalpodautoscaler_status_recommendation_containerrecommendations_upperbound #Gauge类型，在VerticalPodAutoscaler更新程序逐出容器之前，容器可以使用的最大资源。
kube_verticalpodautoscaler_labels #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_verticalpodautoscaler_spec_updatepolicy_updatemode #Gauge类型，VerticalPodAutoscaler的更新模式。
```

## VolumeAttachment

```cn
kube_volumeattachment_info #Gauge类型，有关volumeattachment的信息。
kube_volumeattachment_created #Gauge类型，Unix创建时间戳。
kube_volumeattachment_labels #Gauge类型，Kubernetes标签转换为Prometheus标签。
kube_volumeattachment_spec_source_persistentvolume #Gauge类型，PersistentVolume源参考。
kube_volumeattachment_status_attached #Gauge类型，Information about volumeattachment. status
kube_volumeattachment_status_attachment_metadata #Gauge类型，volumeattachment metadata.
```