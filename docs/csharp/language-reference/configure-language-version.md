---
title: C#przechowywanie wersji języka — C# przewodnik
description: Dowiedz się więcej o tym, jak C# wersja językowa jest określana na podstawie projektu i różne wartości możesz ręcznie dostosować go do.
ms.date: 07/10/2019
ms.openlocfilehash: e35fdf2bcdb1a31b752c760f3f6df59232e498a4
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236093"
---
# <a name="c-language-versioning"></a>C#przechowywanie wersji języka

C# Kompilator określa domyślną wersję języka na podstawie platformy docelowej projektu lub struktury. Jest to spowodowane C# język może mieć funkcje, które zależą od typów lub składniki środowiska uruchomieniowego, które nie są dostępne w każdej implementacji .NET. Dzięki temu, niezależnie od docelowego, projekt został skompilowany przed uzyskasz najwyższa wersja zgodna język domyślny.

## <a name="defaults"></a>Wartość domyślna

Kompilator Określa domyślny na podstawie tych reguł:

|Platforma docelowa|version|C#Domyślna wersja języka|
|----------------|-------|---------------------------|
|.NET Core|3.x|C#8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|wszystkie|C# 7.3|
|.NET Framework|wszystkie|C# 7.3|

## <a name="default-for-previews"></a>Domyślne dla wersji zapoznawczych

Jeśli projekt jest przeznaczony dla framework w wersji zapoznawczej, która jest odpowiednia wersja językowa (wersja zapoznawcza), wersja językowa, używana jest wersja językowa (wersja zapoznawcza). Gwarantuje to, czy można użyć najnowsze funkcje, które mogą pracować w dowolnym środowisku w tej wersji zapoznawczej bez wywierania wpływu na swoje projekty przeznaczone wydanej wersji platformy .NET Core.

## <a name="overriding-a-default"></a>Zastępowanie domyślnego

Jeśli trzeba określić swoje C# wersji jawnie, możesz to zrobić na kilka sposobów:

- Ręcznie Edytuj swoje [pliku projektu](#edit-the-project-file).
- Ustawianie wersji języka [dla wielu projektów w podkatalogu](#configure-multiple-projects).
- Konfigurowanie [ `-langversion` — opcja kompilatora](compiler-options/langversion-compiler-option.md)

### <a name="edit-the-project-file"></a>Edytuj plik projektu

Wersja językowa można ustawić w pliku projektu. Na przykład jeżeli chcesz jawnie dostęp do funkcji w wersji zapoznawczej, można dodać elementu następująco:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Wartość `preview` najnowsza wersja zapoznawcza C# język, który kompilator obsługuje.

### <a name="configure-multiple-projects"></a>Konfigurowanie wielu projektów

Możesz utworzyć **Directory.Build.props** pliku, który zawiera `<LangVersion>` element, aby skonfigurować wiele katalogów. Należy zwykle to zrobić w katalogu rozwiązania. Dodaj następujące polecenie, aby **Directory.Build.props** pliku w katalogu rozwiązania:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Teraz kompilacje w każdym podkatalogu katalogu zawierającego ten plik będzie używać wersji zapoznawczej C# wersji. Aby uzyskać więcej informacji, zobacz artykuł [Dostosowywanie kompilacji](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>C#Dokumentacja wersji języka

W poniższej tabeli przedstawiono wszystkie bieżące C# wersji językowych. Kompilator nie może zawsze zrozumieć każda wartość, jeżeli jest starszy. Po zainstalowaniu programu .NET Core 3.0, będą mieć dostęp do wszystkiego, na liście.

|Wartość|Znaczenie|
|------------|-------------|
|wersja zapoznawcza|Kompilator akceptuje wszystkie składni języka prawidłowy z najnowszej wersji zapoznawczej.|
|najnowsza|Kompilator akceptuje składni z najnowszej wersji, kompilator (w tym wersja pomocnicza).|
|latestMajor|Kompilator akceptuje składnię najnowszej głównej wersji kompilatora.|
|8.0|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 8.0 lub niższą.|
|7.3|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 7.3 lub niższy.|
|7.2|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 7.2 lub niższy.|
|7.1|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 7.1 lub niższą.|
|7|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 7.0 lub niższą.|
|6|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 6.0 lub niższą.|
|5|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 5.0 lub niższą.|
|4|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 4.0 lub niższą.|
|3|Kompilator akceptuje tylko w przypadku składni, która znajduje się w C# 3.0 lub niższą.|
|ISO-2|Kompilator akceptuje tylko w przypadku składni, która znajduje się w 23270:2006 ISO/IEC C# (2.0) |
|ISO-1|Kompilator akceptuje tylko w przypadku składni, która znajduje się w 23270:2003 ISO/IEC C# (1.0/1.2) |
