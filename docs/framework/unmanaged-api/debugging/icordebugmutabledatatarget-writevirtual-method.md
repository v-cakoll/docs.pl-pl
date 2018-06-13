---
title: ICorDebugMutableDataTarget::WriteVirtual — metoda
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 184ae290b3a7d86a3c0351d4cfb072bce37337d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417417"
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
 `S_OK` na powodzenie lub innych `HRESULT` w przypadku awarii.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie można zapisać wszystkich bajtów, wywołanie metody kończy się niepowodzeniem bez zmieniania żadnych bajtów w docelowej przestrzeni adresowej. (W przeciwnym razie element docelowy będzie można w stanie niespójnym, która sprawia, że dalsze debugowania zawodne.)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugMutableDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
