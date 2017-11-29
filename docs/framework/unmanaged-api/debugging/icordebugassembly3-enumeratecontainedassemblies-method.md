---
title: Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b927d065f26a13d496aec8cd6c8cbc69cf3a8bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 `S_OK`Jeśli `ICorDebugAssembly3` obiektu jest kontenerem; w przeciwnym razie `S_FALSE`, a wyliczenie jest pusta.  
  
## <a name="remarks"></a>Uwagi  
 Symbole są wymagane do wyliczenia zawartych w niej zestawów. Jeśli nie są obecne, metoda zwraca `S_FALSE`, i nie prawidłowym modułem wyliczającym jest dostępne.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z platformą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ICorDebugAssembly3](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
