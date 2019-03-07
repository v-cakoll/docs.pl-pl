---
title: LoadStringRC — Funkcja
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e020b65966dc03bf326220ab0bab26bc61155c0c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485489"
---
# <a name="loadstringrc-function"></a>LoadStringRC — Funkcja
Tłumaczy wartość HRESULT na komunikat o błędzie przy użyciu domyślnej kultury bieżącego wątku.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iResourceID`  
 [in] Wartość HRESULT.  
  
 `szBuffer`  
 [out] Bufor, który zawiera komunikat o błędzie po pomyślnym zakończeniu.  
  
 `iMax`  
 [in] Rozmiar buforu komunikatu błędu.  
  
 `bQuiet`  
 [in] Ignorowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów Component Object Model (COM), zgodnie z definicją w pliku WinError.h oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_INVALIDARG|`szBuffer` ma wartość null lub `iMax` wynosi zero (0).|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli metoda nie została zakończona pomyślnie, `szBuffer` zawiera pusty ciąg.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll i Mscorwks.dll. Użyj MSCorEE.dll zamiast Mscorwks.dll zapewnienie docelowych poprawną wersję programu .NET Framework.  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [LoadStringRCEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
