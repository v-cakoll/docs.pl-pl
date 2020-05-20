---
title: NOTIFY_FILTER — Wyliczenie
ms.date: 03/30/2017
api_name:
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
ms.openlocfilehash: b20e18d5f4314a0ab1442ac7bd5c6514e4db85d5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609485"
---
# <a name="notify_filter-enumeration"></a>NOTIFY_FILTER — Wyliczenie
Identyfikuje wywołania zwrotne dla funkcji debugera. Aby uzyskać więcej informacji, zobacz metodę [INotifySource2:: SetNotifyFilter —](inotifysource2-setnotifyfilter-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|Wskazuje, że metoda [INotifySink2:: OnSyncCallOut —](inotifysink2-onsynccallout-method.md) powinna być wywoływana.|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|Wskazuje, że metoda [INotifySink2:: OnSyncCallEnter —](inotifysink2-onsynccallenter-method.md) powinna być wywoływana.|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|Wskazuje, że metoda [INotifySink2:: OnSyncCallExit —](inotifysink2-onsynccallexit-method.md) powinna być wywoływana.|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|Wskazuje, że metoda [INotifySink2:: OnSyncCallReturn —](inotifysink2-onsynccallreturn-method.md) powinna być wywoływana.|  
|`NOTIFY_FILTER_ALLSYNC`|Wskazuje, że wszystkie metody [INotifySink2](inotifysink2-interface.md) powinny być wywoływane.|  
|`NOTIFY_FILTER_ALL`|Aktywuje wszystkie istniejące i przyszłe powiadomienia.|  
|`NOTIFY_FILTER_NONE`|Wskazuje, że nie powinny być wywoływane żadne metody powiadamiania.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ProtocolNotify2. idl  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia magazynu symboli diagnostycznych](diagnostics-symbol-store-enumerations.md)
