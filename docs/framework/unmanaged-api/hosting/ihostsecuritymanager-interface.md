---
title: "IHostSecurityManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager
helpviewer_keywords: IHostSecurityManager interface [.NET Framework hosting]
ms.assetid: c3be2cbd-2d93-438b-9888-9a0251b63c03
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2b3d67328dbf68491d319e55e63a9c3540cd1ee4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanager-interface"></a>IHostSecurityManager — Interfejs
Udostępnia metody, które umożliwiają dostęp do i kontrolę nad wątku aktualnie wykonywane w kontekście zabezpieczeń.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetSecurityContext — metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)|Pobiera żądanie [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) z hosta.|  
|[ImpersonateLoggedOnUser — metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-impersonateloggedonuser-method.md)|Żądania który kodu można wykonać przy użyciu poświadczeń Bieżąca tożsamość użytkownika.|  
|[OpenThreadToken — metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-openthreadtoken-method.md)|Otwiera token dostępu skojarzone z bieżącego wątku.|  
|[RevertToSelf — metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-reverttoself-method.md)|Przerywa personifikacji bieżącej tożsamości użytkownika i zwraca oryginalnego tokenu wątku.|  
|[SetSecurityContext — metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)|Ustawia kontekst zabezpieczeń dla wątku aktualnie wykonywane.|  
|[SetThreadToken — metoda](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setthreadtoken-method.md)|Ustawia dojście wątku aktualnie wykonywane.|  
  
## <a name="remarks"></a>Uwagi  
 Hosta można kontrolować kod dostęp do tokenów wątku przez środowisko uruchomieniowe języka wspólnego (CLR) i kod użytkownika. Zapewnia również Zabezpieczenia pełne informacje o kontekście jest przekazywany przez operacje asynchroniczne lub punktów kodowych z ograniczeniami kod dostępu. `IHostSecurityContext`hermetyzuje informacje kontekstu zabezpieczeń, które jest nieprzezroczysta dla środowiska CLR.  
  
 Środowisko CLR wewnętrznie obsługuje kontekstu zarządzanego wątku. Wysyła zapytanie dotyczące procesu `IHostSecurityManager` w następujących sytuacjach:  
  
-   W wątku finalizatora podczas wykonywania finalizatora.  
  
-   Podczas wykonywania konstruktora klasy i modułu.  
  
-   W punktach asynchronicznych w wątku roboczego w wywołaniach [IHostThreadPoolManager::QueueUserWorkItem](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md) metody.  
  
-   W obsługę portów We/Wy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IHostSecurityContext — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [Hosting — interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
