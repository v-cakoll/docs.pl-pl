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
ms.openlocfilehash: 3a6da0e845fa50d090cdf0808b211a5806c40961
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178217"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage — Funkcja
Sprawdza poprawność obrazów modułów zarządzanych i powiadamia moduł ładujący systemu operacyjnego po ich załadowaniu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ImageBase`  
 [w] Wskaźnik do lokalizacji początkowej obrazu, aby sprawdzić poprawność jako kod zarządzany. Obraz musi być już załadowany do pamięci.  
  
 `FileName`  
 [w] Nazwa pliku obrazu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta funkcja zwraca `E_INVALIDARG`wartości `E_OUTOFMEMORY` `E_UNEXPECTED`standardowe `E_FAIL`, , i , a także następujące wartości.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|Obraz jest nieprawidłowy. Ta wartość ma HRESULT 0xC000007BL.|  
|`STATUS_SUCCESS`|Obraz jest prawidłowy. Ta wartość ma HRESULT 0x0000000L.|  
  
## <a name="remarks"></a>Uwagi  
 W systemie Windows XP i nowszych wersjach program ładujący systemu operacyjnego sprawdza moduły zarządzane, sprawdzając bit katalogu deskryptora COM w nagłówku wspólnego formatu pliku obiektu (COFF). Bit zestawu wskazuje moduł zarządzany. Jeśli moduł ładujący wykryje moduł zarządzany, ładuje msCorEE.dll i wywołuje `_CorValidateImage`, który wykonuje następujące akcje:  
  
- Potwierdza, że obraz jest prawidłowym modułem zarządzanym.  
  
- Zmienia punkt wejścia na obrazie na punkt wejścia w czasie wykonywania języka wspólnego (CLR).  
  
- W przypadku 64-bitowych wersji systemu Windows modyfikuje obraz w pamięci, przekształcając go z pe32 do formatu PE32+.  
  
- Powraca do modułu ładującego po załadowaniu obrazów modułu zarządzanego.  
  
 W przypadku obrazów wykonywalnych program ładujący systemu operacyjnego wywołuje następnie funkcję [_CorExeMain,](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) niezależnie od punktu wejścia określonego w pliku wykonywalnym. W przypadku obrazów zestawu DLL moduł ładujący wywołuje funkcję [_CorDllMain.](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
  
 `_CorExeMain`lub `_CorDllMain` wykonuje następujące czynności:  
  
- Inicjuje clr.  
  
- Lokalizuje zarządzany punkt wejścia z nagłówka CLR zestawu.  
  
- Rozpoczyna wykonywanie.  
  
 Moduł ładujący wywołuje funkcję [_CorImageUnloading,](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) gdy obrazy modułów zarządzanych są zwalniane. Jednak ta funkcja nie wykonuje żadnych akcji; po prostu powraca.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
