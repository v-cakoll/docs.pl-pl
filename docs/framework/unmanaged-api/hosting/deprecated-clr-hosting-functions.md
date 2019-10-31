---
title: Przestarzałe funkcje hostingu środowiska CLR
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 62773ce526b1f21c57ab85a106708589fcf92f6f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138273"
---
# <a name="deprecated-clr-hosting-functions"></a>Przestarzałe funkcje hostingu środowiska CLR
W tej sekcji opisano niezarządzane globalne funkcje statyczne, które są używane we wcześniejszych wersjach interfejsu API hostingu.  
  
 Z wyjątkiem funkcji infrastruktury (`_Cor*` funkcje), które są używane tylko przez .NET Framework, funkcje te zostały zaniechane w .NET Framework 4.  
  
## <a name="activation-functions"></a>Funkcje aktywacji  
 [ClrCreateManagedInstance, funkcja](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 Przestarzałe. Tworzy wystąpienie określonego typu zarządzanego.  
  
 [CoInitializeCor, funkcja](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 Nieaktualne. Aby zainicjować środowisko uruchomieniowe języka wspólnego (CLR), użyj opcji [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).  
  
 [CoInitializeEE, funkcja](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 Przestarzałe. Zapewnia, że aparat wykonywania CLR jest ładowany do procesu. Zamiast tego użyj metody [ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) .  
  
 [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 Przestarzałe. Ładuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu przy użyciu informacji o wersji przechowywanych w pliku XML.  
  
 [CorBindToRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 Przestarzałe. Umożliwia niezarządzanym hostom ładowanie środowiska CLR do procesu.  
  
 [CorBindToRuntimeByCfg, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 Przestarzałe. Ładuje środowisko CLR do procesu przy użyciu informacji o wersji, które są odczytywane z pliku XML.  
  
 [CorBindToRuntimeEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 Przestarzałe. Włącza niezarządzane hosty do załadowania środowiska CLR do procesu i pozwala ustawić flagi, aby określić zachowanie środowiska CLR.  
  
 [CorBindToRuntimeHost, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 Przestarzałe. Włącza hosty do załadowania określonej wersji środowiska CLR do procesu.  
  
 [GetCORRequiredVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 Przestarzałe. Pobiera wymagany numer wersji środowiska CLR.  
  
 [GetCORSystemDirectory, funkcja](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 Przestarzałe. Zwraca katalog instalacyjny środowiska CLR, który jest ładowany do procesu.  
  
 [GetRealProcAddress, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 Przestarzałe. Pobiera adres określonej funkcji wyeksportowanej z najnowszej zainstalowanej wersji środowiska CLR.  
  
 [GetRequestedRuntimeInfo, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 Przestarzałe. Pobiera informacje o wersji i katalogu dla środowiska CLR żądanego przez aplikację.  
  
## <a name="clr-version-functions"></a>Funkcje wersji środowiska CLR  
 Funkcje w tej sekcji zwracają wersję środowiska CLR; nie aktywuje środowiska CLR.  
  
 [GetCORVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 Przestarzałe. Zwraca numer wersji środowiska CLR uruchomionego w bieżącym procesie.  
  
 [GetFileVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 Przestarzałe. Pobiera informacje o wersji środowiska CLR określonego pliku przy użyciu określonego buforu.  
  
 [GetRequestedRuntimeVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 Przestarzałe. Pobiera numer wersji środowiska CLR żądanego przez określoną aplikację. Jeśli ta wersja nie jest zainstalowana, program pobierze najnowszą wersję, która jest zainstalowana przed żądaną wersją.  
  
 [GetRequestedRuntimeVersionForCLSID, funkcja](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 Przestarzałe. Pobiera odpowiednie informacje o wersji środowiska CLR dla klasy o określonym identyfikatorze CLSID.  
  
 [GetVersionFromProcess, funkcja](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 Przestarzałe. Pobiera numer wersji środowiska CLR skojarzonego z określonym dojściem do procesu.  
  
 [LockClrVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 Przestarzałe. Umożliwia hostowi określenie, która wersja środowiska CLR zostanie użyta w procesie przed jawnym inicjalizacją środowiska CLR.  
  
## <a name="hosting-functions"></a>Funkcje hostingu  
 [CallFunctionShim, funkcja](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 Przestarzałe. Wywołuje funkcję, która ma określoną nazwę i parametry w określonej bibliotece.  
  
 [CoEEShutDownCOM, funkcja](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 Przestarzałe. Zwalnia zestaw COM z procesu.  
  
 [CorExitProcess, funkcja](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 Przestarzałe. Zamyka bieżący proces niezarządzany.  
  
 [CorLaunchApplication, funkcja](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 Przestarzałe. Uruchamia aplikację pod określoną ścieżką sieciową przy użyciu określonych manifestów i innych danych aplikacji.  
  
 [CorMarkThreadInThreadPool, funkcja](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 Przestarzałe. Oznacza aktualnie wykonywany wątek puli wątków na potrzeby wykonywania kodu zarządzanego. Począwszy od .NET Framework w wersji 2,0, ta funkcja nie ma żadnego wpływu. Nie jest to wymagane i można je usunąć z kodu.  
  
 [CoUninitializeCor, funkcja](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 Nieaktualne. Nie można zwolnić środowiska CLR z procesu.  
  
 [CoUninitializeEE, funkcja](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 Nieaktualne.  
  
 [CreateDebuggingInterfaceFromVersion, funkcja](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 Przestarzałe. Tworzy obiekt [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) na podstawie informacji o określonej wersji.  
  
 [CreateICeeFileGen, funkcja](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 Przestarzałe. Tworzy obiekt [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) .  
  
 [DestroyICeeFileGen, funkcja](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 Przestarzałe. Niszczy obiekt [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) .  
  
 [FExecuteInAppDomainCallback, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, którą środowisko CLR wywołuje do wykonywania kodu zarządzanego.  
  
 [FLockClrVersionCallback, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, którą wywołuje środowisko CLR w celu powiadomienia hosta, że inicjalizacja została uruchomiona lub została ukończona.  
  
 [GetCLRIdentityManager, funkcja](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 Przestarzałe. Pobiera wskaźnik do interfejsu, który umożliwia CLR Zarządzanie tożsamościami.  
  
 [LoadLibraryShim, funkcja](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 Przestarzałe. Ładuje określoną wersję biblioteki DLL .NET Framework.  
  
 [LoadStringRC, funkcja](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 Przestarzałe. Tłumaczy wartość HRESULT na komunikat o błędzie przy użyciu domyślnej kultury bieżącego wątku.  
  
 [LoadStringRCEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 Przestarzałe. Tłumaczy wartość HRESULT na odpowiedni komunikat o błędzie dla określonej kultury.  
  
 [LPOVERLAPPED_COMPLETION_ROUTINE, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, która powiadamia hosta, gdy nakładają się (czyli asynchroniczne) operacje wejścia/wyjścia do urządzenia.  
  
 [LPTHREAD_START_ROUTINE, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, która powiadamia hosta o rozpoczęciu wykonywania wątku.  
  
 [RunDll32ShimW, funkcja](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 Przestarzałe. Wykonuje określone polecenie.  
  
 [WAITORTIMERCALLBACK, wskaźnik funkcji](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, która powiadamia hosta o zasygnalizowaniu lub przekroczeniu limitu czasu dojścia oczekiwania.  
  
## <a name="infrastructure-functions"></a>Funkcje infrastruktury  
 Funkcje w tej sekcji służą wyłącznie do .NET Framework.  
  
 [_CorDllMain, funkcja](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 Inicjuje środowisko CLR, lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu DLL i rozpoczyna wykonywanie.  
  
 [_CorExeMain, funkcja](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 Inicjuje środowisko CLR, lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu wykonywalnego i rozpoczyna wykonywanie.  
  
 [_CorExeMain2, funkcja](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 Wykonuje punkt wejścia w określonym kodzie mapowanym w pamięci. Ta funkcja jest wywoływana przez program ładujący systemu operacyjnego.  
  
 [_CorImageUnloading, funkcja](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 Powiadamia moduł ładujący, gdy obrazy modułu zarządzanego są zwolnione.  
  
 [_CorValidateImage, funkcja](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 Sprawdza poprawność obrazów modułu zarządzanego i powiadamia program ładujący system operacyjny po ich załadowaniu.  
  
## <a name="see-also"></a>Zobacz także

- [.NET Framework 4 — statyczne funkcje globalne hostingu](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md)
