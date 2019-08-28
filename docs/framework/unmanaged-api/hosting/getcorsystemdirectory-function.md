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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d30384ea8b9ff4eee41abd43ae39486f770039e7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041427"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory — Funkcja
Zwraca katalog instalacyjny środowiska uruchomieniowego języka wspólnego (CLR), który jest ładowany do procesu. Katalog instalacyjny jest w pełni kwalifikowany, na przykład "c:\Windows\Microsoft.NET\Framework\v1.0.3705".  
  
 Ta funkcja jest przestarzała. Jest zastępowany przez metodę [ICLRRuntimeInfo:: GetRuntimeDirectory —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) podaną w .NET Framework 4.  
  
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
 określoną Bufor, w którym środowisko uruchomieniowe zwraca ciąg, który zawiera w pełni kwalifikowaną nazwę katalogu instalacyjnego dla środowiska uruchomieniowego, które jest ładowane do procesu. Jeśli środowisko uruchomieniowe nie zostało jeszcze załadowane do procesu, funkcja zwróci odpowiednie informacje dotyczące katalogu dla najnowszej wersji środowiska uruchomieniowego zainstalowanej na komputerze.  
  
 `cchBuffer`  
 podczas Rozmiar, w bajtach, z `pbuffer`.  
  
 `dwLength`  
 określoną Liczba znaków zwrócona w `pbuffer`.  
  
## <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
> Nie należy używać tej funkcji w procesach, w których jest uruchomiona wersja 4 środowiska CLR. Jeśli na komputerze jest zainstalowana starsza wersja środowiska CLR, ta funkcja zwróci katalog instalacji dla tej wersji.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** MSCorEE. h  
  
 **Biblioteki** MSCorEE.dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
