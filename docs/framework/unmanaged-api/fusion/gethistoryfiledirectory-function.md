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
ms.openlocfilehash: adbbf94dc36c6d82360ed532b283cd666a1a52ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796850"
---
# <a name="gethistoryfiledirectory-function"></a>GetHistoryFileDirectory — Funkcja
Pobiera ścieżkę katalogu historii aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetHistoryFileDirectory (  
    [in]      LPWSTR      wzDir,  
    [in,out]  LPCWSTR  *pdwsize,  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wzDir`  
 określoną Bufor służący do przechowywania ścieżki do katalogu historii aplikacji.  
  
 `pdwSize`  
 [in. out] Długość buforu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca kody błędów standardowego modelu COM, jak zdefiniowano w pliku WinError. h oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_INVALIDARG|`wzDir`lub `pdwSize` ma wartość null lub ciąg wersji jest niepoprawny.|  
  
## <a name="remarks"></a>Uwagi  
 Po pomyślnym zakończeniu `pdwSize` argument ma ustawioną długość ciągu ścieżki.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Fusion. h  
  
 **Biblioteki** Fusion. dll i mscorwks. dll. Aby upewnić się, że docelowa wersja .NET Framework, należy użyć pliku Fusion. dll zamiast Mscorwks. dll.  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [CreateHistoryReader, funkcja](createhistoryreader-function.md)
- [NukeDownloadedCache, funkcja](nukedownloadedcache-function.md)
- [Łączenie statycznych funkcji globalnych](fusion-global-static-functions.md)
