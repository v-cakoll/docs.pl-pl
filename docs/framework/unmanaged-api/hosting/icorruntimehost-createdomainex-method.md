---
title: ICorRuntimeHost::CreateDomainEx — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
ms.openlocfilehash: 4e5856fbcda83c1dd30559c6f59f63495faea78d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762347"
---
# <a name="icorruntimehostcreatedomainex-method"></a>ICorRuntimeHost::CreateDomainEx — Metoda
Tworzy domenę aplikacji. Obiekt wywołujący otrzymuje wskaźnik interfejsu, typu <xref:System._AppDomain> , do wystąpienia typu <xref:System.AppDomain?displayProperty=nameWithType> . Ta metoda umożliwia obiektowi wywołującemu przekazanie wystąpienia IAppDomainSetup — w celu skonfigurowania dodatkowych funkcji zwracanego <xref:System._AppDomain> wystąpienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzFriendlyName`  
 podczas Opcjonalny parametr używany do nadawania przyjaznej nazwy do domeny. Ta przyjazna nazwa może być wyświetlana w interfejsach użytkownika, takich jak debugery, aby identyfikować domenę.  
  
 `pSetup`  
 podczas Opcjonalny wskaźnik interfejsu typu `IAppDomainSetup` , uzyskany przez wywołanie metody [ICorRuntimeHost:: CreateDomainSetup —](icorruntimehost-createdomainsetup-method.md) .  
  
 `pIdentityArray`  
 podczas Opcjonalna tablica wskaźników do `IIdentity` wystąpień, które reprezentują dowody mapowane za pomocą zasad zabezpieczeń w celu ustanowienia zestawu uprawnień. `IIdentity`Obiekt można uzyskać przez wywołanie metody. [CreateEvidence](icorruntimehost-createevidence-method.md)  
  
 `pAppDomain`  
 określoną Wskaźnik interfejsu typu <xref:System._AppDomain> do wystąpienia <xref:System.AppDomain?displayProperty=nameWithType> , które może służyć do dalszej kontroli nad domeną.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Operacja zakończyła się pomyślnie.|  
|S_FALSE|Nie można ukończyć operacji.|  
|E_FAIL|Wystąpił nieznany, Katastrofalny błąd. Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie. Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 `CreateDomainEx`rozszerza możliwości funkcji CreateInstance [przez](icorruntimehost-createdomain-method.md) umożliwienie obiektowi wywołującemu przekazania do `IAppDomainSetup` wystąpienia z wartościami właściwości w celu skonfigurowania domeny aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersja .NET Framework:** 1,0, 1,1  
  
## <a name="see-also"></a>Zobacz też

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [CreateDomain, metoda](icorruntimehost-createdomain-method.md)
- [ICorRuntimeHost, interfejs](icorruntimehost-interface.md)
