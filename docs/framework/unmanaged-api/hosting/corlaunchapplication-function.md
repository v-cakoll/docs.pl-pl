---
title: CorLaunchApplication — Funkcja
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f2a05009caed7bef6da9edee57a4a54b876b18f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580996"
---
# <a name="corlaunchapplication-function"></a>CorLaunchApplication — Funkcja
Uruchamia aplikację w określonej ścieżce sieciowej, przy użyciu określonych manifestów i innych danych aplikacji.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwClickOnceHost`  
 [in] Wartość [host_type —](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) wyliczenie, który określa typ hosta, który uruchamia aplikację.  
  
 `pwzAppFullName`  
 [in] Pełna nazwa aplikacji, który jest on uruchamiany.  
  
 `dwManifestPaths`  
 [in] Liczba ścieżek manifestu dla aplikacji.  
  
 `ppwzManifestPaths`  
 [in] Tablica ciągów, z których każdy określa ścieżkę do manifestu aplikacji, który jest on uruchamiany.  
  
 `dwActivationData`  
 [in] Liczba elementów danych aktywacji dla aplikacji, który jest on uruchamiany.  
  
 `ppwzActivationData`  
 [in] Tablica ciągów, z których każdy jest element danych aktywacji dla aplikacji, który jest on uruchamiany.  
  
 `lpProcessInformation`  
 [out] Wskaźnik do informacji na temat procesu, w którym został załadowany w aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
