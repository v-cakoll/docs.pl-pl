---
title: "_CorValidateImage — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorValidateImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: _CorValidateImage
helpviewer_keywords: _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 03deb62a84a1e9c6cee898fe0023c34b8c538ece
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corvalidateimage-function"></a>_CorValidateImage — Funkcja
Weryfikuje obrazy moduł zarządzany i powiadamia modułu ładującego systemu operacyjnego po ich załadowaniu.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ImageBase`  
 [in] Wskaźnik do początkową lokalizację obrazu do sprawdzania poprawności jako kodu zarządzanego. Obraz musi być już załadowana do pamięci.  
  
 `FileName`  
 [in] Nazwa pliku obrazu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta funkcja zwraca standardowe wartości `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, i `E_FAIL`, a także następujące wartości.  
  
|Wartość zwracana|Opis|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|Obraz jest nieprawidłowy. Ta wartość ma HRESULT 0xC000007BL.|  
|`STATUS_SUCCESS`|Obraz jest nieprawidłowy. Ta wartość ma HRESULT 0x00000000L.|  
  
## <a name="remarks"></a>Uwagi  
 W systemach Windows XP i nowsze wersje modułu ładującego systemu operacyjnego sprawdza, czy modułów zarządzanych, sprawdzając bit katalogu deskryptora COM w typowych nagłówka formatu (COFF) pliku obiektu. Bit zestaw wskazuje modułu zarządzanego. Jeśli moduł ładujący wykryje moduł zarządzany, załadowanie biblioteki MsCorEE.dll i wywołania `_CorValidateImage`, który wykonuje następujące czynności:  
  
-   Potwierdza, że obraz jest prawidłowy moduł zarządzany.  
  
-   Punkt wejścia w obrazie zmienia się na punkt wejścia w środowisku uruchomieniowym języka (wspólnego CLR).  
  
-   64-bitowe wersje systemu Windows modyfikuje obrazu, który znajduje się w pamięci przez przekształcania z plikiem PE32 plikiem PE32 + format.  
  
-   Zwraca do modułu ładującego po załadowaniu obrazów modułu zarządzanego.  
  
 Dla pliku wykonywalnego obrazów, następnie wywołuje modułu ładującego systemu operacyjnego [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) funkcji, niezależnie od punkt wejścia określony w pliku wykonywalnym. Biblioteka DLL zestawu obrazów, wywołuje moduł ładujący [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) funkcji.  
  
 `_CorExeMain`lub `_CorDllMain` wykonuje następujące czynności:  
  
-   Inicjuje środowisko CLR.  
  
-   Lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu.  
  
-   Rozpoczyna wykonanie.  
  
 Wywołania modułu ładującego [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) działać, gdy zarządzany modułu obrazy są usuwane z pamięci. Jednak ta funkcja nie wykonuje żadnych czynności; Zwraca tylko.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Statyczne funkcje globalne metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
