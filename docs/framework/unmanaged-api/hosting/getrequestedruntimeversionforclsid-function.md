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
ms.openlocfilehash: 6132e94544b30486b70ecfec49c1ddd5e3c0f50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178113"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID — Funkcja
Pobiera odpowiednie informacje o wersji wspólnego środowiska wykonawczego języka (CLR) dla klasy z określonym `CLSID`.  
  
 Ta funkcja została przestarzała w .NET Framework 4.  
  
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
 [w]  Składnika. `CLSID`  
  
 `pVersion`  
 [na zewnątrz]  Bufor, który zawiera ciąg numeru wersji po pomyślnym zakończeniu.  
  
 `cchBuffer`  
 [w]  Rozmiar buforu `pVersion` w postaci szerokich znaków.  
  
 `dwLength`  
 [na zewnątrz] Długość w bajtach zwracanego buforu.  
  
 `dwResolutionFlags`  
 [w]  Jedną z CLSID_RESOLUTION_FLAGS wartości. Obsługiwane są następujące wartości:  
  
- CLSID_RESOLUTION_DEFAULT: (0x0) Określa, że domyślne zachowanie interop powinny być używane.  
  
- CLSID_RESOLUTION_REGISTERED: (0x1) Określa, że rejestr powinien być przeszukiwany i zasady podkładki powinny być stosowane.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Funkcja została zwrócona pomyślnie.|  
|E_invalidarg|Jeden z parametrów ma nieprawidłowy typ lub format.|  
|ERROR_INSUFFICIENT_BUFFER|Bufor `pVersion` nie jest wystarczająco duży, aby pomieścić cały ciąg wersji.|  
|REGDB_E_CLASSNOTREG|Nie ma żadnej klasy `CLSID`zarejestrowanej z określonym .|  
|E_pointer|`dwLength`jest null `cchBuffer` lub jest wystarczająco duży, aby `pVersion` pomieścić ciąg wersji, ale jest null.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
