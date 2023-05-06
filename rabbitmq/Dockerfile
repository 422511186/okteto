FROM rabbitmq:3.8-management

# 添加插件到指定目录 可按照此方式自行扩展其他插件
ADD ./rabbitmq_delayed_message_exchange.ez /plugins

# 开启插件
RUN rabbitmq-plugins enable rabbitmq_management
RUN rabbitmq-plugins enable rabbitmq_delayed_message_exchange

# 创建RabbitMQ管理员
RUN rabbitmqctl add_user admin admin
RUN rabbitmqctl set_user_tags admin administrator
RUN rabbitmqctl set_permissions -p / admin ".*" ".*" ".*"

# 打开管理页面远程访问
RUN rabbitmq-plugins enable rabbitmq_management_agent
RUN rabbitmqctl stop_app && rabbitmqctl start_app --management

EXPOSE 5672
EXPOSE 15672

ENTRYPOINT ["rabbitmq-server"]
