https://github.com/SCamopby/c4issues

Public github repository for c4fixes and issues, 
	• Rsults of investigation and testing
	• Items mentioned in the CFOUR forum that amy be essential to know.

Fixes addressed
	• Bad data in molden and molden_nat files for d, f, and g functions.
		○ H functions are incorrect but not fixed. CFOUR molden files with H funtions are unusable.
		○ Molden file s and p functions have always been are correct, but the presence of higher type functions create incorrect scaling and incorrect results when post-processed with programs like multiwfn, gabedit, orbkit, molden, and others.

  			○ A tar file is provided with the code updates.
			§ From inside the directory containing a functioning install of CFOUR 2.1, the tar file should be extracted, as
				□ tar -xvf (dir)/c4fff.tar 
			§ Then run make to implement the fixes.
Issues.
	• Incorrect results with geometry optimization using NCC if ECP are used.
		○ GEO opt  CCSD(T) NCC with FROZEN_CORE=ON requires
			§ FCGRADNEW=NEW
	• Missing files from cubic fcubic.f (Westerfield correction)
	• Extra [Molden Format] fro rdbas.f can caus file to be mis-interpreted oand / or rejected
	• Overflow of array when many atoms in vibrtional analysis Bauschlicher
 	  ![image](https://github.com/SCamopby/c4issues/assets/71558036/e8c06ba9-6903-45dc-89aa-195247db7d78)

# c4issues

fixes for CFOUR and issues

Update to the source tree of a working installation of CFOUR 2.1
*	Contents of c4fff.tar. To be untar'd into the install, and make rerun.
*	*	./qcscf/libvscf.f
		./libr/reorderdf.f
		./vscf/moldenorb.f
		./joda/rdbas.f
		./cubic/fcubic.f
		./cubic/wrtzmats2.f
		./libecf/ecpdef.f

MOLDEN and MOLDEN_NAT files from CFOUR
	*	Fixes in reorderdf.f correct the coefficients of d,f,g functions. Even if these functions are little populated the files are not useful. Files with 'h' functions are still note useful
 	*	Additonal minor fixes in rdbas.f and moldenorb (in moldenorb.f and libvscf.f correct the Occup parameter in the RHF case by making it 2.0 since only Alpha data is written, and that is the expected value in MOLDEN files for that case. This only applies to the SCF molden file; the MOLDEN_NAT file is already written correctly.
  	*	The fix to rdbas.f consists in commenting out the writing out of an extra [Molden Format] line that causes problems with ORBKIT. (It is also possible to make a fix to ORBKIT to eliminate the problem.)

Westerfield fix (fcubic.f) fix to fcubic.f to write files needed for XGUINEA (VPT2 to XGUINEA for intensities). Per Stanton in forum.

Bauschlicher fix for long atom list. (wrtzmats2.f)
Fan Wang ECP bug reported onthe forum in libecp/ecpdef.f


