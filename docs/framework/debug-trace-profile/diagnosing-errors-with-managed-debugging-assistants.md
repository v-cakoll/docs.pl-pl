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
ms.openlocfilehash: 6cb2a240a2e7e82b7015eb7a6d99c2117fa63045
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052900"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a>Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania

Zarządzane Asystenci debugowania (MDA) to pomoce debugowania, które działają w połączeniu ze środowiskiem uruchomieniowym języka wspólnego (CLR) w celu zapewnienia informacji o stanie środowiska uruchomieniowego. Asystenci generują komunikaty informacyjne dotyczące zdarzeń środowiska uruchomieniowego, które nie mogą być pułapki w przeciwnym razie. Możesz użyć MDA, aby wyizolować trudne do znalezienia usterki aplikacji występujące podczas przechodzenia między kodem zarządzanym i niezarządzanym.

Możesz [włączyć lub wyłączyć](#enable-and-disable-mdas) wszystkie MDA przez dodanie klucza do rejestru systemu Windows lub przez ustawienie zmiennej środowiskowej. Konkretne MDA można włączyć za pomocą ustawień konfiguracji aplikacji. Można ustawić dodatkowe ustawienia konfiguracji dla niektórych pojedynczych MDA w pliku konfiguracyjnym aplikacji. Ponieważ te pliki konfiguracji są analizowane podczas ładowania środowiska uruchomieniowego, przed uruchomieniem aplikacji zarządzanej należy włączyć funkcję MDA. Nie można go włączyć dla aplikacji, które zostały już uruchomione.

Poniższa tabela zawiera listę MDA, które są dostarczane z .NET Framework:

|||
|-|-|
|[asynchronousThreadAbort](asynchronousthreadabort-mda.md)|[bindingFailure](bindingfailure-mda.md)|
|[callbackOnCollectedDelegate](callbackoncollecteddelegate-mda.md)|[contextSwitchDeadlock](contextswitchdeadlock-mda.md)|
|[dangerousThreadingAPI](dangerousthreadingapi-mda.md)|[dateTimeInvalidLocalFormat](datetimeinvalidlocalformat-mda.md)|
|[dirtyCastAndCallOnInterface](dirtycastandcalloninterface-mda.md)|[disconnectedContext](disconnectedcontext-mda.md)|
|[dllMainReturnsFalse](dllmainreturnsfalse-mda.md)|[exceptionSwallowedOnCallFromCom](exceptionswallowedoncallfromcom-mda.md)|
|[failedQI](failedqi-mda.md)|[fatalExecutionEngineError](fatalexecutionengineerror-mda.md)|
|[gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)|[gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)|
|[illegalPrepareConstrainedRegion](illegalprepareconstrainedregion-mda.md)|[invalidApartmentStateChange](invalidapartmentstatechange-mda.md)|
|[invalidCERCall](invalidcercall-mda.md)|[invalidFunctionPointerInDelegate](invalidfunctionpointerindelegate-mda.md)|
|[invalidGCHandleCookie](invalidgchandlecookie-mda.md)|[invalidIUnknown](invalidiunknown-mda.md)|
|[invalidMemberDeclaration](invalidmemberdeclaration-mda.md)|[invalidOverlappedToPinvoke](invalidoverlappedtopinvoke-mda.md)|
|[invalidVariant](invalidvariant-mda.md)|[jitCompilationStart](jitcompilationstart-mda.md)|
|[loaderLock](loaderlock-mda.md)|[loadFromContext](loadfromcontext-mda.md)|
|[marshalCleanupError](marshalcleanuperror-mda.md)|[marshaling](marshaling-mda.md)|
|[memberInfoCacheCreation](memberinfocachecreation-mda.md)|[moduloObjectHashcode](moduloobjecthashcode-mda.md)|
|[nonComVisibleBaseClass](noncomvisiblebaseclass-mda.md)|[notMarshalable](notmarshalable-mda.md)|
|[openGenericCERCall](opengenericcercall-mda.md)|[overlappedFreeError](overlappedfreeerror-mda.md)|
|[pInvokeLog](pinvokelog-mda.md)|[pInvokeStackImbalance](pinvokestackimbalance-mda.md)|
|[raceOnRCWCleanup](raceonrcwcleanup-mda.md)|[reentrancy](reentrancy-mda.md)|
|[releaseHandleFailed](releasehandlefailed-mda.md)|[reportAvOnComRelease](reportavoncomrelease-mda.md)|
|[streamWriterBufferedDataLost](streamwriterbuffereddatalost-mda.md)|[virtualCERCall](virtualcercall-mda.md)|

Domyślnie .NET Framework aktywuje podzbiór MDA dla wszystkich zarządzanych debugerów. Możesz wyświetlić domyślny zestaw w programie Visual Studio, wybierając pozycję**Ustawienia wyjątków** **systemu Windows** > w menu **Debuguj** , a następnie rozwijając listę **asystentów debugowania zarządzanego** .

![Okno ustawień wyjątków w programie Visual Studio](./media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a>Włączanie i wyłączanie MDA

MDA można włączać i wyłączać za pomocą klucza rejestru, zmiennej środowiskowej i ustawień konfiguracji aplikacji. Należy włączyć klucz rejestru lub zmienną środowiskową, aby użyć ustawień konfiguracji aplikacji.

> [!TIP]
> Zamiast wyłączać MDA, można zapobiec wyświetlaniu przez program Visual Studio okna dialogowego MDA przy każdym odebraniu powiadomienia MDA. W tym celu wybierz pozycję**Ustawienia wyjątków** **systemu Windows** > w menu **debugowanie** , rozwiń listę **Asystenci debugowania zarządzanego** , a następnie zaznacz lub wyczyść pole wyboru **Przerwij, gdy zostanie zgłoszone dla pojedynczego przerzucania** .

### <a name="registry-key"></a>Klucz rejestru

Aby włączyć MDA, Dodaj **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Podklucz NETFramework\MDA** (typ REG_SZ, wartość 1) w rejestrze systemu Windows. Skopiuj poniższy przykład do pliku tekstowego o nazwie *MDAEnable. reg*. Otwórz Edytor rejestru systemu Windows (regedit. exe), a następnie z menu **plik** wybierz pozycję **Importuj**. Wybierz plik *MDAEnable. reg* , aby włączyć MDA na tym komputerze. Ustawienie podklucza do wartości ciągu **1** (wartość nietypu DWORD **1**) umożliwia odczytywanie ustawień programu MDA z pliku *ApplicationName.* config. Na przykład plik konfiguracji MDA dla programu Notepad ma nazwę Notepad. exe. MDA. config.

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

Jeśli na komputerze działa aplikacja 32-bitowa w 64-bitowym systemie operacyjnym, należy ustawić klucz MDA podobny do następującego:

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji specyficzne dla aplikacji](#application-specific-configuration-settings) . Ustawienie rejestru może być zastąpione przez zmienną środowiskową COMPLUS_MDA. Aby uzyskać więcej informacji, zobacz [zmienna środowiskowa](#environment-variable) .

Aby wyłączyć MDA, ustaw podklucz MDA na **0** (zero) przy użyciu Edytora rejestru systemu Windows.

Domyślnie niektóre MDA są włączane po uruchomieniu aplikacji dołączonej do debugera, nawet bez dodawania klucza rejestru. Te Asystenci można wyłączyć, uruchamiając plik *MDADisable. reg* zgodnie z wcześniejszym opisem w tej sekcji.

### <a name="environment-variable"></a>Zmienna środowiskowa

Aktywację MDA można również kontrolować przy użyciu zmiennej środowiskowej COMPLUS_MDA, która zastępuje klucz rejestru. Ciąg COMPLUS_MDA to rozdzielana średnikami lista nazw MDA lub innych specjalnych ciągów sterujących. Uruchomienie w debugerze zarządzanym lub niezarządzanym domyślnie włącza zestaw MDA. Jest to realizowane przez niejawnie oczekującą listę rozdzielonych średnikami MDA włączonych domyślnie w obszarze debugery do wartości zmiennej środowiskowej lub klucza rejestru. Specjalne ciągi sterujące są następujące:

- `0`— Dezaktywuje wszystkie MDA.

- `1`-Odczytuje ustawienia MDA z pliku *ApplicationName*. MDA. config.

- `managedDebugger`— Jawnie aktywuje wszystkie MDA, które są niejawnie aktywowane, gdy zarządzany plik wykonywalny jest uruchamiany w debugerze.

- `unmanagedDebugger`— Jawnie aktywuje wszystkie MDA, które są niejawnie aktywowane, gdy niezarządzany plik wykonywalny jest uruchamiany w debugerze.

Jeśli istnieją jakieś ustawienia powodujące konflikt, ostatnie ustawienia zastępują poprzednie ustawienia:

- `COMPLUS_MDA=0`wyłącza wszystkie MDA, włącznie z niejawnie włączonymi w debugerze.

- `COMPLUS_MDA=gcUnmanagedToManaged`Włącza `gcUnmanagedToManaged` dodatek do wszystkich MDA, które są niejawnie włączone w debugerze.

- `COMPLUS_MDA=0;gcUnmanagedToManaged`Włącza `gcUnmanagedToManaged` , ale wyłącza MDA, które w przeciwnym razie byłyby niejawnie włączone w debugerze.

### <a name="application-specific-configuration-settings"></a>Ustawienia konfiguracji specyficzne dla aplikacji

Niektóre Asystenci można włączać, wyłączać i konfigurować pojedynczo w pliku konfiguracji MDA dla aplikacji. Aby umożliwić korzystanie z pliku konfiguracji aplikacji do konfigurowania MDA, należy ustawić klucz rejestru MDA lub zmienną środowiskową COMPLUS_MDA. Plik konfiguracji aplikacji zwykle znajduje się w tym samym katalogu, co plik wykonywalny (exe) aplikacji. Nazwa pliku przyjmuje postać *ApplicationName*. MDA. config; na przykład Notepad. exe. MDA. config. Asystenci, którzy są włączeni w pliku konfiguracji aplikacji, mogą mieć atrybuty lub elementy zaprojektowane specjalnie pod kątem kontrolowania zachowania tego asystenta.

Poniższy przykład pokazuje, jak włączyć i skonfigurować [kierowanie](marshaling-mda.md):

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

`Marshaling` MDA emituje informacje o zarządzanym typie, który jest przekazywany do niezarządzanego typu dla każdego przejścia zarządzanego do niezarządzanego w aplikacji. MDA może również filtrować nazwy metod i pól struktury dostarczonych odpowiednio w elementach podrzędnych **methodFilter** i **fieldFilter.** `Marshaling`

Poniższy przykład pokazuje, jak włączyć wiele MDA przy użyciu ich ustawień domyślnych:

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
> W przypadku określenia więcej niż jednego asystenta w pliku konfiguracji należy je wyświetlić w kolejności alfabetycznej. Na przykład, jeśli `virtualCERCall` chcesz włączyć zarówno obiekt, `invalidCERCall` jak i MDA `<invalidCERCall />` , należy `<virtualCERCall />` dodać wpis przed wpisem. Jeśli wpisy nie są w kolejności alfabetycznej, zostanie wyświetlony nieobsługiwany komunikat wyjątku pliku konfiguracji.

## <a name="mda-exceptions"></a>Wyjątki MDA

Gdy zdarzenie MDA jest włączone, jest aktywne nawet wtedy, gdy kod nie jest wykonywany w debugerze. Jeśli zdarzenie MDA jest zgłaszane, gdy debuger nie jest obecny, komunikat o zdarzeniu jest wyświetlany w oknie dialogowym nieobsłużonego wyjątku, chociaż nie jest to nieobsługiwany wyjątek. Aby uniknąć tego okna dialogowego, Usuń ustawienia włączania MDA, gdy kod nie jest wykonywany w środowisku debugowania.

Gdy kod jest wykonywany w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio, można uniknąć okna dialogowego wyjątek, które pojawia się dla określonych zdarzeń MDA. W tym celu w menu **Debuguj** wybierz pozycję**Ustawienia wyjątków** **systemu Windows** > . W oknie **Ustawienia wyjątku** rozwiń listę **Asystenci debugowania zarządzanego** , a następnie usuń zaznaczenie pola wyboru Przerwij, **gdy zostanie zgłoszone** dla pojedynczego elementu MDA. Tego okna dialogowego można także użyć, aby *włączyć* wyświetlanie okien dialogowych wyjątków MDA.

## <a name="mda-output"></a>Wyjście MDA

Dane wyjściowe MDA są podobne do poniższego przykładu, który wyświetla dane wyjściowe `PInvokeStackImbalance` z MDA:

**Wywołanie funkcji PInvoke "MDATest! MDATest. program:: StdCall ' ma niezrównoważony stos. Prawdopodobnie jest to spowodowane tym, że zarządzana sygnatura PInvoke nie jest zgodna z niezarządzanym podpisem docelowym. Sprawdź, czy Konwencja wywoływania i parametry sygnatury PInvoke pasują do docelowego podpisu niezarządzanego.**

## <a name="see-also"></a>Zobacz także

- [Debugowanie, śledzenie i profilowanie](index.md)
