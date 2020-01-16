---
title: Migrowanie C++projektów/CLI do platformy .NET Core
description: Dowiedz się więcej C++na temat przenoszenia projektów/CLI do platformy .NET Core.
author: mjrousos
ms.date: 01/10/2020
ms.openlocfilehash: eb03f2a5ff42e8279fd3ebd6ee6fb6d955f6798d
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964931"
---
# <a name="how-to-port-a-ccli-project-to-net-core"></a>Jak przenieść projekt C++/CLI do platformy .NET Core

Począwszy od platformy .NET Core 3,1 i programu Visual Studio 2019 w wersji 16,4, [ C++/CLI projekty](/cpp/dotnet/dotnet-programming-with-cpp-cli-visual-cpp) mogą kierować platformą .NET Core. Ta obsługa umożliwia przenoszenie aplikacji klasycznych systemu Windows z C++warstwami międzyoperacyjnymi/CLI do platformy .NET Core. W tym artykule opisano sposób przenoszenia C++projektów/CLI z .NET Framework do programu .net Core 3,1.

## <a name="ccli-net-core-limitations"></a>C++Ograniczenia dotyczące/CLI .NET Core

Istnieją pewne ważne ograniczenia dotyczące przenoszenia projektów C++/CLI do platformy .NET Core w porównaniu z innymi językami:

* C++Obsługa/CLI dla platformy .NET Core jest tylko w systemie Windows.
* C++Projekty/CLI nie mogą wskazywać .NET Standard, tylko .NET Core (lub .NET Framework).
* C++Projekty/CLI nie obsługują nowego formatu pliku projektu w stylu zestawu SDK. Zamiast tego, nawet w przypadku określania programu C++.NET Core, projekty/CLI używają istniejącego formatu pliku VCXPROJ.
* C++Projekty/CLI nie mogą wiele obiektów docelowych w wielu platformach .NET. Jeśli konieczne jest skompilowanie projektu C++/CLI dla obu .NET Framework i .NET Core, należy użyć oddzielnych plików projektu.
* Platforma .NET Core nie obsługuje kompilacji `-clr:pure` ani `-clr:safe`, tylko nowej opcji `-clr:netcore` (która jest równoważna z `-clr` dla .NET Framework).

## <a name="port-a-ccli-project"></a>Port projektu C++/CLI

Aby przenieść projekt C++/CLI do platformy .NET Core, wprowadź następujące zmiany w pliku VCXPROJ. Te kroki migracji różnią się od czynności wymaganych dla innych typów projektów C++, ponieważ projekty/CLI nie używają plików projektu w stylu zestawu SDK.

