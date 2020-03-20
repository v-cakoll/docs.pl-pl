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
ms.openlocfilehash: db721e1ef774c87de0fa7da178463d832a3da756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178152"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo — Funkcja
Pobiera informacje o wersji i katalogu o wspólnym czasie wykonywania języka (CLR) wymagane przez aplikację.  
  
 Ta funkcja została przestarzała w .NET Framework 4.  
  
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
 [w] Nazwa aplikacji.  
  
 `pwszVersion`  
 [w] Ciąg określający numer wersji środowiska wykonawczego.  
  
 `pConfigurationFile`  
 [w] Nazwa pliku konfiguracyjnego skojarzonego `pExe`z programem .  
  
 `startupFlags`  
 [w] Co najmniej jedna [z STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) wartości wyliczenia.  
  
 `runtimeInfoFlags`  
 [w] Co najmniej jedna [z RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) wartości wyliczenia.  
  
 `pDirectory`  
 [na zewnątrz] Bufor, który zawiera ścieżkę katalogu do środowiska wykonawczego po pomyślnym zakończeniu.  
  
 `dwDirectory`  
 [w] Długość buforu katalogu.  
  
 `dwDirectoryLength`  
 [na zewnątrz] Wskaźnik do długości ciągu ścieżki katalogu.  
  
 `pVersion`  
 [na zewnątrz] Bufor, który zawiera numer wersji środowiska wykonawczego po pomyślnym zakończeniu.  
  
 `cchBuffer`  
 [w] Długość buforu ciągu wersji.  
  
 `dwlength`  
 [na zewnątrz] Wskaźnik do długości ciągu wersji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca standardowe kody błędów modelu com (Component Object Model), zgodnie z definicją w pliku WinError.h, oprócz następujących wartości.  
  
|Kod powrotu|Opis|  
|-----------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|ERROR_INSUFFICIENT_BUFFER|Bufor katalogu nie jest wystarczająco duży, aby przechowywać ścieżkę katalogu.<br /><br /> — lub —<br /><br /> Bufor wersji nie jest wystarczająco duży, aby przechowywać ciąg wersji.|  
  
## <a name="remarks"></a>Uwagi  
 Metoda `GetRequestedRuntimeInfo` zwraca informacje w czasie wykonywania o wersji załadowanej do procesu, który niekoniecznie jest najnowszą wersją zainstalowaną na komputerze.  
  
 W .NET Framework w wersji 2.0 można uzyskać informacje o `GetRequestedRuntimeInfo` najnowszej zainstalowanej wersji przy użyciu metody w następujący sposób:  
  
- Określ `pExe` `pwszVersion`, `pConfigurationFile` i parametry jako null.  
  
- Określ flagę RUNTIME_INFO_UPGRADE_VERSION `RUNTIME_INFO_FLAGS` w wyliczeniu `runtimeInfoFlags` parametru.  
  
 Metoda `GetRequestedRuntimeInfo` nie zwraca najnowszej wersji CLR w następujących okolicznościach:  
  
- Istnieje plik konfiguracji aplikacji, który określa ładowanie określonej wersji CLR. Należy zauważyć, że program .NET Framework użyje pliku `pConfigurationFile` konfiguracyjnego, nawet jeśli określisz wartość null dla parametru.  
  
- [Metoda CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) została wywołana określając wcześniejszą wersję CLR.  
  
- Aplikacja, która została skompilowana dla wcześniejszej wersji CLR jest obecnie uruchomiona.  
  
 Dla `runtimeInfoFlags` parametru można określić tylko jedną ze `RUNTIME_INFO_FLAGS` stałych architektury wyliczenia w czasie:  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [GetRequestedRuntimeVersion — Funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess, funkcja](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
