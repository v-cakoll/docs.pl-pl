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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bd398a5b214ac0046d5fe1965f70eef2eedaa6b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490398"
---
# <a name="getcorversion-function"></a>GetCORVersion — Funkcja
Zwraca numer wersji środowisko uruchomieniowe języka wspólnego (CLR) działającego w bieżącym procesie.  
  
 Ta funkcja jest przestarzała w programie .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a>Parametry  
 `pbuffer`  
 Wskaźnik do buforu, w którym środowisko CLR zwraca ciąg określający wersję środowiska uruchomieniowego, która jest aktualnie załadowana do procesu. Zwracanego ciągu ma postać ten sam, jak ciągi przekazywane do [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), na przykład "v1.0.1216". Jeśli środowisko wykonawcze nie został jeszcze załadowany do procesu, funkcja zwraca informacje odpowiedniego katalogu dla najnowszej wersji środowiska uruchomieniowego zainstalowanego na komputerze.  
  
 `cchBuffer`  
 Liczba znaków (`WCHAR`s) mogą być przechowywane w `pbuffer`.  
  
 `dwLength`  
 Wskaźnik do liczby znaków, które faktycznie są zwracane w `pbuffer`. Jeśli `pbuffer` jest wskaźnikiem typu null, środowisko wykonawcze zwraca E_POINTER. Jeśli liczba znaków jest większa następnie długość `pbuffer` , środowisko wykonawcze zwraca ERROR_INSUFFICIENT_BUFFER.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
