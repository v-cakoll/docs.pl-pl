---
title: "ICorDebugThread::GetUserState — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetUserState
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9af89f355916f01fad118a4b63b57b23b2671f54
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetuserstate-method"></a>ICorDebugThread::GetUserState — Metoda
Pobiera bieżący stan to ICorDebugThread użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pState`  
 [out] Wskaźnik do bitowe połączenie wartości wyliczenia CorDebugUserState, które opisują bieżący stan użytkownika tego wątku.  
  
## <a name="remarks"></a>Uwagi  
 Stanu użytkownika w wątku jest stan wątku, gdy jest on analizowane przez program, który jest debugowany. Wątek może mieć wiele bitów stanu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
