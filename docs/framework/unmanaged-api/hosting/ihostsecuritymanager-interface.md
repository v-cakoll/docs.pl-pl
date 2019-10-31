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
ms.openlocfilehash: 9b7cc41848e41976f388e38bf22c9ea0f90abbae
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121479"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager — Interfejs
Zapewnia metody, które umożliwiają dostęp do i kontrolę nad kontekstem zabezpieczeń aktualnie wykonywanego wątku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetSecurityContext, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|Pobiera żądany [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hosta.|  
|[ImpersonateLoggedOnUser, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|Żąda wykonania kodu przy użyciu poświadczeń bieżącego użytkownika.|  
|[OpenThreadToken, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|Otwiera token dostępu swobodnego skojarzony z bieżącym wątkiem.|  
|[RevertToSelf, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|Kończy personifikację bieżącej tożsamości użytkownika i zwraca oryginalny token wątku.|  
|[SetSecurityContext, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|Ustawia kontekst zabezpieczeń aktualnie wykonywanego wątku.|  
|[SetThreadToken, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|Ustawia dojście dla aktualnie wykonywanego wątku.|  
  
## <a name="remarks"></a>Uwagi  
 Host może kontrolować cały dostęp kodu do tokenów wątków przez środowisko uruchomieniowe języka wspólnego (CLR) i kod użytkownika. Może także zapewnić, że pełne informacje kontekstu zabezpieczeń są przesyłane przez operacje asynchroniczne lub punkty kodowe z ograniczonym dostępem do kodu. `IHostSecurityContext` hermetyzuje informacje kontekstu zabezpieczeń, nieprzezroczyste dla środowiska CLR.  
  
 Środowisko CLR obsługuje wewnętrznie zarządzane kontekstu wątku. Wysyła zapytanie do `IHostSecurityManager` specyficznych dla procesu w następujących sytuacjach:  
  
- W wątku finalizatora podczas wykonywania finalizatora.  
  
- Podczas wykonywania konstruktora klasy i modułu.  
  
- W przypadku asynchronicznych punktów w wątku roboczym w wywołaniach metody [IHostThreadPoolManager:: QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) .  
  
- W trakcie obsługi portów zakończenia we/wy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IHostSecurityContext, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
