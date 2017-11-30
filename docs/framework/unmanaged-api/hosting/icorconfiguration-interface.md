---
title: "ICorConfiguration — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorConfiguration
helpviewer_keywords: ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6bc66abf28e90d858d993bd62e9c67f840af137b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration — Interfejs
Udostępnia metody konfigurowania środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AddDebuggerSpecialThread — metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|Do debugowania usług wskazuje, że określonego wątku powinien mieć możliwość kontynuowania wykonywania, gdy debuger został zatrzymany w scenariuszach debugowania zarządzanych lub niezarządzanych aplikacji.|  
|[SetDebuggerThreadControl — metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|Określa interfejs wywołania zwrotnego, który usług debugowania wywoła wątków CLR są zablokowane i odblokowany do debugowania.|  
|[SetGCHostControl — metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|Ustawia wywołanie zwrotne interfejsu używanego przez moduł garbage collector na żądanie hosta, aby zmienić limit pamięci wirtualnej.|  
|[SetGCThreadControl — metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|Określa interfejs wywołania zwrotnego dla planowania wątków dla zadań z systemem innym niż środowisko uruchomieniowe, które można zablokować dla wyrzucania elementów bezużytecznych.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting — interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Corruntimehost — klasa Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
