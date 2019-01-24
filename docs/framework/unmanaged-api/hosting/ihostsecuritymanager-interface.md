---
title: IHostSecurityManager — Interfejs
ms.date: 03/30/2017
api_name:
- IHostSecurityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager
helpviewer_keywords:
- IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2637f54fcddaf82d30527d7318503a2b9aa740dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565842"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager — Interfejs
Udostępnia metody, które umożliwiają dostęp do i kontrolę nad kontekstu zabezpieczeń aktualnie wykonywany wątek.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetSecurityContext, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|Pobiera żądany [ihostsecuritycontext —](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hosta.|  
|[ImpersonateLoggedOnUser, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|Żądania, kod można wykonać przy użyciu poświadczeń bieżącej tożsamości użytkownika.|  
|[OpenThreadToken, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|Zostanie otwarty token dostępu skojarzone z bieżącym wątkiem.|  
|[RevertToSelf, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|Kończy działanie personifikacji bieżącej tożsamości użytkownika, a następnie zwraca oryginalny tokenu wątku.|  
|[SetSecurityContext, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|Ustawia kontekst zabezpieczeń dla aktualnie wykonywany wątek.|  
|[SetThreadToken, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|Ustawia obsługi do aktualnie wykonywany wątek.|  
  
## <a name="remarks"></a>Uwagi  
 Hosta można kontrolować wszelki dostęp kodu do tokenów wątku przez środowisko uruchomieniowe języka wspólnego (CLR) i kod użytkownika. Można to także zapewnić pełne zabezpieczenia informacji kontekstowych jest przekazywany w operacji asynchronicznych lub punkty kodowe dostęp ograniczony kod. `IHostSecurityContext` hermetyzuje informacje kontekstu zabezpieczeń, która jest nieprzezroczysta dla środowiska CLR.  
  
 Środowisko CLR obsługuje kontekstu wątków zarządzanych wewnętrznie. Wysyła zapytanie dotyczące procesu `IHostSecurityManager` w następujących sytuacjach:  
  
-   W wątku finalizatora podczas wykonywania finalizatora.  
  
-   Podczas wykonywania konstruktora klasy i moduł.  
  
-   W punktach asynchroniczne w wątku roboczego, w wywołaniach [ihostthreadpoolmanager::QueueUserWorkItem —](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) metody.  
  
-   Obsługę portów zakończenia operacji We/Wy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [IHostSecurityContext, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
