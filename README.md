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
