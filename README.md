fvcompy
=======
Python3 version of FVCOM toolbox.

Coming Soon ...


Creating a mesh_grid for FVCOM
----------------------------

    from fvcompy.meshgrid import FVCOM
    my_mgrid = FVCOM()

    my_mgrid.read('tst.2dm','tst.dep')
    my_mgrid.write('tst_grd.dat','tst_dep.dat')


Wind forcing
------------

    from fvcompy.forces import Wind
    my_wind = Wind(my_mgrid)

    my_wind.ttime = ...
    my_wind.U10 = ...  # or my_wind.Uwind
    my_wind.V10 = ...  # or my_wind.Vwind

    my_wind.write('tst_wnd.nc','title',mode='w')


River
-----

    from fvcompy.forces import River
    my_river = River(my_mgrid)

    riv1 = my_river.add('river1','[1,2,3,4,5]')
    riv1.ttime = ...
    riv2.flux = ...
    riv2.temp = ...
    riv2.salt = ...

    my_river.write('tst_riv.nc',title='title',info='info')


OBC: Temp & Salt
----------------

    from fvcompy.forces import OBC,TSOBC
    my_obc = OBC(my_mgrid)
    my_ts = TSOBC(my_mgrid,my_obc)

    my_ts.ttime = ...
    my_ts.temp = ...
    my_ts.salt = ...

    my_ts.write('tst_tsobc.nc')
