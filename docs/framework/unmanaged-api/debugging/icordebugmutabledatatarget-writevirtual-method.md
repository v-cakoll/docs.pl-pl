---
title: 'ICorDebugMutableDataTarget:: WriteVirtual —, Metoda'
ms.date: 03/30/2017
ms.assetid: 80833648-58a7-491a-8dc8-9a48e9bb3adc
ms.openlocfilehash: 2b4bd1dc97f37f5a514ab54f9e4d778fe3b91736
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792832"
---
# <a name="icordebugmutabledatatargetwritevirtual-method"></a>ICorDebugMutableDataTarget:: WriteVirtual —, Metoda
Zapisuje pamięć w przestrzeni adresowej procesu docelowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT WriteVirtual(  
   [in] CORDB_ADDRESS address,  
   [in, size_is(bytesRequested)] const BYTE * pBuffer,  
   [in] ULONG32 bytesRequested);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 podczas Adres, pod który należy napisać zawartość `pBuffer`.  
  
 `pBuffer`  
 podczas Wskaźnik do tablicy bajtów zawierającej bajty do zapisania.  
  
 `address`  
 podczas Liczba bajtów w `pBuffer`.  
  
## <a name="return-value"></a>Wartość zwrócona  
 `S_OK` po powodzeniu lub innych `HRESULT` w przypadku awarii.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli nie można zapisać żadnych bajtów, wywołanie metody zakończy się niepowodzeniem bez zmiany jakichkolwiek bajtów w docelowej przestrzeni adresowej. (W przeciwnym razie element docelowy będzie w stanie niespójnym, co sprawia, że dalsze debugowanie jest niezawodne).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMutableDataTarget, interfejs](icordebugmutabledatatarget-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
