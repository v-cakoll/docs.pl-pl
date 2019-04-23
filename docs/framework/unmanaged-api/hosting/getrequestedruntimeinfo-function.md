---
title: GetRequestedRuntimeInfo — Funkcja
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1290aa864a3f65e549bc26173dcd23648b8dee90
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074888"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo — Funkcja
Pobiera informacje wersji i katalogu o środowisko uruchomieniowe języka wspólnego (CLR) żądane przez aplikację.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,   
    [in]  LPCWSTR  pwszVersion,   
    [in]  LPCWSTR  pConfigurationFile,   
    [in]  DWORD    startupFlags,   
    [in]  DWORD    runtimeInfoFlags,   
    [out] LPWSTR   pDirectory,   
    [in]  DWORD    dwDirectory,   
    [out] DWORD   *dwDirectoryLength,   
    [out] LPWSTR   pVersion,   
    [in]  DWORD    cchBuffer,   
    [out] DWORD   *dwlength  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pExe`  
 [in] Nazwa aplikacji.  
  
 `pwszVersion`  
 [in] Ciąg określający numer wersji środowiska uruchomieniowego.  
  
 `pConfigurationFile`  
 [in] Nazwa pliku konfiguracji, który jest skojarzony z `pExe`.  
  
 `startupFlags`  
 [in] Co najmniej jeden [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wartości wyliczenia.  
  
 `runtimeInfoFlags`  
 [in] Co najmniej jeden [runtime_info_flags —](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) wartości wyliczenia.  
  
 `pDirectory`  
 [out] Bufor, który zawiera ścieżkę katalogu do środowiska uruchomieniowego, po pomyślnym zakończeniu.  
  
 `dwDirectory`  
 [in] Długość buforu katalogu.  
  
 `dwDirectoryLength`  
 [out] Wskaźnik do długości ciągu ścieżki katalogu.  
  
 `pVersion`  
 [out] Bufor, który zawiera numer wersji środowiska uruchomieniowego, po pomyślnym zakończeniu.  
  
 `cchBuffer`  
 [in] Długość buforu ciągu wersji.  
  
 `dwlength`  
 [out] Wskaźnik do długości ciągu wersji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów Component Object Model (COM), zgodnie z definicją w pliku WinError.h oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|ERROR_INSUFFICIENT_BUFFER|Bufor katalogu nie jest wystarczająco duży, aby zapisać ścieżki katalogu.<br /><br /> - lub -<br /><br /> Bufor wersji nie jest wystarczająco duży, aby zapisać ciąg wersji.|  
  
## <a name="remarks"></a>Uwagi  
 `GetRequestedRuntimeInfo` Metoda zwraca wartość czasu wykonywania informacji o wersji załadowany do procesu, który nie musi być najnowszej wersji, które są zainstalowane na komputerze.  
  
 W .NET Framework w wersji 2.0, można uzyskać informacji na temat najnowszej zainstalowanej wersji za pomocą `GetRequestedRuntimeInfo` metody w następujący sposób:  
  
-   Określ `pExe`, `pwszVersion`, i `pConfigurationFile` parametry o wartości null.  
  
-   Określ flagę RUNTIME_INFO_UPGRADE_VERSION `RUNTIME_INFO_FLAGS` wyliczenia dla `runtimeInfoFlags` parametru.  
  
 `GetRequestedRuntimeInfo` Metoda nie zwraca najnowszą wersję środowiska CLR w następujących okolicznościach:  
  
-   Istnieje plik konfiguracji aplikacji, określający, ładowanie określonej wersji środowiska CLR. Pamiętaj, że nawet w przypadku określenia wartości null dla programu .NET Framework będą używać pliku konfiguracji `pConfigurationFile` parametru.  
  
-   [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) wywołano metodę określania starszej wersji środowiska CLR.  
  
-   Aplikacji skompilowanej dla starszej wersji środowiska CLR jest obecnie uruchomiony.  
  
 Dla `runtimeInfoFlags` parametru, można określić tylko jeden stałe architektury `RUNTIME_INFO_FLAGS` wyliczenia w czasie:  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetRequestedRuntimeVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess, funkcja](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
