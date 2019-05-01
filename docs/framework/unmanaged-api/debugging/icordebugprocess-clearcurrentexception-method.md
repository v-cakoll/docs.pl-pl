---
title: ICorDebugProcess::ClearCurrentException — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f014f9213a4b9a2d5119af9a6dceebb9a9d54b52
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775606"
---
# <a name="icordebugprocessclearcurrentexception-method"></a>ICorDebugProcess::ClearCurrentException — Metoda
Czyści niezarządzane bieżącego wyjątku dla danego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 [in] Identyfikator wątku, wyczyszczone bieżący wyjątek niezarządzanych.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, przed wywołaniem [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) kiedy wątek zgłosił wyjątek niezarządzanych, które mają być ignorowane przez debugowany program. Spowoduje to wyczyszczenie zarówno oczekujących wewnątrzpasmowe (IB), jak i poza pasmem (OOB) zdarzenia dla danego wątku. Wszystkie punkty przerwania OOB i wyjątki pojedynczy krok zostaną automatycznie wyczyszczone.  
  
 Użyj [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) przechwycić bieżący wyjątek w wątku zarządzanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
