---
title: "ICorDebugThread::CreateEval — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.CreateEval
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aebabf12e6dcf12f0e1e1f24ec2ad69ea55ec86c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthreadcreateeval-method"></a>ICorDebugThread::CreateEval — Metoda
Tworzy obiekt ICorDebugEval, który zbiera i udostępnia funkcje tego ICorDebugThread.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEval`  
 [out] Wskaźnik do adresu `ICorDebugEval` obiektu, który zbiera i udostępnia funkcje tego wątku.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt oceny przeprowadzi wypychanie nowy łańcuch w wątku, przed wykonaniem jego obliczeń. To przerwania obliczenia aktualnie wykonywane w wątku dopiero po zakończeniu oceny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
