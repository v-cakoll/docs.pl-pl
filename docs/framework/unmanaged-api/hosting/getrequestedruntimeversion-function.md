---
title: GetRequestedRuntimeVersion — Funkcja
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4083440903e6147ae645f2d6420f19160471841c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779572"
---
# <a name="getrequestedruntimeversion-function"></a>GetRequestedRuntimeVersion — Funkcja
Pobiera numer wersji środowisko uruchomieniowe języka wspólnego (CLR) wymagane przez określoną aplikację. Jeśli ta wersja nie jest zainstalowana, pobiera najbardziej aktualną wersję zainstalowaną przed żądaną wersją.  
  
 Ta funkcja jest przestarzała w programie .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pExe`  
 [in] Nazwa aplikacji.  
  
 `pVersion`  
 [out] Bufor, który zawiera ciąg numeru wersji, po pomyślnym zakończeniu.  
  
 `cchBuffer`  
 [in] Długość buforu wersji.  
  
 `pdwLength`  
 [out] Wskaźnik do długości ciągu numeru wersji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów Component Object Model (COM), zgodnie z definicją w pliku WinError.h oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|ERROR_INSUFFICIENT_BUFFER|Bufor wersji nie jest wystarczająco duży, aby zapisać ciąg wersji.|  
|E_POINTER|`pdwLength` ma wartość null.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetRequestedRuntimeInfo, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetVersionFromProcess, funkcja](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
