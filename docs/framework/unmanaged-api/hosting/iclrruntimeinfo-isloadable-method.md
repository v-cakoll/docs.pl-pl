---
title: ICLRRuntimeInfo::IsLoadable — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9780020abe609212fe3c4bd65f70200467ff9c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533692"
---
# <a name="iclrruntimeinfoisloadable-method"></a>ICLRRuntimeInfo::IsLoadable — Metoda
Wskazuje, czy środowisko uruchomieniowe skojarzona z tym interfejsem, może być załadowany do bieżącego procesu, biorąc pod uwagę innych środowisk wykonawczych, które mogą już być załadowany do procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbLoadable`  
 [out] `true` Jeżeli to środowisko wykonawcze może być załadowany do bieżącego procesu; w przeciwnym razie `false`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pbLoadable` ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli innego środowiska uruchomieniowego jest już załadowany do procesu i środowiska uruchomieniowego skojarzona z tym interfejsem, mogą być ładowane w trakcie wykonywania side-by-side, `pbLoadable` zwraca `true`. Jeśli dwa środowiska uruchomieniowe, nie można uruchomić side-by-side w procesie, `pbLoadable` zwraca `false`. Na przykład środowisko uruchomieniowe języka wspólnego (CLR) w wersji 4, można uruchomić side-by-side jest ten sam proces, za pomocą środowiska CLR w wersji 2.0 lub środowisko CLR w wersji 1.1. Środowisko CLR w wersji 1.1 i środowisko CLR w wersji 2.0 nie można jednak uruchomić side-by-side w procesie.  
  
 Jeśli bez środowisk uruchomieniowych są ładowane do procesu, ta metoda zawsze zwraca `true`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