1. Zastąp właściwości `<CLRSupport>true</CLRSupport>` `<CLRSupport>NetCore</CLRSupport>`. Ta właściwość często występuje w grupach właściwości specyficznych dla konfiguracji, więc może być konieczne zamienienie jej w wielu miejscach.
2. Zastąp właściwości `<TargetFrameworkVersion>` `<TargetFramework>netcoreapp3.1</TargetFramework>`.
3. Usuń wszystkie odnośniki .NET Framework (takie jak `<Reference Include="System" />`). Zestawy zestaw .NET Core SDK są automatycznie przywoływane podczas korzystania z `<CLRSupport>NetCore</CLRSupport>`.
4. W razie potrzeby zaktualizuj użycie interfejsu API w plikach CPP, aby usunąć interfejsy API niedostępne dla platformy .NET Core. Ponieważ C++projekty/CLI mają dość wąskie warstwy międzyoperacyjności, często nie trzeba zmieniać wielu zmian. [Analizator przenośności platformy .NET](../../standard/analyzers/portability-analyzer.md) może służyć do identyfikowania nieobsługiwanych interfejsów API C++platformy .NET używanych przez pliki binarne/CLI tak samo jak w przypadku czystych, zarządzanych plików binarnych. Wskazówki dotyczące określania przenośności kodu i aktualizowania projektów do pracy z interfejsami API programu .NET Core są dostępne w obszarze [wskazówki dotyczące przenoszenia biblioteki](./libraries.md#determine-portability).

### <a name="wpf-and-windows-forms-usage"></a>Użycie WPF i Windows Forms

Projekty platformy C++.NET Core/CLI mogą używać interfejsów API Windows Forms i WPF. Aby użyć tych interfejsów API pulpitu systemu Windows, należy dodać jawne odwołania do bibliotek interfejsu użytkownika. Projekty w stylu zestawu SDK, które używają interfejsów API systemu Windows, są automatycznie odwołujące się do niezbędnych bibliotek struktury przy użyciu zestawu SDK `Microsoft.NET.Sdk.WindowsDesktop`. Ponieważ C++projekty/CLI nie używają formatu projektu w stylu zestawu SDK, muszą dodać jawne odwołania do struktury w przypadku określania platformy .NET Core.

Aby użyć Windows Forms interfejsów API, należy dodać to odwołanie do pliku VCXPROJ:

```xml
<!-- Reference all of Windows Forms -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WindowsForms" />
```

Aby używać interfejsów API WPF, należy dodać to odwołanie do pliku VCXPROJ:

```xml
<!-- Reference all of WPF -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App.WPF" />
```

Aby użyć zarówno Windows Forms, jak i interfejsów API WPF, należy dodać to odwołanie do pliku VCXPROJ:

```xml
<!-- Reference the entirety of the Windows desktop framework:
     Windows Forms, WPF, and the types that provide integration between them -->
<FrameworkReference Include="Microsoft.WindowsDesktop.App" />
```

Obecnie nie jest możliwe dodawanie tych odwołań za pomocą Menedżera odwołań programu Visual Studio. Zamiast tego należy ręcznie zaktualizować plik projektu. Tę aktualizację można wykonać w programie Visual Studio, zwalniając projekt, a następnie edytując plik projektu. Można również użyć innego edytora, takiego jak VS Code.

## <a name="build-without-msbuild"></a>Kompiluj bez programu MSBuild

Możliwe jest również tworzenie C++projektów/CLI bez użycia programu MSBuild. Wykonaj następujące kroki, aby utworzyć C++projekt/CLI dla platformy .NET Core bezpośrednio przy użyciu *CL. exe* i *link. exe*:

1. Podczas kompilowania Przekaż `-clr:netcore` do *CL. exe*.
2. Odwołuje się do niezbędnych zestawów referencyjnych platformy .NET Core.
3. Podczas łączenia należy udostępnić katalog hosta aplikacji .NET Core jako `LibPath` (aby można było znaleźć *ijwhost. lib* ).
4. Skopiuj *ijwhost. dll* (z katalogu hosta aplikacji .NET Core) do katalogu wyjściowego projektu.
5. Upewnij się, że plik [runtimeconfig. JSON](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) istnieje dla pierwszego składnika aplikacji, w którym będzie uruchamiany kod zarządzany. Jeśli aplikacja ma zarządzany punkt wejścia, plik `runtime.config` zostanie utworzony i skopiowany automatycznie. Jeśli aplikacja ma natywny punkt wejścia, należy utworzyć plik `runtimeconfig.json` dla pierwszej C++biblioteki/CLI, aby użyć środowiska uruchomieniowego platformy .NET Core.

## <a name="known-issues"></a>Znane problemy

Istnieje kilka znanych problemów, które należy wyszukać podczas pracy z C++projektami/CLI przeznaczonymi dla platformy .NET Core.

* Odwołanie do struktury WPF w projektach platformy C++.NET Core/CLI obecnie powoduje, że niektóre nadmiarowe ostrzeżenia o nie mogą zaimportować symboli. Te ostrzeżenia można bezpiecznie zignorować i powinny zostać wkrótce naprawione.
* Jeśli aplikacja ma natywny punkt wejścia, biblioteka C++/CLI, która najpierw wykonuje kod zarządzany, wymaga pliku [runtimeconfig. JSON](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) . Ten plik konfiguracji jest używany podczas uruchamiania środowiska uruchomieniowego .NET Core. C++Projekty/CLI nie tworzą jeszcze automatycznie plików `runtimeconfig.json` w czasie kompilacji, więc plik musi być wygenerowany ręcznie. Jeśli biblioteka C++/CLI jest wywoływana z zarządzanego punktu wejścia, biblioteka C++/CLI nie wymaga pliku `runtimeconfig.json` (ponieważ zestaw punktów wejścia będzie używany podczas uruchamiania środowiska uruchomieniowego). Poniżej przedstawiono prosty przykładowy plik `runtimeconfig.json`. Aby uzyskać więcej informacji, zobacz [specyfikację w witrynie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

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
