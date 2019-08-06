
FROM continuumio/anaconda3 AS gnuradio

# gnu radio install
# only works with python 2
RUN apt update
RUN apt install python3 python3-pip sudo python-six python-numpy python-lxml python-mako -y
RUN pip3 install PyBOMBS
RUN pybombs recipes add gr-recipes git+https://github.com/gnuradio/gr-recipes.git  
RUN mkdir -p /home/prefix/default/
RUN pybombs prefix init /home/prefix/default/
RUN pybombs install gnuradio

RUN pybombs install gr-ieee-80211

RUN ldconfig && source /home/prefix/default/setup_env.sh 

CMD bash