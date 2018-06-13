---
title: ICorDebugProcess5::GetGCHeapInformation — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8824ce004cac8bc2ad675c83dc6b5f167f183e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421050"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a>ICorDebugProcess5::GetGCHeapInformation — Metoda
Ogólne informacje dotyczące pamięci sterty kolekcji, w tym, czy jest ono aktualnie wyliczalny.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pHeapInfo`  
 [out] Wskaźnik do [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) wartość, która zawiera ogólne informacje dotyczące odzyskiwania pamięci sterty kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugProcess5::GetGCHeapInformation` Metoda musi zostać wywołana przed wyliczania sterty lub sterty poszczególnych regionów, aby upewnić się, że wyrzucanie elementów bezużytecznych struktury w procesie nie jest prawidłowy. Nie może być udał pamięci sterty kolekcji, gdy kolekcja jest w toku. W przeciwnym razie wartość wyliczenia może przechwycić struktury kolekcji pamięci, które nie są prawidłowe.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugProcess5, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
