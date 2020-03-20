---
title: Jak debugować problemy z aktywacją CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
ms.openlocfilehash: 602ee3c88237a902d48339836fbe25f636ae9705
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716507"
---
# <a name="how-to-debug-clr-activation-issues"></a>Jak debugować problemy z aktywacją CLR

Jeśli wystąpią problemy z uruchomieniem aplikacji z poprawną wersją środowiska wykonawczego języka wspólnego (CLR), można wyświetlać i debugować dzienniki aktywacji CLR. Te dzienniki mogą być bardzo przydatne w określaniu głównej przyczyny problemu z aktywacją, gdy aplikacja ładuje inną wersję CLR niż oczekiwano lub w ogóle nie ładuje clr. [Błędy inicjowania programu .NET Framework: Zarządzanie środowiska użytkownika](initialization-errors-managing-the-user-experience.md) omówiono środowisko, gdy nie znaleziono clr dla aplikacji.

Rejestrowanie aktywacji CLR można włączyć w całym systemie za pomocą HKEY_LOCAL_MACHINE klucz rejestru lub zmiennej środowiska systemowego. Dziennik zostanie wygenerowany do momentu usunięcia wpisu rejestru lub zmiennej środowiskowej. Alternatywnie można użyć zmiennej środowiskowej użytkownika lub procesu lokalnego, aby włączyć rejestrowanie z innym zakresem i czasem trwania.

Dzienniki aktywacji CLR nie powinny być mylone z [dziennikami wiązania zestawu,](../tools/fuslogvw-exe-assembly-binding-log-viewer.md)które są zupełnie inne.

## <a name="to-enable-clr-activation-logging"></a>Aby włączyć rejestrowanie aktywacji CLR

### <a name="using-the-registry"></a>Korzystanie z rejestru

1. W Edytorze rejestru przejdź do HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework (na komputerze 32-bitowym) lub HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework (na komputerze 64-bitowym).

2. Dodaj wartość ciągu `CLRLoadLogDir`o nazwie i ustaw ją na pełnej ścieżce istniejącego katalogu, w którym chcesz przechowywać dzienniki aktywacji CLR.

Rejestrowanie aktywacji pozostaje włączone do momentu usunięcia wartości ciągu.

### <a name="using-an-environment-variable"></a>Korzystanie ze zmiennej środowiskowej

- Ustaw `COMPLUS_CLRLoadLogDir` zmienną środowiskową na ciąg reprezentujący pełną ścieżkę istniejącego katalogu, w którym chcesz przechowywać dzienniki aktywacji CLR.

    Sposób ustawienia zmiennej środowiskowej określa jej zakres:

  - Jeśli ustawisz go na poziomie systemu, rejestrowanie aktywacji jest włączone dla wszystkich aplikacji .NET Framework na tym komputerze, dopóki zmienna środowiskowa nie zostanie usunięta.

  - Jeśli ustawisz go na poziomie użytkownika, rejestrowanie aktywacji jest włączone tylko dla bieżącego konta użytkownika. Rejestrowanie jest kontynuowane do momentu usunięcia zmiennej środowiskowej.

  - Jeśli ustawisz go z poziomu procesu przed załadowaniem CLR, rejestrowanie aktywacji jest włączone do czasu zakończenia procesu.

  - Jeśli ustawisz go w wierszu polecenia przed uruchomieniem aplikacji, rejestrowanie aktywacji jest włączone dla każdej aplikacji, która jest uruchamiana z tego wiersza polecenia.

    Na przykład, aby przechowywać dzienniki aktywacji w katalogu c:\clrloadlogs z zakresem na poziomie procesu, otwórz okno wiersza polecenia i wpisz następujące elementy przed uruchomieniem aplikacji:

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a>Przykład

Dzienniki aktywacji CLR zapewniają dużą ilość danych dotyczących aktywacji CLR i korzystania z interfejsów API hostingu CLR. Większość tych danych jest używana wewnętrznie przez firmę Microsoft, ale niektóre dane mogą być również przydatne dla deweloperów, zgodnie z opisem w tym artykule.

Dziennik odzwierciedla kolejność, w jakiej zostały wywołane interfejsy API hostowania CLR. Zawiera również przydatne dane dotyczące zestawu zainstalowanych runtimes wykrytych na komputerze. Format dziennika aktywacji CLR nie jest sam udokumentowany, ale może służyć do pomocy deweloperom, którzy muszą rozwiązać problemy z aktywacją programu CLR.

> [!NOTE]
> Nie można otworzyć dziennika aktywacji, dopóki proces korzystający z programu CLR nie zostanie zakończony.

> [!NOTE]
> Dzienniki aktywacji CLR nie są zlokalizowane; są one zawsze generowane w języku angielskim.

W poniższym przykładzie dziennika aktywacji najbardziej przydatne informacje są wyróżnione i opisane po dzienniku.

```output
532,205950.367,CLR Loading log for C:\Tests\myapp.exe
532,205950.367,Log started at 4:26:12 PM on 10/6/2011
532,205950.367,-----------------------------------
532,205950.382,FunctionCall: _CorExeMain
532,205950.382,FunctionCall: ClrCreateInstance, Clsid: {2EBCD49A-1B47-4A61-B13A-4A03701E594B}, Iid: {E2190695-77B2-492E-8E14-C4B3A7FDD593}
532,205950.382,MethodCall: ICLRMetaHostPolicy::GetRequestedRuntime. Version: (null), Metahost Policy Flags: 0x168, Binary: (null), Iid: {BD39D1D2-BA2F-486A-89B0-B4B0CB466891}
532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
532,205950.382,Input values for ComputeVersionString follow this line
532,205950.382,-----------------------------------
532,205950.382,Default Application Name: C:\Tests\myapp.exe
532,205950.382,IsLegacyBind is: 0
532,205950.382,IsCapped is 0
532,205950.382,SkuCheckFlags are 0
532,205950.382,ShouldEmulateExeLaunch is 0
532,205950.382,LegacyBindRequired is 0
532,205950.382,-----------------------------------
532,205950.382,Parsing config file: C:\Tests\myapp.exe
532,205950.382,UseLegacyV2RuntimeActivationPolicy is set to 0
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe
532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
532,205950.382,ERROR: Version v2.0.50727 is not present on the machine.
532,205950.398,SEM_FAILCRITICALERRORS is set to 0
532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
532,205950.398,FunctionCall: RealDllMain. Reason: 0
532,205950.398,FunctionCall: OnShimDllMainCalled. Reason: 0
```

- **Dziennik ładowania programu CLR** udostępnia ścieżkę do pliku wykonywalnego, który rozpoczął proces załadowany kod zarządzany. Należy zauważyć, że może to być host macierzysty.

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- **Zainstalowane środowisko uruchomieniowe** to zestaw wersji CLR zainstalowanych na komputerze, które są kandydatami do żądania aktywacji.

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- **zbudowany z wersji** jest wersja CLR, który został użyty do zbudowania pliku binarnego, który został dostarczony do metody, takich jak [ICLRMetaHostPolicy::GetRequestedRuntime](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- **instalacja funkcji na żądanie** odnosi się do włączania programu .NET Framework 3.5 w systemie Windows 8. Zobacz [błędy inicjowania programu .NET Framework: Zarządzanie środowiska użytkownika,](initialization-errors-managing-the-user-experience.md) aby uzyskać więcej informacji na temat tego scenariusza.

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a>Zobacz też

- [Wdrożenie](index.md)
- [Jak: Konfigurowanie aplikacji do obsługi wersji programu .NET Framework 4 lub nowszych](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
