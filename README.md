# arki-server

Arki-server is an Mles WebSocket proxy service for [Mles](https://github.com/jq-rs/mles-rs) WebSocket protocol, like [MlesTalk](http://mles.io/app).

## Example how to create your own personal proxy server

 1. [Install](https://www.rust-lang.org/tools/install) Rust and Cargo package manager to your preferred server
 2. Install Mles server: cargo install mles
 3. Start mles on your local server: `MLES_KEY=<secket-key-string-here> mles --history-limit=1000`
 4. Clone arki-server repository: git clone https://github.com/jq-rs/arki-server.git
 5. Compile arki-server: cargo build --release
 6. Configure TCP keepalive settings to clear up zombie connections efficiently:
    - `vi /etc/sysctl.conf` (file to edit, or similar file based on your distribution)
    - add following entries
      - `net.ipv4.tcp_keepalive_time = 20`
      - `net.ipv4.tcp_keepalive_intvl = 10`
      - `net.ipv4.tcp_keepalive_probes = 2`
    - `sysctl -p` (apply changes)
 7. Startup arki-server websocket proxy in your local server: `MLES_KEY=<secket-key-string-here> target/release/arki-server`
     - default port 80 may need root privileges
 8. Connect to port 80 of your local server with Mles Websocket application
 9. Open port 80 of your firewall for Mles WebSocket protocol, if you plan to connect from outer world
 
 Optional: You can configure with provided systemctl scripts the services to be started automatically on server reboot.
 
 Enjoy talking over Mles WebSocket proxy!
 
 ## Available public proxy servers
 
   * http://mles.io:80
   * \<add your public server here\>
 
 P.S. Please send a PR if some of this info is outdated.
