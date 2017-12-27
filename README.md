Latex docker container
=====

This container helps compiling latex sources without the need to install all latex packages on your system.

Check out the [blog post](https://www.blang.io/posts/2015-04_docker-tooling-latex/) of the original maintainer.

Setup
-----
First, add your local user to docker group:
```bash
sudo usermod -aG docker YOURUSERNAME
```

Pull image ([from Hub](https://registry.hub.docker.com/u/srehwald/latex)):
```bash
docker pull srehwald/latex
```
or build:
```bash
docker build -t srehwald/latex .

```

Usage:
-----

```bash
cd example

# Double to process refs
../dockercmd.sh pdflatex example.tex
../dockercmd.sh pdflatex example.tex

# Or better in one go (does not start container twice)
../dockercmd.sh /bin/sh -c "pdflatex example.tex && pdflatex example.tex"

# View
./example.pdf
```
Use `dockercmd.sh` to execute any command you like inside the container. `WORKDIRs` match, mounted to `/data` inside container.

Why should I use this container?
-----

- Easy setup
- Preserves UID and GID of local user
- Use container like local command
- `texlive-full` covers most of the available packages
