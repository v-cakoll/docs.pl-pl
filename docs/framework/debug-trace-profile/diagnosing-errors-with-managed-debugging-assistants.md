---
title: "Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EHMDA
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
caps.latest.revision: "63"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e23de3ea6e9693c05aa81da056ac7763bced8e9a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="diagnosing-errors-with-managed-debugging-assistants"></a>Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania
Asystenci debugowania zarządzanego (mda) debugowania pomocy, które działają w połączeniu z środowisko uruchomieniowe języka wspólnego (CLR), aby podać informacje dotyczące stanu czasu wykonywania. Asystenci Generowanie komunikaty o zdarzeniach środowiska uruchomieniowego, które w przeciwnym razie nie komunikat pułapki. Mda można użyć do izolowania usterki twarde do znalezienia aplikacji, występujących podczas przejścia między zarządzanymi i niezarządzanymi kodu. Można włączyć lub wyłączyć wszystkie mda przez dodanie klucza do rejestru systemu Windows lub przez ustawienie zmiennej środowiskowej. Można włączyć mda określone przy użyciu ustawienia konfiguracji aplikacji. Dodatkowe ustawienia konfiguracji dla niektórych poszczególnych mda można ustawić w pliku konfiguracji aplikacji. Ponieważ te pliki konfiguracji są w sytuacji, gdy załadowano środowiska uruchomieniowego, należy włączyć MDA przed uruchomieniem aplikacji zarządzanej. Nie można go włączyć dla aplikacji, które zostało już rozpoczęte.  
  
> [!NOTE]
>  Po włączeniu MDA jest aktywna nawet gdy kodu nie jest wykonywana w debugerze. Jeśli zdarzenie MDA jest wywoływane, gdy nie jest obecny debuger, komunikaty o zdarzeniach są prezentowane w nieobsługiwanych wyjątków — okno dialogowe, chociaż nie jest nieobsługiwany wyjątek. Aby uniknąć okno dialogowe, należy usunąć ustawienia umożliwiające MDA, gdy kodu nie jest wykonywana w środowisku debugowania.  
  
