---
title: "LoadStringRC — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadStringRC
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: LoadStringRC
helpviewer_keywords: LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc93adf575af7f2803b20f24a3261a447772ffd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="loadstringrc-function"></a>LoadStringRC — Funkcja
Tłumaczy wartość HRESULT na komunikat o błędzie, za pomocą domyślną kulturę bieżącego wątku.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iResourceID`  
 [in] HRESULT.  
  
 `szBuffer`  
 [out] Bufor, który zawiera komunikat o błędzie po pomyślnym zakończeniu.  
  
 `iMax`  
 [in] Rozmiar buforu komunikatu błędu.  
  
 `bQuiet`  
 [in] Ignorowane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowy składnik modelu COM. kody błędów, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|E_INVALIDARG|`szBuffer`ma wartość null lub `iMax` wynosi zero (0).|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli metoda nie została zakończona pomyślnie, `szBuffer` zawiera pusty ciąg.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll i Mscorwks.dll.a;a;pierwsza. Użyj biblioteki MSCorEE.dll zamiast Mscorwks.dll.a;a;pierwsza, aby upewnić się, że docelowy poprawna wersja programu .NET Framework.  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [LoadStringRCEx — funkcja](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 [Przestarzałe funkcje hostingu środowiska CLR.](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
