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
ms.openlocfilehash: 9dfce10c94e04dcd405e06ab6d0984e64984709e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779562"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID — Funkcja
Pobiera odpowiednie wspólnego języka wspólnego (CLR) informacje o wersji dla klasy z określonym `CLSID`.  
  
 Ta funkcja jest przestarzała w programie .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
- CLSID_RESOLUTION_DEFAULT: (0x0) określa, że powinny być używane domyślne zachowanie międzyoperacyjnego.  
  
- CLSID_RESOLUTION_REGISTERED: (0x1) określa, że powinna być dodatkowo rejestru i podkładek zasady powinny zostać zastosowane.  
  
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
