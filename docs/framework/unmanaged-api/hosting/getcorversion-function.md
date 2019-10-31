---
title: GetCORVersion — Funkcja
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
ms.openlocfilehash: 1283abaf6b08af1d842d8fe4469f7f6c15e38ec5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136419"
---
# <a name="getcorversion-function"></a>GetCORVersion — Funkcja
Zwraca numer wersji środowiska uruchomieniowego języka wspólnego (CLR), który jest uruchomiony w bieżącym procesie.  
  
 Ta funkcja jest przestarzała w .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a>Parametry  
 `pbuffer`  
 Wskaźnik do buforu, w którym środowisko CLR zwraca ciąg określający wersję środowiska uruchomieniowego, która jest aktualnie załadowana do procesu. Zwrócony ciąg przyjmuje ten sam formularz, co ciągi przesłane do [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), na przykład "v 1.0.1216". Jeśli środowisko uruchomieniowe nie zostało jeszcze załadowane do procesu, funkcja zwróci odpowiednie informacje dotyczące katalogu dla najnowszej wersji środowiska uruchomieniowego zainstalowanej na komputerze.  
  
 `cchBuffer`  
 Liczba znaków (`WCHAR`s), które mogą być przechowywane w `pbuffer`.  
  
 `dwLength`  
 Wskaźnik do liczby znaków faktycznie zwróconych w `pbuffer`. Jeśli `pbuffer` jest wskaźnikiem typu null, środowisko uruchomieniowe zwraca E_POINTER. Jeśli liczba znaków jest większa niż długość `pbuffer`, środowisko uruchomieniowe zwróci wartość ERROR_INSUFFICIENT_BUFFER.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
