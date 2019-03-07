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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a48396f8ef668cfe7755b2718180317b465793b6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475293"
---
# <a name="icordebugframegetfunction-method"></a>ICorDebugFrame::GetFunction — Metoda
Pobiera funkcję, która zawiera kod skojarzony z tą ramką stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppFunction`  
 [out] Wskaźnik na adres obiektu ICorDebugFunction, który reprezentuje funkcję zawierające kod skojarzony z tą ramką stosu.  
  
## <a name="remarks"></a>Uwagi  
 `GetFunction` Metoda może zakończyć się niepowodzeniem, jeśli ramka nie jest skojarzona z dowolną określoną funkcję.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
