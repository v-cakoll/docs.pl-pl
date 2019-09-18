---
title: Jak debugować problemy dotyczące aktywacji środowiska CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR activation, debugging issues
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bed01a74c5b3338df958a3e178c06602bd69866
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052115"
---
# <a name="how-to-debug-clr-activation-issues"></a>Jak debugować problemy dotyczące aktywacji środowiska CLR

Jeśli wystąpią problemy z rozpoczęciem pracy aplikacji z poprawną wersją środowiska uruchomieniowego języka wspólnego (CLR), można wyświetlać i debugować dzienniki aktywacji środowiska CLR. Te dzienniki mogą być bardzo przydatne podczas określania głównej przyczyny problemu z aktywacją, gdy aplikacja ładuje inną wersję środowiska CLR niż oczekiwano lub nie ładuje środowiska CLR. Błędy [inicjowania .NET Framework: Zarządzanie środowiskiem](initialization-errors-managing-the-user-experience.md) użytkownika omawia środowisko, w którym nie znaleziono środowiska CLR dla aplikacji.

Rejestrowanie aktywacji środowiska CLR można włączyć na poziomie systemu przy użyciu klucza rejestru HKEY_LOCAL_MACHINE lub zmiennej środowiskowej system. Dziennik zostanie wygenerowany do momentu usunięcia wpisu rejestru lub zmiennej środowiskowej. Alternatywnie można użyć zmiennej środowiskowej użytkownika lub procesu lokalnego, aby włączyć rejestrowanie z innym zakresem i czasem trwania.

Dzienników aktywacji środowiska CLR nie należy mylić z [dziennikami powiązań zestawów](../tools/fuslogvw-exe-assembly-binding-log-viewer.md), które są całkowicie inne.

## <a name="to-enable-clr-activation-logging"></a>Aby włączyć rejestrowanie aktywacji środowiska CLR

### <a name="using-the-registry"></a>Korzystanie z rejestru

1. W Edytorze rejestru przejdź do HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework (na komputerze 32-bitowym) lub HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. Folder NETFramework (na komputerze 64-bitowym).

2. Dodaj wartość ciągu o nazwie `CLRLoadLogDir`i ustaw ją na pełną ścieżkę do istniejącego katalogu, w którym chcesz przechowywać dzienniki aktywacji środowiska CLR.

Rejestrowanie aktywacji pozostaje włączone do momentu usunięcia wartości ciągu.

### <a name="using-an-environment-variable"></a>Użycie zmiennej środowiskowej

- Ustaw zmienną `COMPLUS_CLRLoadLogDir` środowiskową na ciąg, który reprezentuje pełną ścieżkę do istniejącego katalogu, w którym chcesz przechowywać dzienniki aktywacji środowiska CLR.

    Sposób ustawiania zmiennej środowiskowej określa jej zakres:

  - Jeśli ustawisz ją na poziomie systemu, rejestrowanie aktywacji jest włączone dla wszystkich aplikacji .NET Framework na tym komputerze do momentu usunięcia zmiennej środowiskowej.

  - Jeśli ustawisz ją na poziomie użytkownika, rejestrowanie aktywacji jest włączone tylko dla bieżącego konta użytkownika. Rejestrowanie jest kontynuowane do momentu usunięcia zmiennej środowiskowej.

  - Jeśli ustawisz ją z poziomu procesu przed załadowaniem środowiska CLR, rejestrowanie aktywacji zostanie włączone do momentu zakończenia procesu.

  - Jeśli ustawisz go w wierszu polecenia przed uruchomieniem aplikacji, rejestrowanie aktywacji jest włączone dla każdej aplikacji, która jest uruchamiana z tego wiersza polecenia.

    Aby na przykład przechowywać dzienniki aktywacji w katalogu c:\clrloadlogs z zakresem poziomu procesu, Otwórz okno wiersza polecenia i wpisz następujące polecenie, aby uruchomić aplikację:

    ```console
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs
    ```

## <a name="example"></a>Przykład

Dzienniki aktywacji środowiska CLR zapewniają dużą ilość danych dotyczących aktywacji środowiska CLR i używania interfejsów API hostingu środowiska CLR. Większość tych danych jest używana wewnętrznie przez firmę Microsoft, ale niektóre dane mogą być również przydatne dla deweloperów, zgodnie z opisem w tym artykule.

Dziennik odzwierciedla kolejność wywoływania interfejsów API hostingu środowiska CLR. Zawiera również przydatne dane dotyczące zestawu zainstalowanych środowisk uruchomieniowych na komputerze. Format dziennika aktywacji środowiska CLR nie jest udokumentowany, ale może służyć do ułatwienia deweloperom, którzy muszą rozwiązać problemy związane z aktywacją środowiska CLR.

> [!NOTE]
> Nie można otworzyć dziennika aktywacji do momentu zakończenia procesu, który używa środowiska CLR.

> [!NOTE]
> Dzienniki aktywacji środowiska CLR nie są zlokalizowane; są one zawsze generowane w języku angielskim.

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

- **Dziennik ładowania środowiska CLR** zawiera ścieżkę do pliku wykonywalnego, który uruchomił proces, który załadował kod zarządzany. Należy pamiętać, że może to być Host macierzysty.

    ```output
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe
    ```

- **Zainstalowane środowisko uruchomieniowe** to zestaw wersji środowiska CLR zainstalowanych na komputerze, który jest kandydatem do żądania aktywacji.

    ```output
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0
    ```

- **wersja wbudowana** to wersja środowiska CLR, która została użyta do skompilowania pliku binarnego, który został dostarczony do metody, takiej jak [ICLRMetaHostPolicy:: GetRequestedRuntime —](../unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md).

    ```output
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727
    ```

- **Instalacja funkcji na żądanie** dotyczy .NET Framework 3,5 w systemie Windows 8. Zobacz [Błędy inicjowania .NET Framework: Zarządzanie czynnościami](initialization-errors-managing-the-user-experience.md) użytkownika w celu uzyskania dodatkowych informacji o tym scenariuszu.

    ```output
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3
    ```

## <a name="see-also"></a>Zobacz także

- [Wdrażanie](index.md)
- [Instrukcje: Skonfiguruj aplikację do obsługi .NET Framework 4 lub nowszej wersji](../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
