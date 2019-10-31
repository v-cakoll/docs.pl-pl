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
ms.openlocfilehash: ce0c6307defd93dcf63ac4e9051fc798041475f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127051"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID — Funkcja
Pobiera odpowiednie informacje o wersji środowiska uruchomieniowego języka wspólnego (CLR) dla klasy z określonym `CLSID`.  
  
 Ta funkcja jest przestarzała w .NET Framework 4.  
  
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
 podczas  `CLSID` składnika.  
  
 `pVersion`  
 określoną  Bufor zawierający ciąg numeru wersji po pomyślnym zakończeniu.  
  
 `cchBuffer`  
 podczas  Rozmiar (w bajtach) w buforze `pVersion`.  
  
 `dwLength`  
 określoną Długość (w bajtach) zwróconego buforu.  
  
 `dwResolutionFlags`  
 podczas  Jedna z wartości CLSID_RESOLUTION_FLAGS. Obsługiwane są następujące wartości:  
  
- CLSID_RESOLUTION_DEFAULT: (0x0) określa, że należy użyć domyślnego zachowania międzyoperacyjności.  
  
- CLSID_RESOLUTION_REGISTERED: (0x1) określa, że rejestr powinien być przeszukiwany, a zasady podkładki powinny być stosowane.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Funkcja została pomyślnie zwrócona.|  
|E_INVALIDARG|Jeden z parametrów ma nieprawidłowy typ lub format.|  
|ERROR_INSUFFICIENT_BUFFER|Bufor `pVersion` nie jest wystarczająco duży, aby pomieścić cały ciąg wersji.|  
|REGDB_E_CLASSNOTREG|Nie ma żadnej klasy zarejestrowanej w określonym `CLSID`.|  
|E_POINTER|`dwLength` ma wartość null lub `cchBuffer` jest wystarczająco duży, aby pomieścić ciąg wersji, ale `pVersion` ma wartość null.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
