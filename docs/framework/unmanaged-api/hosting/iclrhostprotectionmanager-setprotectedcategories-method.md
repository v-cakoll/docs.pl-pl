---
title: "ICLRHostProtectionManager::SetProtectedCategories — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRHostProtectionManager.SetProtectedCategories
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 984a88a9b75a03f421f1dd3f834665fee932876a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a>ICLRHostProtectionManager::SetProtectedCategories — Metoda
Określa, które kategorie typy zarządzane i elementów członkowskich powinien zostać zablokowany uruchomionych w częściowo zaufany kod.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `categories`  
 [in] Kombinację [EApiCategories](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md) wartości i wskazujący kategorie, które typy zarządzane i elementów członkowskich powinien zostać zablokowany w częściowo zaufany kod.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetProtectedCategories`zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Każdy `EApiCategories` wartość odwołuje się do listy typy zarządzane i elementów członkowskich. `EApiCategories` Wyliczenie i `SetProtectedCategories` metody są bezpośrednio związane do zarządzanej <xref:System.Security.Permissions.HostProtectionAttribute> klasy, która służy do oznaczania typy zarządzane i elementów członkowskich, które ujawnia możliwości odpowiadający kategorii opisanego przez `EApiCategories`. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.HostProtectionAttribute> i <xref:System.Security.Permissions.HostProtectionResource> wyliczenia, która odpowiada bezpośrednio `EApiCategories`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Permissions.HostProtectionAttribute>  
 <xref:System.Security.Permissions.HostProtectionResource>  
 [EApiCategories — wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eapicategories-enumeration.md)  
 [ICLRControl — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICLRHostProtectionManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
