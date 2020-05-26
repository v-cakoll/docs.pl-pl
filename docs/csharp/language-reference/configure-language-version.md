---
title: Obsługa wersji języka c# — Przewodnik C#
description: Dowiedz się, w jaki sposób wersja języka C# jest określana na podstawie projektu i przyczyn związanych z tym wyborem. Dowiedz się, jak ręcznie przesłonić wartość domyślną.
ms.date: 05/20/2020
ms.openlocfilehash: bbe5b12e378cf47b7c9b2c8576088e949e526a9a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803008"
---
# <a name="c-language-versioning"></a>Przechowywanie wersji języka C#

Najnowsza kompilator języka C# określa domyślną wersję językową opartą na docelowej platformie lub strukturach projektu. Program Visual Studio nie udostępnia interfejsu użytkownika do zmiany wartości, ale można go zmienić, edytując plik *csproj* . Wybór domyślny zapewnia, że jest używana najnowsza wersja językowa zgodna z platformą docelową. Korzystasz z dostępu do najnowszych funkcji języka zgodnych z celem projektu. To ustawienie domyślne gwarantuje również, że nie używasz języka wymagającego typów lub zachowania środowiska uruchomieniowego, które nie jest dostępne w platformie docelowej. Wybranie wersji językowej nowszej niż domyślna może spowodować trudne zdiagnozowanie błędów kompilacji i czasu wykonywania.

Reguły w tym artykule mają zastosowanie do kompilatora dostarczonego z programem Visual Studio 2019 lub zestawem SDK programu .NET Core 3,0. Kompilatory języka C#, które są częścią instalacji programu Visual Studio 2017 lub starsze wersje zestaw .NET Core SDK wersji docelowej C# 7,0.

Języki C# 8,0 (i nowsze) są obsługiwane tylko w programie .NET Core 3. x i nowszych wersjach. Wiele najnowszych funkcji wymaga funkcji biblioteki i środowiska uruchomieniowego wprowadzonych w programie .NET Core 3. x:

- [Domyślna implementacja interfejsu](../whats-new/csharp-8.md#default-interface-methods) wymaga nowych funkcji w środowisku CLR programu .net Core 3,0.
- [Strumienie asynchroniczne](../whats-new/csharp-8.md#asynchronous-streams) wymagają nowych typów <xref:System.IAsyncDisposable?displayProperty=nameWithType> , <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> i <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> .
- [Indeksy i zakresy](../whats-new/csharp-8.md#indices-and-ranges) wymagają nowych typów <xref:System.Index?displayProperty=nameWithType> i <xref:System.Range?displayProperty=nameWithType> .
- [Typy odwołań dopuszczających wartości null](../whats-new/csharp-8.md#nullable-reference-types) wykorzystują kilka [atrybutów](attributes/nullable-analysis.md) w celu zapewnienia lepszych ostrzeżeń. Te atrybuty zostały dodane w programie .NET Core 3,0. Inne platformy docelowe nie zostały opatrzone adnotacją z żadnym z tych atrybutów. Oznacza to, że ostrzeżenia dopuszczające wartość null mogą nie odzwierciedlać dokładnie potencjalnych problemów.

## <a name="defaults"></a>Wartość domyślna

Kompilator określa wartość domyślną na podstawie następujących reguł:

| Platforma docelowa | version | Domyślna wersja języka C# |
|------------------|---------|-----------------------------|
| .NET Core        | wersji     | C# 8.0                      |
| .NET Core        | 2.x     | C# 7.3                      |
| .NET Standard    | 2.1     | C# 8.0                      |
| .NET Standard    | 2.0     | C# 7.3                      |
| .NET Standard    | 1.x     | C# 7.3                      |
| .NET Framework   | all     | C# 7.3                      |

Jeśli projekt jest przeznaczony dla platformy wersji zapoznawczej, która ma odpowiednią wersję języka wersji zapoznawczej, używana jest wersja języka w wersji zapoznawczej. Należy używać najnowszych funkcji w wersji zapoznawczej w dowolnym środowisku, bez wywierania wpływu na projekty przeznaczone do wydania .NET Core.

## <a name="override-a-default"></a>Zastąp wartość domyślną

Jeśli musisz jawnie określić wersję języka C#, możesz to zrobić na kilka sposobów:

- Edytuj ręcznie [plik projektu](#edit-the-project-file).
- Ustaw wersję językową [dla wielu projektów w podkatalogu](#configure-multiple-projects).
- Skonfiguruj [ `-langversion` opcję kompilatora](compiler-options/langversion-compiler-option.md).

### <a name="edit-the-project-file"></a>Edytuj plik projektu

Możesz ustawić wersję językową w pliku projektu. Jeśli na przykład jawnie chcesz uzyskać dostęp do funkcji w wersji zapoznawczej, Dodaj element podobny do tego:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Ta wartość `preview` używa najnowszej dostępnej wersji językowej C# obsługiwanej przez kompilator.

### <a name="configure-multiple-projects"></a>Konfigurowanie wielu projektów

Aby skonfigurować wiele projektów, można utworzyć plik **Directory. Build. props** , który zawiera `<LangVersion>` element. Zwykle jest to wykonywane w katalogu rozwiązania. Dodaj następujący element do pliku **Directory. Build. props** w katalogu rozwiązania:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Kompilacje we wszystkich podkatalogach katalogu zawierającego ten plik będą korzystać z wersji zapoznawczej języka C#. Aby uzyskać więcej informacji, zobacz artykuł na temat [dostosowywania kompilacji](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>Dokumentacja wersji języka C#

W poniższej tabeli przedstawiono wszystkie bieżące wersje języka C#. Kompilator może niekoniecznie zrozumieć każdą wartość, jeśli jest starszy. Jeśli zainstalujesz program .NET Core 3,0 lub nowszy, masz dostęp do wszystkich elementów na liście.

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> Otwórz [wiersz polecenia dla deweloperów dla programu Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md)i uruchom następujące polecenie, aby wyświetlić listę wersji językowych dostępnych na komputerze.
>
> ```CMD
> csc -langversion:?
> ```
>
> Pytania dotyczące opcji Kompiluj [-langversion](compiler-options/langversion-compiler-option.md) w następujący sposób spowoduje wydrukowanie coś podobnego do poniższego:
>
> ```CMD
> Supported language versions:
> default
> 1
> 2
> 3
> 4
> 5
> 6
> 7.0
> 7.1
> 7.2
> 7.3
> 8.0 (default)
> latestmajor
> preview
> latest
> ```
