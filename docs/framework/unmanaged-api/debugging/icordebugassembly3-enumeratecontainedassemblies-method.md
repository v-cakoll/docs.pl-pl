---
title: Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54ccb52468a530280527252e0e0c43cc9edbb2c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645477"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a>Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
Pobiera moduł wyliczający dla zestawów znajdujących się w tym zestawie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppAssemblies`  
 [out] Wskaźnik na adres icordebugassemblyenum — interfejs obiekt modułu wyliczającego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli ten `ICorDebugAssembly3` obiekt to kontener, a w przeciwnym razie `S_FALSE`, i wyliczenia jest pusty.  
  
## <a name="remarks"></a>Uwagi  
 Symbole są wymagane do wyliczenia zawarte zestawów. Jeśli nie są obecne, metoda zwraca `S_FALSE`, i jest dostępne nie prawidłowym modułem wyliczającym.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugAssembly3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
