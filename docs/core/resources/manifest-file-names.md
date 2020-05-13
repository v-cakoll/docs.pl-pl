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
# <a name="how-resource-manifest-files-are-named"></a><span data-ttu-id="5c253-103">Jak nazywa się plik manifestu zasobów</span><span class="sxs-lookup"><span data-stu-id="5c253-103">How resource manifest files are named</span></span>

<span data-ttu-id="5c253-104">Gdy MSBuild kompiluje projekt .NET Core, pliki zasobów XML, które mają rozszerzenie pliku *. resx* , są konwertowane na pliki binarne *. resources* .</span><span class="sxs-lookup"><span data-stu-id="5c253-104">When MSBuild compiles a .NET Core project, XML resource files, which have the *.resx* file extension, are converted into binary *.resources* files.</span></span> <span data-ttu-id="5c253-105">Pliki binarne są osadzane w danych wyjściowych kompilatora i mogą być odczytywane przez <xref:System.Resources.ResourceManager> .</span><span class="sxs-lookup"><span data-stu-id="5c253-105">The binary files are embedded into the output of the compiler and can be read by the <xref:System.Resources.ResourceManager>.</span></span> <span data-ttu-id="5c253-106">W tym artykule opisano, jak MSBuild wybiera nazwę dla każdego pliku *resources* .</span><span class="sxs-lookup"><span data-stu-id="5c253-106">This article describes how MSBuild chooses a name for each *.resources* file.</span></span>

