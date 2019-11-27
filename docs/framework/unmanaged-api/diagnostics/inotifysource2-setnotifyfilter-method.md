---
title: INotifySource2::SetNotifyFilter — Metoda
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
ms.openlocfilehash: 554756bdda6e7167b013e7114e647f952cd1069d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435950"
---
# <a name="inotifysource2setnotifyfilter-method"></a>INotifySource2::SetNotifyFilter — Metoda
Przypisuje filtr powiadomień do użycia z tym źródłem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `in_NotifyFilter`  
 podczas Bitowa kombinacja [NOTIFY_FILTER](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md) wartości wyliczenia, które identyfikują wywołania zwrotne dla interfejsu API debugera.  
  
 `in_pUserThreadFilter`  
 podczas Wskaźnik do struktury [USER_THREAD](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) , który identyfikuje wątki dla interfejsu API debugera.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Zobacz także

- [INotifySource2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [INotifyConnection2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [INotifySink2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
