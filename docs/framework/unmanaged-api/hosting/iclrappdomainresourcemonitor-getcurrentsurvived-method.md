---
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 648a2c044920b7524ad96ff656e83268ffd55652
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612219"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>ICLRAppDomainResourceMonitor::GetCurrentSurvived — Metoda
Pobiera liczbę bajtów, które przetrwały ostatniej pełnej, blokowanie wyrzucania elementów bezużytecznych i które są przywoływane przez bieżącej domeny aplikacji.  
  
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
 [out] Wskaźnik do liczby bajtów, które przetrwały po ostatnim wyrzucania elementów bezużytecznych, które są przechowywane w tej domenie aplikacji. Po pełnego ta liczba jest dokładne i kompletne. Po pobraniu tymczasowych ta liczba jest potencjalnie niekompletne. Ten parametr może być `null`.  
  
 `pRuntimeBytesSurvived`  
 [out] Wskaźnik do całkowita liczba bajtów, które przetrwały od ostatniego wyrzucania elementów bezużytecznych. Po pełnego ta wartość liczbowa określa liczbę bajtów, które są przechowywane w zarządzanej sterty. Po pobraniu tymczasowych ta wartość liczbowa określa liczbę bajtów, które są przechowywane na żywo w generacje efemeryczne. Ten parametr może być `null`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|COR_E_APPDOMAINUNLOADED|Domeny aplikacji został zwolniony lub nie istnieje.|  
  
## <a name="remarks"></a>Uwagi  
 Statystyki są aktualizowane tylko po pełnej, blokowanie wyrzucania elementów bezużytecznych; oznacza to, że występuje kolekcję zawierającą wszystkie generacje i który zatrzymuje aplikację podczas zbierania. Na przykład <xref:System.GC.Collect?displayProperty=nameWithType> przeciążenie metody wykonywania pełnego, blokowanie pamięci. Współbieżne wyrzucanie elementów bezużytecznych występuje w tle i nie są blokowane w aplikacji.  
  
 `GetCurrentSurvived` Metody odpowiada niezarządzanych zarządzaną <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICLRAppDomainResourceMonitor, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [Monitorowanie zasobów domen aplikacji](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
