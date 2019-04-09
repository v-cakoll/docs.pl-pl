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
ms.openlocfilehash: 4f5307ce00160bb4151a7559daac4724367c6497
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157785"
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

- [INotifyConnection2 — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [INotifySource2 — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [Interfejsy magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
