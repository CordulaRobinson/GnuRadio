
FROM phusion/baseimage:master

# gnu radio install
# only works with python 2
RUN apt-get update && apt install git python3-pip sudo -y
RUN pip3 install PyBOMBS
RUN pybombs recipes add gr-recipes git+https://github.com/gnuradio/gr-recipes.git
RUN pybombs recipes add gr-recipes-cust git+https://gist.github.com/78e43c8b283a7bbc69fb6670d8e44076.git
RUN mkdir -p ~/gnuradio/
RUN pybombs prefix init ~/gnuradio/
RUN pybombs install gnuradio38_nogui

RUN export PATH="/root/gnuradio/bin:$PATH" \
    export PYTHONPATH="/root/gnuradio/python:/root/gnuradio/lib/python3.6/site-packages:/root/gnuradio/lib/python3.6/dist-packages:/root/gnuradio/lib/python3.7/dist-packages:$PYTHONPATH" \
    export LD_LIBRARY_PATH="/root/gnuradio/lib:$LD_LIBRARY_PATH" \
    export LIBRARY_PATH="/root/gnuradio/lib:$LIBRARY_PATH" \
    export PKG_CONFIG_PATH="/root/gnuradio/lib/pkgconfig:$PKG_CONFIG_PATH" \
    export PYBOMBS_PREFIX="/root/gnuradio"

# RUN pybombs install gr-ieee-80211

# RUN ldconfig && source /home/prefix/default/setup_env.sh 

CMD bash
