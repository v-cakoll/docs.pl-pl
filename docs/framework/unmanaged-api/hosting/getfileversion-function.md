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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1f5508e9ee41d8670b43d5b219846237e11fc8f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778143"
---
# <a name="getfileversion-function"></a>GetFileVersion — Funkcja
Pobiera wspólnego języka wspólnego (CLR) informacje o wersji określonego pliku, przy użyciu określonego bufora.  
  
 Ta funkcja jest przestarzała w programie .NET Framework 4.  
  
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
 [in] Ścieżka pliku do badania.  
  
 `szBuffer`  
 [out w] Bufor przydzielony, aby uzyskać informacje o wersji, która jest zwracana.  
  
 `cchBuffer`  
 [in] Rozmiar w szerokich znaków z `szBuffer`.  
  
 `dwLength`  
 [out] Rozmiar w bajtach zwracanego `szBuffer`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
