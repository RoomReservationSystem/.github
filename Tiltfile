# Allow only minikube context
allow_k8s_contexts('minikube')

# Load all service Tiltfiles
include('./config-service/config-service/Tiltfile')
include('./user-service/user-service/Tiltfile')
include('./room-service/room-service/Tiltfile')
include('./reservation-service /reservation-service/Tiltfile')
include('./notification-service/notification-service/Tiltfile')
include('./edge-service/edge-service/Tiltfile')

# Resource ordering (dependencies)
k8s_resource('config-service', resource_deps=[])
k8s_resource('user-service', resource_deps=['config-service', 'user-postgres'])
k8s_resource('room-service', resource_deps=['config-service', 'room-postgres'])
k8s_resource('reservation-service', resource_deps=['config-service', 'reservation-postgres', 'roomreservation-rabbitmq'])
k8s_resource('notification-service', resource_deps=['roomreservation-rabbitmq'])
k8s_resource('edge-service', resource_deps=['redis', 'user-service', 'room-service', 'reservation-service'])

