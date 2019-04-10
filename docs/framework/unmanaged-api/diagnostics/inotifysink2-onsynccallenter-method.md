---
title: INotifySink2::OnSyncCallEnter — Metoda
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallEnter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78aaa5d8031e7b554eee2a147d9940ff8d7f7e02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201900"
---
# <a name="inotifysink2onsynccallenter-method"></a>INotifySink2::OnSyncCallEnter — Metoda
Pobiera element wywoływany w przypadku wprowadzania wywołanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `in_CallID`  
 [in] Identyfikator wywołania wprowadzanych. Zobacz [call_id — struktura](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).  
  
 `in_pBuffer`  
 [in] Bufor wywołań.  
  
 `in_BufferSize`  
 [in] Rozmiar buforu wywołania, w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Zobacz także

- [INotifySink2 — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [INotifySource2 — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [INotifyConnection2 — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
