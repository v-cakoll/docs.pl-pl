---
title: ICorDebugMutableDataTarget::WriteVirtual Method
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fba970de6e5882d3cbe9be17b5b49be5a3e81aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171655"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>ICorDebugMutableDataTarget::WriteVirtual Method
Zapisuje w pamięci do przestrzeni adresowej procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
