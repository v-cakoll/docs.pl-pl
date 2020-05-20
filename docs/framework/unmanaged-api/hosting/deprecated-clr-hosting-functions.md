---
title: Przestarzałe funkcje hostingu środowiska CLR
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 8925278bdf4d48efc9e589ffc4e181d904444e6b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616427"
---
# <a name="deprecated-clr-hosting-functions"></a>Przestarzałe funkcje hostingu środowiska CLR
W tej sekcji opisano niezarządzane globalne funkcje statyczne, które są używane we wcześniejszych wersjach interfejsu API hostingu.  
  
 Z wyjątkiem funkcji infrastruktury ( `_Cor*` funkcji), które są używane tylko przez .NET Framework, funkcje te zostały zaniechane w .NET Framework 4.  
  
## <a name="activation-functions"></a>Funkcje aktywacji  
 [ClrCreateManagedInstance, funkcja](clrcreatemanagedinstance-function.md)  
 Przestarzałe. Tworzy wystąpienie określonego typu zarządzanego.  
  
 [CoInitializeCor, funkcja](coinitializecor-function.md)  
 Nieaktualne. Aby zainicjować środowisko uruchomieniowe języka wspólnego (CLR), użyj opcji [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).  
  
 [CoInitializeEE — Funkcja](coinitializeee-function.md)  
 Przestarzałe. Zapewnia, że aparat wykonywania CLR jest ładowany do procesu. Zamiast tego użyj metody [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) .  
  
 [CorBindToCurrentRuntime, funkcja](corbindtocurrentruntime-function.md)  
 Przestarzałe. Ładuje środowisko uruchomieniowe języka wspólnego (CLR) do procesu przy użyciu informacji o wersji przechowywanych w pliku XML.  
  
 [CorBindToRuntime, funkcja](corbindtoruntime-function.md)  
 Przestarzałe. Umożliwia niezarządzanym hostom ładowanie środowiska CLR do procesu.  
  
 [CorBindToRuntimeByCfg — Funkcja](corbindtoruntimebycfg-function.md)  
 Przestarzałe. Ładuje środowisko CLR do procesu przy użyciu informacji o wersji, które są odczytywane z pliku XML.  
  
 [CorBindToRuntimeEx, funkcja](corbindtoruntimeex-function.md)  
 Przestarzałe. Włącza niezarządzane hosty do załadowania środowiska CLR do procesu i pozwala ustawić flagi, aby określić zachowanie środowiska CLR.  
  
 [CorBindToRuntimeHost — Funkcja](corbindtoruntimehost-function.md)  
 Przestarzałe. Włącza hosty do załadowania określonej wersji środowiska CLR do procesu.  
  
 [GetCORRequiredVersion, funkcja](getcorrequiredversion-function.md)  
 Przestarzałe. Pobiera wymagany numer wersji środowiska CLR.  
  
 [GetCORSystemDirectory, funkcja](getcorsystemdirectory-function.md)  
 Przestarzałe. Zwraca katalog instalacyjny środowiska CLR, który jest ładowany do procesu.  
  
 [GetRealProcAddress — Funkcja](getrealprocaddress-function.md)  
 Przestarzałe. Pobiera adres określonej funkcji wyeksportowanej z najnowszej zainstalowanej wersji środowiska CLR.  
  
 [GetRequestedRuntimeInfo, funkcja](getrequestedruntimeinfo-function.md)  
 Przestarzałe. Pobiera informacje o wersji i katalogu dla środowiska CLR żądanego przez aplikację.  
  
## <a name="clr-version-functions"></a>Funkcje wersji środowiska CLR  
 Funkcje w tej sekcji zwracają wersję środowiska CLR; nie aktywuje środowiska CLR.  
  
 [GetCORVersion, funkcja](getcorversion-function.md)  
 Przestarzałe. Zwraca numer wersji środowiska CLR uruchomionego w bieżącym procesie.  
  
 [GetFileVersion, funkcja](getfileversion-function.md)  
 Przestarzałe. Pobiera informacje o wersji środowiska CLR określonego pliku przy użyciu określonego buforu.  
  
 [GetRequestedRuntimeVersion — Funkcja](getrequestedruntimeversion-function.md)  
 Przestarzałe. Pobiera numer wersji środowiska CLR żądanego przez określoną aplikację. Jeśli ta wersja nie jest zainstalowana, program pobierze najnowszą wersję, która jest zainstalowana przed żądaną wersją.  
  
 [GetRequestedRuntimeVersionForCLSID — Funkcja](getrequestedruntimeversionforclsid-function.md)  
 Przestarzałe. Pobiera odpowiednie informacje o wersji środowiska CLR dla klasy o określonym identyfikatorze CLSID.  
  
 [GetVersionFromProcess, funkcja](getversionfromprocess-function.md)  
 Przestarzałe. Pobiera numer wersji środowiska CLR skojarzonego z określonym dojściem do procesu.  
  
 [LockClrVersion, funkcja](lockclrversion-function.md)  
 Przestarzałe. Umożliwia hostowi określenie, która wersja środowiska CLR zostanie użyta w procesie przed jawnym inicjalizacją środowiska CLR.  
  
