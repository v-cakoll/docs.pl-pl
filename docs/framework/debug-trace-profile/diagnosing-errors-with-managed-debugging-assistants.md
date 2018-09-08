---
title: Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania
ms.date: 08/14/2018
f1_keywords:
- EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b745fa6a78ab2a7ab0b3a94c9921883d3c56c1b7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135500"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a>Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania

Zarządzanie debugowaniem asystentów (mda) jest debugowany pomocy, które działają w połączeniu z środowisko uruchomieniowe języka wspólnego (CLR) zawiera informacje na temat stanu środowiska uruchomieniowego. Asystenci Generowanie komunikaty o zdarzeniach środowiska uruchomieniowego, które w przeciwnym razie nie komunikat pułapki. Mda umożliwia oddzieleniu błędów twardych znajdowanie aplikacji, które występują podczas przenoszenia między kodem zarządzanym i niezarządzanym.

Możesz [włączać lub wyłączać](#enable-and-disable-mdas) wszystkich mda przez dodanie klucza w rejestrze Windows lub przez ustawienie zmiennej środowiskowej. Można włączyć określonego mda przy użyciu ustawień konfiguracji aplikacji. Dodatkowe ustawienia konfiguracji dla niektórych poszczególnych mda można ustawić w pliku konfiguracji aplikacji. Ponieważ te pliki konfiguracyjne są w sytuacji, gdy jest ładowany przez środowisko uruchomieniowe, należy włączyć MDA przed uruchomieniem aplikacji zarządzanej. Nie możesz włączyć dla aplikacji, które zostały już uruchomione.

W poniższej tabeli wymieniono mda, które są dostarczane za pomocą programu .NET Framework:

|||
|-|-|
|[asynchronousThreadAbort](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[bindingFailure](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|
|[callbackOnCollectedDelegate](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|
|[dangerousThreadingAPI](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[dateTimeInvalidLocalFormat](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|
|[dirtyCastAndCallOnInterface](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[disconnectedContext](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|
|[dllMainReturnsFalse](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[exceptionSwallowedOnCallFromCom](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|
|[failedQI](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[fatalExecutionEngineError](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|
|[gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|
|[illegalPrepareConstrainedRegion](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|
|[invalidCERCall](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[invalidFunctionPointerInDelegate](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|
|[invalidGCHandleCookie](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[invalidIUnknown](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|
|[invalidMemberDeclaration](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[invalidOverlappedToPinvoke](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|
|[invalidVariant](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|
|[loaderLock](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[loadFromContext](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|
|[marshalCleanupError](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|
|[memberInfoCacheCreation](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[moduloObjectHashcode](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|
|[nonComVisibleBaseClass](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[notMarshalable](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|
|[openGenericCERCall](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[overlappedFreeError](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|
|[pInvokeLog](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|
|[raceOnRCWCleanup](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[reentrancy](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|
|[releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[reportAvOnComRelease](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|
|[streamWriterBufferedDataLost](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[virtualCERCall](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|

Domyślnie program .NET Framework aktywuje podzbiór mda dla wszystkich zarządzanych debugerów. Możesz wyświetlić domyślnie w programie Visual Studio, wybierając **Windows** > **ustawienia wyjątków** na **debugowania** menu, a następnie rozwijając **Asystentów zarządzanego debugowania** listy.

![Okno ustawień wyjątków w programie Visual Studio](media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a>Włączanie i wyłączanie mda

Można włączyć i wyłączyć mda przy użyciu klucza rejestru, zmienna środowiskowa i ustawienia konfiguracji aplikacji. Należy włączyć klucz rejestru lub zmienną środowiskową Aby użyć ustawienia konfiguracji aplikacji.

> [!TIP]
> Zamiast wyłączanie mda, można zapobiec programu Visual Studio wyświetlanie okna dialogowego MDA zawsze wtedy, gdy zostanie odebrana wiadomość z powiadomieniem MDA. Aby to zrobić, wybierz **Windows** > **ustawienia wyjątków** na **debugowania** menu, rozwiń węzeł **zarządzane debugowanie asystentów**listy, a następnie zaznacz lub wyczyść **Przerwij gdy zgłoszony** pole wyboru dla poszczególnych MDA.

### <a name="registry-key"></a>Klucz rejestru

Aby włączyć mda, Dodaj **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\MDA** podklucz (typu REG_SZ, wartość 1) w rejestrze systemu Windows. Skopiuj poniższy przykład do pliku tekstowego o nazwie *MDAEnable.reg*. Otwórz Edytor rejestru (RegEdit.exe), Windows i z **pliku** menu wybierz opcję **importu**. Wybierz *MDAEnable.reg* plik, aby umożliwić mda na tym komputerze. Ustawienie go na wartość ciągu **1** (nie wartość DWORD **1**) umożliwia odczyt ustawień MDA *ApplicationName.suffix*. plik mda.config. Na przykład plik konfiguracji MDA Notatnik będzie nosić notepad.exe.mda.config.

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

Jeśli komputer działa aplikacja 32-bitowa w 64-bitowym systemie operacyjnym, klucz MDA powinna być ustawiona podobnie do poniższych:

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

Zobacz [ustawień konfiguracji specyficznych dla aplikacji](#application-specific-configuration-settings) Aby uzyskać więcej informacji. Ustawienie rejestru może być zastąpiona przez zmienną środowiskową COMPLUS_MDA. Zobacz [zmienna środowiskowa](#environment-variable) Aby uzyskać więcej informacji.

Aby wyłączyć mda, równa podklucz MDA **0** (zero) za pomocą Edytora rejestru Windows.

Domyślnie niektóre mda są włączone podczas uruchamiania aplikacji, która jest dołączona do debugera, nawet bez dodanie klucza rejestru. Można wyłączyć tych osób, uruchamiając *MDADisable.reg* plików zgodnie z wcześniejszym opisem w tej sekcji.

### <a name="environment-variable"></a>Zmienna środowiskowa

MDA aktywacji może także kontrolowane przez zmienną środowiskową COMPLUS_MDA, która zastępuje klucz rejestru. Ciąg COMPLUS_MDA jest bez uwzględniania wielkości liter, rozdzielaną średnikami listę nazw MDA lub inne ciągi kontroli. Uruchamianie w debugerze zarządzanych lub niezarządzanych zapewnia zestaw mda domyślnie. Odbywa się przez niejawnie poprzedzenie jej rozdzieloną średnikami listę mda włączona domyślnie w ramach debugery wartość środowiska zmiennej lub klucza rejestru. Ciągi kontroli specjalne są następujące:

- `0` -Dezaktywuje wszystkich mda.

- `1` -Odczytuje ustawienia MDA z *ApplicationName*. mda.config.

- `managedDebugger` -Jawnie aktywuje wszystkich mda, niejawnie są aktywowane podczas uruchamiania zarządzanego pliku wykonywalnego w debugerze.

- `unmanagedDebugger` -Jawnie aktywuje wszystkich mda, niejawnie są aktywowane podczas uruchamiania pliku wykonywalnego niezarządzanych w debugerze.

W przypadku ustawienia powodujące konflikt ostatnio używanych ustawień Zastąp poprzednie ustawienia:

- `COMPLUS_MDA=0` Wyłącza wszystkie mda, łącznie z tymi włączana domyślnie w debugerze.

- `COMPLUS_MDA=gcUnmanagedToManaged` Włącza `gcUnmanagedToManaged` oprócz wszelkich mda, które są domyślnie włączone w debugerze.

- `COMPLUS_MDA=0;gcUnmanagedToManaged` Włącza `gcUnmanagedToManaged` , ale wyłącza mda, które w przeciwnym razie można włączyć niejawnie w debugerze.

### <a name="application-specific-configuration-settings"></a>Ustawienia konfiguracji specyficzne dla aplikacji

Można włączyć, wyłączyć i skonfigurować niektóre asystentów osobno w pliku konfiguracyjnym MDA dla aplikacji. Aby włączyć korzystanie z pliku konfiguracji aplikacji do konfigurowania mda, można ustawić klucz rejestru MDA lub zmiennej środowiskowej COMPLUS_MDA. Plik konfiguracyjny aplikacji zwykle znajduje się w tym samym katalogu co plik wykonywalny (.exe) aplikacji. Nazwa pliku ma postać *ApplicationName*. mda.config, na przykład notepad.exe.mda.config. Asystenci, które są włączone w pliku konfiguracji aplikacji mogą mieć atrybutów lub elementów zaprojektowane specjalnie w celu sterowania zachowaniem tej Asystenta ustawień.

Poniższy przykład pokazuje, jak włączyć i skonfigurować [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md):

```xml
<mdaConfig>
  <assistants>
    <marshaling>
      <methodFilter>
        <match name="*"/>
      </methodFilter>
      <fieldFilter>
        <match name="*"/>
      </fieldFilter>
    </marshaling>
  </assistants>
</mdaConfig>
```

`Marshaling` MDA emituje informacje o typ zarządzany, który jest są przekazywane do typu niezarządzanego, dla każdego przejścia zarządzane do niezarządzanego w aplikacji. `Marshaling` MDA można również filtrować nazwy metod i pól struktury dostarczane w **methodFilter** i **fieldFilter** elementy podrzędne, odpowiednio.

Poniższy przykład pokazuje, jak włączyć wielu mda przy użyciu ustawień domyślnych:

```xml
<mdaConfig>
  <assistants>
    <illegalPrepareConstrainedRegion />
    <invalidCERCall />
    <openGenericCERCall />
    <virtualCERCall />
  </assistants>
</mdaConfig>
```

> [!IMPORTANT]
> Po określeniu więcej niż jeden Asystenta ustawień w pliku konfiguracji należy wyświetlić je w kolejności alfabetycznej. Na przykład, jeśli chcesz włączyć obie opcje `virtualCERCall` i `invalidCERCall` mda, należy dodać `<invalidCERCall />` wpis przed `<virtualCERCall />` wpisu. Jeśli wpisy nie są w kolejności alfabetycznej, zostanie wyświetlony komunikat wyjątku pliku nieobsługiwany nieprawidłowej konfiguracji.

## <a name="mda-exceptions"></a>Wyjątki MDA

Po włączeniu MDA jest aktywna nawet po kodzie nie może być wykonane w debugerze. Jeśli zdarzenie MDA jest wywoływane, gdy nie jest debugera, komunikatów o zdarzeniach są prezentowane w oknie dialogowym nieobsługiwany wyjątek, chociaż nie jest to nieobsługiwany wyjątek. Aby uniknąć okno dialogowe, należy usunąć ustawienia włączania MDA, gdy kod nie jest wykonywany w środowisku debugowania.

Podczas wykonywania kodu w programie Visual Studio zintegrowane środowisko programistyczne (IDE), można uniknąć, okno dialogowe wyjątku, który pojawia się dla określonego zdarzenia MDA. Aby to zrobić, na **debugowania** menu, wybierz **Windows** > **ustawienia wyjątków**. W **ustawienia wyjątków** okna, rozwiń węzeł **asystentów zarządzanego debugowania** listy, a następnie wyczyść **Przerwij gdy zgłoszony** pole wyboru dla poszczególnych MDA. Można również użyć tego okna dialogowego do *Włącz* wyświetlanie okien dialogowych wyjątek MDA.

## <a name="mda-output"></a>Dane wyjściowe MDA

MDA rezultat jest podobny do poniższego przykładu, który pokazuje dane wyjściowe z `PInvokeStackImbalance` MDA:

**Wywołanie funkcji PInvoke "MDATest! MDATest.Program::StdCall "ma niezrównoważone stosu. Jest to prawdopodobnie, ponieważ zarządzanego podpisu PInvoke jest niezgodna z niezarządzanego podpisu docelowego. Sprawdź, czy Konwencja wywoływania i parametry podpisu funkcji PInvoke odpowiadają niezarządzanego podpisu docelowego.**

## <a name="see-also"></a>Zobacz także

- [Debugowanie, śledzenie i profilowanie](../../../docs/framework/debug-trace-profile/index.md)
