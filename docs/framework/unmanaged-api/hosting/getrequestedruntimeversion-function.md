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
ms.openlocfilehash: 6be0bc5d08f612dcb8ed7d256711e0c4367b9274
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178135"
---
# <a name="getrequestedruntimeversion-function"></a>GetRequestedRuntimeVersion — Funkcja
Pobiera numer wersji środowiska wykonawczego języka wspólnego (CLR) wymagane przez określoną aplikację. Jeśli ta wersja nie jest zainstalowana, pobiera najnowszą wersję, która jest zainstalowana przed żądaną wersją.  
  
 Ta funkcja została przestarzała w .NET Framework 4.  
  
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
 [w] Nazwa aplikacji.  
  
 `pVersion`  
 [na zewnątrz] Bufor, który zawiera ciąg numeru wersji po pomyślnym zakończeniu.  
  
 `cchBuffer`  
 [w] Długość buforu wersji.  
  
 `pdwLength`  
 [na zewnątrz] Wskaźnik do długości ciągu numeru wersji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów modelu com (Component Object Model), zgodnie z definicją w pliku WinError.h, oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|ERROR_INSUFFICIENT_BUFFER|Bufor wersji nie jest wystarczająco duży, aby przechowywać ciąg wersji.|  
|E_pointer|`pdwLength`ma wartość null.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [GetRequestedRuntimeInfo, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetVersionFromProcess, funkcja](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
