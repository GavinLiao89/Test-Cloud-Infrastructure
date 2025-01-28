FROM mcr.microsoft.com/mmlspark/release:latest

RUN apt-get update && apt-get install -y git && apt-get clean

# env setting for the Jupyter Notebook
ENV ACCEPT_EULA=yes
ENV JUPYTER_CONFIG_DIR=/etc/jupyter

# disable security token
RUN mkdir -p $JUPYTER_CONFIG_DIR && \
    echo "c.NotebookApp.token = ''" >> $JUPYTER_CONFIG_DIR/jupyter_notebook_config.py && \
    echo "c.NotebookApp.ip = '0.0.0.0'" >> $JUPYTER_CONFIG_DIR/jupyter_notebook_config.py && \
    echo "c.NotebookApp.open_browser = False" >> $JUPYTER_CONFIG_DIR/jupyter_notebook_config.py

EXPOSE 8888

# start Jupyter Notebook when open
ENTRYPOINT ["jupyter", "notebook", "--allow-root", "--no-browser", "--port=8888", "--notebook-dir=/"]