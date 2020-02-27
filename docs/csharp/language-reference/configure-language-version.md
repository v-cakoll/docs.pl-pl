---
title: C#Obsługa wersji języka — C# Przewodnik
description: Dowiedz się, C# w jaki sposób wersja językowa jest określana na podstawie projektu i przyczyn związanych z tym wyborem. Dowiedz się, jak ręcznie przesłonić wartość domyślną.
ms.date: 02/21/2020
ms.openlocfilehash: 2be76fdac471a7175b661d896b0da2910b3609f3
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626767"
---
# <a name="c-language-versioning"></a>C#przechowywanie wersji języka

Najnowszy C# kompilator Określa domyślną wersję językową opartą na docelowej platformie lub strukturach projektu. Program Visual Studio nie udostępnia interfejsu użytkownika do zmiany wartości, ale można go zmienić, edytując plik *csproj* . Wybór domyślny zapewnia, że jest używana najnowsza wersja językowa zgodna z platformą docelową. Korzystasz z dostępu do najnowszych funkcji języka zgodnych z celem projektu. To ustawienie domyślne gwarantuje również, że nie używasz języka wymagającego typów lub zachowania środowiska uruchomieniowego, które nie jest dostępne w platformie docelowej. Wybranie wersji językowej nowszej niż domyślna może spowodować trudne zdiagnozowanie błędów kompilacji i czasu wykonywania.

C#8,0 (i nowsze) jest obsługiwana tylko w programie .NET Core 3. x i nowszych wersjach. Wiele najnowszych funkcji wymaga funkcji biblioteki i środowiska uruchomieniowego wprowadzonych w programie .NET Core 3. x:

- Implementacja domyślnego elementu członkowskiego interfejsu wymaga nowych funkcji w środowisku CLR programu .NET Core 3,0.
- Strumienie asynchroniczne wymagają nowych typów <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>i <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>.
- Indeksy i zakresy wymagają nowych typów <xref:System.Index?displayProperty=nameWithType> i <xref:System.Range?displayProperty=nameWithType>.
- Typy odwołań dopuszczających wartości null wykorzystują kilka [atrybutów](../nullable-attributes.md) w celu zapewnienia lepszych ostrzeżeń. Te atrybuty zostały dodane w programie .NET Core 3,0. Inne platformy docelowe nie zostały opatrzone adnotacją z żadnym z tych atrybutów. Oznacza to, że ostrzeżenia dopuszczające wartość null mogą nie odzwierciedlać dokładnie potencjalnych problemów.

## <a name="defaults"></a>Wartość domyślna

Kompilator określa wartość domyślną na podstawie następujących reguł:

|Platforma docelowa|version|C#domyślna wersja języka|
|----------------|-------|---------------------------|
|.NET Core|wersji|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|2.1|C# 8.0|
|.NET Standard|2.0|C# 7.3|
|.NET Standard|1.x|C# 7.3|
|.NET Framework|all|C# 7.3|

Jeśli projekt jest przeznaczony dla platformy wersji zapoznawczej, która ma odpowiednią wersję języka wersji zapoznawczej, używana jest wersja języka w wersji zapoznawczej. Należy używać najnowszych funkcji w wersji zapoznawczej w dowolnym środowisku, bez wywierania wpływu na projekty przeznaczone do wydania .NET Core.

## <a name="override-a-default"></a>Zastąp wartość domyślną

Jeśli musisz określić C# wersję jawnie, możesz to zrobić na kilka sposobów:

- Edytuj ręcznie [plik projektu](#edit-the-project-file).
- Ustaw wersję językową [dla wielu projektów w podkatalogu](#configure-multiple-projects).
- Skonfiguruj [opcję kompilatora`-langversion`](compiler-options/langversion-compiler-option.md).

### <a name="edit-the-project-file"></a>Edytuj plik projektu

Możesz ustawić wersję językową w pliku projektu. Jeśli na przykład jawnie chcesz uzyskać dostęp do funkcji w wersji zapoznawczej, Dodaj element podobny do tego:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Wartość `preview` używa najnowszej dostępnej wersji języka zapoznawczej C# obsługiwanej przez kompilator.

### <a name="configure-multiple-projects"></a>Konfigurowanie wielu projektów

Aby skonfigurować wiele projektów, można utworzyć plik **Directory. Build. props** , który zawiera element `<LangVersion>`. Zwykle jest to wykonywane w katalogu rozwiązania. Dodaj następujący element do pliku **Directory. Build. props** w katalogu rozwiązania:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Kompilacje we wszystkich podkatalogach katalogu zawierającego ten plik będą korzystać z wersji zapoznawczej C# . Aby uzyskać więcej informacji, zobacz artykuł na temat [dostosowywania kompilacji](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>C#dokumentacja wersji języka

W poniższej tabeli przedstawiono wszystkie bieżące C# wersje językowe. Kompilator może niekoniecznie zrozumieć każdą wartość, jeśli jest starszy. Jeśli zainstalujesz program .NET Core 3,0 lub nowszy, masz dostęp do wszystkich elementów na liście.

|Wartość|Znaczenie|
|------------|-------------|
|wersja zapoznawcza|Kompilator akceptuje całą poprawną składnię języka od najnowszej wersji zapoznawczej.|
|najnowsza|Kompilator akceptuje składnię z najnowszej wydanej wersji kompilatora (w tym wersji pomocniczej).|
|latestMajor|Kompilator akceptuje składnię z najnowszej wydanej wersji głównej kompilatora.|
|8.0|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 8,0 lub niższej.|
|7.3|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,3 lub niższej.|
|7.2|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,2 lub niższej.|
|7.1|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,1 lub niższej.|
|7|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,0 lub niższej.|
|6|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 6,0 lub niższej.|
|5|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 5,0 lub niższej.|
|4|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 4,0 lub niższej.|
|3|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 3,0 lub niższej.|
|ISO-2|Kompilator akceptuje tylko składnię zawartą w normie ISO/ C# IEC 23270:2006 (2,0). |
|ISO-1|Kompilator akceptuje tylko składnię zawartą w ISO/IEC 23270:2003 C# (1.0/1.2). |
