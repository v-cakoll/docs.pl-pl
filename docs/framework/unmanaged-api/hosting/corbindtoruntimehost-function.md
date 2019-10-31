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
ms.openlocfilehash: a6d9708e7281a72c88ba28012006784f7b0ee9d9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124357"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost — Funkcja
Włącza hosty do załadowania określonej wersji środowiska uruchomieniowego języka wspólnego (CLR) do procesu.  
  
 Ta funkcja jest przestarzała w .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `pwszVersion`  
 podczas Ciąg opisujący wersję środowiska CLR, które chcesz załadować.  
  
 Numer wersji w .NET Framework składa się z czterech części oddzielonych kropkami: *główna. pomocnicza. kompilacja. poprawka*. Ciąg przesłany jako `pwszVersion` musi rozpoczynać się od znaku "v", po którym następuje pierwsze trzy części numeru wersji (na przykład "v 1.0.1529").  
  
 Niektóre wersje środowiska CLR są instalowane z instrukcją zasad, która określa zgodność z poprzednimi wersjami środowiska CLR. Domyślnie podkładka uruchamiania szacuje `pwszVersion` względem instrukcji zasad i ładuje najnowszą wersję środowiska uruchomieniowego, która jest zgodna z żądaną wersją. Host może zmusić podkładkę do pominięcia oceny zasad i załadowania dokładnej wersji określonej w `pwszVersion` przez przekazanie wartości STARTUP_LOADER_SAFEMODE dla parametru `startupFlags`.  
  
 Jeśli `pwszVersion` jest `null,` Metoda nie ładuje żadnej wersji środowiska CLR. Zamiast tego zwraca CLR_E_SHIM_RUNTIMELOAD, co oznacza, że ładowanie środowiska uruchomieniowego nie powiodło się.  
  
 `pwszBuildFlavor`  
 podczas Ciąg określający, czy załadować serwer lub kompilację stacji roboczej środowiska CLR. Prawidłowe wartości to `svr` i `wks`. Kompilacja serwera jest zoptymalizowana pod kątem wykorzystania wielu procesorów na potrzeby wyrzucania elementów bezużytecznych, a kompilacja stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich uruchomionych na komputerze z jednym procesorem.  
  
 Jeśli `pwszBuildFlavor` ma wartość null, zostanie załadowana kompilacja stacji roboczej. W przypadku uruchamiania na komputerze z jednym procesorem kompilacja stacji roboczej jest zawsze ładowana, nawet jeśli `pwszBuildFlavor` jest ustawiona na `svr`. Jeśli jednak `pwszBuildFlavor` jest ustawiona na `svr` i zostanie określone współbieżne wyrzucanie elementów bezużytecznych (zobacz opis parametru `startupFlags`), kompilacja serwera zostanie załadowana.  
  
> [!NOTE]
> Współbieżne wyrzucanie elementów bezużytecznych nie jest obsługiwane w aplikacjach uruchamiających emulator WOW64 x86 w systemach 64-bitowych, które implementują architekturę Intel Itanium (dawniej zwane IA-64). Aby uzyskać więcej informacji na temat korzystania z emulatora WOW64 w systemach 64-bitowych systemu Windows, zobacz [Uruchamianie aplikacji 32-bitowych](/windows/desktop/WinProg64/running-32-bit-applications).  
  
 `pwszHostConfigFile`  
 podczas Nazwa pliku konfiguracji hosta, który określa wersję środowiska CLR do załadowania. Jeśli nazwa pliku nie zawiera w pełni kwalifikowanej ścieżki, zakłada się, że plik znajduje się w tym samym katalogu co plik wykonywalny, który wykonuje wywołanie.  
  
 `pReserved`  
 podczas Zarezerwowane do użytku w przyszłości.  
  
 `startupFlags`  
 podczas Zestaw flag kontrolujących współbieżne odzyskiwanie pamięci, kod neutralny przez domenę i zachowanie parametru `pwszVersion`. Wartość domyślna to pojedyncza domena, jeśli flaga nie jest ustawiona. Aby uzyskać listę obsługiwanych wartości, zobacz [Wyliczenie STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
 `rclsid`  
 podczas `CLSID` klasy coclass implementującej interfejs [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) . Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.  
  
 `riid`  
 podczas `IID` żądanego interfejsu. Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.  
  
 `ppv`  
 określoną Wskaźnik interfejsu do wersji środowiska uruchomieniowego, która została załadowana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. idl  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
