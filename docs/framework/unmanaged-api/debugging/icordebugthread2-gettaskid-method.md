---
title: "ICorDebugThread2::GetTaskID — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2.GetTaskID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b94478a0dfb8cc4d90dea611620238024634799
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2gettaskid-method"></a>ICorDebugThread2::GetTaskID — Metoda
Pobiera identyfikator zadania uruchomione w tym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pTaskId`  
 [out] Wskaźnik do identyfikatora zadania uruchamiane w wątku reprezentowany przez ten obiekt ICorDebugThread2.  
  
## <a name="remarks"></a>Uwagi  
 Zadanie może być uruchomiony tylko w wątku, jeśli wątek jest skojarzone z połączeniem. `GetTaskID`Zwraca zero `pTaskId` Jeśli wątek nie jest skojarzone z połączeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
