# node_usage
A tool for use on EPCC's Cirrus cluster

Prints summary and detailed info on the state of nodes in the cluster (based on output from the ``pbsnodes`` command).

A node which has some jobs running on it but is not in exclusive mode (i.e. other jobs may make use of the remaining CPUs) is considered to be ``Partfree``.  Nodes on which no CPUs are available (either because they are all being used, or the node is in exclusive mode) and considered to be ``Busy`` as are all of their cores, whether they are actually in use or not.

## Usage:

    node_usage [-a]
    
    -a: Print long-format node usage information, includeing PBS Job IDs running on each node
      
## Example output:

    [ibethune@cirrus-login0 node_usage]$ ./node_usage -a
    Node usage detail:
     Name      Avail. CPUs  PBS Job IDs
     r1i0n0        38 / 72  52539, 52576, 52584, 52591, 52608, 56810, 56811, 56812, 56813, 56814, 56815, 56816, 56817, 56818, 56819, 56820, 56821
     r1i0n1         0 / 72  57369
     r1i0n2        44 / 72  51133, 51134, 51136, 51141, 51142, 51144, 51149, 51150, 51152, 51157, 51158, 51160, 51165, 51166
     r1i0n3        72 / 72  
     r1i0n4         0 / 72  57370
     ... (removed for clarity)
     r1i1n34       72 / 72   
     r1i1n35       72 / 72  

    Node usage summary:
         Total     Free Partfree     Busy     Down
            56       44        6        4        2
    CPU usage summary:
         Total     Free     Busy     Down
          4032     3532      356      144
