import numpy as np
import h5py


def change_voltage(path,voltage):
    with h5py.File(path,'r+') as f:
        for i in f['SolverSpecificSettings/EmLfBoundaries']:
            if f['SolverSpecificSettings/EmLfBoundaries/'+i].attrs['name']=='Patch_up':
                f['SolverSpecificSettings/EmLfBoundaries/' + i].attrs['dirichlet_value']=float(voltage)#be careful, it must be a float or it will crash



    return
