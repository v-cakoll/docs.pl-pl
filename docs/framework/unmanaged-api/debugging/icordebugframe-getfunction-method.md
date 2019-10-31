---
title: ICorDebugFrame::GetFunction — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
ms.openlocfilehash: 39175e338e4fd98dd4af1325138da732ed81c764
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137918"
---
# <a name="icordebugframegetfunction-method"></a>ICorDebugFrame::GetFunction — Metoda
Pobiera funkcję, która zawiera kod skojarzony z tą ramką stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppFunction`  
 określoną Wskaźnik do adresu obiektu ICorDebugFunction, który reprezentuje funkcję zawierającą kod skojarzony z tą ramką stosu.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `GetFunction` może zakończyć się niepowodzeniem, jeśli ramka nie jest skojarzona z żadną określoną funkcją.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
