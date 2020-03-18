---
title: Migrowanie projektów C++/CLI do programu .NET Core
description: Dowiedz się więcej o przenoszeniu projektów C++/CLI do programu .NET Core.
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: eb03f2a5ff42e8279fd3ebd6ee6fb6d955f6798d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75964931"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a>Jak przenieść projekt C++/CLI do programu .NET Core

Począwszy od .NET Core 3.1 i Visual Studio 2019 w wersji 16.4, [projekty C++/CLI](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) mogą być przeznaczone dla programu .NET Core. Ta obsługa umożliwia przenoszenie aplikacji klasycznych systemu Windows z warstwami współprocesorowymi c++/CLI do .NET Core. W tym artykule opisano sposób przenoszenia projektów c++/CLI z platformy .NET Framework do .NET Core 3.1.

## <a name="ccli-net-core-limitations"></a>Ograniczenia rdzenia C++/CLI .NET

Istnieją pewne ważne ograniczenia dotyczące przenoszenia projektów C++/CLI do .NET Core w porównaniu z innymi językami:

* Obsługa c++/CLI dla programu .NET Core to tylko system Windows.
* Projekty C++/CLI nie mogą być kierowane na program .NET Standard, tylko program .NET Core (lub .NET Framework).
* Projekty c++/CLI nie obsługują nowego formatu pliku projektu w stylu SDK. Zamiast tego nawet podczas kierowania na .NET Core projekty C++/CLI używają istniejącego formatu pliku vcxproj.
* Projekty c++/CLI nie mogą kierować wielu platform .NET. Jeśli musisz utworzyć projekt C++/CLI dla programu .NET Framework i .NET Core, użyj oddzielnych plików projektu.
* .NET Core nie `-clr:pure` obsługuje `-clr:safe` ani kompilacji, tylko nowa `-clr:netcore` `-clr` opcja (która jest równoważna dla .NET Framework).

## <a name="port-a-ccli-project"></a>Przenoszenie projektu C++/CLI

Aby przenieść projekt C++/CLI do programu .NET Core, należy wprowadzić następujące zmiany w pliku vcxproj. Te kroki migracji różnią się od kroków wymaganych dla innych typów projektów, ponieważ projekty C++/CLI nie używają plików projektu w stylu SDK.