## <a name="hosting-functions"></a>Funkcje hostingu  
 [CallFunctionShim, funkcja](callfunctionshim-function.md)  
 Przestarzałe. Wywołuje funkcję, która ma określoną nazwę i parametry w określonej bibliotece.  
  
 [CoEEShutDownCOM, funkcja](coeeshutdowncom-function.md)  
 Przestarzałe. Zwalnia zestaw COM z procesu.  
  
 [CorExitProcess, funkcja](corexitprocess-function.md)  
 Przestarzałe. Zamyka bieżący proces niezarządzany.  
  
 [CorLaunchApplication, funkcja](corlaunchapplication-function.md)  
 Przestarzałe. Uruchamia aplikację pod określoną ścieżką sieciową przy użyciu określonych manifestów i innych danych aplikacji.  
  
 [CorMarkThreadInThreadPool — Funkcja](cormarkthreadinthreadpool-function.md)  
 Przestarzałe. Oznacza aktualnie wykonywany wątek puli wątków na potrzeby wykonywania kodu zarządzanego. Począwszy od .NET Framework w wersji 2,0, ta funkcja nie ma żadnego wpływu. Nie jest to wymagane i można je usunąć z kodu.  
  
 [CoUninitializeCor, funkcja](couninitializecor-function.md)  
 Nieaktualne. Nie można zwolnić środowiska CLR z procesu.  
  
 [CoUninitializeEE, funkcja](couninitializeee-function.md)  
 Nieaktualne.  
  
 [CreateDebuggingInterfaceFromVersion — Funkcja](createdebugginginterfacefromversion-function.md)  
 Przestarzałe. Tworzy obiekt [ICorDebug](../debugging/icordebug-interface.md) na podstawie informacji o określonej wersji.  
  
 [CreateICeeFileGen, funkcja](createiceefilegen-function.md)  
 Przestarzałe. Tworzy obiekt [ICeeFileGen](iceefilegen-class.md) .  
  
 [DestroyICeeFileGen — Funkcja](destroyiceefilegen-function.md)  
 Przestarzałe. Niszczy obiekt [ICeeFileGen](iceefilegen-class.md) .  
  
 [FExecuteInAppDomainCallback — Wskaźnik funkcji](fexecuteinappdomaincallback-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, którą środowisko CLR wywołuje do wykonywania kodu zarządzanego.  
  
 [FLockClrVersionCallback, wskaźnik funkcji](flockclrversioncallback-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, którą wywołuje środowisko CLR w celu powiadomienia hosta, że inicjalizacja została uruchomiona lub została ukończona.  
  
 [GetCLRIdentityManager, funkcja](getclridentitymanager-function.md)  
 Przestarzałe. Pobiera wskaźnik do interfejsu, który umożliwia CLR Zarządzanie tożsamościami.  
  
 [LoadLibraryShim — Funkcja](loadlibraryshim-function.md)  
 Przestarzałe. Ładuje określoną wersję biblioteki DLL .NET Framework.  
  
 [LoadStringRC, funkcja](loadstringrc-function.md)  
 Przestarzałe. Tłumaczy wartość HRESULT na komunikat o błędzie przy użyciu domyślnej kultury bieżącego wątku.  
  
 [LoadStringRCEx — Funkcja](loadstringrcex-function.md)  
 Przestarzałe. Tłumaczy wartość HRESULT na odpowiedni komunikat o błędzie dla określonej kultury.  
  
 [LPOVERLAPPED_COMPLETION_ROUTINE, wskaźnik funkcji](lpoverlapped-completion-routine-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, która powiadamia hosta, gdy nakładają się (czyli asynchroniczne) operacje wejścia/wyjścia do urządzenia.  
  
 [LPTHREAD_START_ROUTINE — Wskaźnik funkcji](lpthread-start-routine-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, która powiadamia hosta o rozpoczęciu wykonywania wątku.  
  
 [RunDll32ShimW, funkcja](rundll32shimw-function.md)  
 Przestarzałe. Wykonuje określone polecenie.  
  
 [WAITORTIMERCALLBACK — Wskaźnik funkcji](waitortimercallback-function-pointer.md)  
 Przestarzałe. Wskazuje funkcję, która powiadamia hosta o zasygnalizowaniu lub przekroczeniu limitu czasu dojścia oczekiwania.  
  
## <a name="infrastructure-functions"></a>Funkcje infrastruktury  
 Funkcje w tej sekcji służą wyłącznie do .NET Framework.  
  
 [_CorDllMain — Funkcja](cordllmain-function.md)  
 Inicjuje środowisko CLR, lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu DLL i rozpoczyna wykonywanie.  
  
 [_CorExeMain, funkcja](corexemain-function.md)  
 Inicjuje środowisko CLR, lokalizuje zarządzany punkt wejścia w nagłówku CLR zestawu wykonywalnego i rozpoczyna wykonywanie.  
  
 [_CorExeMain2, funkcja](corexemain2-function.md)  
 Wykonuje punkt wejścia w określonym kodzie mapowanym w pamięci. Ta funkcja jest wywoływana przez program ładujący systemu operacyjnego.  
  
 [_CorImageUnloading, funkcja](corimageunloading-function.md)  
 Powiadamia moduł ładujący, gdy obrazy modułu zarządzanego są zwolnione.  
  
 [_CorValidateImage, funkcja](corvalidateimage-function.md)  
 Sprawdza poprawność obrazów modułu zarządzanego i powiadamia program ładujący system operacyjny po ich załadowaniu.  
  
## <a name="see-also"></a>Zobacz także

- [.NET Framework 4 — statyczne funkcje globalne hostingu](net-framework-4-hosting-global-static-functions.md)
