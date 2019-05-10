---
title: _CorValidateImage — Funkcja
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04e562b41b3d835d66fb9b803ee7db1c7fb8537f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662558"
---
# <a name="corvalidateimage-function"></a>_CorValidateImage — Funkcja
Sprawdza poprawność obrazów modułu zarządzanego i powiadamia moduł ładujący systemu operacyjnego po ich załadowaniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ImageBase`  
 [in] Wskaźnik do początkową lokalizację obrazu do weryfikacji jako kod zarządzany. Obraz musi już być ładowane do pamięci.  
  
 `FileName`  
 [in] Nazwa pliku obrazu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta funkcja zwraca wartości standardowych `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, i `E_FAIL`, a także poniższych wartości.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|Obraz jest nieprawidłowy. Ta wartość ma HRESULT 0xC000007BL.|  
|`STATUS_SUCCESS`|Obraz jest prawidłowy. Ta wartość ma HRESULT 0x00000000L.|  
  
## <a name="remarks"></a>Uwagi  
 Windows XP i nowszych wersjach moduł ładujący systemu operacyjnego sprawdza, czy modułów zarządzanych, sprawdzając bit COM deskryptora katalogu, w nagłówku format (COFF) pliku obiektu wspólnego. Ustawionego bitu wskazuje modułu zarządzanego. Jeśli moduł ładujący wykryje modułu zarządzanego, ładuje MsCorEE.dll i wywołania `_CorValidateImage`, który wykonuje następujące czynności:  
  
- Potwierdza, że obraz jest prawidłowy modułu zarządzanego.  
  
- Zmiany punktu wejścia w obrazie punktu wejścia w środowisku uruchomieniowym języka (wspólnego CLR).  
  
- Dla 64-bitowej wersji systemu Windows modyfikuje obrazu, który znajduje się w pamięci przez przekształcenie go z PE32 je typu PE32 + format.  
  
- Zwraca do modułu ładującego, gdy obrazy modułu zarządzanego są ładowane.  
  
 Obrazy wykonywalne, następnie wywołuje moduł ładujący systemu operacyjnego [_corexemain —](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) funkcji, niezależnie od tego, w punkcie wejścia określonym w pliku wykonywalnym. Biblioteka DLL zestawu obrazów, wywołuje moduł ładujący [_cordllmain —](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) funkcji.  
  
 `_CorExeMain` lub `_CorDllMain` wykonuje następujące czynności:  
  
- Inicjuje środowisko CLR.  
  
- Lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu.  
  
- Rozpoczyna wykonywanie.  
  
 Wywołania modułu ładującego [_corimageunloading —](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) działają w przypadku zarządzanych obrazów modułu są usuwane z pamięci. Jednak ta funkcja nie wykonuje żadnych akcji; po prostu zwraca.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
