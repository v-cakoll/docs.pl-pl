---
title: Jak MSBuild generuje nazwy plików manifestu
description: Opisuje czynniki wpływające na nazwę pliku manifestu zasobu, który jest generowany przez MSBuild w czasie kompilacji.
ms.date: 05/08/2020
ms.topic: conceptual
ms.openlocfilehash: 383bf6a077b0631e70ddaa4721b20e992127a73c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83232327"
---
# <a name="how-resource-manifest-files-are-named"></a>Jak nazywa się plik manifestu zasobów

Gdy MSBuild kompiluje projekt .NET Core, pliki zasobów XML, które mają rozszerzenie pliku *. resx* , są konwertowane na pliki binarne *. resources* . Pliki binarne są osadzane w danych wyjściowych kompilatora i mogą być odczytywane przez <xref:System.Resources.ResourceManager> . W tym artykule opisano, jak MSBuild wybiera nazwę dla każdego pliku *resources* .

> [!TIP]
> W przypadku jawnego dodania elementu zasobu do pliku projektu, który jest również dołączony do [domyślnej dyrektywy include elementy globalne for .NET Core](../project-sdk/overview.md#default-compilation-includes), zostanie wyświetlony błąd kompilacji. Aby ręcznie uwzględnić pliki zasobów jako `EmbeddedResource` elementy, należy ustawić `EnableDefaultEmbeddedResourceItems` Właściwość na false.

## <a name="default-name"></a>Nazwa domyślna

W przypadku platformy .NET Core 3,0 i nowszych nazwa domyślna manifestu zasobu jest używana w przypadku spełnienia obu następujących warunków:

- Plik zasobów nie jest jawnie zawarty w pliku projektu jako `EmbeddedResource` element z `LogicalName` , `ManifestResourceName` lub `DependentUpon` metadanych.
- `EmbeddedResourceUseDependentUponConvention`Właściwość nie jest ustawiona na `false` w pliku projektu. Domyślnie wartość tej właściwości to `true`. Aby uzyskać więcej informacji, zobacz [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).

Jeśli plik zasobów znajduje się w pliku źródłowym (*. cs* lub *. vb*) o tej samej nazwie pliku głównego, pełna nazwa pierwszego typu zdefiniowanego w pliku źródłowym jest używana jako nazwa pliku manifestu. Na przykład, jeśli `MyNamespace.Form1` jest pierwszym typem zdefiniowanym w *Form1.cs*, a *Form1.cs* jest umieszczony przy użyciu *formularza Form1. resx*, wygenerowana nazwa manifestu dla tego pliku zasobów to "Moja *przestrzeń nazw. Form1. resources*.

## <a name="logicalname-metadata"></a>Metadane logicznename

Jeśli plik zasobów jest jawnie zawarty w pliku projektu jako `EmbeddedResource` element z `LogicalName` metadanymi, `LogicalName` wartość jest używana jako nazwa manifestu. `LogicalName`ma pierwszeństwo przed wszystkimi innymi metadanymi lub ustawieniem.

Na przykład nazwa manifestu dla pliku zasobu, który jest zdefiniowany w poniższym fragmencie kodu projektu, to *częśćname. resources*.

```xml
<EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
```

— lub —

```xml
<EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
```

## <a name="manifestresourcename-metadata"></a>Metadane ManifestResourceName

Jeśli plik zasobów jest jawnie zawarty w pliku projektu jako `EmbeddedResource` element z `ManifestResourceName` metadanymi (i `LogicalName` nieobecny), `ManifestResourceName` wartość, w połączeniu z rozszerzeniem pliku *. resources*, jest używana jako nazwa pliku manifestu.

Na przykład nazwa manifestu dla pliku zasobu, który jest zdefiniowany w poniższym fragmencie kodu projektu, to *częśćname. resources*.

```xml
<EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
```

Nazwa manifestu dla pliku zasobu, który jest zdefiniowany w poniższym fragmencie kodu projektu, to *SomeName.fr-fr. resources*.

```xml
<EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
```

## <a name="dependentupon-metadata"></a>Metadane DependentUpon

Jeśli plik zasobów jest jawnie zawarty w pliku projektu jako `EmbeddedResource` element z `DependentUpon` metadanymi (i `LogicalName` i nie `ManifestResourceName` są obecne), informacje z pliku źródłowego zdefiniowanego przez programu `DependentUpon` są używane dla nazwy pliku manifestu zasobu. W zależności od nazwy pierwszego typu zdefiniowanego w pliku źródłowym jest używana w nazwie manifestu w następujący sposób: *Namespace. ClassName \[ . Culture]. resources*.

Na przykład nazwa manifestu dla pliku zasobu, który jest zdefiniowany w poniższym fragmencie kodu projektu, to *Namespace. ClassName. resources* (gdzie `Namespace.Classname` jest pierwszą klasą, która jest zdefiniowana w *MyTypes.cs*).

```xml
<EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
```

Nazwa manifestu dla pliku zasobu, który jest zdefiniowany w poniższym fragmencie kodu projektu, to *Namespace.ClassName.fr-fr. resources* (gdzie `Namespace.Classname` jest pierwszą klasą zdefiniowaną w *MyTypes.cs*).

```xml
<EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
```

## <a name="embeddedresourceusedependentuponconvention-property"></a>Właściwość EmbeddedResourceUseDependentUponConvention

Jeśli `EmbeddedResourceUseDependentUponConvention` jest ustawiona na `false` w pliku projektu, każda nazwa pliku manifestu zasobu jest oparta na głównej przestrzeni nazw dla projektu i ścieżki względnej z katalogu głównego projektu do pliku *resx* . Dokładniej mówiąc, wygenerowana nazwa pliku manifestu zasobu to *RootNamespace. RelativePathWithDotsForSlashes. \[ Kultura] zasoby*. Jest to również Logika używana do generowania nazw manifestów w wersjach .NET Core wcześniejszych niż 3,0.

> [!NOTE]
>
> - Jeśli `RootNamespace` nie jest zdefiniowana, domyślnie jest to nazwa projektu.
> - Jeśli `LogicalName` `ManifestResourceName` `DependentUpon` dla elementu w pliku projektu określono,, lub metadanych `EmbeddedResource` , ta reguła nazewnictwa nie ma zastosowania do tego pliku zasobów.

## <a name="see-also"></a>Zobacz też

- [Jak działa nazywanie zasobów manifestu](https://gist.github.com/BenVillalobos/041673b9a73bec60fdc3bf0f86fae62a)
- [Właściwości programu MSBuild dla projektów zestaw .NET Core SDK](../project-sdk/msbuild-props.md)
- [Zmiany w programie MSBuild](../compatibility/msbuild.md)
