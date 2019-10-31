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
ms.openlocfilehash: cd1d9e768698115bee22e35699b044e0c3526d2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136321"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo — Funkcja
Pobiera informacje o wersji i katalogu dotyczące środowiska uruchomieniowego języka wspólnego (CLR) żądanego przez aplikację.  
  
 Ta funkcja jest przestarzała w .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 podczas Nazwa aplikacji.  
  
 `pwszVersion`  
 podczas Ciąg określający numer wersji środowiska uruchomieniowego.  
  
 `pConfigurationFile`  
 podczas Nazwa pliku konfiguracji, który jest skojarzony z `pExe`.  
  
 `startupFlags`  
 podczas Co najmniej jedna wartość wyliczenia [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .  
  
 `runtimeInfoFlags`  
 podczas Co najmniej jedna wartość wyliczenia [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) .  
  
 `pDirectory`  
 określoną Bufor, który zawiera ścieżkę katalogu do środowiska uruchomieniowego po pomyślnym zakończeniu.  
  
 `dwDirectory`  
 podczas Długość buforu katalogów.  
  
 `dwDirectoryLength`  
 określoną Wskaźnik do długości ciągu ścieżki katalogu.  
  
 `pVersion`  
 określoną Bufor zawierający numer wersji środowiska uruchomieniowego po pomyślnym zakończeniu.  
  
 `cchBuffer`  
 podczas Długość buforu ciągu wersji.  
  
 `dwlength`  
 określoną Wskaźnik do długości ciągu wersji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca kody błędów standardowego Component Object Model (COM), jak zdefiniowano w WinError. h, oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|ERROR_INSUFFICIENT_BUFFER|Bufor katalogów nie jest wystarczająco duży, aby można było przechowywać ścieżkę do katalogu.<br /><br /> oraz<br /><br /> Bufor wersji nie jest wystarczająco duży, aby można było przechowywać ciąg wersji.|  
  
## <a name="remarks"></a>Uwagi  
 Metoda `GetRequestedRuntimeInfo` zwraca informacje o wersji załadowanej do procesu, co nie musi być Najnowsza wersja zainstalowana na komputerze.  
  
 W .NET Framework w wersji 2,0 można uzyskać informacje o najnowszej zainstalowanej wersji za pomocą metody `GetRequestedRuntimeInfo` w następujący sposób:  
  
- Określ parametry `pExe`, `pwszVersion`i `pConfigurationFile` jako wartości null.  
  
- Określ flagę RUNTIME_INFO_UPGRADE_VERSION w wyliczeniach `RUNTIME_INFO_FLAGS` dla parametru `runtimeInfoFlags`.  
  
 Metoda `GetRequestedRuntimeInfo` nie zwraca najnowszej wersji środowiska CLR w następujących okolicznościach:  
  
- Istnieje plik konfiguracji aplikacji, który określa ładowanie konkretnej wersji środowiska CLR. Należy pamiętać, że .NET Framework użyje pliku konfiguracji, nawet jeśli dla parametru `pConfigurationFile` określono wartość null.  
  
- Wywołana została Metoda [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) określająca wcześniejszą wersję środowiska CLR.  
  
- Aplikacja, która została skompilowana dla starszej wersji środowiska CLR, jest obecnie uruchomiona.  
  
 Dla parametru `runtimeInfoFlags` można określić tylko jeden z stałych architektury `RUNTIME_INFO_FLAGS` Wyliczenie w danym momencie:  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetRequestedRuntimeVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess, funkcja](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
