---
title: ICorDebugThread2::GetTaskID — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 417f99c2b9fa7e77f8696c27cb3929c92956c08c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494652"
---
# <a name="icordebugthread2gettaskid-method"></a>ICorDebugThread2::GetTaskID — Metoda
Pobiera identyfikator zadania uruchomione w tym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pTaskId`  
 [out] Wskaźnik do identyfikatora zadania uruchamiane w wątku, reprezentowane przez ten obiekt icordebugthread2 —.  
  
## <a name="remarks"></a>Uwagi  
 Zadanie może być uruchomiony tylko w wątku, jeśli wątek jest skojarzona z połączeniem. `GetTaskID` Zwraca zero `pTaskId` Jeśli wątek nie jest skojarzona z połączeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
