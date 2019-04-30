---
title: ICorConfiguration — Interfejs
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b24e278b3449d0e17377495cef0f445c1ebed734
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763279"
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration — Interfejs
Udostępnia metody do konfigurowania środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AddDebuggerSpecialThread, metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|Do debugowania usług wskazuje, że określonego wątku powinny mieć możliwość kontynuowania wykonywania, gdy debuger został zatrzymany w zarządzanych lub niezarządzanych scenariusze debugowania aplikacji.|  
|[SetDebuggerThreadControl, metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|Określa interfejs wywołania zwrotnego, który będzie dzwonić, usług debugowania do debugowania wątków CLR są zablokowane i odblokowane.|  
|[SetGCHostControl, metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|Określa interfejs wywołania zwrotnego do użycia przez moduł zbierający elementy bezużyteczne na żądanie hosta, aby zmienić limity pamięci wirtualnej.|  
|[SetGCThreadControl, metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|Określa interfejs wywołania zwrotnego, planowanie wątków dla zadań innych niż środowiska uruchomieniowego, które w przeciwnym razie zostałby zablokowany dla wyrzucania elementów bezużytecznych.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost, klasa coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
