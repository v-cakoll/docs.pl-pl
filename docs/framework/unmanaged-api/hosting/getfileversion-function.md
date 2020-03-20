---
title: GetFileVersion — Funkcja
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
ms.openlocfilehash: f3b51c1b376fa9c664de53aa76ec724ca305ae6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178178"
---
# <a name="getfileversion-function"></a>GetFileVersion — Funkcja
Pobiera informacje o wersji wspólnego środowiska wykonawczego języka (CLR) określonego pliku przy użyciu określonego buforu.  
  
 Ta funkcja została przestarzała w .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szFilename`  
 [w] Ścieżka pliku, który ma zostać zbadany.  
  
 `szBuffer`  
 [w, na zewnątrz] Bufor przydzielony dla zwracanych informacji o wersji.  
  
 `cchBuffer`  
 [w] Rozmiar, w szerokich `szBuffer`znaków, z .  
  
 `dwLength`  
 [na zewnątrz] Rozmiar (w bajtach) `szBuffer`zwracanego .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
