---
title: C# wersja językowa - C# Przewodnik
description: Dowiedz się, jak wersja językowa języka C# jest określana na podstawie projektu i przyczyn tego wyboru. Dowiedz się, jak ręcznie zastąpić wartość domyślną.
ms.date: 02/21/2020
ms.openlocfilehash: 850c4a860878593d80aaa3b7b38efaff9e003f43
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102661"
---
# <a name="c-language-versioning"></a>Przechowywanie wersji językowych języka języka C#

Najnowszy kompilator języka C# określa domyślną wersję językową na podstawie struktury docelowej lub struktury projektu. Visual Studio nie udostępnia interfejsu użytkownika, aby zmienić wartość, ale można go zmienić, edytując plik *csproj.* Wybór wartości domyślnej gwarantuje, że używasz najnowszej wersji językowej zgodnej z platformą docelową. Korzystasz z dostępu do najnowszych funkcji językowych zgodnych z celem projektu. Ten domyślny wybór zapewnia również, że nie używasz języka, który wymaga typów lub zachowanie środowiska uruchomieniowego nie są dostępne w ramach docelowej. Wybranie wersji języka nowszej niż domyślna może spowodować trudne do zdiagnozowania błędów w czasie kompilacji i środowiska wykonawczego.

Reguły w tym artykule dotyczą kompilatora dostarczanego z programem Visual Studio 2019 lub zestawem SDK .NET Core 3.0. Kompilatory języka C#, które są częścią instalacji programu Visual Studio 2017 lub wcześniejszych wersji .NET Core SDK docelowy C# 7.0 domyślnie.

C# 8.0 (i nowsze) jest obsługiwany tylko w .NET Core 3.x i nowszych wersjach. Wiele najnowszych funkcji wymaga funkcji biblioteki i środowiska uruchomieniowego wprowadzonych w pliku .NET Core 3.x:

- Domyślna implementacja elementu członkowskiego interfejsu wymaga nowych funkcji w programie .NET Core 3.0 CLR.
- Strumienie asynchroniowe <xref:System.IAsyncDisposable?displayProperty=nameWithType>wymagają <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>nowych <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>typów , i .
- Indeksy i zakresy wymagają <xref:System.Index?displayProperty=nameWithType> <xref:System.Range?displayProperty=nameWithType>nowych typów i .
- Typy odwołań nullable używać kilku [atrybutów,](attributes/nullable-analysis.md) aby zapewnić lepsze ostrzeżenia. Te atrybuty zostały dodane w .NET Core 3.0. Inne struktury docelowe nie zostały oś tym adnotacjami o żadnej z tych atrybutów. Oznacza to, że ostrzeżenia możliwe do anulowania mogą nie odzwierciedlać dokładnie potencjalnych problemów.

## <a name="defaults"></a>Wartość domyślna

Kompilator określa wartość domyślną na podstawie tych reguł:

|Struktura docelowa|version|Domyślna wersja języka języka języka C#|
|----------------|-------|---------------------------|
|.NET Core|3.x|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|2.1|C# 8.0|
|.NET Standard|2.0|C# 7.3|
|.NET Standard|1.x|C# 7.3|
|.NET Framework|all|C# 7.3|

Gdy projekt jest przeznaczony dla struktury w wersji zapoznawczej, która ma odpowiednią wersję języka w wersji zapoznawczej, używana wersja językowa jest wersją języka podglądu. Używane są najnowsze funkcje z tym podglądem w dowolnym środowisku, bez wpływu na projekty przeznaczone dla wydanej wersji .NET Core.

## <a name="override-a-default"></a>Zastępowanie wartości domyślnej

Jeśli musisz jawnie określić wersję języka C#, możesz to zrobić na kilka sposobów:

- Ręcznie edytuj [plik projektu](#edit-the-project-file).
- Ustaw wersję językową [dla wielu projektów w podkatalogu](#configure-multiple-projects).
- Skonfiguruj opcję [ `-langversion` kompilatora](compiler-options/langversion-compiler-option.md).

### <a name="edit-the-project-file"></a>Edytowanie pliku projektu

Wersję językową można ustawić w pliku projektu. Na przykład, jeśli jawnie chcesz uzyskać dostęp do funkcji w wersji zapoznawczej, dodaj element w ten sposób:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Wartość `preview` używa najnowszej dostępnej wersji języka języka języka C# w wersji, którą obsługuje kompilator.

### <a name="configure-multiple-projects"></a>Konfigurowanie wielu projektów

Aby skonfigurować wiele projektów, można utworzyć plik **Directory.Build.props,** który zawiera `<LangVersion>` element. Zazwyczaj można to zrobić w katalogu rozwiązania. Dodaj następujące elementy do pliku **Directory.Build.props** w katalogu rozwiązania:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Kompilacje we wszystkich podkatalogach katalogu zawierającego ten plik będą używać wersji w wersji w wersji języka C#. Aby uzyskać więcej informacji, zobacz artykuł na [dostosowywanie kompilacji](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>Odwołanie do wersji językowej języka języka C#

W poniższej tabeli przedstawiono wszystkie bieżące wersje języka języka C#. Kompilator może nie koniecznie zrozumieć każdą wartość, jeśli jest starsza. Jeśli zainstalujesz .NET Core 3.0 lub nowszą, masz dostęp do wszystkiego, co się znajduje na liście.

|Wartość|Znaczenie|
|------------|-------------|
|preview|Kompilator akceptuje wszystkie prawidłowe składnię języka z najnowszej wersji zapoznawczej.|
|najnowsza|Kompilator akceptuje składnię z najnowszej wersji wydanej kompilatora (w tym wersji pomocniczej).|
|najnowszeMajor|Kompilator akceptuje składnię z najnowszej wydanej wersji głównej kompilatora.|
|8.0|Kompilator akceptuje tylko składnię, która jest uwzględniona w języku C# 8.0 lub niższym.|
|7.3|Kompilator akceptuje tylko składnię, która jest uwzględniona w języku C# 7.3 lub niższym.|
|7.2|Kompilator akceptuje tylko składnię, która jest uwzględniona w języku C# 7.2 lub niższym.|
|7.1|Kompilator akceptuje tylko składnię, która jest uwzględniona w języku C# 7.1 lub niższym.|
|7|Kompilator akceptuje tylko składnię, która jest uwzględniona w języku C# 7.0 lub niższym.|
|6|Kompilator akceptuje tylko składnię, która jest uwzględniona w języku C# 6.0 lub niższym.|
|5|Kompilator akceptuje tylko składnię, która jest uwzględniona w języku C# 5.0 lub niższym.|
|4|Kompilator akceptuje tylko składnię, która jest uwzględniona w języku C# 4.0 lub niższym.|
|3|Kompilator akceptuje tylko składnię, która jest uwzględniona w języku C# 3.0 lub niższym.|
|ISO-2|Kompilator akceptuje tylko składnię, która jest uwzględniona w ISO/IEC 23270:2006 C# (2.0). |
|ISO-1|Kompilator akceptuje tylko składnię zawartą w iso/IEC 23270:2003 C# (1.0/1.2). |
