---
title: GetCORSystemDirectory — Funkcja
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: bdafacfe52d678aacfcd44de1e924bcb88547424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178205"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory — Funkcja
Zwraca katalog instalacyjny środowiska wykonawczego języka wspólnego (CLR), który jest ładowany do procesu. Katalog instalacyjny jest w pełni kwalifikowany, na przykład "c:\windows\microsoft.net\framework\v1.0.3705".  
  
 Ta funkcja jest przestarzała. Zastępuje go metoda [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) dostępna w ramach .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a>Parametry  
 `pbuffer`  
 [na zewnątrz] Bufor, w którym środowisko wykonawcze zwraca ciąg zawierający w pełni kwalifikowaną nazwę katalogu instalacyjnego dla środowiska wykonawczego, który jest ładowany do procesu. Jeśli środowisko wykonawcze nie zostało jeszcze załadowane do procesu, funkcja zwraca odpowiednie informacje o katalogu dla najnowszej wersji środowiska wykonawczego zainstalowanego na komputerze.  
  
 `cchBuffer`  
 [w] Rozmiar w bajtach `pbuffer`.  
  
 `dwLength`  
 [na zewnątrz] Liczba znaków zwróconych `pbuffer`w pliku .  
  
## <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
> Nie należy używać tej funkcji w procesach, które są uruchomione w wersji 4 CLR. Jeśli na komputerze jest zainstalowana wcześniejsza wersja programu CLR, ta funkcja zwraca katalog instalacyjny dla tej wersji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
