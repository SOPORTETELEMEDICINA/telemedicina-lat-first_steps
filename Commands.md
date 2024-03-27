# Comandos para imágenes en servidores

Los nombres de las imágenes utilizadas en cada comando se tienen que actualizar dependiendo del servidor o el nombre de la imagen que se haya hecho en local

# ECE Telemedicina

docker container run -d -p 9113:9113 --restart=unless-stopped --name tlm-ece-security --link eureka-server --add-host ece.telemedicina.lat:98.142.96.170 -v /var/www/telemedicina/logs:/logs 98.142.96.170:5000/nio-security:20042022

docker container run -d -p 9120:9120 --restart=unless-stopped --name tlm-ece-catalogos --link eureka-server --add-host ece.telemedicina.lat:98.142.96.170 -v /opt/docker-registry:/opt/lucee -v /var/www/telemedicina/logs:/logs 98.142.96.170:5000/nio-catalogos:20072021

docker container run -d -p 9114:9114 --restart=unless-stopped --name tlm-ece-expediente --link eureka-server --add-host ece.telemedicina.lat:98.142.96.170 -v /opt/docker-registry:/opt/lucee -v /var/www/telemedicina/logs:/logs -v /var/www/html/niomedic/documentos:/var/www/html/niomedic/documentos -v /var/www/html/niomedic/imagenesLaboratorio:/var/www/html/niomedic/imagenesLaboratorio 98.142.96.170:5000/tlm-ece-expediente:10082022

docker container run -d -p 9115:9115 --restart=unless-stopped --name tlm-ece-medicos --link eureka-server --add-host ece.telemedicina.lat:98.142.96.170 -v /opt/docker-registry:/opt/lucee -v /var/www/telemedicina/logs:/logs -v /var/www/html/niomedic/cedula:/var/www/html/niomedic/cedula -v /var/www/html/niomedic/titulo:/var/www/html/niomedic/titulo 98.142.96.170:5000/nio-medicos:11012022

docker container run -d -p 9119:9119 --restart=unless-stopped --name tlm-ece-receta --link eureka-server --add-host ece.telemedicina.lat:98.142.96.170 -v /var/www/telemedicina/logs:/logs 98.142.96.170:5000/nio-receta:20072021

docker container run -d -p 9112:9112 --restart=unless-stopped --name tlm-ece-pacientes --link eureka-server --add-host ece.telemedicina.lat:98.142.96.170 -v /var/www/telemedicina/logs:/logs 98.142.96.170:5000/tlm-ece-pacientes:10082022

docker container run -d -p 9121:9121 --restart=unless-stopped --name tlm-ece-agenda-medicos --link eureka-server --add-host ece.telemedicina.lat:98.142.96.170 -v /opt/docker-registry:/opt/lucee -v /var/www/telemedicina/logs:/logs 98.142.96.170:5000/nio-agenda-medicos:20042022

docker container run -d -p 9111:9111 --restart=unless-stopped --name tlm-ece-gateway --link tlm-ece-medicos:nio-medicos --link tlm-ece-pacientes:nio-pacientes --link tlm-ece-expediente:nio-expediente --link eureka-server --link tlm-ece-security:nio-security --link tlm-ece-receta:nio-receta --link tlm-ece-catalogos:nio-catalogos --link tlm-ece-agenda-medicos:nio-agenda-medicos --add-host ece.telemedicina.lat:98.142.96.170 -v /var/www/telemedicina/logs:/logs -v /opt/docker-registry:/opt/lucee 98.142.96.170:5000/tlm-ece-gateway:10082022

# CCT Telemedicina

docker container run -d -p 9214:9214 --restart=unless-stopped --name nio-expediente2 --link eureka-server2 --add-host cct.telemedicina.lat:98.142.96.171 -v /opt/docker-registry:/opt/lucee -v /home/logstmed2:/logs -v /var/www/html/niomedic/documentos:/var/www/html/niomedic/documentos -v /var/www/html/niomedic/imagenesLaboratorio:/var/www/html/niomedic/imagenesLaboratorio 98.142.96.171:5000/nio-expediente:EventosFix

