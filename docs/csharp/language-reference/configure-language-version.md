---
title: C#Obsługa wersji języka — C# Przewodnik
description: Dowiedz się, C# w jaki sposób wersja językowa jest określana na podstawie projektu, i różne wartości, które można dostosować ręcznie do programu.
ms.date: 07/10/2019
ms.openlocfilehash: aa4f16d91b38fec7f5d4cd0b2632e62552b64eb7
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698809"
---
# <a name="c-language-versioning"></a>C#przechowywanie wersji języka

Najnowszy C# kompilator Określa domyślną wersję językową opartą na docelowej platformie lub strukturach projektu. Jest to spowodowane tym C# , że język może mieć funkcje, które są zależne od typów lub składników środowiska uruchomieniowego, które nie są dostępne w każdej implementacji platformy .NET. Zapewnia to również, że dla każdego elementu docelowego projektu jest tworzona z myślą o największej zgodnej wersji językowej.

Reguły w tym artykule mają zastosowanie do kompilatora dostarczonego z programem Visual Studio 2019 lub zestawem SDK programu .NET Core 3,0. C# Kompilatory, które są częścią instalacji programu Visual Studio 2017 lub starszej wersji zestaw .NET Core SDK C# wersje Target 7,0 domyślnie. 

## <a name="defaults"></a>Wartość domyślna

Kompilator określa wartość domyślną na podstawie następujących reguł:

|Platforma docelowa|version|C#domyślna wersja języka|
|----------------|-------|---------------------------|
|.NET Core|wersji|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|2,1|C# 8.0|
|.NET Standard|2.0|C# 7.3|
|.NET Standard|1.x|C# 7.3|
|.NET Framework|wszystkie|C# 7.3|

## <a name="default-for-previews"></a>Domyślnie dla wersji zapoznawczych

Jeśli projekt jest przeznaczony dla platformy wersji zapoznawczej, która ma odpowiednią wersję języka wersji zapoznawczej, używana jest wersja języka w wersji zapoznawczej. Dzięki temu można korzystać z najnowszych funkcji, które są gwarantowane do pracy z tą wersją zapoznawczą w dowolnym środowisku bez wpływu na projekty przeznaczone dla wydanej wersji platformy .NET Core.

## <a name="override-a-default"></a>Zastąp wartość domyślną

Jeśli musisz określić C# wersję jawnie, możesz to zrobić na kilka sposobów:

- Edytuj ręcznie [plik projektu](#edit-the-project-file).
- Ustaw wersję językową [dla wielu projektów w podkatalogu](#configure-multiple-projects).
- Konfigurowanie [opcji kompilatora `-langversion`](compiler-options/langversion-compiler-option.md)

### <a name="edit-the-project-file"></a>Edytuj plik projektu

Możesz ustawić wersję językową w pliku projektu. Jeśli na przykład jawnie chcesz uzyskać dostęp do funkcji w wersji zapoznawczej, Dodaj element podobny do tego:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Wartość `preview` używa najnowszej dostępnej wersji C# językowej, która obsługuje kompilator.

### <a name="configure-multiple-projects"></a>Konfigurowanie wielu projektów

Można utworzyć plik **Directory. Build. props** , który zawiera element `<LangVersion>`, aby skonfigurować wiele katalogów. Zwykle jest to wykonywane w katalogu rozwiązania. Dodaj następujący element do pliku **Directory. Build. props** w katalogu rozwiązania:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Teraz kompilacje w każdym podkatalogu katalogu zawierającego ten plik będą korzystać z wersji zapoznawczej C# . Aby uzyskać więcej informacji, zobacz artykuł na temat [dostosowywania kompilacji](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>C#dokumentacja wersji języka

W poniższej tabeli przedstawiono wszystkie bieżące C# wersje językowe. Kompilator może niekoniecznie zrozumieć każdą wartość, jeśli jest starszy. Jeśli zainstalujesz program .NET Core 3,0, będziesz mieć dostęp do wszystkich elementów na liście.

|Wartość|Znaczenie|
|------------|-------------|
|Przeglądania|Kompilator akceptuje całą poprawną składnię języka od najnowszej wersji zapoznawczej.|
|Ostatnia|Kompilator akceptuje składnię z najnowszej wydanej wersji kompilatora (w tym wersji pomocniczej).|
|latestMajor|Kompilator akceptuje składnię z najnowszej wydanej wersji głównej kompilatora.|
|8.0|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 8,0 lub niższej.|
|7,3|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,3 lub niższej.|
|7,2|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,2 lub niższej.|
|7,1|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,1 lub niższej.|
|7|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 7,0 lub niższej.|
|6|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 6,0 lub niższej.|
|5|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 5,0 lub niższej.|
|4|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 4,0 lub niższej.|
|3|Kompilator akceptuje tylko składnię, która jest uwzględniona w C# 3,0 lub niższej.|
|ISO-2|Kompilator akceptuje tylko składnię zawartą w ISO/IEC 23270:2006 C# (2,0) |
|ISO-1|Kompilator akceptuje tylko składnię zawartą w ISO/IEC 23270:2003 C# (1.0/1.2) |
