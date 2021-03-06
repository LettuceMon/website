---
title: ft_read_header
---
```plaintext
 FT_READ_HEADER reads header information from a variety of EEG, MEG and other time
 series data files and represents the header information in a common
 data-independent structure. The supported formats are listed below.

 Use as
   hdr = ft_read_header(filename, ...)

 Additional options should be specified in key-value pairs and can be
   'headerformat'   = string
   'fallback'       = can be empty or 'biosig' (default = [])
   'checkmaxfilter' = boolean, whether to check that maxfilter has been correctly applied (default = true)
   'chanindx'       = list with channel indices in case of different sampling frequencies (only for EDF)
   'coordsys'       = string, 'head' or 'dewar' (default = 'head')
   'chantype'       = string or cell of strings, channel types to be read (NeuroOmega, BlackRock).
   'headerformat'   = name of a MATLAB function that takes the filename as input (default is automatic)

 This returns a header structure with the following elements
   hdr.Fs                  sampling frequency
   hdr.nChans              number of channels
   hdr.nSamples            number of samples per trial
   hdr.nSamplesPre         number of pre-trigger samples in each trial
   hdr.nTrials             number of trials
   hdr.label               Nx1 cell-array with the label of each channel
   hdr.chantype            Nx1 cell-array with the channel type, see FT_CHANTYPE
   hdr.chanunit            Nx1 cell-array with the physical units, see FT_CHANUNIT

 For continuously recorded data, this will return nSamplesPre=0 and nTrials=1.

 For some data formats that are recorded on animal electrophysiology
 systems (e.g. Neuralynx, Plexon), the following optional fields are
 returned, which allows for relating the timing of spike and LFP data
   hdr.FirstTimeStamp      number, represented as 32-bit or 64-bit unsigned integer
   hdr.TimeStampPerSample  number, represented in double precision

 Depending on the file format, additional header information can be
 returned in the hdr.orig subfield.

 To use an external reading function, you can specify an external function as the
 'headerformat' option. This function should take the filename as input argument.
 Please check the code of this function for details, and search for BIDS_TSV as
 example.

 Use cfg.chantype='chaninfo' to get hdr.chaninfo table. For BlackRock
 specify decimation with chantype:skipfactor (e.g. cfg.chantype='analog:10')

 The following MEG dataformats are supported
   CTF (*.ds, *.res4, *.meg4)
   Neuromag/Elekta (*.fif)
   BTi/4D (*.m4d, *.pdf, *.xyz)
   Yokogawa/Ricoh (*.ave, *.con, *.raw)
   NetMEG (*.nc)
   ITAB - Chieti (*.mhd)
   Tristan Babysquid (*.fif)

 The following EEG dataformats are supported
   ANT - Advanced Neuro Technology, EEProbe (*.avr, *.eeg, *.cnt)
   BCI2000 (*.dat)
   Biosemi (*.bdf)
   BrainVision (*.eeg, *.seg, *.dat, *.vhdr, *.vmrk)
   CED - Cambridge Electronic Design (*.smr)
   EGI - Electrical Geodesics, Inc. (*.egis, *.ave, *.gave, *.ses, *.raw, *.sbin, *.mff)
   GTec (*.mat, *.hdf5)
   Generic data formats (*.edf, *.gdf)
   Megis/BESA (*.avr, *.swf, *.besa)
   NeuroScan (*.eeg, *.cnt, *.avg)
   Nexstim (*.nxe)
   TMSi (*.Poly5)
   Mega Neurone (directory)
   Natus/Nicolet/Nervus (.e files)
   Nihon Kohden (*.m00, *.EEG)

 The following spike and LFP dataformats are supported
   Neuralynx (*.ncs, *.nse, *.nts, *.nev, *.nrd, *.dma, *.log)
   Plextor (*.nex, *.plx, *.ddt)
   CED - Cambridge Electronic Design (*.smr)
   MPI - Max Planck Institute (*.dap)
   Neurosim  (neurosim_spikes, neurosim_signals, neurosim_ds)
   Windaq (*.wdq)

 The following NIRS dataformats are supported
   BUCN - Birkbeck college, London (*.txt)
   Artinis - Artinis Medical Systems B.V. (*.oxy3, *.oxy4, *.oxyproj)

 The following Eyetracker dataformats are supported
   EyeLink - SR Research (*.asc)
   Tobii - (*.tsv)
   SensoMotoric Instruments - (*.txt)

 See also FT_READ_DATA, FT_READ_EVENT, FT_WRITE_DATA, FT_WRITE_EVENT,
 FT_CHANTYPE, FT_CHANUNIT
```
