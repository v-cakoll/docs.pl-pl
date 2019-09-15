---
title: Ustawianie atrybutów zestawu
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: d0809ec3da5a12abe950e63f9665037323a0ab39
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991677"
---
# <a name="set-assembly-attributes"></a>Ustawianie atrybutów zestawu

Atrybuty zestawu są wartościami, które zawierają informacje o zestawie. Atrybuty są podzielone na następujące zestawy informacji:

- Atrybuty tożsamości zestawu

- Atrybuty informacyjne

- Atrybuty manifestu zestawu

- Atrybuty silnej nazwy

## <a name="assembly-identity-attributes"></a>Atrybuty tożsamości zestawu

Trzy atrybuty wraz z silną nazwą (jeśli dotyczy) określają tożsamość zestawu: nazwę, wersję i kulturę. Te atrybuty tworzą pełną nazwę zestawu i są wymagane podczas odwoływania się do zestawu w kodzie. Można użyć atrybutów, aby ustawić wersję i kulturę zestawu. Kompilator lub [konsolidator zestawu (Al. exe)](../../framework/tools/al-exe-assembly-linker.md) ustawia wartość nazwy podczas tworzenia zestawu, na podstawie pliku zawierającego manifest zestawu.

W poniższej tabeli opisano atrybuty wersji i kultury.

|Atrybut tożsamości zestawu|Opis|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|Pole wyliczane wskazujące kulturę obsługiwaną przez zestaw. Zestaw może również określać niezależność kultury, wskazując, że zawiera zasoby dla kultury domyślnej. **Uwaga:**  Środowisko uruchomieniowe traktuje dowolny zestaw, który nie ma atrybutu kultury ustawionego na wartość null jako zestaw satelicki. Takie zestawy podlegają regułom powiązania zestawu satelickiego. Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../framework/deployment/how-the-runtime-locates-assemblies.md).|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Wartość, która ustawia atrybuty zestawu, na przykład czy zestaw może być uruchamiany obok siebie.|
|<xref:System.Reflection.AssemblyVersionAttribute>|Wartość liczbowa w formacie *głównym*. *pomocnicze*. *kompilacja*. *poprawka* (na przykład 2.4.0.0). Środowisko uruchomieniowe języka wspólnego używa tej wartości do wykonywania operacji powiązań w zestawach o silnej nazwie. **Uwaga:**  <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> <xref:System.Reflection.AssemblyVersionAttribute> Jeśli atrybut nie jest stosowany do zestawu, numer wersji określony przez atrybut jest używany przez, i właściwości. <xref:System.Reflection.AssemblyInformationalVersionAttribute>|

Poniższy przykład kodu pokazuje, jak zastosować wersję i atrybuty kultury do zestawu.

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

Można użyć atrybutów informacyjnych w celu podania dodatkowych informacji o firmie lub produkcie dla zestawu. W poniższej tabeli opisano atrybuty informacyjne, które można zastosować do zestawu.

|Atrybut informacyjny|Opis|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Wartość ciągu określająca nazwę firmy.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Wartość ciągu określająca informacje o prawach autorskich.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Wartość ciągu określająca numer wersji pliku Win32. Zwykle jest to domyślna wersja zestawu.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Wartość ciągu określająca informacje o wersji, które nie są używane przez środowisko uruchomieniowe języka wspólnego, takie jak pełny numer wersji produktu. **Uwaga:**  Jeśli ten atrybut jest stosowany do zestawu, ciąg, który określa, można uzyskać w czasie wykonywania przy użyciu <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> właściwości. Ten ciąg jest również używany w ścieżce i klucz rejestru dostarczonych przez <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> właściwości.|
|<xref:System.Reflection.AssemblyProductAttribute>|Wartość ciągu określająca informacje o produkcie.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Wartość ciągu określająca informacje o znakach towarowych.|

Te atrybuty mogą być wyświetlane na stronie właściwości systemu Windows zestawu lub można je zastąpić przy użyciu opcji kompilatora **/win32res** , aby określić własny plik zasobów Win32.

## <a name="assembly-manifest-attributes"></a>Atrybuty manifestu zestawu

Można użyć atrybutów manifestu zestawu, aby podać informacje w manifeście zestawu, w tym tytuł, opis, alias domyślny i konfigurację. W poniższej tabeli opisano atrybuty manifestu zestawu.

|Atrybut manifestu zestawu|Opis|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Wartość ciągu określająca konfigurację zestawu, na przykład detaliczną lub debug. Środowisko uruchomieniowe nie używa tej wartości.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Wartość ciągu określająca domyślny alias, który będzie używany przez odwołania do zestawów. Ta wartość zapewnia przyjazną nazwę, gdy nazwa samego zestawu nie jest przyjazna (na przykład wartość identyfikatora GUID). Ta wartość może być również używana jako krótka forma pełnej nazwy zestawu.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Wartość ciągu określająca Krótki opis, który podsumowuje charakter i cel zestawu.|
|<xref:System.Reflection.AssemblyTitleAttribute>|Wartość ciągu określająca przyjazną nazwę zestawu. Na przykład zestaw o nazwie *comdlg* może mieć tytuł Microsoft Common Dialogs Control.|

## <a name="strong-name-attributes"></a>Atrybuty silnej nazwy

Aby ustawić silną nazwę zestawu, można użyć atrybutów silnej nazwy. W poniższej tabeli opisano atrybuty silnej nazwy.

|Atrybut silnej nazwy|Opis|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|Wartość logiczna wskazująca, że jest używane podpisywanie opóźnienia.|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|Wartość ciągu wskazująca nazwę pliku, który zawiera klucz publiczny (w przypadku korzystania z opóźnienia podpisywania) lub klucze publiczny i prywatny przekazanie jako parametr do konstruktora tego atrybutu. Należy pamiętać, że nazwa pliku jest względna w stosunku do ścieżki pliku wyjściowego ( *. exe* lub *. dll*), a nie ścieżki pliku źródłowego.|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|Wskazuje kontener kluczy, który zawiera parę kluczy przekazaną jako parametr do konstruktora tego atrybutu.|

Poniższy przykład kodu pokazuje atrybuty do zastosowania podczas korzystania z opóźnienia podpisywania w celu utworzenia zestawu o silnej nazwie z plikiem klucza publicznego o nazwie *klucze. snk*.

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

## <a name="see-also"></a>Zobacz także

- [Tworzenie zestawów](create.md)
- [Program z zestawami](program.md)
