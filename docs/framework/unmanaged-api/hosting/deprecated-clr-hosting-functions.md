---
title: Przestarzałe funkcje hostingu środowiska CLR
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa84ca0defd173563817673aad183a8b64226d41
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135814"
---
# <a name="deprecated-clr-hosting-functions"></a>Przestarzałe funkcje hostingu środowiska CLR
W tej sekcji opisano niezarządzane statyczne funkcje globalne, używane w starszych wersjach interfejsu API.  
  
 Z wyjątkiem funkcji infrastruktury (`_Cor*` funkcji), które są używane tylko przez program .NET Framework, funkcje te zostały zaniechane w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="activation-functions"></a>Aktywacja funkcji  
 [ClrCreateManagedInstance, funkcja](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 Przestarzałe. Tworzy wystąpienie określonego typu zarządzanego.  
  
 [CoInitializeCor, funkcja](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 Nieaktualne. Aby zainicjować środowisko uruchomieniowe języka wspólnego (CLR), należy użyć [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).  
  
 [CoInitializeEE, funkcja](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 Przestarzałe. Zapewnia, że aparat wykonywania CLR jest załadowany do procesu. Użyj [iclrruntimehost::Start —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metody zamiast tego.  
  
 [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 Przestarzałe. Ładuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu za pomocą informacji o wersji przechowywanych w pliku XML.  
  
 [CorBindToRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 Przestarzałe. Włącza niezarządzane hosty do ładowania CLR do procesu.  
  
 [CorBindToRuntimeByCfg, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 Przestarzałe. Ładuje środowisko CLR do procesu za pomocą informacji o wersji, które są odczytywane z pliku XML.  
  
 [CorBindToRuntimeEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 Przestarzałe. Włącza niezarządzane hosty do ładowania CLR do procesu i pozwala na ustawienie flagi, aby określić zachowanie środowiska CLR.  
  
 [CorBindToRuntimeHost, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 Przestarzałe. Włącza hosty do załadowania określonej wersji środowiska CLR do procesu.  
  
 [GetCORRequiredVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 Przestarzałe. Pobiera wymagany numer wersji środowiska CLR.  
  
 [GetCORSystemDirectory, funkcja](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 Przestarzałe. Zwraca katalog instalacyjny środowiska CLR, który jest ładowany do procesu.  
  
 [GetRealProcAddress, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 Przestarzałe. Pobiera adres określonej funkcji, która została wyeksportowana z najnowszej zainstalowanej wersji środowiska CLR.  
  
 [GetRequestedRuntimeInfo, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 Przestarzałe. Pobiera informacje wersji i katalogu dla środowiska CLR żądane przez aplikację.  
  
## <a name="clr-version-functions"></a>Funkcje wersji środowiska CLR  
 Funkcje w tej sekcji zwracają wersję CLR; nie uaktywniają CLR.  
  
 [GetCORVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 Przestarzałe. Zwraca numer wersji środowiska CLR, która działa w bieżącym procesie.  
  
 [GetFileVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 Przestarzałe. Pobiera informacje o wersji środowiska CLR określonego pliku, przy użyciu określonego bufora.  
  
 [GetRequestedRuntimeVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 Przestarzałe. Pobiera numer wersji środowiska CLR wymaganego przez określoną aplikację. Jeśli ta wersja nie jest zainstalowana, pobiera najbardziej aktualną wersję zainstalowaną przed żądaną wersją.  
  
 [GetRequestedRuntimeVersionForCLSID, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 Przestarzałe. Pobiera odpowiednie informacje o wersji środowiska CLR dla klasy z określonym identyfikatorem CLSID.  
  
 [GetVersionFromProcess, funkcja](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 Przestarzałe. Pobiera numer wersji środowiska CLR, który jest skojarzony z określonym dojściem do procesu.  
  
 [LockClrVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 Przestarzałe. Umożliwia hostowi na określenie, która wersja środowiska CLR, będzie używany w ramach procesu przed jawnym zainicjowaniem środowiska CLR.  
  
## <a name="hosting-functions"></a>Funkcje hostingu  
 [CallFunctionShim, funkcja](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 Przestarzałe. Wywołuje funkcję, która ma określoną nazwę i parametry w określonej bibliotece.  
  
 [CoEEShutDownCOM, funkcja](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 Przestarzałe. Usuwa zestaw COM z procesu.  
  
 [CorExitProcess, funkcja](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 Przestarzałe. Zamyka bieżący proces niezarządzany.  
  
 [CorLaunchApplication, funkcja](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 Przestarzałe. Uruchamia aplikację w określonej ścieżce sieciowej, przy użyciu określonych manifestów i innych danych aplikacji.  
  
 [CorMarkThreadInThreadPool, funkcja](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 Przestarzałe. Znaki aktualnie wykonywany wątek puli wątków do wykonywania kodu zarządzanego. Począwszy od programu .NET Framework w wersji 2.0, ta funkcja nie ma znaczenia. Nie jest wymagana i może zostać usunięty z Twojego kodu.  
  
 [CoUninitializeCor, funkcja](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 Nieaktualne. Środowisko CLR nie może być zwolnione z procesu.  
  
 [CoUninitializeEE, funkcja](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 Nieaktualne.  
  
 [CreateDebuggingInterfaceFromVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 Przestarzałe. Tworzy [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) obiektu na podstawie określonej wersji informacji.  
  
 [CreateICeeFileGen, funkcja](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 Przestarzałe. Tworzy [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) obiektu.  
  
 [DestroyICeeFileGen, funkcja](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 Przestarzałe. Niszczy [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) obiektu.  
  
 [FExecuteInAppDomainCallback, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, którą środowisko CLR wywołuje wykonywanie kodu zarządzanego.  
  
 [FLockClrVersionCallback, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, która wywołuje środowisko CLR w celu powiadomienia hosta tego inicjowania uruchomiona lub ukończone.  
  
 [GetCLRIdentityManager, funkcja](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 Przestarzałe. Pobiera wskaźnik do interfejsu, który umożliwia środowisku CLR Zarządzanie tożsamościami.  
  
 [LoadLibraryShim, funkcja](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 Przestarzałe. Ładuje określoną wersję biblioteki dll platformy .NET Framework.  
  
 [LoadStringRC, funkcja](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 Przestarzałe. Tłumaczy wartość HRESULT na komunikat o błędzie przy użyciu domyślnej kultury bieżącego wątku.  
  
 [LoadStringRCEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 Przestarzałe. Tłumaczy wartość HRESULT do odpowiedniego komunikatu o błędzie dla określonej kultury.  
  
 [LPOVERLAPPED_COMPLETION_ROUTINE, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, która powiadamia hosta, gdy nakładająca (czyli asynchroniczne) we/wy na urządzeniu została zakończona.  
  
 [LPTHREAD_START_ROUTINE, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, która powiadamia hosta, który wątek rozpoczęło się wykonanie.  
  
 [RunDll32ShimW, funkcja](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 Przestarzałe. Wykonuje określone polecenie.  
  
 [WAITORTIMERCALLBACK, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, która powiadamia hosta, że dojście oczekiwania ma zostały zasygnalizowane lub przekroczyło limit czasu.  
  
## <a name="infrastructure-functions"></a>Funkcje infrastruktury  
 Funkcje w tej sekcji są do użytku tylko platforma .NET Framework.  
  
 [_CorDllMain, funkcja](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 Inicjuje środowisko CLR, lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu biblioteki DLL i rozpoczyna wykonywanie.  
  
 [_CorExeMain, funkcja](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 Inicjuje środowisko CLR, lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu pliku wykonywalnego i rozpoczyna wykonywanie.  
  
 [_CorExeMain2, funkcja](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 Uruchamia punkt wejścia w określonym kodzie mapowanym w pamięci. Ta funkcja jest wywoływana przez program ładujący systemu operacyjnego.  
  
 [_CorImageUnloading, funkcja](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 Powiadamia moduł ładujący, gdy obrazy modułu zarządzanego są usuwane z pamięci.  
  
 [_CorValidateImage, funkcja](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 Sprawdza poprawność obrazów modułu zarządzanego i powiadamia moduł ładujący systemu operacyjnego po ich załadowaniu.  
  
## <a name="see-also"></a>Zobacz także

- [.NET Framework 4 — statyczne funkcje globalne hostingu](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md)
