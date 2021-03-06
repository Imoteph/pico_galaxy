Galaxy tool to find ORFs or simple CDSs
=======================================

This tool is copyright 2011-2015 by Peter Cock, The James Hutton Institute
(formerly SCRI, Scottish Crop Research Institute), UK. All rights reserved.
Additions copyright 2015-2016 by Eric Rasche.
See the licence text below (MIT licence).

This tool is a short Python script (using Biopython library functions)
to search nucleotide sequences for open reading frames (ORFs) or coding
sequences (CDSs) where the first potential start codon is used. See the
help text in the XML file for more information.

This tool is available from the Galaxy Tool Shed at:

* http://toolshed.g2.bx.psu.edu/view/peterjc/get_orfs_or_cdss

See also the EMBOSS tool ``getorf`` which offers similar functionality and
has also been wrapped for use within Galaxy.


Automated Installation
======================

This should be straightforward using the Galaxy Tool Shed, which should be
able to automatically install the dependency on Biopython, and then install
this tool and run its unit tests.


Manual Installation
===================

There are just two files to install to use this tool from within Galaxy:

* ``get_orfs_or_cdss.py`` (the Python script)
* ``get_orfs_or_cdss.xml`` (the Galaxy tool definition)

The suggested location is in a dedicated ``tools/get_orfs_or_cdss`` folder.

You will also need to modify the ``tools_conf.xml`` file to tell Galaxy to offer the
tool. One suggested location is in the filters section. Simply add the line::

    <tool file="get_orfs_or_cdss/get_orfs_or_cdss.xml" />

You will also need to install Biopython 1.65 or later (slightly older versions
should be fine, but will not have the latest NCBI genetic code tables).

If you wish to run the unit tests, also	move/copy the ``test-data/`` files
under Galaxy's ``test-data/`` folder. Then::

    ./run_tests.sh -id get_orfs_or_cdss

That's it.


History
=======

======= ======================================================================
Version Changes
------- ----------------------------------------------------------------------
v0.0.1  - Initial version.
v0.0.2  - Correct labelling issue on reverse strand.
        - Use the new <stdio> settings in the XML wrappers to catch errors
v0.0.3  - Include unit tests.
        - Record Python script version when run from Galaxy.
v0.0.4  - Link to Tool Shed added to help text and this documentation.
v0.0.5  - Automated intallation of the Biopython dependency.
        - Use reStructuredText for this README file.
        - Adopt standard MIT License.
        - Updated citation information (Cock et al. 2013).
        - Renamed folder and adopted README.rst naming.
v0.0.6  - Corrected automated dependency defintion.
v0.0.7  - Tool definition now embeds citation information.
v0.1.0  - Tool now outputs BED formatted calls (by @erasche, Eric Rasche).
        - Using ``optparse`` for the Python command line API (Eric Rasche).
        - Added NCBI genetic code table 24, Pterobranchia Mitochondrial.
v0.1.1  - Reorder XML elements (internal change only).
v0.2.0  - Tool now also outputs GFF3 formatted calls (Eric Rasche).
======= ======================================================================


Developers
==========

This script and related tools were initially developed on the following hg branch:
http://bitbucket.org/peterjc/galaxy-central/src/tools

Development has now moved to a dedicated GitHub repository:
https://github.com/peterjc/pico_galaxy/tree/master/tools

For pushing a release to the test or main "Galaxy Tool Shed", use the following
Planemo commands (which requires you have set your Tool Shed access details in
``~/.planemo.yml`` and that you have access rights on the Tool Shed)::

    $ planemo shed_update -t testtoolshed --check_diff ~/repositories/pico_galaxy/tools/get_orfs_or_cdss/
    ...

or::

    $ planemo shed_update -t toolshed --check_diff ~/repositories/pico_galaxy/tools/get_orfs_or_cdss/
    ...

To just build and check the tar ball, use::

    $ planemo shed_upload --tar_only  ~/repositories/pico_galaxy/tools/get_orfs_or_cdss/
    ...
    $ tar -tzf shed_upload.tar.gz
    test-data/Ssuis.fasta
    test-data/get_orf_input.Suis_ORF.bed
    test-data/get_orf_input.Suis_ORF.nuc.fasta
    test-data/get_orf_input.Suis_ORF.prot.fasta
    test-data/get_orf_input.fasta
    test-data/get_orf_input.t11_bed_out.bed
    test-data/get_orf_input.t11_nuc_out.fasta
    test-data/get_orf_input.t11_open_bed_out.bed
    test-data/get_orf_input.t11_open_nuc_out.fasta
    test-data/get_orf_input.t11_open_prot_out.fasta
    test-data/get_orf_input.t11_prot_out.fasta
    test-data/get_orf_input.t1_bed_out.bed
    test-data/get_orf_input.t1_nuc_out.fasta
    test-data/get_orf_input.t1_prot_out.fasta
    tools/get_orfs_or_cdss/get_orfs_or_cdss.py
    tools/get_orfs_or_cdss/get_orfs_or_cdss.xml
    tools/get_orfs_or_cdss/README.rst
    tools/get_orfs_or_cdss/tool_dependencies.xml


Licence (MIT)
=============

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
