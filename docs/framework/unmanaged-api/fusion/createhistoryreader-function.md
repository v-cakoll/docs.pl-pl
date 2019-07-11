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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee30d4f32e05fab27ae70052b28d3d152594cf90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778416"
---
# <a name="createhistoryreader-function"></a>CreateHistoryReader — Funkcja
Tworzy czytnik historii dla określonego pliku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `wzFilePath`  
 [in] Ścieżka do pliku.  
  
 `ppHistoryReader`  
 [out] Po pomyślnym zakończeniu zawiera wskaźnik do czytnika historii.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowych kodów błędu modelu COM, zgodnie z definicją w pliku WinError.h, oprócz wartości opisanych w poniższej tabeli.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Wskazuje, czy metoda zakończyła się pomyślnie.|  
|E_INVALIDARG|Oznacza to, że `wzFilePath` lub `ppHistoryReader` są ustawione na odwołanie o wartości null.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Biblioteka:** Fusion.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Łączenie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
