---
title: ICorDebugMergedAssemblyRecord::Metoda GetPublicKey
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 632e990899346493d5a7df08d293e25b83ed7ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178742"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a>ICorDebugMergedAssemblyRecord::Metoda GetPublicKey
Pobiera klucz publiczny zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cbPublicKey`  
 [w] Maksymalna liczba bajtów `pbPublicKey` w tablicy.  
  
 `pcbPublicKey`  
 [na zewnątrz] Wskaźnik do rzeczywistej liczby bajtów `pbPublicKey` zapisanych w tablicy.  
  
 `pbPublicKey`  
 [na zewnątrz] Wskaźnik do tablicy bajtów, która zawiera klucz publiczny zestawu.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko w przypadku platformy .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugMergedAssemblyRecord, interfejs](icordebugmergedassemblyrecord-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
