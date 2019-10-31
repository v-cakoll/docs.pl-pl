---
title: ICorDebugFrameEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
ms.openlocfilehash: ff74a9849b74b8a8e6b8c03f1fc4e7c7eee1ec14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124058"
---
# <a name="icordebugframeenumnext-method"></a>ICorDebugFrameEnum::Next — Metoda
Pobiera określoną liczbę wystąpień ICorDebugFrame, rozpoczynając od bieżącego położenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba wystąpień `ICorDebugFrame` do pobrania.  
  
 `frames`  
 określoną Tablica wskaźników, z których każdy wskazuje obiekt `ICorDebugFrame`.  
  
 `pceltFetched`  
 określoną Wskaźnik do liczby zwróconych wystąpień `ICorDebugFrame`. Ta wartość może być równa null, jeśli `celt` to jeden.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
