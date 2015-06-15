Performance test for delegate lookup feature
============================================

The goal of this project is to test the performance impact of the delegate lookup feature proposed in PSR-11 on a compiler container
in a real-case environment.

For this test, I chose to use Symfony 2.
I'm testing performance by loading the demo controller page.

Performance is tested using:

- Docker containers
- Blackfire.io as a profiler

The "prod" environment is used in Symfony and Composer autoloader is optimized using the "-o" option.

This project has several branches, one for each performance test.

- **standard**: the standard, unpatched Symfony distribution
- **psr11**: Symfony with a patched container to add delegate lookup support. The feature is added to the container but is
  not used.
- **2-containers**: Symfony with a patched container. A second container is added (Picotainer). Symfony is first and Picotainer second container
- **2-containers-sf-last**: Symfony with a patched container. A second container is added (Picotainer). Picotainer is first and Symfony second container
- **20-containers-sf-last**: Symfony with a patched container. 20 Picotainer containers are added (!). Symfony is last

