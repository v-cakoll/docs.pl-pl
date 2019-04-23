---
title: GetHistoryFileDirectory — Funkcja
ms.date: 03/30/2017
api_name:
- GetHistoryFileDirectory
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- GetHistoryFileDirectory
helpviewer_keywords:
- GetHistoryFileDirectory function [.NET Framework fusion]
ms.assetid: 93232222-926e-42ac-b85d-8a6d33977672
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b60dde31707175a27d2dc6c50484d6089adaeaa6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229630"
---
# <a name="gethistoryfiledirectory-function"></a>GetHistoryFileDirectory — Funkcja
Pobiera ścieżkę katalogu historii aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wzDir`  
 [out] Bufor do przechowywania ścieżkę do katalogu historii aplikacji.  
  
 `pdwSize`  
 [out w] Długość buforu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędu modelu COM, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_INVALIDARG|`wzDir` lub `pdwSize` ma wartość null lub wersji ciąg jest niepoprawny.|  
  
## <a name="remarks"></a>Uwagi  
 Po pomyślnym zakończeniu `pdwSize` argument jest równa długości ciągu ścieżki.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Biblioteka:** Fusion.dll i Mscorwks.dll. Użyj Fusion.dll zamiast Mscorwks.dll zapewnienie docelowych poprawną wersję programu .NET Framework.  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [CreateHistoryReader, funkcja](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)
- [NukeDownloadedCache, funkcja](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)
- [Łączenie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
