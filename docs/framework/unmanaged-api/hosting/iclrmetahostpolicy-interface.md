---
title: ICLRMetaHostPolicy — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
ms.openlocfilehash: 79b62a5e2aad9cfcd14ba40c1abf0342bfe57a4b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703529"
---
# <a name="iclrmetahostpolicy-interface"></a>ICLRMetaHostPolicy — Interfejs
Udostępnia metodę [GetRequestedRuntime —](iclrmetahostpolicy-getrequestedruntime-method.md) , która zwraca wskaźnik do interfejsu środowiska uruchomieniowego języka wspólnego (CLR) na podstawie kryteriów zasad, zestawu zarządzanego, wersji i pliku konfiguracji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetRequestedRuntime, metoda](iclrmetahostpolicy-getrequestedruntime-method.md)|Udostępnia preferowany interfejs CLR na podstawie kryteriów zasad, zestawu zarządzanego, wersji i pliku konfiguracji.|  
  
## <a name="remarks"></a>Uwagi  
 Odwołanie do tego interfejsu można uzyskać, wywołując funkcję [CLRCreateInstance](clrcreateinstance-function.md) , jak pokazano w poniższym kodzie:  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> Ten interfejs nie ładuje ani nie aktywuje środowiska CLR, ale po prostu zwraca preferowaną wersję środowiska CLR na podstawie dostępnych wersji zainstalowanych lub załadowanych.  
  
 Interfejs API hostingu .NET Framework 4 konsoliduje zasady tak, aby hosty z konkretnymi potrzebami mogły korzystać z podstawowych funkcji bez ponoszenia niezamierzonych kar. Przykładowo wiele eksportów biblioteki MSCorEE. dll zostanie powiązana z określonym środowiskiem CLR, chociaż Metoda ta może nie być logicznie wymagana. Wyliczenie [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) zawiera zasady powiązań, które są wspólne dla większości hostów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Hosting, interfejsy](hosting-interfaces.md)
- [Hosting](index.md)
