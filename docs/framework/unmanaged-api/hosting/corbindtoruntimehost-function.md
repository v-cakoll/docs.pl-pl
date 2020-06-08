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
ms.openlocfilehash: 9d1c7f4f5b881f7f55539602c152b557a7950472
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504410"
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
  
 Numer wersji w .NET Framework składa się z czterech części oddzielonych kropkami: *główna. pomocnicza. kompilacja. poprawka*. Ciąg przeszedł jako `pwszVersion` musi rozpoczynać się od znaku "v", po którym następuje pierwsze trzy części numeru wersji (na przykład "v 1.0.1529").  
  
 Niektóre wersje środowiska CLR są instalowane z instrukcją zasad, która określa zgodność z poprzednimi wersjami środowiska CLR. Domyślnie podkładka uruchamiania szacuje się `pwszVersion` przed instrukcjami zasad i ładuje najnowszą wersję środowiska uruchomieniowego, która jest zgodna z żądaną wersją. Host może zmusić podkładkę do pominięcia oceny zasad i załadowania dokładnej wersji określonej w `pwszVersion` wyniku przekazania wartości STARTUP_LOADER_SAFEMODE dla `startupFlags` parametru.  
  
 If `pwszVersion` to `null,` Metoda nie ładuje żadnej wersji środowiska CLR. Zamiast tego zwraca CLR_E_SHIM_RUNTIMELOAD, co oznacza, że ładowanie środowiska uruchomieniowego nie powiodło się.  
  
 `pwszBuildFlavor`  
 podczas Ciąg określający, czy załadować serwer lub kompilację stacji roboczej środowiska CLR. Prawidłowe wartości to `svr` i `wks` . Kompilacja serwera jest zoptymalizowana pod kątem wykorzystania wielu procesorów na potrzeby wyrzucania elementów bezużytecznych, a kompilacja stacji roboczej jest zoptymalizowana pod kątem aplikacji klienckich uruchomionych na komputerze z jednym procesorem.  
  
 Jeśli `pwszBuildFlavor` jest ustawiona na wartość null, kompilacja stacji roboczej zostanie załadowana. W przypadku uruchamiania na komputerze z jednym procesorem kompilacja stacji roboczej jest zawsze ładowana, nawet jeśli `pwszBuildFlavor` jest ustawiona na `svr` . Jeśli jednak `pwszBuildFlavor` jest ustawiona na `svr` i zostanie określone współbieżne wyrzucanie elementów bezużytecznych (zobacz Opis `startupFlags` parametru), kompilacja serwera zostanie załadowana.  
  
> [!NOTE]
> Współbieżne wyrzucanie elementów bezużytecznych nie jest obsługiwane w aplikacjach uruchamiających emulator WOW64 x86 w systemach 64-bitowych, które implementują architekturę Intel Itanium (dawniej zwane IA-64). Aby uzyskać więcej informacji na temat korzystania z emulatora WOW64 w systemach 64-bitowych systemu Windows, zobacz [Uruchamianie aplikacji 32-bitowych](/windows/desktop/WinProg64/running-32-bit-applications).  
  
 `pwszHostConfigFile`  
 podczas Nazwa pliku konfiguracji hosta, który określa wersję środowiska CLR do załadowania. Jeśli nazwa pliku nie zawiera w pełni kwalifikowanej ścieżki, zakłada się, że plik znajduje się w tym samym katalogu co plik wykonywalny, który wykonuje wywołanie.  
  
 `pReserved`  
 podczas Zarezerwowane do użytku w przyszłości.  
  
 `startupFlags`  
 podczas Zestaw flag kontrolujących współbieżne odzyskiwanie pamięci, kod neutralny przez domenę i zachowanie `pwszVersion` parametru. Wartość domyślna to pojedyncza domena, jeśli flaga nie jest ustawiona. Aby uzyskać listę obsługiwanych wartości, zobacz [wyliczenie STARTUP_FLAGS](startup-flags-enumeration.md).  
  
 `rclsid`  
 podczas `CLSID`Klasy coclass implementującej interfejs [ICorRuntimeHost](icorruntimehost-interface.md) lub [ICLRRuntimeHost](iclrruntimehost-interface.md) . Obsługiwane wartości to CLSID_CorRuntimeHost lub CLSID_CLRRuntimeHost.  
  
 `riid`  
 podczas Żądanego `IID` interfejsu. Obsługiwane wartości to IID_ICorRuntimeHost lub IID_ICLRRuntimeHost.  
  
 `ppv`  
 określoną Wskaźnik interfejsu do wersji środowiska uruchomieniowego, która została załadowana.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. idl  
  
 **Biblioteka:** MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [CorBindToCurrentRuntime, funkcja](corbindtocurrentruntime-function.md)
- [CorBindToRuntime, funkcja](corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg — Funkcja](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx, funkcja](corbindtoruntimeex-function.md)
- [ICorRuntimeHost, interfejs](icorruntimehost-interface.md)
- [Przestarzałe funkcje hostingu środowiska CLR](deprecated-clr-hosting-functions.md)
