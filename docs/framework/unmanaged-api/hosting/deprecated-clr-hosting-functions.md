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
ms.openlocfilehash: d86f9b4903663604094895f6747b1407ff98c990
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="deprecated-clr-hosting-functions"></a>Przestarzałe funkcje hostingu środowiska CLR
W tej sekcji opisano niezarządzane statyczne funkcje globalne, które używany w starszych wersjach programu obsługi interfejsu API.  
  
 Z wyjątkiem funkcji infrastruktury (`_Cor*` funkcji), które są używane tylko w programie .NET Framework, te funkcje są przestarzałe w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="activation-functions"></a>Funkcje aktywacji  
 [ClrCreateManagedInstance, funkcja](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 Przestarzałe. Tworzy wystąpienie określonego typu zarządzanego.  
  
 [CoInitializeCor, funkcja](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 Nieaktualne. Aby zainicjować środowisko uruchomieniowe języka wspólnego (CLR), użyj [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).  
  
 [CoInitializeEE, funkcja](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 Przestarzałe. Zapewnia, że aparat CLR wykonywania jest ładowany do procesu. Użyj [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metody zamiast tego.  
  
 [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 Przestarzałe. Ładuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu za pomocą wersji informacje przechowywane w pliku XML.  
  
 [CorBindToRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 Przestarzałe. Umożliwia niezarządzane hostów można załadować środowiska CLR do procesu.  
  
 [CorBindToRuntimeByCfg, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 Przestarzałe. Ładuje środowiska CLR do procesu za pomocą informacji o wersji, która jest do odczytu z pliku XML.  
  
 [CorBindToRuntimeEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 Przestarzałe. Umożliwia hostom niezarządzane można załadować środowiska CLR do procesu, a można ustawić flagi, aby określić zachowanie środowiska CLR.  
  
 [CorBindToRuntimeHost, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 Przestarzałe. Umożliwia hostom do ładowania określonej wersji środowiska CLR do procesu.  
  
 [GetCORRequiredVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 Przestarzałe. Pobiera wymagany numer wersji środowiska CLR.  
  
 [GetCORSystemDirectory, funkcja](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 Przestarzałe. Zwraca katalog instalacyjny środowiska CLR, który jest ładowany do procesu.  
  
 [GetRealProcAddress, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 Przestarzałe. Pobiera adres określonej funkcji, który został wyeksportowany z najnowszej zainstalowanej wersji środowiska CLR.  
  
 [GetRequestedRuntimeInfo, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 Przestarzałe. Pobiera informacje o wersji i katalogu o CLR żądany przez aplikację.  
  
## <a name="clr-version-functions"></a>Funkcje wersji środowiska CLR  
 Funkcje w tej sekcji zwracają wersję środowiska CLR; nie należy aktywować środowiska CLR.  
  
 [GetCORVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 Przestarzałe. Zwraca numer wersji środowiska CLR, która działa w ramach bieżącego procesu.  
  
 [GetFileVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 Przestarzałe. Pobiera informacje o wersji środowiska CLR określonego pliku, używając określonego bufora.  
  
 [GetRequestedRuntimeVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 Przestarzałe. Pobiera numer wersji środowiska CLR zażądał określonej aplikacji. Jeśli ta wersja nie jest zainstalowany, otrzymuje najnowszą wersję, która została zainstalowana przed żądanej wersji.  
  
 [GetRequestedRuntimeVersionForCLSID, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 Przestarzałe. Pobiera odpowiednie informacje o wersji środowiska CLR dla klasy o określonym identyfikatorze CLSID.  
  
 [GetVersionFromProcess, funkcja](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 Przestarzałe. Pobiera numer wersji środowiska CLR skojarzony z dojściem określony proces.  
  
 [LockClrVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 Przestarzałe. Umożliwia hosta określić wersję środowiska CLR będzie używany w ramach procesu przed jawnie inicjowania CLR.  
  
## <a name="hosting-functions"></a>Funkcje hostingu  
 [CallFunctionShim, funkcja](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 Przestarzałe. Wykonuje wywołanie funkcji, które ma określoną nazwę i parametrów w określonej bibliotece.  
  
 [CoEEShutDownCOM, funkcja](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 Przestarzałe. Zwalnia zestawem COM z procesu.  
  
 [CorExitProcess, funkcja](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 Przestarzałe. Zamyka bieżący proces niezarządzany.  
  
 [CorLaunchApplication, funkcja](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 Przestarzałe. Uruchamia aplikację w ścieżce określonej sieci przy użyciu określonego manifestów i innych danych aplikacji.  
  
 [CorMarkThreadInThreadPool, funkcja](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 Przestarzałe. Oznacza aktualnie wykonywane wątku puli wątków dla wykonania kodu zarządzanego. W programie .NET Framework w wersji 2.0, ta funkcja nie ma znaczenia. Nie jest wymagane, a można ją usunąć z kodu.  
  
 [CoUninitializeCor, funkcja](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 Nieaktualne. Środowisko CLR nie może być zwolniony z procesem.  
  
 [CoUninitializeEE, funkcja](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 Nieaktualne.  
  
 [CreateDebuggingInterfaceFromVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 Przestarzałe. Tworzy [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) obiekt na podstawie określonej wersji informacji.  
  
 [CreateICeeFileGen, funkcja](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 Przestarzałe. Tworzy [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) obiektu.  
  
 [DestroyICeeFileGen, funkcja](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 Przestarzałe. Niszczy [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) obiektu.  
  
 [FExecuteInAppDomainCallback, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, która wywołuje środowiska CLR do wykonania kodu zarządzanego.  
  
 [FLockClrVersionCallback, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 Przestarzałe. Punkty funkcji, które wywołuje CLR powiadomiono hosta tego inicjowania albo rozpoczął się lub zakończona.  
  
 [GetCLRIdentityManager, funkcja](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 Przestarzałe. Pobiera wskaźnik do interfejsu, który umożliwia CLR do zarządzania tożsamościami.  
  
 [LoadLibraryShim, funkcja](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 Przestarzałe. Ładuje określona wersja biblioteki DLL .NET Framework.  
  
 [LoadStringRC, funkcja](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 Przestarzałe. Tłumaczy wartość HRESULT na komunikat o błędzie, za pomocą domyślną kulturę bieżącego wątku.  
  
 [LoadStringRCEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 Przestarzałe. Tłumaczy wartość HRESULT odpowiedni komunikat o błędzie dla określonej kultury.  
  
 [LPOVERLAPPED_COMPLETION_ROUTINE, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 Przestarzałe. Wskazuje funkcji, które powiadamia hosta przy nakładających się (oznacza to, asynchroniczne) zostało ukończone operacje We/Wy na urządzeniu.  
  
 [LPTHREAD_START_ROUTINE, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 Przestarzałe. Punkty funkcji, które powiadamia hosta, który wątek został uruchomiony w trybie wykonywania.  
  
 [RunDll32ShimW, funkcja](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 Przestarzałe. Wykonuje określone polecenie.  
  
 [WAITORTIMERCALLBACK, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 Przestarzałe. Punkty funkcji, które powiadamia hosta, że dojście oczekiwania albo został sygnalizowane lub upłynął limit czasu.  
  
## <a name="infrastructure-functions"></a>Funkcje infrastruktury  
 Funkcje w tej sekcji służą do użytku przez tylko platformę .NET.  
  
 [_CorDllMain, funkcja](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 Inicjuje środowisko CLR, lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu biblioteki DLL i rozpoczyna się wykonanie.  
  
 [_CorExeMain, funkcja](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 Inicjuje środowisko CLR, lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu pliku wykonywalnego i rozpoczyna się wykonanie.  
  
 [_CorExeMain2, funkcja](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 Wykonuje punkt wejścia określony kod mapowanych na pamięć. Ta funkcja jest wywoływana przez moduł ładujący systemu operacyjnego.  
  
 [_CorImageUnloading, funkcja](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 Powiadamia program ładujący, gdy moduł zarządzany obrazy są usuwane z pamięci.  
  
 [_CorValidateImage, funkcja](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 Weryfikuje obrazy moduł zarządzany i powiadamia modułu ładującego systemu operacyjnego po ich załadowaniu.  
  
## <a name="see-also"></a>Zobacz też  
 [.NET Framework 4 — statyczne funkcje globalne hostingu](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md) 
