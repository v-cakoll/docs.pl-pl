---
title: INotifySink2::OnSyncCallOut — Metoda
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
ms.openlocfilehash: ce0e192a9d7d5abf56a55f844cf886c386f1c563
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441997"
---
# <a name="inotifysink2onsynccallout-method"></a>INotifySink2::OnSyncCallOut — Metoda
Wywoływana, gdy wywołanie jest wychodzące.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `in_CallID`  
 podczas Identyfikator wywołania, które jest wychodzące. Zobacz [strukturę CALL_ID](call-id-structure.md).  
  
 `out_ppBuffer`  
 określoną Bufor wywołań.  
  
 `out_pBufferSize`  
 określoną Rozmiar buforu wywołań w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Zobacz także

- [INotifySink2 — Interfejs](inotifysink2-interface.md)
- [INotifySource2 — Interfejs](inotifysource2-interface.md)
- [INotifyConnection2 — Interfejs](inotifyconnection2-interface.md)
