The SWEET-Cat catalog
==============================

.. currentmodule:: PyAstronomy.pyasl

.. autoclass:: SWEETCat
   :members:


Example: Access catalog via pandas data frame   
-----------------------------------------------
   
::

  from __future__ import print_function
  from PyAstronomy import pyasl
  
  sc = pyasl.SWEETCat()
  
  # Access via pandas data frame
  # Show first three rows
  print(sc.data[0:3])
  print()
  
  # Which stars are available?
  print("Available stars: ", sc.data["star"].values)
  print()
  
  # Check whether star is "available"
  star = "XO-5"
  starInTable = (star in sc.data.star.values)
  print("Is " + star + " in the table? ", starInTable)
  
  if starInTable:
    # Get information on that star
    print("Data for star: ", star)
    info = sc.data[sc.data["star"] == star]
    print(info)
    print()
    print("Get the effective temperature")
    teff, erteff = info["teff"], info["erteff"]
    print("Effective temperature of " + star + " = %6.1f +/- %6.1f K" % (teff, erteff))
