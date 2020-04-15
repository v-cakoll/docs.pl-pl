---
title: 'Atrybuty zastrzeżone języka C#: atrybuty globalne'
ms.date: 04/09/2020
description: Atrybuty zapewniają metadane używane przez kompilator do zrozumienia większej semantyki programu
ms.openlocfilehash: f855f32cd7349da34ffbd20fededdf42c3023938
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389857"
---
# <a name="reserved-attributes-assembly-level-attributes"></a>Atrybuty zarezerwowane: atrybuty poziomu złożenia

Większość atrybutów są stosowane do określonych elementów języka, takich jak klasy lub metody; jednak niektóre atrybuty są globalne — mają zastosowanie do całego zestawu lub modułu. Na przykład <xref:System.Reflection.AssemblyVersionAttribute> atrybut może służyć do osadzania informacji o wersji do zestawu, w tym:

```csharp
[assembly: AssemblyVersion("1.0.0.0")]
```

Atrybuty globalne pojawiają się w `using` kodzie źródłowym po wszystkich dyrektyw najwyższego poziomu i przed wszelkiego typu, modułu lub deklaracji obszaru nazw. Atrybuty globalne mogą pojawiać się w wielu plikach źródłowych, ale pliki muszą być kompilowane w jednym przebiegu kompilacji. Program Visual Studio dodaje atrybuty globalne do pliku AssemblyInfo.cs w projektach programu .NET Framework. Te atrybuty nie są dodawane do projektów .NET Core.

Atrybuty zestawu są wartościami, które dostarczają informacji o zestawie. Należą one do następujących kategorii:

- Atrybuty tożsamości zestawu
- Atrybuty informacyjne
- Atrybuty manifestu zestawu

## <a name="assembly-identity-attributes"></a>Atrybuty tożsamości zestawu

Trzy atrybuty (o silnej nazwie, jeśli dotyczy) określają tożsamość zestawu: nazwa, wersja i kultura. Te atrybuty tworzą pełną nazwę zestawu i są wymagane, gdy odwołujesz się do niego w kodzie. Można ustawić wersję zestawu i kultury przy użyciu atrybutów. Jednak wartość nazwy jest ustawiana przez kompilator, IDE programu Visual Studio w [oknie dialogowym informacje o zestawie](/visualstudio/ide/reference/assembly-information-dialog-box)lub konsolidator zestawu (Al.exe) podczas tworzenia zestawu. Nazwa zestawu jest oparta na manifeście zestawu. Atrybut <xref:System.Reflection.AssemblyFlagsAttribute> określa, czy wiele kopii zestawu może współistnieć.

W poniższej tabeli przedstawiono atrybuty tożsamości.

|Atrybut|Przeznaczenie|
|---------------|-------------|
|<xref:System.Reflection.AssemblyVersionAttribute>|Określa wersję złożenia.|
|<xref:System.Reflection.AssemblyCultureAttribute>|Określa, która kultura obsługuje zestaw.|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Określa, czy zestaw obsługuje wykonywanie side-by-side na tym samym komputerze, w tym samym procesie lub w tej samej domenie aplikacji.|

## <a name="informational-attributes"></a>Atrybuty informacyjne

Atrybuty informacyjne są używane do dostarczania dodatkowych informacji o firmie lub produkcie dla zestawu. W poniższej tabeli przedstawiono <xref:System.Reflection?displayProperty=nameWithType> atrybuty informacyjne zdefiniowane w obszarze nazw.

|Atrybut|Przeznaczenie|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|Określa nazwę produktu manifestu złożenia.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Określa znak towarowy dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Określa wersję informacyjną manifestu zestawu.|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Określa nazwę firmy dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Definiuje atrybut niestandardowy, który określa prawa autorskie do manifestu zestawu.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Ustawia określony numer wersji zasobu wersji pliku Win32.|
|<xref:System.CLSCompliantAttribute>|Wskazuje, czy zestaw jest zgodny ze specyfikacją języka wspólnego (CLS).|

## <a name="assembly-manifest-attributes"></a>Atrybuty manifestu zestawu

Można użyć atrybutów manifestu zestawu, aby podać informacje w manifeście zestawu. Atrybuty obejmują tytuł, opis, alias domyślny i konfigurację. W poniższej tabeli przedstawiono <xref:System.Reflection?displayProperty=nameWithType> atrybuty manifestu zestawu zdefiniowane w obszarze nazw.

|Atrybut|Przeznaczenie|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|Określa tytuł złożenia manifestu złożenia.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Określa opis zestawu dla manifestu złożenia.|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Określa konfigurację zestawu (na przykład sprzedaży detalicznej lub debugowania) dla manifestu zestawu.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Definiuje przyjazny alias domyślny dla manifestu złożenia|
