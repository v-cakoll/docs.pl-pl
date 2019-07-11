---
title: ICorDebugMutableDataTarget::WriteVirtual Method
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0a6a58a1a270cb67b75cf34ac5df8d45ccf307c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764579"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>ICorDebugMutableDataTarget::WriteVirtual Method
Zapisuje w pamięci do przestrzeni adresowej procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 [in] Adres, w którym należy zapisać zawartość `pBuffer`.  
  
 `pBuffer`  
 [in] Wskaźnik do tablicy typu byte, zawierająca bajty do zapisania.  
  
 `address`  
 [in] Liczba bajtów w `pBuffer`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` na powodzenie lub innych `HRESULT` w przypadku niepowodzenia.  
  
## <a name="remarks"></a>Uwagi  
 Nie można zapisać wszystkich bajtów, wywołanie metody nie powiedzie się bez zmieniania żadnych bajty w przestrzeni adresowej docelowego. (W przeciwnym razie element docelowy będzie można w niespójnym stanie, który sprawia, że dodatkowe debugowanie zawodne.)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMutableDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
