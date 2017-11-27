---
title: "GetRequestedRuntimeVersionForCLSID — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeVersionForCLSID
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeVersionForCLSID
helpviewer_keywords: GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a5b9e4b186b6c9b91c1182e8700268f0e1c038f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID — Funkcja
Pobiera odpowiednie wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) informacje o wersji dla klasy z określonym `CLSID`.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `rclsid`  
 [in]  `CLSID` Składnika.  
  
 `pVersion`  
 [out]  Buforu, który zawiera ciąg numer wersji na pomyślne zakończenie.  
  
 `cchBuffer`  
 [in]  Rozmiar w znaki dwubajtowe z `pVersion` buforu.  
  
 `dwLength`  
 [out] Długość, w bajtach buforu zwrócony.  
  
 `dwResolutionFlags`  
 [in]  Jedna z wartości CLSID_RESOLUTION_FLAGS. Obsługiwane są następujące wartości:  
  
-   CLSID_RESOLUTION_DEFAULT: (0x0) określa, że domyślne zachowanie międzyoperacyjnego powinien być używany.  
  
-   CLSID_RESOLUTION_REGISTERED: (0x1) określa, czy rejestr powinna być dodatkowo przeszukiwana i użyć podkładek zasad powinny być stosowane.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Wartość zwrócona przez funkcję pomyślnie.|  
|E_INVALIDARG|Jeden z parametrów ma nieprawidłowy typ lub format.|  
|ERROR_INSUFFICIENT_BUFFER|`pVersion` Bufor nie jest wystarczająco duży, aby pomieścić ciąg całej wersji.|  
|REGDB_E_CLASSNOTREG|Istnieje klasa nie jest zarejestrowany z określonym `CLSID`.|  
|E_POINTER|`dwLength`ma wartość null, lub `cchBuffer` jest wystarczająco duży, aby pomieścić ciąg wersji, ale `pVersion` ma wartość null.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przestarzałe funkcje hostingu środowiska CLR.](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
