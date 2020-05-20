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
ms.openlocfilehash: fbaf45da0902ded8a2f7bf0d470aaed3b5f531aa
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617129"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess — Funkcja
Pobiera numer wersji środowiska uruchomieniowego języka wspólnego (CLR), który jest skojarzony z określonym dojściem do procesu.  
  
 Ta funkcja jest przestarzała w .NET Framework 4.  
  
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
 podczas Dojście do procesu.  
  
 `pVersion`  
 określoną Bufor zawierający ciąg numeru wersji po pomyślnym zakończeniu metody.  
  
 `cchBuffer`  
 podczas Długość buforu wersji.  
  
 `pdwLength`  
 określoną Wskaźnik do długości ciągu numeru wersji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca kody błędów standardowego Component Object Model (COM), jak zdefiniowano w WinError. h, oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_INVALIDARG|`pVersion`ma wartość null i `cchBuffer` nie ma wartości null lub odwrotnie.<br /><br /> -lub-<br /><br /> `hProcess`nie jest prawidłowym dojściem do procesu.<br /><br /> -lub-<br /><br /> Środowisko CLR nie jest załadowane.|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer`ma wartość null lub jest mniejsza niż długość ciągu wersji.|  
|E_NOTIMPL|Ta metoda nie jest dostępna w systemie operacyjnym Microsoft Windows 95, Microsoft Windows 98 lub Microsoft Windows Millennium Edition.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetRequestedRuntimeInfo, funkcja](getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion — Funkcja](getrequestedruntimeversion-function.md)
- [Przestarzałe funkcje hostingu środowiska CLR](deprecated-clr-hosting-functions.md)
