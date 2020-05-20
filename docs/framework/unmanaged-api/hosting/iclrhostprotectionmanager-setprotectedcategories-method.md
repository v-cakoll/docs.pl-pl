---
title: ICLRHostProtectionManager::SetProtectedCategories — Metoda
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetProtectedCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetProtectedCategories
helpviewer_keywords:
- SetProtectedCategories method [.NET Framework hosting]
- ICLRHostProtectionManager::SetProtectedCategories method [.NET Framework hosting]
ms.assetid: fa21dc7b-5da7-440b-b59e-9180e5181f9d
topic_type:
- apiref
ms.openlocfilehash: 5cf6f942add3d090cf830e71a545b9f4d4f69f00
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703166"
---
# <a name="iclrhostprotectionmanagersetprotectedcategories-method"></a>ICLRHostProtectionManager::SetProtectedCategories — Metoda
Określa kategorie typów zarządzanych i elementów członkowskich, które mają być blokowane z uruchamiania w częściowo zaufanym kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetProtectedCategories (  
    [in] EApiCategories  categories  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `categories`  
 podczas Kombinacja wartości [EApiCategories —](eapicategories-enumeration.md) , wskazujących kategorie typów zarządzanych i elementów członkowskich, które powinny być blokowane w kodzie częściowo zaufanym.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetProtectedCategories`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Każda `EApiCategories` wartość odnosi się do listy typów zarządzanych i elementów członkowskich. `EApiCategories`Wyliczenie i `SetProtectedCategories` Metoda są bezpośrednio powiązane z klasą zarządzaną <xref:System.Security.Permissions.HostProtectionAttribute> , która jest używana do oznaczania typów zarządzanych i członków, które uwidaczniają możliwości odpowiadające kategoriom opisanym przez `EApiCategories` . Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.HostProtectionAttribute> i <xref:System.Security.Permissions.HostProtectionResource> Wyliczenie, które bezpośrednio odnosi się do `EApiCategories` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Permissions.HostProtectionAttribute>
- <xref:System.Security.Permissions.HostProtectionResource>
- [EApiCategories, wyliczenie](eapicategories-enumeration.md)
- [ICLRControl — Interfejs](iclrcontrol-interface.md)
- [ICLRHostProtectionManager, interfejs](iclrhostprotectionmanager-interface.md)
