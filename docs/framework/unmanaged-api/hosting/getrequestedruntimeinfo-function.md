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
ms.openlocfilehash: 0efda458d51677fcd16140cd0f0a835b76c20173
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617181"
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
 podczas Nazwa pliku konfiguracji, który jest skojarzony z `pExe` .  
  
 `startupFlags`  
 podczas Co najmniej jedna [STARTUP_FLAGS](startup-flags-enumeration.md) wartości wyliczenia.  
  
 `runtimeInfoFlags`  
 podczas Co najmniej jedna [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) wartości wyliczenia.  
  
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
|ERROR_INSUFFICIENT_BUFFER|Bufor katalogów nie jest wystarczająco duży, aby można było przechowywać ścieżkę do katalogu.<br /><br /> — lub —<br /><br /> Bufor wersji nie jest wystarczająco duży, aby można było przechowywać ciąg wersji.|  
  
## <a name="remarks"></a>Uwagi  
 `GetRequestedRuntimeInfo`Metoda zwraca informacje w czasie wykonywania dotyczące wersji załadowanej do procesu, która nie musi być zainstalowana na komputerze.  
  
 W .NET Framework w wersji 2,0 można uzyskać informacje o najnowszej zainstalowanej wersji za pomocą `GetRequestedRuntimeInfo` metody w następujący sposób:  
  
- Określ `pExe` Parametry, `pwszVersion` i `pConfigurationFile` jako wartości null.  
  
- Określ flagę RUNTIME_INFO_UPGRADE_VERSION w `RUNTIME_INFO_FLAGS` wyliczeniach dla `runtimeInfoFlags` parametru.  
  
 `GetRequestedRuntimeInfo`Metoda nie zwraca najnowszej wersji środowiska CLR w następujących okolicznościach:  
  
- Istnieje plik konfiguracji aplikacji, który określa ładowanie konkretnej wersji środowiska CLR. Należy pamiętać, że .NET Framework użyje pliku konfiguracji nawet w przypadku określenia wartości null dla `pConfigurationFile` parametru.  
  
- Wywołana została Metoda [CorBindToRuntimeEx](corbindtoruntimeex-function.md) określająca wcześniejszą wersję środowiska CLR.  
  
- Aplikacja, która została skompilowana dla starszej wersji środowiska CLR, jest obecnie uruchomiona.  
  
 Dla `runtimeInfoFlags` parametru można określić tylko jedną ze stałych architektury dla `RUNTIME_INFO_FLAGS` wyliczenia jednocześnie:  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetRequestedRuntimeVersion — Funkcja](getrequestedruntimeversion-function.md)
- [GetVersionFromProcess, funkcja](getversionfromprocess-function.md)
- [Przestarzałe funkcje hostingu środowiska CLR](deprecated-clr-hosting-functions.md)
