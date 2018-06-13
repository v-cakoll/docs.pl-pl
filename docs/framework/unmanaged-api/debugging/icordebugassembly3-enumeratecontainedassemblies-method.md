---
title: Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb84efe78568bbae03f76efc456fc8ae605e4db9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404846"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a>Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
Pobiera moduł wyliczający dla zestawów zawartych w tym zestawie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppAssemblies`  
 [out] Wskaźnik do adresu ICorDebugAssemblyEnum obiektu interfejsu, który moduł wyliczający.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli `ICorDebugAssembly3` obiektu jest kontenerem; w przeciwnym razie `S_FALSE`, a wyliczenie jest pusta.  
  
## <a name="remarks"></a>Uwagi  
 Symbole są wymagane do wyliczenia zawartych w niej zestawów. Jeśli nie są obecne, metoda zwraca `S_FALSE`, i nie prawidłowym modułem wyliczającym jest dostępne.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z platformą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugAssembly3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
