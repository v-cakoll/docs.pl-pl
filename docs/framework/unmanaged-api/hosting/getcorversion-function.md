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
ms.openlocfilehash: 1f40f27651d2d75cf2c3e4d7d1c21e1f47d402af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178190"
---
# <a name="getcorversion-function"></a>GetCORVersion — Funkcja
Zwraca numer wersji środowiska wykonawczego języka wspólnego (CLR), który jest uruchomiony w bieżącym procesie.  
  
 Ta funkcja została przestarzała w .NET Framework 4.  
  
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
 Wskaźnik do buforu, w którym CLR zwraca ciąg określający wersję środowiska wykonawczego, który jest aktualnie ładowany do procesu. Zwracany ciąg ma taką samą formę jak ciągi przekazywane do [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), na przykład "v1.0.1216". Jeśli środowisko wykonawcze nie zostało jeszcze załadowane do procesu, funkcja zwraca odpowiednie informacje o katalogu dla najnowszej wersji środowiska wykonawczego zainstalowanego na komputerze.  
  
 `cchBuffer`  
 Liczba znaków (`WCHAR`s), które mogą `pbuffer`być przechowywane w .  
  
 `dwLength`  
 Wskaźnik do liczby znaków faktycznie `pbuffer`zwróconych w . Jeśli `pbuffer` jest wskaźnikiem zerowym, środowisko wykonawcze zwraca E_POINTER. Jeśli liczba znaków jest większa niż `pbuffer` długość , środowisko wykonawcze zwraca ERROR_INSUFFICIENT_BUFFER.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
