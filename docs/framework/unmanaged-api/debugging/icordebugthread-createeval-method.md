---
title: ICorDebugThread::CreateEval — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2016795e7b2c0588e2bd69e764fb96f7f90b24d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994074"
---
# <a name="icordebugthreadcreateeval-method"></a>ICorDebugThread::CreateEval — Metoda
Tworzy obiekt ICorDebugEval, który zbiera i udostępnia funkcje to ICorDebugThread.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEval`  
 [out] Wskaźnik na adres `ICorDebugEval` obiektu, który zbiera i udostępnia funkcje tego wątku.  
  
## <a name="remarks"></a>Uwagi  
 Obiekt oceny będzie umożliwiać wypychanie powiadomień nowy łańcuch w wątku, przed wykonaniem jego obliczeń. Przerywa to działanie obliczeń obecnie wykonywane w wątku do chwili zakończenia oceny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
