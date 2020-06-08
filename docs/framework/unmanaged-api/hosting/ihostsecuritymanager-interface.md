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
ms.openlocfilehash: 237fe23493460df77a79ba3aed9f0a809cd8aa23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501472"
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager — Interfejs
Zapewnia metody, które umożliwiają dostęp do i kontrolę nad kontekstem zabezpieczeń aktualnie wykonywanego wątku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetSecurityContext, metoda](ihostsecuritymanager-getsecuritycontext-method.md)|Pobiera żądany [IHostSecurityContext](ihostsecuritycontext-interface.md) z hosta.|  
|[ImpersonateLoggedOnUser, metoda](ihostsecuritymanager-impersonateloggedonuser-method.md)|Żąda wykonania kodu przy użyciu poświadczeń bieżącego użytkownika.|  
|[OpenThreadToken, metoda](ihostsecuritymanager-openthreadtoken-method.md)|Otwiera token dostępu swobodnego skojarzony z bieżącym wątkiem.|  
|[RevertToSelf, metoda](ihostsecuritymanager-reverttoself-method.md)|Kończy personifikację bieżącej tożsamości użytkownika i zwraca oryginalny token wątku.|  
|[SetSecurityContext, metoda](ihostsecuritymanager-setsecuritycontext-method.md)|Ustawia kontekst zabezpieczeń aktualnie wykonywanego wątku.|  
|[SetThreadToken, metoda](ihostsecuritymanager-setthreadtoken-method.md)|Ustawia dojście dla aktualnie wykonywanego wątku.|  
  
## <a name="remarks"></a>Uwagi  
 Host może kontrolować cały dostęp kodu do tokenów wątków przez środowisko uruchomieniowe języka wspólnego (CLR) i kod użytkownika. Może także zapewnić, że pełne informacje kontekstu zabezpieczeń są przesyłane przez operacje asynchroniczne lub punkty kodowe z ograniczonym dostępem do kodu. `IHostSecurityContext`hermetyzuje te informacje kontekstu zabezpieczeń, które nie są nieprzezroczyste dla środowiska CLR.  
  
 Środowisko CLR obsługuje wewnętrznie zarządzane kontekstu wątku. Wysyła zapytanie do określonego procesu `IHostSecurityManager` w następujących sytuacjach:  
  
- W wątku finalizatora podczas wykonywania finalizatora.  
  
- Podczas wykonywania konstruktora klasy i modułu.  
  
- W przypadku asynchronicznych punktów w wątku roboczym w wywołaniach metody [IHostThreadPoolManager:: QueueUserWorkItem](ihostthreadpoolmanager-queueuserworkitem-method.md) .  
  
- W trakcie obsługi portów zakończenia we/wy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IHostSecurityContext — Interfejs](ihostsecuritycontext-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
