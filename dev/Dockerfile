
FROM continuumio/miniconda3

WORKDIR /app

ADD environment.yml /tmp/environment.yml
RUN conda env create -f /tmp/environment.yml
RUN echo "source activate nenv" > ~/.bashrc
ENV PATH /opt/conda/envs/nenv/bin:$PATH

EXPOSE 8002

# COPY wait-for-it.sh /usr/local/bin/
# ADD https://raw.githubusercontent.com/vishnubob/wait-for-it/master/wait-for-it.sh  /usr/local/bin/
ADD https://raw.githubusercontent.com/vishnubob/wait-for-it/9995b721327eac7a88f0dce314ea074d5169634f/wait-for-it.sh  /usr/local/bin/
RUN chmod +x /usr/local/bin/wait-for-it.sh
CMD ["/usr/local/bin/wait-for-it.sh", "postgres:5432", "--", "python", "manage.py", "runserver", "0.0.0.0:8002"]