1. Zamień `<CLRSupport>true</CLRSupport>` `<CLRSupport>NetCore</CLRSupport>`właściwości na . Ta właściwość jest często w grupach właściwości specyficznych dla konfiguracji, więc może być konieczne zastąpienie go w wielu miejscach.
2. Zamień `<TargetFrameworkVersion>` `<TargetFramework>netcoreapp3.1</TargetFramework>`właściwości na .
3. Usuń wszystkie odwołania programu `<Reference Include="System" />`.NET Framework (np. ). Podczas korzystania `<CLRSupport>NetCore</CLRSupport>`z zestawów SDK .NET Core core są automatycznie odwoływane.
4. Zaktualizuj użycie interfejsu API w plikach cpp, w razie potrzeby, aby usunąć interfejsy API niedostępne dla programu .NET Core. Ponieważ projekty C++/CLI są zazwyczaj dość cienkimi warstwami współdziałania, często nie są potrzebne wiele zmian. [Analizator przenośności .NET](../../standard/analyzers/portability-analyzer.md) może służyć do identyfikowania nieobsługiwanych interfejsów API .NET używanych przez pliki binarne C++/CLI, podobnie jak w zapomocą czysto zarządzanych plików binarnych. Wskazówki dotyczące określania przenośności kodu i aktualizowania projektów do pracy z interfejsami API .NET Core są dostępne w [wytycznych dotyczących przenoszenia biblioteki.](./libraries.md#determine-portability)

### <a name="wpf-and-windows-forms-usage"></a>Użycie w pfi i formularzach systemu Windows

Projekty .NET Core C++/CLI mogą używać formularzy systemu Windows i interfejsów API WPF. Aby korzystać z tych interfejsów API pulpitu systemu Windows, należy dodać jawne odwołania framework do bibliotek interfejsu użytkownika. Projekty w stylu SDK, które używają interfejsów API pulpitu systemu Windows, automatycznie odwołują się do niezbędnych bibliotek framework przy użyciu sdk. `Microsoft.NET.Sdk.WindowsDesktop` Ponieważ projekty C++/CLI nie używają formatu projektu w stylu zestawu SDK, należy dodać jawne odwołania framework podczas kierowania .NET Core.

Aby korzystać z interfejsów API formularzy systemu Windows, dodaj to odwołanie do pliku vcxproj:

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

Aby użyć interfejsów API WPF, dodaj to odwołanie do pliku vcxproj:

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

Aby używać zarówno formularzy systemu Windows, jak i interfejsów API WPF, dodaj to odwołanie do pliku vcxproj:

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

Obecnie nie jest możliwe dodanie tych odwołań za pomocą menedżera odwołań programu Visual Studio. Zamiast tego zaktualizuj plik projektu ręcznie. Tę aktualizację można wykonać w programie Visual Studio, zwalniając projekt, a następnie edytując plik projektu. Można również użyć innego edytora, takiego jak VS Code.

## <a name="build-without-msbuild"></a>Kompilacja bez MSBuild

Istnieje również możliwość tworzenia projektów C++/CLI bez użycia MSBuild. Wykonaj następujące kroki, aby utworzyć projekt C++/CLI dla usługi .NET Core bezpośrednio z *programami cl.exe* i *link.exe:*

1. Podczas kompilowania `-clr:netcore` przekaż do *cl.exe*.
2. Odwołanie niezbędne .NET Core zestawów odwołań.
3. Podczas łączenia należy podać katalog hosta `LibPath` aplikacji .NET Core jako katalog (aby można było znaleźć *ijwhost.lib).*
4. *Skopiuj plik ijwhost.dll* (z katalogu hosta aplikacji .NET Core) do katalogu wyjściowego projektu.
5. Upewnij się, że plik [runtimeconfig.json](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) istnieje dla pierwszego składnika aplikacji, który będzie uruchamiał kod zarządzany. Jeśli aplikacja ma zarządzany punkt `runtime.config` wejścia, plik zostanie utworzony i skopiowany automatycznie. Jeśli aplikacja ma natywny punkt wejścia, `runtimeconfig.json` należy jednak utworzyć plik dla pierwszej biblioteki C++/CLI, aby użyć punktu uruchomieniowego .NET Core.

## <a name="known-issues"></a>Znane problemy

Istnieje kilka znanych problemów, na które należy zwrócić uwagę podczas pracy z projektami C++/CLI przeznaczonymi dla programu .NET Core.

* Odwołanie do struktury WPF w projektach .NET Core C++/CLI powoduje obecnie niektóre obce ostrzeżenia dotyczące niemożnej importowania symboli. Ostrzeżenia te można bezpiecznie zignorować i należy je wkrótce naprawić.
* Jeśli aplikacja ma natywny punkt wejścia, biblioteka C++/CLI, która najpierw wykonuje kod zarządzany, wymaga pliku [runtimeconfig.json.](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) Ten plik konfiguracyjny jest używany podczas uruchamiania programu .NET Core. Projekty C++/CLI nie `runtimeconfig.json` tworzą jeszcze plików w czasie kompilacji, więc plik musi zostać wygenerowany ręcznie. Jeśli biblioteka C++/CLI jest wywoływana z zarządzanego punktu wejścia, biblioteka C++/CLI nie potrzebuje `runtimeconfig.json` pliku (ponieważ zestaw punktu wejścia będzie miał taki, który jest używany podczas uruchamiania programu runtime). Poniżej przedstawiono `runtimeconfig.json` prosty przykładowy plik. Aby uzyskać więcej informacji, zobacz [specyfikację w githubie](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

    ```json
    {
          "runtimeOptions": {
             "tfm": "netcoreapp3.1",
             "framework": {
                "name": "Microsoft.NETCore.App",
                "version": "3.1.0"
             }
          }
    }
    ```
