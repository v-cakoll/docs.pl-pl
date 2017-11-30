---
title: "ICLRAppDomainResourceMonitor::GetCurrentSurvived — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9fe624c83be5dcf762f1c6036f8e4264f0e45c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>ICLRAppDomainResourceMonitor::GetCurrentSurvived — Metoda
Pobiera liczbę bajtów, który udało się przetrwać ostatniego pełnego, blokowanie odzyskiwania pamięci i który odwołuje się bieżącej domeny aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwAppDomainId`  
 [in] Identyfikator domeny żądanej aplikacji.  
  
 `pAppDomainBytesSurvived`  
 [out] Wskaźnik do liczba bajtów, które udało przetrwać po ostatnim wyrzucanie elementów bezużytecznych, które są przechowywane w tej domenie aplikacji. Po pełnej kolekcji ta liczba jest dokładne i kompletne. Po pobraniu tymczasowych ta liczba jest potencjalnie niekompletna. Ten parametr może być `null`.  
  
 `pRuntimeBytesSurvived`  
 [out] Wskaźnik do całkowita liczba bajtów, które udało przetrwać z ostatnich wyrzucanie elementów bezużytecznych. Po pełnej kolekcji liczba ta reprezentuje liczbę bajtów, które są przechowywane w stertach zarządzanych. Po pobraniu tymczasowych liczba ta reprezentuje liczbę bajtów, które są przechowywane na żywo w generacje tymczasowych. Ten parametr może być `null`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|COR_E_APPDOMAINUNLOADED|Domeny aplikacji został zwolniony lub nie istnieje.|  
  
## <a name="remarks"></a>Uwagi  
 Statystyki są aktualizowane tylko po pełnej, blokowanie odzyskiwania pamięci; występuje, oznacza to, kolekcję zawierającą wszystkie generacje i zatrzymuje się podczas pobierania aplikacji. Na przykład <xref:System.GC.Collect?displayProperty=nameWithType> przeciążenie metody wykonuje pełne, blokowanie kolekcji. Współbieżne odzyskiwanie pamięci przebiega w tle i nie są blokowane w aplikacji.  
  
 `GetCurrentSurvived` Metody jest odpowiednikiem niezarządzane zarządzanej <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRAppDomainResourceMonitor — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [Zasobów domen aplikacji monitorowania](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [Hosting — interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