docker container run -d -p 9215:9215 --restart=unless-stopped --name nio-medicos2 --link eureka-server2 --add-host cct.telemedicina.lat:98.142.96.171 -v /opt/docker-registry:/opt/lucee -v /var/www/telemedicina/logs:/logs -v /var/www/html/niomedic/cedula:/var/www/html/niomedic/cedula -v /var/www/html/niomedic/titulo:/var/www/html/niomedic/titulo 98.142.96.171:5000/nio-medicos:BugsAgenda

docker container run -d -p 9221:9221 --restart=unless-stopped --name nio-agenda-medicos --link eureka-server2 --add-host cct.telemedicina.lat:98.142.96.171 -v /opt/docker-registry:/opt/lucee -v /var/www/telemedicina/logs:/logs 98.142.96.171:5000/tlm-agenda-medicos:BugsAgenda

docker container run -d -p 9213:9213 --restart=unless-stopped --name nio-security2 --link eureka-server2 --add-host cct.telemedicina.lat:98.142.96.171 -v /home/logstmed2:/logs 98.142.96.171:5000/nio-security:BugLogin

docker container run -d -p 9212:9212 --restart=unless-stopped --name nio-pacientes2 --link eureka-server2 --add-host cct.telemedicina.lat:98.142.96.171 -v /var/www/telemedicina/logs:/logs 98.142.96.171:5000/nio-pacientes:CampoUnidadMedica

docker container run -d -p 9211:9211 --restart=unless-stopped --name nio-gateway2 --link nio-medicos2:nio-medicos --link nio-pacientes2:nio-pacientes --link nio-expediente2:nio-expediente --link eureka-server2 --link nio-security2:nio-security --link nio-receta2:nio-receta --link nio-catalogos2:nio-catalogos --link nio-agenda-medicos:nio-agenda-medicos --add-host cct.telemedicina.lat:98.142.96.171 -v /home/logstmed2:/logs -v /opt/docker-registry:/opt/lucee 98.142.96.171:5000/nio-gateway:EventosFix

# Consulta en Linea

docker container run -d -p 9120:9120 --restart=unless-stopped --name tlm-catalogos --link eureka-server --add-host expediente.consultaenlinea.mx:74.208.19.84 -v /opt/docker-registry:/opt/lucee -v /var/www/telemedicina/logs:/logs 74.208.19.84:5000/tlm-catalogos:latest

docker container run -d -p 9114:9114 --restart=unless-stopped --name tlm-expediente --link eureka-server --add-host expediente.consultaenlinea.mx:74.208.19.84 -v /opt/docker-registry:/opt/lucee -v /var/www/telemedicina/logs:/logs -v /var/www/html/niomedic/documentos:/var/www/html/niomedic/documentos -v /var/www/html/niomedic/imagenesLaboratorio:/var/www/html/niomedic/imagenesLaboratorio 74.208.19.84:5000/nio-expediente:IndicadoresMedidas

docker container run -d -p 9115:9115 --restart=unless-stopped --name tlm-medicos --link eureka-server --add-host expediente.consultaenlinea.mx:74.208.19.84 -v /opt/docker-registry:/opt/lucee -v /var/www/telemedicina/logs:/logs -v /var/www/html/niomedic/cedula:/var/www/html/niomedic/cedula -v /var/www/html/niomedic/titulo:/var/www/html/niomedic/titulo 74.208.19.84:5000/tlm-medicos:latest

docker container run -d -p 9119:9119 --restart=unless-stopped --name tlm-receta --link eureka-server --add-host expediente.consultaenlinea.mx:74.208.19.84 -v /var/www/telemedicina/logs:/logs 74.208.19.84:5000/tlm-receta:latest

docker container run -d -p 9112:9112 --restart=unless-stopped --name tlm-pacientes --link eureka-server --add-host expediente.consultaenlinea.mx:74.208.19.84 -v /var/www/telemedicina/logs:/logs 74.208.19.84:5000/tlm-pacientes:latest

