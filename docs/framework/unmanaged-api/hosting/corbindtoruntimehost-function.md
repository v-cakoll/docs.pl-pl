---
title: CorBindToRuntimeHost — Funkcja
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c1d83b32402343f3cd2b5403e328698abd6a930
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436218"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost — Funkcja
Umożliwia hostom do ładowania określonej wersji środowisko uruchomieniowe języka wspólnego (CLR) do procesu.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszVersion`  
 [in] Ciąg opisujący wersję środowiska CLR chcesz załadować.  
  
 Numer wersji w programie .NET Framework składa się z czterech części oddzielone kropkami: *główna.pomocnicza.kompilacja.poprawka*. Ciąg przekazany jako `pwszVersion` musi rozpoczynać się od znaku "v" następuje pierwsze trzy części numer wersji (na przykład "v1.0.1529").  
  
 Niektóre wersje środowiska CLR są instalowane z instrukcji zasad, która określa zgodność z poprzednimi wersjami środowiska CLR. Domyślnie, ocenia podkładki uruchamiania `pwszVersion` przed deklaracji zasad i obciążeń najnowszą wersję środowiska uruchomieniowego który jest zgodny z wersją żądanej. Hosta można wymusić podkładki, aby pominąć oceny zasad i załadować dokładnej wersji określonej w `pwszVersion` przez przekazanie wartości STARTUP_LOADER_SAFEMODE dla `startupFlags` parametru.  
  
 Jeśli `pwszVersion` jest `null,` metody nie zostanie załadowany z dowolnej wersji środowiska CLR. W zamian zwraca CLR_E_SHIM_RUNTIMELOAD, co oznacza, że nie można załadować środowiska wykonawczego.  
  
 `pwszBuildFlavor`  
 [in] Ciąg, który określa, czy ładowanie serwera lub stacji roboczej kompilacji środowiska CLR. Prawidłowe wartości to `svr` i `wks`. Zoptymalizowano kompilacji serwera mógł korzystać z wielu procesorów do wyrzucania i kompilacji stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich działających na maszynie jeden procesor.  
  
 Jeśli `pwszBuildFlavor` ma wartość null, jest ładowany kompilacji stacji roboczej. Podczas uruchamiania na maszynie jeden procesor, zawsze jest ładowany kompilacji stacji roboczej, nawet jeśli `pwszBuildFlavor` ma ustawioną wartość `svr`. Jednak jeśli `pwszBuildFlavor` ustawiono `svr` i określono współbieżne odzyskiwanie pamięci (w opisie `startupFlags` parametru), serwer kompilacji został załadowany.  
  
> [!NOTE]
>  Współbieżne odzyskiwanie pamięci nie jest obsługiwany w aplikacji uruchomionych WOW64 x86 emulator na 64-bitowe systemy, które implementują architektura Intel Itanium (nazywanych IA-64). Aby uzyskać więcej informacji o używaniu WOW64 na 64-bitowym systemie Windows, temacie [uruchomiona 32-bitowych aplikacji](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx).  
  
 `pwszHostConfigFile`  
 [in] Nazwa pliku konfiguracji hosta, który określa wersję środowiska CLR do załadowania. Jeśli nazwa pliku nie ma w pełni kwalifikowana, plik zakłada się, że w tym samym katalogu co plik wykonywalny, który jest wywołania.  
  
 `pReserved`  
 [in] Zarezerwowane dla przyszłego rozszerzalności.  
  
 `startupFlags`  
 [in] Zestaw flag, które kontroluje współbieżne odzyskiwanie pamięci, kod o neutralnym poziomie domeny i zachowanie `pwszVersion` parametru. Wartość domyślna to jednej domenie, jeśli flaga nie jest ustawiona. Aby uzyskać listę obsługiwanych wartości, zobacz [STARTUP_FLAGS — wyliczenie](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
 `rclsid`  
 [in] `CLSID` Klasy coclass, który implementuje albo [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interfejsu. Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.  
  
 `riid`  
 [in] `IID` Interfejsu żądania dostępu. Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Wskaźnik interfejsu do wersji środowiska uruchomieniowego, które zostały załadowane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [CorBindToRuntimeByCfg, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
