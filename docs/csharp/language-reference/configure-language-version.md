---
title: C# language versioning - C# Przewodnik
description: Dowiedz się, jak wersja językowa języka C# jest określana na podstawie projektu i przyczyn tego wyboru. Dowiedz się, jak ręcznie zastąpić domyślne.
ms.date: 02/21/2020
ms.openlocfilehash: ef7275aad7638f52ecbfca1dfbdb962ae242fb48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399540"
---
# <a name="c-language-versioning"></a>Przechowywanie wersji językowych języka Języka C#

Najnowszy kompilator Języka C# określa domyślną wersję językową na podstawie struktury docelowej projektu lub struktur. Program Visual Studio nie udostępnia interfejsu, aby zmienić wartość, ale można go zmienić, edytując plik *csproj.* Wybór domyślnego zapewnia, że używasz najnowszej wersji językowej zgodnej z platformą docelową. Możesz korzystać z dostępu do najnowszych funkcji językowych zgodnych z celem projektu. Ten domyślny wybór zapewnia również, że nie używasz języka, który wymaga typów lub zachowania w czasie wykonywania nie są dostępne w ramach docelowej. Wybranie wersji językowej nowszej niż domyślna może spowodować trudne do zdiagnozowania błędy kompilacji i czasu wykonywania.

Reguły w tym artykule mają zastosowanie do kompilatora dostarczonego z visual studio 2019 lub .NET Core 3.0 SDK. Kompilatory Języka C#, które są częścią instalacji programu Visual Studio 2017 lub wcześniejszych wersji sdk .NET Core domyślnie docelowych C# 7.0 domyślnie.

C# 8.0 (i wyższe) jest obsługiwany tylko w .NET Core 3.x i nowszych wersjach. Wiele najnowszych funkcji wymaga funkcji biblioteki i środowiska uruchomieniowego wprowadzonych w .NET Core 3.x:

- Domyślna implementacja elementu członkowskiego interfejsu wymaga nowych funkcji w clr .NET Core 3.0.
- Strumienie asynchroniczne <xref:System.IAsyncDisposable?displayProperty=nameWithType>wymagają <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>nowych <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>typów , i .
- Indeksy i zakresy wymagają <xref:System.Index?displayProperty=nameWithType> <xref:System.Range?displayProperty=nameWithType>nowych typów i .
- Typy odwołań null do wykorzystania kilku [atrybutów,](../nullable-attributes.md) aby zapewnić lepsze ostrzeżenia. Te atrybuty zostały dodane w .NET Core 3.0. Inne platformy docelowe nie zostały adnotowane z żadnym z tych atrybutów. Oznacza to, że ostrzeżenia nullable może nie dokładnie odzwierciedlać potencjalne problemy.

## <a name="defaults"></a>Wartość domyślna

Kompilator określa domyślne na podstawie następujących reguł:

|Ramy docelowe|version|Domyślna wersja językowa języka języka Języka C#|
|----------------|-------|---------------------------|
|.NET Core|3.x|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|2.1|C# 8.0|
|.NET Standard|2.0|C# 7.3|
|.NET Standard|1.x|C# 7.3|
|.NET Framework|all|C# 7.3|

Gdy projekt jest przeznaczony dla struktury podglądu, która ma odpowiednią wersję językową podglądu, używana wersja językowa jest wersją językową w wersji zapoznawczej. Najnowsze funkcje są używane z tym podglądem w dowolnym środowisku, bez wpływu na projekty, które są przeznaczone dla wydanej wersji .NET Core.

## <a name="override-a-default"></a>Zastępowanie wartości domyślnej

Jeśli musisz jawnie określić wersję języka C#, możesz to zrobić na kilka sposobów:

- Ręcznie edytować [plik projektu](#edit-the-project-file).
- Ustaw wersję językową [dla wielu projektów w podkatalogu](#configure-multiple-projects).
- Skonfiguruj opcję [ `-langversion` kompilatora](compiler-options/langversion-compiler-option.md).

### <a name="edit-the-project-file"></a>Edytowanie pliku projektu

Wersję językową można ustawić w pliku projektu. Na przykład, jeśli jawnie chcesz uzyskać dostęp do funkcji podglądu, dodaj taki element:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Wartość `preview` używa najnowszej dostępnej wersji języka C# podglądu, który obsługuje kompilator.

### <a name="configure-multiple-projects"></a>Konfigurowanie wielu projektów

Aby skonfigurować wiele projektów, można utworzyć plik **Directory.Build.props** zawierający `<LangVersion>` element. Zazwyczaj można to zrobić w katalogu rozwiązania. Dodaj następujące elementy do pliku **Directory.Build.props** w katalogu rozwiązania:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Kompilacje we wszystkich podkatalogach katalogu zawierającego ten plik będą używać wersji podglądu C#. Aby uzyskać więcej informacji, zobacz artykuł na [temat Dostosowywanie kompilacji](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>Odwołanie do wersji językowej języka języka C#

W poniższej tabeli przedstawiono wszystkie bieżące wersje językowe języka Języka C#. Kompilator może niekoniecznie zrozumieć każdą wartość, jeśli jest starsza. Jeśli zainstalujesz program .NET Core 3.0 lub nowszy, masz dostęp do wszystkich wymienionych danych.

|Wartość|Znaczenie|
|------------|-------------|
|podgląd|Kompilator akceptuje całą składnię prawidłowego języka z najnowszej wersji zapoznawczej.|
|najnowsza|Kompilator akceptuje składnię z najnowszej wydanej wersji kompilatora (w tym wersji pomocniczej).|
|najnowszeMajor|Kompilator akceptuje składnię z najnowszej wydanej wersji głównej kompilatora.|
|8.0|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 8.0 lub niższym.|
|7.3|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 7.3 lub niższym.|
|7.2|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 7.2 lub niższym.|
|7.1|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 7.1 lub niższym.|
|7|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 7.0 lub niższym.|
|6|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 6.0 lub niższym.|
|5|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 5.0 lub niższej.|
|4|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 4.0 lub niższym.|
|3|Kompilator akceptuje tylko składnię, która jest uwzględniona w Języku C# 3.0 lub niższym.|
|Iso-2|Kompilator akceptuje tylko składnię, która jest uwzględniona w ISO/IEC 23270:2006 C# (2.0). |
|Iso-1|Kompilator akceptuje tylko składnię, która jest uwzględniona w ISO/IEC 23270:2003 C# (1.0/1.2). |
