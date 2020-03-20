---
title: GetVersionFromProcess — Funkcja
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
ms.openlocfilehash: a04a0c5e6865c3664d2cb5fb341c3625e35d4d7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178127"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess — Funkcja
Pobiera numer wersji środowiska wykonawczego języka wspólnego (CLR), który jest skojarzony z określonego dojścia procesu.  
  
 Ta funkcja została przestarzała w .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hProcess`  
 [w] Dojście do procesu.  
  
 `pVersion`  
 [na zewnątrz] Bufor, który zawiera ciąg numeru wersji po pomyślnym zakończeniu metody.  
  
 `cchBuffer`  
 [w] Długość buforu wersji.  
  
 `pdwLength`  
 [na zewnątrz] Wskaźnik do długości ciągu numeru wersji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów modelu com (Component Object Model), zgodnie z definicją w pliku WinError.h, oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_invalidarg|`pVersion`jest null `cchBuffer` i nie jest null lub odwrotnie.<br /><br /> — lub —<br /><br /> `hProcess`nie jest prawidłowym dojściem do procesu.<br /><br /> — lub —<br /><br /> Urządzenie CLR nie jest ładowane.|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer`jest null lub mniejsza niż długość ciągu wersji.|  
|E_notimpl|Ta metoda nie jest dostępna w systemie operacyjnym Microsoft Windows 95, Microsoft Windows 98 lub Microsoft Windows Millennium Edition.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [GetRequestedRuntimeInfo, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion — Funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
