---
title: LoadStringRCEx — Funkcja
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
ms.openlocfilehash: 68332aee895f012bcf6ab6a72936c8dddc7f28a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122039"
---
# <a name="loadstringrcex-function"></a>LoadStringRCEx — Funkcja
Tłumaczy wartość HRESULT na odpowiedni komunikat o błędzie dla określonej kultury.  
  
 Ta funkcja jest przestarzała w .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lcid`  
 podczas Identyfikator kultury. Przekaż wartość 1 dla `lcid`, aby użyć domyślnej kultury.  
  
 `iResourceID`  
 podczas WYNIK HRESULT.  
  
 `szBuffer`  
 określoną Bufor, który zawiera komunikat o błędzie po pomyślnym zakończeniu.  
  
 `iMax`  
 podczas Rozmiar buforu komunikatów o błędach.  
  
 `bQuiet`  
 podczas Ignoruj.  
  
 `pcwchUsed`  
 określoną Wskaźnik do długości komunikatu o błędzie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów COM, jak zdefiniowano w WinError. h, oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_INVALIDARG|`szBuffer` ma wartość null lub `iMax` wynosi zero (0).|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli metoda nie zakończy się pomyślnie, `szBuffer` zawiera pusty ciąg.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [LoadStringRC, funkcja](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
