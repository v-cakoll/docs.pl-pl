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
ms.openlocfilehash: 426b39aa3d1ada5ae44565a742b70681a7bcf6d3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493477"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage — Funkcja
Sprawdza poprawność obrazów modułu zarządzanego i powiadamia program ładujący system operacyjny po ich załadowaniu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ImageBase`  
 podczas Wskaźnik do lokalizacji początkowej obrazu do zweryfikowania jako kod zarządzany. Obraz musi już być załadowany do pamięci.  
  
 `FileName`  
 podczas Nazwa pliku obrazu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta funkcja zwraca wartości standardowe `E_INVALIDARG` , `E_OUTOFMEMORY` , `E_UNEXPECTED` , i `E_FAIL` , jak również następujące wartości.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|Obraz jest nieprawidłowy. Ta wartość ma wynik HRESULT 0xC000007BL.|  
|`STATUS_SUCCESS`|Obraz jest prawidłowy. Ta wartość ma wynik HRESULT.|  
  
## <a name="remarks"></a>Uwagi  
 W systemie Windows XP i nowszych wersjach moduł ładujący systemu operacyjnego sprawdza moduły zarządzane, sprawdzając bit katalogu deskryptorów COM w nagłówku pliku Common Object Format (COFF). Zestaw bit wskazuje moduł zarządzany. W przypadku wykrycia modułu zarządzanego przez moduł ładujący ładuje biblioteki MsCorEE. dll i wywołania `_CorValidateImage` , które wykonują następujące czynności:  
  
- Potwierdza, że obraz jest prawidłowym modułem zarządzanym.  
  
- Zmienia punkt wejścia w obrazie na punkt wejścia w środowisku uruchomieniowym języka wspólnego (CLR).  
  
- W przypadku 64-bitowych wersji systemu Windows program modyfikuje obraz znajdujący się w pamięci, przekształcając go z PE32 na PE32 + format.  
  
- Zwraca do modułu ładującego po załadowaniu obrazów modułu zarządzanego.  
  
 W przypadku obrazów wykonywalnych program ładujący systemu operacyjnego wywołuje funkcję [_CorExeMain](corexemain-function.md) , niezależnie od punktu wejścia określonego w pliku wykonywalnym. W przypadku obrazów zestawów bibliotek DLL moduł ładujący wywołuje funkcję [_CorDllMain](cordllmain-function.md) .  
  
 `_CorExeMain`lub `_CorDllMain` wykonuje następujące akcje:  
  
- Inicjuje środowisko CLR.  
  
- Lokalizuje zarządzany punkt wejścia z nagłówka CLR zestawu.  
  
- Rozpoczyna wykonywanie.  
  
 Moduł ładujący wywołuje funkcję [_CorImageUnloading](corimageunloading-function.md) , gdy zarządzane obrazy modułu są zwolnione. Jednakże ta funkcja nie wykonuje żadnych działań; Zwraca wartość.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Statyczne funkcje globalne metadanych](../metadata/metadata-global-static-functions.md)