docker container run -d -p 9113:9113 --restart=unless-stopped --name tlm-security --link eureka-server --add-host expediente.consultaenlinea.mx:74.208.19.84 -v /var/www/telemedicina/logs:/logs 74.208.19.84:5000/tlm-security:latest

docker container run -d -p 9111:9111 --restart=unless-stopped --name tlm-gateway --link tlm-medicos:tlm-medicos --link tlm-pacientes:tlm-pacientes --link tlm-expediente:tlm-expediente --link eureka-server --link tlm-security:tlm-security --link tlm-receta:tlm-receta --link tlm-catalogos:tlm-catalogos --add-host expediente.consultaenlinea.mx:74.208.19.84 -v /var/www/telemedicina/logs:/logs -v /opt/docker-registry:/opt/lucee 74.208.19.84:5000/tlm-gateway:latest

# Certificación

docker container run -d -p 9001:9001 --restart=unless-stopped --name local-cfg --add-host certificacion.telemedicina.lat:198.251.78.70 -v /var/www/telemedicina/localcfg:/localcfg 198.251.78.70:5000/local-cfg-server:latest

docker container run -d -p 9002:9002 --restart=unless-stopped --name eureka-server --add-host certificacion.telemedicina.lat:198.251.78.70 -v /var/www/telemedicina/localcfg:/localcfg 198.251.78.70:5000/local-eureka-server:latest

docker container run -d -p 9120:9120 --restart=unless-stopped --name nio-catalogos --link eureka-server --add-host certificacion.telemedicina.lat:198.251.78.70 -v /var/www/telemedicina/logs:/logs 198.251.78.70:5000/nio-catalogos:latest

docker container run -d -p 9114:9114 --restart=unless-stopped --name nio-expediente --link eureka-server --add-host certificacion.telemedicina.lat:198.251.78.70 -v /var/www/telemedicina/logs:/logs -v /var/www/telemedicina/localcfg/cifrado:/cifrado -v /var/www/html/niomedic/documentos:/var/www/html/niomedic/documentos -v /var/www/html/niomedic/imagenesLaboratorio:/var/www/html/niomedic/imagenesLaboratorio 198.251.78.70:5000/nio-expediente:latest

docker container run -d -p 9115:9115 --restart=unless-stopped --name nio-medicos --link eureka-server --add-host certificacion.telemedicina.lat:198.251.78.70 -v /var/www/telemedicina/logs:/logs -v /var/www/html/niomedic/cedula:/var/www/html/niomedic/cedula -v /var/www/html/niomedic/titulo:/var/www/html/niomedic/titulo 198.251.78.70:5000/nio-medicos:latest

docker container run -d -p 9112:9112 --restart=unless-stopped --name nio-pacientes --link eureka-server --add-host certificacion.telemedicina.lat:198.251.78.70 -v /var/www/telemedicina/logs:/logs 198.251.78.70:5000/nio-pacientes:latest

docker container run -d -p 9119:9119 --restart=unless-stopped --name nio-receta --link eureka-server --add-host certificacion.telemedicina.lat:198.251.78.70 -v /var/www/telemedicina/logs:/logs 198.251.78.70:5000/nio-receta:latest

docker container run -d -p 9113:9113 --restart=unless-stopped --name nio-security --link eureka-server --add-host certificacion.telemedicina.lat:198.251.78.70 -v /var/www/telemedicina/logs:/logs 198.251.78.70:5000/nio-security:latest

docker container run -d -p 9111:9111 --restart=unless-stopped --name nio-gateway --link nio-medicos:nio-medicos --link nio-pacientes:nio-pacientes --link nio-expediente:nio-expediente --link eureka-server --link nio-security:nio-security --link nio-receta:nio-receta --link nio-catalogos:nio-catalogos --add-host certificacion.telemedicina.lat:198.251.78.70 -v /var/www/telemedicina/logs:/logs -v /var/www/telemedicina/key-store:/opt/lucee 198.251.78.70:5000/nio-gateway:latest
