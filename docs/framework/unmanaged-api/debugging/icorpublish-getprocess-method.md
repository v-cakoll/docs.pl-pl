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
ms.openlocfilehash: 0368349e6c6a566cb569738bf3bda40eb9f5de96
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790733"
---
# <a name="icorpublishgetprocess-method"></a>ICorPublish::GetProcess — Metoda
Pobiera wystąpienie [ICorPublishProcess](icorpublishprocess-interface.md) , które reprezentuje proces o określonym identyfikatorze.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pid`  
 podczas Identyfikator procesu.  
  
 `ppProcess`  
 określoną Wskaźnik do adresu `ICorPublishProcess` wystąpienia, które reprezentuje proces.  
  
## <a name="remarks"></a>Uwagi  
 `GetProcess`, jeśli proces nie istnieje lub nie jest procesem zarządzanym, który może być debugowany przez bieżącego użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorPublish, interfejs](icorpublish-interface.md)
