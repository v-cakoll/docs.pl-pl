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
ms.openlocfilehash: e60c3b06453e0f447249bddf5d4da5c240576577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432963"
---
# <a name="iclrruntimeinfoisloadable-method"></a>ICLRRuntimeInfo::IsLoadable — Metoda
Wskazuje, czy środowisko uruchomieniowe skojarzone z tym interfejsem, mogą zostać załadowane do bieżącego procesu, biorąc pod uwagę innych środowisk uruchomieniowych, który może być już załadowany do procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbLoadable`  
 [out] `true` Jeżeli to środowisko uruchomieniowe może być załadowane do bieżącego procesu; w przeciwnym razie `false`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_POINTER|`pbLoadable` ma wartość null.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli innego środowiska wykonawczego został już załadowany do procesu i mogą być ładowane skojarzone z tym interfejs środowiska uruchomieniowego w trakcie wykonywania side-by-side, `pbLoadable` zwraca `true`. Jeśli dwóch środowisk uruchomieniowych nie można uruchomić side-by-side w procesie, `pbLoadable` zwraca `false`. Na przykład środowisko uruchomieniowe języka wspólnego (CLR) w wersji 4, można uruchomić side-by-side w tym samym procesie z CLR w wersji 2.0 lub CLR w wersji 1.1. Jednak CLR w wersji 1.1 i CLR w wersji 2.0 nie mogą uruchamiać side-by-side w procesie.  
  
 Jeśli żadnych środowisk uruchomieniowych są ładowane do procesu, ta metoda zawsze zwraca `true`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
