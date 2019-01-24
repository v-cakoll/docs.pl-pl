---
title: ICorDebugModuleEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f71901acf8227d018bf288b6cd0265f053e6a3a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510835"
---
# <a name="icordebugmoduleenumnext-method"></a>ICorDebugModuleEnum::Next — Metoda
Pobiera liczbę wystąpień "ICorDebugModule" określonego przez `celt` z wyliczenia, zaczynając od bieżącej pozycji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba `ICorDebugModule` wystąpienia mają zostać pobrane.  
  
 `modules`  
 [out] Tablica wskaźników, z których każdy wskazuje `ICorDebugModule` obiektu.  
  
 `pceltFetched`  
 [out] Wskaźnik do liczby `ICorDebugModule` wystąpień rzeczywistego zwrotu. Ta wartość może mieć wartości null Jeśli `celt` jeden.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

