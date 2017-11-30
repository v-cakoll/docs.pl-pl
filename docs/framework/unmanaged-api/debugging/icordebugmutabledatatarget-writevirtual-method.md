---
title: "ICorDebugMutableDataTarget::WriteVirtual — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9541a324c448312f50858ea0b1b284585d223edf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>ICorDebugMutableDataTarget::WriteVirtual — metoda
Zapisuje pamięci do przestrzeni adresowej procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] Adres, pod którym można zapisać zawartości `pBuffer`.  
  
 `pBuffer`  
 [in] Wskaźnik do tablicy typu byte, który zawiera bajtów do zapisania.  
  
 `address`  
 [in] Liczba bajtów w `pBuffer`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`na powodzenie lub innych `HRESULT` w przypadku awarii.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie można zapisać wszystkich bajtów, wywołanie metody kończy się niepowodzeniem bez zmieniania żadnych bajtów w docelowej przestrzeni adresowej. (W przeciwnym razie element docelowy będzie można w stanie niespójnym, która sprawia, że dalsze debugowania zawodne.)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ICorDebugMutableDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
