---
title: ICorRuntimeHost::CreateEvidence — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
ms.openlocfilehash: 4a91f57126c0cf2074bd086ddb2fb4cd9e0716d4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762321"
---
# <a name="icorruntimehostcreateevidence-method"></a>ICorRuntimeHost::CreateEvidence — Metoda
Pobiera wskaźnik interfejsu typu <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> , który umożliwia hostowi tworzenie dowodu bezpieczeństwa do przekazania do metody [ondomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) lub [CreateDomainEx —](icorruntimehost-createdomainex-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pEvidence`  
 określoną Wskaźnik interfejsu do <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> wystąpienia użytego do utworzenia dowodu bezpieczeństwa. Ten wskaźnik jest wpisywany `IUnknown` , dlatego obiekty wywołujące powinny zwykle wywołać `QueryInterface` na tym interfejsie, aby uzyskać wskaźnik do <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> .  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Operacja zakończyła się pomyślnie.|  
|S_FALSE|Nie można ukończyć operacji.|  
|E_FAIL|Wystąpił nieznany, Katastrofalny błąd. Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie. Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca pustą kolekcję, której nie można wypełnić z kodu natywnego. Zamiast tego należy użyć <xref:System.Security.Policy.Evidence> metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersja .NET Framework:** 1,0, 1,1  
  
## <a name="see-also"></a>Zobacz też

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost, interfejs](icorruntimehost-interface.md)
