---
title: ICorPublish::GetProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 414bc1bbd3578d0707e35fa70fe196b504af9942
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418499"
---
# <a name="icorpublishgetprocess-method"></a>ICorPublish::GetProcess — Metoda
Pobiera [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) wystąpienia, który reprezentuje proces o określonym identyfikatorze.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pid`  
 [in] Identyfikator procesu.  
  
 `ppProcess`  
 [out] Wskaźnik do adresu `ICorPublishProcess` wystąpienia, który reprezentuje procesu.  
  
## <a name="remarks"></a>Uwagi  
 `GetProcess` kończy się niepowodzeniem, jeśli proces nie istnieje lub nie jest zarządzany proces, który może być debugowany przez bieżącego użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub.idl, CorPub.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorPublish, interfejs](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
