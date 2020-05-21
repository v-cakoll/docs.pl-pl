---
title: ICorRuntimeHost::NextDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
ms.openlocfilehash: 079164d15141983711e976e0209cc22c818d9cd9
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760423"
---
# <a name="icorruntimehostnextdomain-method"></a>ICorRuntimeHost::NextDomain — Metoda
Pobiera wskaźnik interfejsu do następnej domeny w wyliczeniu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hEnum`  
 podczas Moduł wyliczający uzyskany za pomocą wywołania do [EnumDomains —](icorruntimehost-enumdomains-method.md).  
  
 `pAppDomain`  
 określoną Wskaźnik interfejsu do <xref:System._AppDomain?displayProperty=nameWithType> typu, który reprezentuje następną domenę w wyliczeniu lub wartość null, jeśli nie ma więcej domen.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Operacja zakończyła się pomyślnie.|  
|S_FALSE|Nie można ukończyć operacji lub w wyliczeniu nie ma więcej domen.|  
|E_FAIL|Wystąpił nieznany, Katastrofalny błąd. Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie. Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:** 1,0, 1,1  
  
## <a name="see-also"></a>Zobacz też

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost, interfejs](icorruntimehost-interface.md)
