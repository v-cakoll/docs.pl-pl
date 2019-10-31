---
title: CreateHistoryReader — Funkcja
ms.date: 03/30/2017
api_name:
- CreateHistoryReader
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateHistoryReader
helpviewer_keywords:
- CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type:
- apiref
ms.openlocfilehash: 80979f0424469bb1d4771ad6507bb8c9d5364ab4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108608"
---
# <a name="createhistoryreader-function"></a>CreateHistoryReader — Funkcja
Tworzy czytelnika historii dla określonego pliku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `wzFilePath`  
 podczas Ścieżka pliku.  
  
 `ppHistoryReader`  
 określoną Po pomyślnym zakończeniu zawiera wskaźnik do czytnika historii.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów COM, jak zdefiniowano w WinError. h, oprócz wartości opisanych w poniższej tabeli.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Wskazuje, że metoda została ukończona pomyślnie.|  
|E_INVALIDARG|Wskazuje, że `wzFilePath` lub `ppHistoryReader` są ustawione na odwołanie o wartości null.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Biblioteka:** Fusion. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Łączenie statycznych funkcji globalnych](fusion-global-static-functions.md)
