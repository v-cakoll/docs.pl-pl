---
title: GetRequestedRuntimeVersionForCLSID — Funkcja
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4b4ac1a37c2b3506216499ed0c9f8194949b768
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081895"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID — Funkcja
Pobiera odpowiednie wspólnego języka wspólnego (CLR) informacje o wersji dla klasy z określonym `CLSID`.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,   
    [out]  LPWSTR     pVersion,   
    [in]  DWORD      cchBuffer,   
    [out] DWORD*     dwLength,   
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `rclsid`  
 [in]  `CLSID` Składnika.  
  
 `pVersion`  
 [out]  Bufor, który zawiera ciąg numeru wersji, po pomyślnym zakończeniu.  
  
 `cchBuffer`  
 [in]  Rozmiar w szerokich znaków z `pVersion` buforu.  
  
 `dwLength`  
 [out] Długość, w bajtach, zwrócone buforu.  
  
 `dwResolutionFlags`  
 [in]  Jedna z wartości clsid_resolution_flags —. Obsługiwane są następujące wartości:  
  
-   CLSID_RESOLUTION_DEFAULT: (0x0) określa, że powinny być używane domyślne zachowanie międzyoperacyjnego.  
  
-   CLSID_RESOLUTION_REGISTERED: (0x1) określa, że powinna być dodatkowo rejestru i podkładek zasady powinny zostać zastosowane.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Wartość zwrócona przez funkcję pomyślnie.|  
|E_INVALIDARG|Jeden z parametrów ma nieprawidłowy typ lub format.|  
|ERROR_INSUFFICIENT_BUFFER|`pVersion` Bufor nie jest wystarczająco duży, aby pomieścić całą wersję ciągu.|  
|REGDB_E_CLASSNOTREG|Istnieje klasa nie zarejestrowana z określonym `CLSID`.|  
|E_POINTER|`dwLength` ma wartość null, lub `cchBuffer` jest wystarczająco duży, aby pomieścić ciąg wersji, ale `pVersion` ma wartość null.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
