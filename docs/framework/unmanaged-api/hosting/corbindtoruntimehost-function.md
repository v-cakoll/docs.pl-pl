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
ms.openlocfilehash: 6566adc442034763e0209869404b60b5afa63866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176490"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost — Funkcja
Umożliwia hostom załadowanie określonej wersji środowiska wykonawczego języka wspólnego (CLR) do procesu.  
  
 Ta funkcja została przestarzała w .NET Framework 4.  
  
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
 [w] Ciąg opisujący wersję programu CLR, którą chcesz załadować.  
  
 Numer wersji w ramach .NET Framework składa się z czterech części oddzielonych kropkami: *major.minor.build.revision*. Ciąg przeszedł `pwszVersion` zgodnie z musi zaczynać się od znaku "v", po którym następuje pierwsze trzy części numeru wersji (na przykład "v1.0.1529").  
  
 Niektóre wersje programu CLR są instalowane z instrukcją zasad określającą zgodność z poprzednimi wersjami programu CLR. Domyślnie podkładka uruchamiania `pwszVersion` ocenia instrukcje zasad i ładuje najnowszą wersję środowiska wykonawczego, która jest zgodna z żądaną wersją. Host może wymusić podkładkę, aby pominąć oceny `pwszVersion` zasad i załadować dokładną wersję `startupFlags` określoną w przekazując wartość STARTUP_LOADER_SAFEMODE dla parametru.  
  
 Jeśli `pwszVersion` `null,` jest metoda nie ładuje żadnej wersji CLR. Zamiast tego zwraca CLR_E_SHIM_RUNTIMELOAD, co wskazuje, że nie można załadować środowiska wykonawczego.  
  
 `pwszBuildFlavor`  
 [w] Ciąg, który określa, czy załadować serwer lub kompilacji stacji roboczej CLR. Prawidłowe `svr` wartości `wks`są i . Kompilacja serwera jest zoptymalizowana pod kątem korzystania z wielu procesorów do wyrzucania elementów bezużytecznych, a kompilacja stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich uruchomionych na komputerze z jednym procesorem.  
  
 Jeśli `pwszBuildFlavor` jest ustawiona na wartość null, kompilacja stacji roboczej jest ładowana. Podczas pracy na komputerze z jednym procesorem kompilacja stacji `pwszBuildFlavor` roboczej `svr`jest zawsze ładowana, nawet jeśli jest ustawiona na . Jednak jeśli `pwszBuildFlavor` jest `svr` ustawiona i równoczesnych wyrzucania elementów `startupFlags` bezużytecznych jest określony (zobacz opis parametru), kompilacja serwera jest ładowany.  
  
> [!NOTE]
> Równoczesne wyrzucanie elementów bezużytecznych nie jest obsługiwane w aplikacjach z emulatorem WOW64 x86 w systemach 64-bitowych, które implementują architekturę Intel Itanium (dawniej nazywaną IA-64). Aby uzyskać więcej informacji na temat używania WOW64 w 64-bitowych systemach Windows, zobacz [Uruchamianie aplikacji 32-bitowych](/windows/desktop/WinProg64/running-32-bit-applications).  
  
 `pwszHostConfigFile`  
 [w] Nazwa pliku konfiguracji hosta, który określa wersję clr do załadowania. Jeśli nazwa pliku nie zawiera w pełni kwalifikowanej ścieżki, zakłada się, że plik znajduje się w tym samym katalogu co plik wykonywalny, który wykonuje wywołanie.  
  
 `pReserved`  
 [w] Zarezerwowane dla przyszłej rozszerzalności.  
  
 `startupFlags`  
 [w] Zestaw flag, który kontroluje równoczesnych wyrzucania elementów bezużytecznych, `pwszVersion` kod neutralny dla domeny i zachowanie parametru. Wartość domyślna to pojedyncza domena, jeśli nie ustawiono żadnej flagi. Aby uzyskać listę obsługiwanych wartości, zobacz [STARTUP_FLAGS wyliczenie](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md).  
  
 `rclsid`  
 [w] Coclass, `CLSID` który implementuje interfejs [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) lub [ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) Obsługiwane wartości są CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.  
  
 `riid`  
 [w] Interfejs, `IID` o który prosisz. Obsługiwane wartości są IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.  
  
 `ppv`  
 [na zewnątrz] Wskaźnik interfejsu do wersji środowiska wykonawczego, który został załadowany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** mscoree.idl  
  
 **Biblioteka:** Mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg — Funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
