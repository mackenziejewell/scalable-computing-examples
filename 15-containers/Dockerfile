# Dockerfile for ADC Scalable Computing Course
# ADC Course Model image
FROM ubuntu:22.04
SHELL ["/bin/bash", "-c"]
WORKDIR /home/scomp
RUN apt update && apt -y install python3 pip virtualenvwrapper vim nano iproute2 tree
RUN groupadd -r scomp && useradd -r -g scomp scomp
RUN mkdir -p /home/scomp && chown scomp.scomp /home/scomp
RUN mkdir -p /var/data && chown scomp.scomp /var/data
USER scomp:scomp
RUN echo "source /usr/share/virtualenvwrapper/virtualenvwrapper.sh" >> /home/scomp/.bashrc
COPY ./requirements.txt .
RUN source /usr/share/virtualenvwrapper/virtualenvwrapper.sh && \
        mkvirtualenv scomp && \
        pip install --no-cache-dir --upgrade -r requirements.txt && \
        echo "workon scomp" >> /home/scomp/.bashrc