---
title: INotifySink2 — Interfejs
ms.date: 03/30/2017
api_name:
- INotifySink2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2
helpviewer_keywords:
- INotifySink2 interface [.NET Framework debugging]
ms.assetid: c1018789-4206-455d-aacc-2d876fc0d0bb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fc5d09ac12919b8c68b9fe4bf9f7dc0009b2d4b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705472"
---
# <a name="inotifysink2-interface"></a>INotifySink2 — Interfejs
Deklaruje metody dla obiektu sink powiadomień.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[OnSyncCallEnter, metoda](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md)|Pobiera element wywoływany w przypadku wprowadzania wywołanie.|  
|[OnSyncCallExit, metoda](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md)|Pobiera wywoływane podczas zamykania połączenia.|  
|[OnSyncCallOut, metoda](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md)|Pobiera wywoływane, gdy wywołanie jest zewnętrzny.|  
|[OnSyncCallReturn, metoda](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md)|Pobiera wywoływane, gdy wywołanie zwraca.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Zobacz także
- [INotifyConnection2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [INotifySource2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