> [!TIP]
> <span data-ttu-id="5c253-107">W przypadku jawnego dodania elementu zasobu do pliku projektu, który jest również dołączony do [domyślnej dyrektywy include elementy globalne for .NET Core](../project-sdk/overview.md#default-compilation-includes), zostanie wyświetlony błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5c253-107">If you explicitly add a resource item to your project file, and it's also [included with the default include globs for .NET Core](../project-sdk/overview.md#default-compilation-includes), you will get a build error.</span></span> <span data-ttu-id="5c253-108">Aby ręcznie uwzględnić pliki zasobów jako `EmbeddedResource` elementy, należy ustawić `EnableDefaultEmbeddedResourceItems` Właściwość na false.</span><span class="sxs-lookup"><span data-stu-id="5c253-108">To manually include resource files as `EmbeddedResource` items, set the `EnableDefaultEmbeddedResourceItems` property to false.</span></span>

## <a name="default-name"></a><span data-ttu-id="5c253-109">Nazwa domyślna</span><span class="sxs-lookup"><span data-stu-id="5c253-109">Default name</span></span>

<span data-ttu-id="5c253-110">W przypadku platformy .NET Core 3,0 i nowszych nazwa domyślna manifestu zasobu jest używana w przypadku spełnienia obu następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="5c253-110">In .NET Core 3.0 and later, the default name for a resource manifest is used when both of the following conditions are met:</span></span>

- <span data-ttu-id="5c253-111">Plik zasobów nie jest jawnie zawarty w pliku projektu jako `EmbeddedResource` element z `LogicalName` , `ManifestResourceName` lub `DependentUpon` metadanych.</span><span class="sxs-lookup"><span data-stu-id="5c253-111">The resource file is not explicitly included in the project file as an `EmbeddedResource` item with `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata.</span></span>
- <span data-ttu-id="5c253-112">`EmbeddedResourceUseDependentUponConvention`Właściwość nie jest ustawiona na `false` w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="5c253-112">The `EmbeddedResourceUseDependentUponConvention` property is not set to `false` in the project file.</span></span> <span data-ttu-id="5c253-113">Domyślnie wartość tej właściwości to `true`.</span><span class="sxs-lookup"><span data-stu-id="5c253-113">By default, this property is set to `true`.</span></span> <span data-ttu-id="5c253-114">Aby uzyskać więcej informacji, zobacz [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).</span><span class="sxs-lookup"><span data-stu-id="5c253-114">For more information, see [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).</span></span>

<span data-ttu-id="5c253-115">Jeśli plik zasobów znajduje się w pliku źródłowym (*. cs* lub *. vb*) o tej samej nazwie pliku głównego, pełna nazwa pierwszego typu zdefiniowanego w pliku źródłowym jest używana jako nazwa pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="5c253-115">If the resource file is colocated with a source file (*.cs* or *.vb*) of the same root file name, the full name of the first type that's defined in the source file is used for the manifest file name.</span></span> <span data-ttu-id="5c253-116">Na przykład, jeśli `MyNamespace.Form1` jest pierwszym typem zdefiniowanym w *Form1.cs*, a *Form1.cs* jest umieszczony przy użyciu *formularza Form1. resx*, wygenerowana nazwa manifestu dla tego pliku zasobów to "Moja *przestrzeń nazw. Form1. resources*.</span><span class="sxs-lookup"><span data-stu-id="5c253-116">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, and *Form1.cs* is colocated with *Form1.resx*, the generated manifest name for that resource file is *MyNamespace.Form1.resources*.</span></span>

## <a name="logicalname-metadata"></a><span data-ttu-id="5c253-117">Metadane logicznename</span><span class="sxs-lookup"><span data-stu-id="5c253-117">LogicalName metadata</span></span>

<span data-ttu-id="5c253-118">Jeśli plik zasobów jest jawnie zawarty w pliku projektu jako `EmbeddedResource` element z `LogicalName` metadanymi, `LogicalName` wartość jest używana jako nazwa manifestu.</span><span class="sxs-lookup"><span data-stu-id="5c253-118">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `LogicalName` metadata, the `LogicalName` value is used as the manifest name.</span></span> <span data-ttu-id="5c253-119">`LogicalName`ma pierwszeństwo przed wszystkimi innymi metadanymi lub ustawieniem.</span><span class="sxs-lookup"><span data-stu-id="5c253-119">`LogicalName` takes precedence over any other metadata or setting.</span></span>

<span data-ttu-id="5c253-120">Na przykład nazwa manifestu dla pliku zasobu, który jest zdefiniowany w poniższym fragmencie kodu projektu, to *częśćname. resources*.</span><span class="sxs-lookup"><span data-stu-id="5c253-120">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
```

<span data-ttu-id="5c253-121">— lub —</span><span class="sxs-lookup"><span data-stu-id="5c253-121">-or-</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
```

## <a name="manifestresourcename-metadata"></a><span data-ttu-id="5c253-122">Metadane ManifestResourceName</span><span class="sxs-lookup"><span data-stu-id="5c253-122">ManifestResourceName metadata</span></span>

<span data-ttu-id="5c253-123">Jeśli plik zasobów jest jawnie zawarty w pliku projektu jako `EmbeddedResource` element z `ManifestResourceName` metadanymi (i `LogicalName` nieobecny), `ManifestResourceName` wartość, w połączeniu z rozszerzeniem pliku *. resources*, jest używana jako nazwa pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="5c253-123">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `ManifestResourceName` metadata (and `LogicalName` is absent), the `ManifestResourceName` value, combined with the file extension *.resources*, is used as the manifest file name.</span></span>

<span data-ttu-id="5c253-124">Na przykład nazwa manifestu dla pliku zasobu, który jest zdefiniowany w poniższym fragmencie kodu projektu, to *częśćname. resources*.</span><span class="sxs-lookup"><span data-stu-id="5c253-124">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
```

<span data-ttu-id="5c253-125">Nazwa manifestu dla pliku zasobu, który jest zdefiniowany w poniższym fragmencie kodu projektu, to *SomeName.fr-fr. resources*.</span><span class="sxs-lookup"><span data-stu-id="5c253-125">The manifest name for the resource file that's defined in the following project file snippet is *SomeName.fr-FR.resources*.</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
```

## <a name="dependentupon-metadata"></a><span data-ttu-id="5c253-126">Metadane DependentUpon</span><span class="sxs-lookup"><span data-stu-id="5c253-126">DependentUpon metadata</span></span>

<span data-ttu-id="5c253-127">Jeśli plik zasobów jest jawnie zawarty w pliku projektu jako `EmbeddedResource` element z `DependentUpon` metadanymi (i `LogicalName` i nie `ManifestResourceName` są obecne), informacje z pliku źródłowego zdefiniowanego przez programu `DependentUpon` są używane dla nazwy pliku manifestu zasobu.</span><span class="sxs-lookup"><span data-stu-id="5c253-127">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `DependentUpon` metadata (and `LogicalName` and `ManifestResourceName` are absent), information from the source file defined by `DependentUpon` is used for the resource manifest file name.</span></span> <span data-ttu-id="5c253-128">W zależności od nazwy pierwszego typu zdefiniowanego w pliku źródłowym jest używana w nazwie manifestu w następujący sposób: *Namespace. ClassName \[ . Culture]. resources*.</span><span class="sxs-lookup"><span data-stu-id="5c253-128">Specifically, the name of the first type that's defined in the source file is used in the manifest name as follows: *Namespace.Classname\[.Culture].resources*.</span></span>

<span data-ttu-id="5c253-129">Na przykład nazwa manifestu dla pliku zasobu, który jest zdefiniowany w poniższym fragmencie kodu projektu, to *Namespace. ClassName. resources* (gdzie `Namespace.Classname` jest pierwszą klasą, która jest zdefiniowana w *MyTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="5c253-129">For example, the manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
```

<span data-ttu-id="5c253-130">Nazwa manifestu dla pliku zasobu, który jest zdefiniowany w poniższym fragmencie kodu projektu, to *Namespace.ClassName.fr-fr. resources* (gdzie `Namespace.Classname` jest pierwszą klasą zdefiniowaną w *MyTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="5c253-130">The manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
```

## <a name="embeddedresourceusedependentuponconvention-property"></a><span data-ttu-id="5c253-131">Właściwość EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="5c253-131">EmbeddedResourceUseDependentUponConvention property</span></span>

<span data-ttu-id="5c253-132">Jeśli `EmbeddedResourceUseDependentUponConvention` jest ustawiona na `false` w pliku projektu, każda nazwa pliku manifestu zasobu jest oparta na głównej przestrzeni nazw dla projektu i ścieżki względnej z katalogu głównego projektu do pliku *resx* .</span><span class="sxs-lookup"><span data-stu-id="5c253-132">If `EmbeddedResourceUseDependentUponConvention` is set to `false` in the project file, each resource manifest file name is based off the root namespace for the project and the relative path from the project root to the *.resx* file.</span></span> <span data-ttu-id="5c253-133">Dokładniej mówiąc, wygenerowana nazwa pliku manifestu zasobu to *RootNamespace. RelativePathWithDotsForSlashes. \[ Kultura] zasoby*.</span><span class="sxs-lookup"><span data-stu-id="5c253-133">More specifically, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="5c253-134">Jest to również Logika używana do generowania nazw manifestów w wersjach .NET Core wcześniejszych niż 3,0.</span><span class="sxs-lookup"><span data-stu-id="5c253-134">This is also the logic used to generate manifest names in .NET Core versions prior to 3.0.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="5c253-135">Jeśli `RootNamespace` nie jest zdefiniowana, domyślnie jest to nazwa projektu.</span><span class="sxs-lookup"><span data-stu-id="5c253-135">If `RootNamespace` is not defined, it defaults to the project name.</span></span>
> - <span data-ttu-id="5c253-136">Jeśli `LogicalName` `ManifestResourceName` `DependentUpon` dla elementu w pliku projektu określono,, lub metadanych `EmbeddedResource` , ta reguła nazewnictwa nie ma zastosowania do tego pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="5c253-136">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item in the project file, this naming rule does not apply to that resource file.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c253-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c253-137">See also</span></span>

- [<span data-ttu-id="5c253-138">Jak działa nazywanie zasobów manifestu</span><span class="sxs-lookup"><span data-stu-id="5c253-138">How Manifest Resource Naming Works</span></span>](https://gist.github.com/BenVillalobos/041673b9a73bec60fdc3bf0f86fae62a)
- [<span data-ttu-id="5c253-139">Właściwości programu MSBuild dla projektów zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="5c253-139">MSBuild properties for .NET Core SDK projects</span></span>](../project-sdk/msbuild-props.md)
- [<span data-ttu-id="5c253-140">Zmiany w programie MSBuild</span><span class="sxs-lookup"><span data-stu-id="5c253-140">MSBuild breaking changes</span></span>](../compatibility/msbuild.md)
