---
title: Ustawianie atrybutów zestawu
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 0e4e2e595ed4f95511bd23ab0ed00139f71b2c8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740475"
---
# <a name="set-assembly-attributes"></a>Ustawianie atrybutów zestawu

Atrybuty zestawu są wartościami, które dostarczają informacji o zestawie. Atrybuty są podzielone na następujące zestawy informacji:

- Atrybuty tożsamości zestawu

- Atrybuty informacyjne

- Atrybuty manifestu zestawu

- Atrybuty silnej nazwy

## <a name="assembly-identity-attributes"></a>Atrybuty tożsamości zestawu

Trzy atrybuty, wraz z silną nazwą (jeśli dotyczy), określają tożsamość zestawu: nazwa, wersja i kultura. Atrybuty te tworzą pełną nazwę zestawu i są wymagane podczas odwoływania się do zestawu w kodzie. Atrybuty służy do ustawiania wersji zestawu i kultury. Kompilator lub [konsolidator zestawu (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) ustawia wartość nazwy podczas tworzenia zestawu, na podstawie pliku zawierającego manifest zestawu.

W poniższej tabeli opisano atrybuty wersji i kultury.

|Atrybut tożsamości zestawu|Opis|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|Pole wyliczone wskazujące kulturę, która obsługuje zestaw. Zestaw można również określić niezależność kultury, wskazując, że zawiera zasoby dla kultury domyślnej. **Uwaga:**  Czas wykonywania traktuje każdy zestaw, który nie ma atrybutkultury ustawiony na null jako zestawu satelickiego. Takie zestawy podlegają regułom wiązania zestawu satelitarnego. Aby uzyskać więcej informacji, zobacz [Jak program runtime lokalizuje zestawy](../../framework/deployment/how-the-runtime-locates-assemblies.md).|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Wartość, która ustawia atrybuty złożenia, takie jak czy zestaw może być uruchamiany obok siebie.|
|<xref:System.Reflection.AssemblyVersionAttribute>|Wartość liczbowa w formacie *głównym*. *drobne*. *budować*. *(na* przykład 2.4.0.0). Czas wykonywania języka wspólnego używa tej wartości do wykonywania operacji wiązania w zestawach o silnej nazwie. **Uwaga:**  Jeśli <xref:System.Reflection.AssemblyInformationalVersionAttribute> atrybut nie jest stosowany do złożenia, numer wersji <xref:System.Reflection.AssemblyVersionAttribute> określony przez <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>atrybut <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>jest <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> używany przez , , i właściwości.|

W poniższym przykładzie kodu pokazano, jak zastosować atrybuty wersji i kultury do zestawu.

```cpp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")];
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")];
```

```csharp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")]
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")]
```

```vb
' Set version number for the assembly.
<Assembly:AssemblyVersionAttribute("4.3.2.1")>
' Set culture as German.
<Assembly:AssemblyCultureAttribute("de")>
```

## <a name="informational-attributes"></a>Atrybuty informacyjne

Atrybutów informacyjnych można użyć do podania dodatkowych informacji o firmie lub produkcie dla zestawu. W poniższej tabeli opisano atrybuty informacyjne, które można zastosować do zestawu.

|Atrybut informacyjny|Opis|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Wartość ciągu określająca nazwę firmy.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Wartość ciągu określająca informacje o prawach autorskich.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Wartość ciągu określająca numer wersji pliku Win32. Jest to zwykle domyślnie do wersji zestawu.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Wartość ciągu określająca informacje o wersji, które nie są używane przez czas wykonywania języka wspólnego, takie jak pełny numer wersji produktu. **Uwaga:**  Jeśli ten atrybut jest stosowany do zestawu, ciąg określa można uzyskać w <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> czasie wykonywania przy użyciu właściwości. Ciąg jest również używany w ścieżce i <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> kluczrejestru dostarczonych przez i właściwości.|
|<xref:System.Reflection.AssemblyProductAttribute>|Wartość ciągu określająca informacje o produkcie.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Wartość ciągu określająca informacje o znaku towarowym.|

Te atrybuty mogą być wyświetlane na stronie Właściwości systemu Windows zestawu lub mogą być zastąpione przy użyciu opcji kompilatora **/win32res,** aby określić własny plik zasobu Win32.

## <a name="assembly-manifest-attributes"></a>Atrybuty manifestu zestawu

Atrybutów manifestu zestawu można użyć do dostarczenia informacji w manifeście zestawu, w tym tytułu, opisu, domyślnego aliasu i konfiguracji. W poniższej tabeli opisano atrybuty manifestu zestawu.

|Atrybut manifestu zestawu|Opis|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Wartość ciągu wskazująca konfigurację zestawu, na przykład Retail lub Debug. Program runtime nie używa tej wartości.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Wartość ciągu określająca alias domyślny, który ma być używany przez odwoływanie się do zestawów. Ta wartość zapewnia przyjazną nazwę, gdy nazwa samego zestawu nie jest przyjazny (na przykład wartość guid). Ta wartość może być również używana jako krótka forma pełnej nazwy zestawu.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Wartość ciągu określająca krótki opis, który podsumowuje charakter i cel zestawu.|
|<xref:System.Reflection.AssemblyTitleAttribute>|Wartość ciągu określająca przyjazną nazwę zestawu. Na przykład zestaw o nazwie *comdlg* może mieć tytuł Microsoft Common Dialog Control.|

## <a name="strong-name-attributes"></a>Atrybuty silnej nazwy

Atrybuty silnej nazwy można użyć, aby ustawić silną nazwę dla zestawu. W poniższej tabeli opisano atrybuty silnej nazwy.

|Atrybut silnej nazwy|Opis|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|Wartość logiczna wskazująca, że używane jest podpisywanie opóźnienia.|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|Wartość ciągu wskazująca nazwę pliku, który zawiera klucz publiczny (jeśli używasz podpisywania opóźnienia) lub klucze publiczne i prywatne przekazywane jako parametr do konstruktora tego atrybutu. Należy zauważyć, że nazwa pliku jest względem ścieżki pliku wyjściowego *(exe* lub *.dll),* a nie ścieżki pliku źródłowego.|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|Wskazuje kontener kluczy, który zawiera parę kluczy przekazany jako parametr do konstruktora tego atrybutu.|

Poniższy przykład kodu pokazuje atrybuty, które należy zastosować podczas podpisywania opóźnienia w celu utworzenia zestawu o silnej nazwie z plikiem klucza publicznego o nazwie *myKey.snk*.

```cpp
[assembly:AssemblyKeyFileAttribute("myKey.snk")];
[assembly:AssemblyDelaySignAttribute(true)];
```

```csharp
[assembly:AssemblyKeyFileAttribute("myKey.snk")]
[assembly:AssemblyDelaySignAttribute(true)]
```

```vb
<Assembly:AssemblyKeyFileAttribute("myKey.snk")>
<Assembly:AssemblyDelaySignAttribute(True)>
```

## <a name="see-also"></a>Zobacz też

- [Tworzenie zestawów](create.md)
