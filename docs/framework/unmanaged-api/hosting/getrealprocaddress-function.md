---
title: GetRealProcAddress — Funkcja
ms.date: 03/30/2017
api_name:
- GetRealProcAddress
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRealProcAddress
helpviewer_keywords:
- GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type:
- apiref
ms.openlocfilehash: 4c914e00987053b1c1e9e00bf8e54632175e1de8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178159"
---
# <a name="getrealprocaddress-function"></a>GetRealProcAddress — Funkcja
Pobiera adres określonej funkcji, która jest eksportowana z najnowszej zainstalowanej wersji środowiska wykonawczego języka wspólnego (CLR).  
  
 Ta funkcja została przestarzała w .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwszProcName`  
 [w] Nazwa funkcji.  
  
 `ppv`  
 [na zewnątrz] Lokalizacja, która odbiera wskaźnik do adresu funkcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów modelu com (Component Object Model), zgodnie z definicją w pliku WinError.h, oprócz następujących wartości zdefiniowanych w pliku CorError.h.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_pointer|`ppv`jest nieprawidłowa.|  
|CLR_E_SHIM_RUNTIMEEXPORT|Funkcja nie jest eksportowana ze środowiska wykonawczego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
