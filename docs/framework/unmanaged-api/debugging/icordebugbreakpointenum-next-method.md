---
title: ICorDebugBreakpointEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBreakpointEnum interface [.NET Framework debugging]
- ICorDebugBreakpointEnum::Next method [.NET Framework debugging]
ms.assetid: 2e6bbaea-79ba-448c-a0e3-7c90fc7c2939
topic_type:
- apiref
ms.openlocfilehash: d29576c6f073f1d0e8e0aea417fc38c09a8327c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122743"
---
# <a name="icordebugbreakpointenumnext-method"></a>ICorDebugBreakpointEnum::Next — Metoda
Pobiera określoną liczbę wystąpień ICorDebugBreakpoint z wyliczenia, rozpoczynając od bieżącego położenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugBreakpoint *breakpoints[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba wystąpień `ICorDebugBreakpoint` do pobrania.  
  
 `breakpoints`  
 określoną Tablica wskaźników, z których każdy wskazuje obiekt `ICorDebugBreakpoint`, który reprezentuje punkt przerwania.  
  
 `pceltFetched`  
 określoną Wskaźnik do liczby zwróconych wystąpień `ICorDebugBreakpoint`. Ta wartość może być równa null, jeśli `celt` to jeden.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
