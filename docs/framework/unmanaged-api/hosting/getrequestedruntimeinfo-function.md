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
ms.openlocfilehash: 9f37be8e3d2e92147e9f13954ab64396062ade2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434984"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo — Funkcja
Pobiera informacje o wersji i katalogu o środowisko uruchomieniowe języka wspólnego (CLR) wymagane przez aplikację.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `pExe`  
 [in] Nazwa aplikacji.  
  
 `pwszVersion`  
 [in] Ciąg określający numer wersji środowiska uruchomieniowego.  
  
 `pConfigurationFile`  
 [in] Nazwa pliku konfiguracji, który jest skojarzony z `pExe`.  
  
 `startupFlags`  
 [in] Co najmniej jednego [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wartości wyliczenia.  
  
 `runtimeInfoFlags`  
 [in] Co najmniej jednego [runtime_info_flags —](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) wartości wyliczenia.  
  
 `pDirectory`  
 [out] Buforu, który zawiera ścieżkę katalogu do środowiska wykonawczego po pomyślnym zakończeniu.  
  
 `dwDirectory`  
 [in] Długość buforu katalogu.  
  
 `dwDirectoryLength`  
 [out] Wskaźnik do długości ciągu ścieżki katalogu.  
  
 `pVersion`  
 [out] Buforu, który zawiera numer wersji środowiska uruchomieniowego na pomyślne zakończenie.  
  
 `cchBuffer`  
 [in] Długość buforu ciągu wersji.  
  
 `dwlength`  
 [out] Wskaźnik do długości ciągu wersji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowy składnik modelu COM. kody błędów, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|ERROR_INSUFFICIENT_BUFFER|Bufor katalogu nie jest wystarczająco duży, aby przechowywać ścieżki katalogu.<br /><br /> - lub -<br /><br /> Bufor wersji nie jest wystarczająco duży, aby zapisać ciąg wersji.|  
  
## <a name="remarks"></a>Uwagi  
 `GetRequestedRuntimeInfo` Metoda zwraca wartość czasu wykonywania informacji o wersji załadowany do procesu, który nie musi być najnowszą wersję zainstalowanego na komputerze.  
  
 Informacje o najnowszej wersji zainstalowanej w programie .NET Framework w wersji 2.0, można uzyskać za pomocą `GetRequestedRuntimeInfo` metody w następujący sposób:  
  
-   Określ `pExe`, `pwszVersion`, i `pConfigurationFile` parametrów jako wartość null.  
  
-   Określ flagę RUNTIME_INFO_UPGRADE_VERSION `RUNTIME_INFO_FLAGS` wyliczenia dla `runtimeInfoFlags` parametru.  
  
 `GetRequestedRuntimeInfo` Metoda nie zwraca najnowszą wersję środowiska CLR w następujących okolicznościach:  
  
-   Istnieje plik konfiguracji aplikacji, która określa ładowania określonej wersji środowiska CLR. Należy pamiętać, że programu .NET Framework będzie pliku konfiguracji nawet, jeśli określono wartość null dla `pConfigurationFile` parametru.  
  
-   [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) wywołano metodę określania starszej wersji środowiska CLR.  
  
-   Obecnie jest uruchomiona aplikacja, która została skompilowana dla starszej wersji środowiska CLR.  
  
 Dla `runtimeInfoFlags` parametru, można określić tylko jeden stałe architektura `RUNTIME_INFO_FLAGS` wyliczenie jednocześnie:  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [GetRequestedRuntimeVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [GetVersionFromProcess, funkcja](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
