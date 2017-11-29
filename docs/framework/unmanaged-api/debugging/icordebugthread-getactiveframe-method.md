---
title: "ICorDebugThread::GetActiveFrame — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetActiveFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8b5d9d42b7c3f7827ce938fdd3dffe57b00142c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadgetactiveframe-method"></a>ICorDebugThread::GetActiveFrame — Metoda
Pobiera wskaźnika interfejsu do aktywnej ramki (najnowsze) dla tego obiektu ICorDebugThread.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppFrame`  
 [out] Wskaźnik do adresu ICorDebugFrame obiektu interfejsu, który reprezentuje ramkę.  
  
## <a name="remarks"></a>Uwagi  
 `ppFrame` Parametr ma wartość null, jeśli ramka nie jest obecnie aktywne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
