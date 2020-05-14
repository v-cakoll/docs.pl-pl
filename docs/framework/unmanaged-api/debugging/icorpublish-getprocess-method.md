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
ms.openlocfilehash: 2cd2238ac67713564922be440ce64a2ebc4bbf44
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396337"
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
 `GetProcess`Niepowodzenie, jeśli proces nie istnieje lub nie jest procesem zarządzanym, który może być debugowany przez bieżącego użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorPub. idl, CorPub. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorPublish — Interfejs](icorpublish-interface.md)
