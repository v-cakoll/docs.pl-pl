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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 843236243563ce3dff82726aaab05845fa295b9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518140"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess — Funkcja
Pobiera numer wersji środowisko uruchomieniowe języka wspólnego (CLR) skojarzony z określonym dojściem do procesu.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *dwLength  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hProcess`  
 [in] Dojście do procesu.  
  
 `pVersion`  
 [out] Bufor, który zawiera ciąg numeru wersji, po pomyślnym zakończeniu metody.  
  
 `cchBuffer`  
 [in] Długość buforu wersji.  
  
 `pdwLength`  
 [out] Wskaźnik do długości ciągu numeru wersji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów Component Object Model (COM), zgodnie z definicją w pliku WinError.h oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_INVALIDARG|`pVersion` ma wartość null i `cchBuffer` nie ma wartości null, lub na odwrót.<br /><br /> —lub—<br /><br /> `hProcess` nie jest prawidłowym dojściem do procesu.<br /><br /> —lub—<br /><br /> Środowisko CLR nie został załadowany.|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer` jest wartość null lub jest mniejsza niż długość ciągu wersji.|  
|E_NOTIMPL|Ta metoda nie jest dostępna w systemie operacyjnym Microsoft Windows 95, Microsoft Windows 98 lub Microsoft Windows Millennium Edition.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [GetRequestedRuntimeInfo, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
