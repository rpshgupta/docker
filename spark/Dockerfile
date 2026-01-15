FROM spark:4.0.1-scala2.13-java17-python3-ubuntu
ENV PATH="$SPARK_HOME/bin:${PATH}"

# SHELL [ "/bin/bash", "-c" ]

USER root
EXPOSE 8080 8888 4040

RUN pip install jupyterlab==4.5.0
RUN pip install pyspark==4.0.1
RUN pip install deltalake==1.2.0
RUN pip install kafka-python==2.2.13

CMD ["python3", "-m", "jupyterlab", "--ip", "0.0.0.0", "--allow-root"]

# CMD [ "pyspark" ]