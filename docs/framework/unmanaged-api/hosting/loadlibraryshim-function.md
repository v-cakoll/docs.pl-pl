---
title: "LoadLibraryShim — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LoadLibraryShim
helpviewer_keywords:
- LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5b8fe8413d0eff332e60508a083f03574e58d7bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim — Funkcja
Ładuje określona wersja biblioteki DLL, która jest uwzględniona w pakiet redystrybucyjny programu .NET Framework.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Użyj [ICLRRuntimeInfo::LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szDllName`  
 [in] Ciąg zakończony zerem, który reprezentuje nazwę biblioteki DLL do załadowania z biblioteki .NET Framework.  
  
 `szVersion`  
 [in] Ciąg zakończony zerem, który reprezentuje wersja biblioteki DLL do załadowania. Jeśli `szVersion` jest null, wersja wybrany na potrzeby ładowania jest najnowsza wersja określonej biblioteki DLL, która jest mniejsza niż w wersji 4. Oznacza to, że wszystkie wersje, równa lub większa niż wersja 4 są ignorowane, jeśli `szVersion` ma wartość null, a jeśli nie wcześniejszą niż wersja w wersji 4 jest zainstalowana, biblioteki DLL nie udało się załadować. Dzięki tej instalacji [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] nie wpływa na istniejące aplikacje lub składników. Zobacz wpis [SxS wewnątrzprocesową i migracji Szybki Start](http://go.microsoft.com/fwlink/?LinkId=200329) w blogu zespołu CLR.  
  
 `pvReserved`  
 Zarezerwowane do użytku w przyszłości.  
  
 `phModDll`  
 [out] Wskaźnik do uchwytu modułu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowy składnik modelu COM. kody błędów, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|CLR_E_SHIM_RUNTIMELOAD|Ładowanie `szDllName` wymaga ładowania środowisko uruchomieniowe języka wspólnego (CLR) i wymaganej wersji aparatu CLR nie może zostać załadowany.|  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja jest używana do załadowania biblioteki dll, które znajdują się w pakiet redystrybucyjny programu .NET Framework. Nie ładuje wygenerowaną przez użytkowników biblioteki dll.  
  
> [!NOTE]
>  Począwszy od programu .NET Framework w wersji 2.0, ładowanie Fusion.dll powoduje, że można załadować środowiska CLR. Jest to spowodowane funkcje w Fusion.dll są teraz otoki którego implementacje znajdują się w czasie wykonywania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
