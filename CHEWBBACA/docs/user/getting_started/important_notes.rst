Important Notes
===============

- chewBBACA only works with **Python 3** (automatic testing for Python 3.8-3.11
  with GitHub Actions).
- We strongly recommend that users install and use **BLAST 2.9.0+** with chewBBACA<=3.3.2, as the files passed to ``-seqidlist`` are not converted to
  a binary format with ``blastdb_aliastool``, which might affect performance in some cases if using BLAST>=2.10. This is not an issue in chewBBACA>=3.3.3
  because it determines if the files should be converted to the binary format based on the BLAST version.
- chewBBACA includes Prodigal training files for some species. You can consult the list of
  Prodigal training files that are readily available `here <https://github.com/B-UMMI/chewBBACA/tree/master/CHEWBBACA/prodigal_training_files>`_.
  We strongly recommend using the same Prodigal training file for schema creation and allele calling to ensure consistent results.
- chewBBACA defines an allele as a complete Coding DNA Sequence (CDS), with start and stop codons
  according to the `NCBI genetic code table 11 <http://www.ncbi.nlm.nih.gov/Taxonomy/Utils/wprintgc.cgi>`_
  (identified using `Prodigal <https://github.com/hyattpd/prodigal/releases/>`_ for chewBBACA<=3.2.0 and
  `Pyrodigal <https://github.com/althonos/pyrodigal>`_ for chewBBACA>=3.3.0, but with the option to provide FASTA
  files with CDSs). It will automatically exclude any allele for which the DNA sequence does not contain start or stop
  codons and for which the length is not multiple of three. Alleles that contain ambiguous bases are also excluded.
- Make sure that your FASTA files are UNIX format. If they were created in Linux or MacOS
  systems they should be in the correct format, but if they were created in Windows systems,
  you should do a quick conversion using for example `dos2unix <https://waterlan.home.xs4all.nl/dos2unix.html>`_.
- If you installed chewBBACA v3 and want to use a schema created with chewBBACA v2, please use the
  :doc:`PrepExternalSchema </user/modules/PrepExternalSchema>` module to convert the schema to a format
  fully compatible with chewBBACA v3.
- If you are running chewBBACA in an environment with multiple processes accessing the same schema please use the ``--no-inferred``
  option (more information in the page about the :doc:`AlleleCall module </user/modules/AlleleCall>`).
- Input files should have short names without blank spaces or special characters. It is also important to ensure each input file has
  a short (maximum 30 characters) and unique basename prefix (everything before the first ``.`` in the basename). You can read more about this in the :doc:`FAQ </user/help_support/faq>` section.

.. important::
  Have a look at the :doc:`FAQ </user/help_support/faq>` section for answers to common questions. You can suggest questions and answers
  to add to the FAQ section by opening an `issue <https://github.com/B-UMMI/chewBBACA/issues>`_ on GitHub or sending an e-mail to imm-bioinfo@medicina.ulisboa.pt.