> [!NOTE]
>  Gdy kod jest wykonywany w Visual Studio zintegrowane środowisko programistyczne (IDE), można uniknąć, okno dialogowe wyjątek pojawiający się określonych zdarzeń MDA. Aby to zrobić, na **debugowania** menu, kliknij przycisk **wyjątki**. (Jeśli **debugowania** nie zawiera menu **wyjątki** polecenia, kliknij przycisk **Dostosuj** na **narzędzia** menu, aby dodać go.) W **wyjątki** okna dialogowego rozwiń **Asystenci zarządzanego debugowania** listy, a następnie wyczyść **wyrzuconych** pole wyboru dla poszczególnych MDA. Na przykład, aby uniknąć okno dialogowe wyjątek [contextSwitchDeadlock](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md) wyczyść **wyrzuconych** pole wyboru znajdujące się obok jego nazwy w **Asystenci zarządzanego debugowania** listy. Aby włączyć wyświetlanie okien dialogowych wyjątek MDA umożliwia także tego okna dialogowego.  
  
 W poniższej tabeli wymieniono mda, które są dostarczane z programu .NET Framework.  
  
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
|[marshalCleanupError](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[organizowanie](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|  
|[memberInfoCacheCreation](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[moduloObjectHashcode](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|  
|[nonComVisibleBaseClass](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[notMarshalable](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|  
|[openGenericCERCall](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[overlappedFreeError](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|  
|[pInvokeLog](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|  
|[raceOnRCWCleanup](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[wielobieżność](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|  
|[releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[reportAvOnComRelease](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|  
|[streamWriterBufferedDataLost](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[virtualCERCall](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|  
  
 Domyślnie program .NET Framework aktywuje podzbiór mda dla wszystkich zarządzanych debugery. Możesz wyświetlić domyślnie w programie Visual Studio, klikając **wyjątki** na **debugowania** menu i rozszerzanie **Asystenci zarządzanego debugowania** listy.  
  
## <a name="enabling-and-disabling-mdas"></a>Włączanie i wyłączanie mda  
 Można włączyć lub wyłączyć mda przy użyciu klucza rejestru, wartość zmiennej środowiskowej i ustawienia konfiguracji aplikacji. Należy włączyć klucz rejestru lub zmiennej środowiskowej, aby użyć ustawienia konfiguracji aplikacji.  
  
 W programie Visual Studio 2005 i nowszych wersjach podczas procesu hostingu jest włączone, nie można wyłączyć mda, które znajdują się w domyślnym zestawem lub Włącz mda ustawionych nie w domyślnym. Proces hostingu jest włączona domyślnie, więc musi być jawnie wyłączone.  
  
 Aby wyłączyć procesu hostingu w programie Visual Studio, wykonaj następujące czynności:  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt.  
  
2.  Na **projektu** menu, kliknij przycisk **właściwości**.  
  
     **Projektanta projektu** zostanie wyświetlone okno.  
  
3.  Kliknij przycisk **debugowania** kartę.  
  
4.  W **włączyć debugery** sekcji, wyczyść **włączyć procesu hostingu Visual Studio** pole wyboru.  
  
 Jednak wyłączanie procesu hostingu może wpłynąć na wydajność. Aby uniknąć konieczności wyłączanie mda przy uniemożliwia wyświetlanie okna dialogowego MDA zawsze, gdy otrzyma powiadomienie o MDA programu Visual Studio. Aby to zrobić, kliknij przycisk **wyjątki** na **debugowania** menu, rozwiń węzeł **Asystenci zarządzanego debugowania** listy, a następnie zaznacz lub wyczyść **wyrzuconych**pole wyboru dla poszczególnych MDA.  
  
### <a name="enabling-and-disabling-mdas-by-using-a-registry-key"></a>Włączanie i wyłączanie mda przy użyciu klucza rejestru  
 Można włączyć mda, dodając HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. Podklucz NETFramework\MDA (typ: REG_SZ, wartość 1) w rejestrze systemu Windows. Skopiuj poniższy przykład do pliku tekstowego o nazwie MDAEnable.reg. Otwórz Edytor rejestru (RegEdit.exe) systemu Windows i z **pliku** menu wybierz **importu**. Wybierz plik MDAEnable.reg, aby umożliwić mda na tym komputerze. Ustawienie podklucz ciąg wartość 1 (nie wartość DWORD 1) umożliwia odczytywanie ustawień MDA *ApplicationName.suffix*. mda.config pliku. (Na przykład Notatnik pliku konfiguracyjnego MDA będą miały postać notepad.exe.mda.config)  
  
```  
Windows Registry Editor Version 5.00  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 Jeśli komputer działa w 32-bitowej aplikacji na 64-bitowym systemie operacyjnym, klucz MDA powinna być ustawiona podobne do poniższych:  
  
```  
      Windows Registry Editor Version 5.00   
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]  
"MDA"="1"  
```  
  
 Zobacz [Włączanie i wyłączanie mda przez za pomocą ustawień konfiguracji specyficznych dla aplikacji](#appConfig) Aby uzyskać więcej informacji. Ustawienia rejestru mogą zostać zastąpione przez zmienną środowiskową COMPLUS_MDA. Zobacz [Włączanie i wyłączanie mda za pomocą zmiennej środowiskowej](#envVariable) Aby uzyskać więcej informacji.  
  
 Aby wyłączyć mda, ustaw podklucz MDA 0 (zero), za pomocą Edytora rejestru systemu Windows.  
  
 Domyślnie niektóre mda są włączone po uruchomieniu aplikacji, która jest dołączona do debugera, nawet jeśli nie Dodawanie klucza rejestru. Przykłady takich Asystenci [pInvokeStackImbalance](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) i [invalidApartmentStateChange](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md). Asystenci te można wyłączyć, uruchamiając plik MDADisable.reg, jak opisano wcześniej w tej sekcji.  
  
<a name="envVariable"></a>   
### <a name="enabling-and-disabling-mdas-by-using-an-environment-variable"></a>Włączanie i wyłączanie mda za pomocą zmiennej środowiskowej  
 MDA aktywacji można również kontrolowane przez zmienną środowiskową COMPLUS_MDA, zastępująca klucza rejestru. Ciąg COMPLUS_MDA jest bez uwzględniania wielkości liter, Rozdzielana średnikami lista nazw MDA lub inne ciągi kontroli. Uruchamianie w debugerze zarządzane lub niezarządzane udostępnia zestaw mda domyślnie. Jest to realizowane dołączając niejawnie Rozdzielana średnikami lista mda domyślnie włączone w obszarze debugery do wartości środowiskowej zmiennej lub klucza rejestru. Ciągi kontroli specjalne są następujące:  
  
-   `0`-Dezaktywuje mda wszystkie.  
  
-   `1`-Odczytuje ustawienia MDA z *ApplicationName*. mda.config.  
  
-   `managedDebugger`-Jawnie aktywuje wszystkie mda, niejawnie aktywowanych przy uruchamianiu zarządzanego pliku wykonywalnego w debugerze.  
  
-   `unmanagedDebugger`-Jawnie aktywuje wszystkie mda, niejawnie aktywowanych przy uruchamianiu niezarządzany plik wykonywalny w debugerze.  
  
 W przypadku wystąpienia konfliktu ustawień ostatnio używanych ustawień zastąpić poprzednie ustawienia:  
  
-   `COMPLUS_MDA=0`Wyłącza wszystkie mda, w tym niejawnie włączone w debugerze.  
  
-   `COMPLUS_MDA=gcUnmanagedToManaged`Włącza `gcUnmanagedToManaged` oprócz żadnych mda, które są domyślnie włączone w debugerze.  
  
-   `COMPLUS_MDA=0;gcUnmanagedToManaged`Włącza `gcUnmanagedToManaged` , ale wyłącza mda, które w przeciwnym razie mogłyby być niejawnie włączone w debugerze.  
  
<a name="appConfig"></a>   
### <a name="enabling-and-disabling-mdas-by-using-application-specific-configuration-settings"></a>Włączanie i wyłączanie mda przy użyciu ustawień konfiguracji specyficznych dla aplikacji  
 Można włączyć, wyłączyć i indywidualnie skonfigurować niektóre Asystenci w pliku konfiguracyjnym MDA dla aplikacji. Aby włączyć korzystanie z pliku konfiguracji aplikacji do konfigurowania mda, można ustawić klucz rejestru MDA lub zmiennej środowiskowej COMPLUS_MDA. Plik konfiguracji aplikacji jest zazwyczaj znajduje się w tym samym katalogu co plik wykonywalny (.exe) aplikacji. Nazwa pliku ma postać *ApplicationName*. mda.config, na przykład notepad.exe.mda.config. Asystenci, które są włączone w pliku konfiguracji aplikacji może mieć atrybutów ani elementów specjalnie zaprojektowane do kontrolowania zachowania tego pomocnika. Poniższy przykład przedstawia sposób włączania i konfigurowania [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md).  
  
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
  
 `Marshaling` MDA emituje informacje o typ zarządzany, który jest są przekazywane do niezarządzanego typu dla każdego przejścia niezarządzany zarządzany w aplikacji. `Marshaling` MDA można również filtrować nazwy metody i pola struktury dostarczane w `<methodFilter>` i `<fieldFilter>` elementy podrzędne, odpowiednio.  
  
 Poniższy przykład przedstawia sposób włączania wielu mda przy użyciu ustawień domyślnych.  
  
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
>  Po określeniu więcej niż jeden Asystenta w pliku konfiguracji musi zawierać je w kolejności alfabetycznej. Na przykład, jeśli chcesz włączyć zarówno `virtualCERCall` i `invalidCERCall` mda, należy dodać `<invalidCERCall />` wpis przed `<virtualCERCall />` wpisu. Jeśli dane nie są w porządku alfabetycznym, zostanie wyświetlony komunikat wyjątku pliku nieobsługiwany nieprawidłową konfigurację.  
  
### <a name="mda-output"></a>Dane wyjściowe MDA  
 MDA wynik jest podobny do poniższego przykładu, które zawierają dane wyjściowe z `pInvokeStackImbalance` MDA.  
  
 `A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.`  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, śledzenie i profilowanie](../../../docs/framework/debug-trace-profile/index.md)
