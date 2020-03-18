---
ms.openlocfilehash: 16ee73bfc0ab33b04ea3e2fa6d0eec521a9b8634
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968139"
---
### <a name="resource-manifest-file-names"></a><span data-ttu-id="d3c44-101">Nazwy plików manifestu zasobów</span><span class="sxs-lookup"><span data-stu-id="d3c44-101">Resource manifest file names</span></span>

<span data-ttu-id="d3c44-102">Począwszy od .NET Core 3.0, nazwa pliku manifestu wygenerowanego zasobu została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="d3c44-102">Starting in .NET Core 3.0, the generated resource manifest file name has changed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d3c44-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="d3c44-103">Version introduced</span></span>

<span data-ttu-id="d3c44-104">3.0</span><span class="sxs-lookup"><span data-stu-id="d3c44-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="d3c44-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="d3c44-105">Change description</span></span>

<span data-ttu-id="d3c44-106">Przed .NET Core 3.0, gdy w pliku projektu MSBuild ustawiono metadane [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) dla pliku zasobu *(.resx),* wygenerowaną nazwą manifestu była *namespace.Classname.resources*.</span><span class="sxs-lookup"><span data-stu-id="d3c44-106">Prior to .NET Core 3.0, when [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadata was set for a resource (*.resx*) file in the MSBuild project file, the generated manifest name was *Namespace.Classname.resources*.</span></span> <span data-ttu-id="d3c44-107">Gdy nie ustawiono [dependentUpon,](/visualstudio/msbuild/common-msbuild-project-items#compile) wygenerowaną nazwą manifestu był *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span><span class="sxs-lookup"><span data-stu-id="d3c44-107">When [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) was not set, the generated manifest name was *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span></span>

<span data-ttu-id="d3c44-108">Począwszy od .NET Core 3.0, gdy plik *.resx* jest współlokowane z plikiem źródłowym o tej samej nazwie, na przykład w aplikacjach Formularzy systemu Windows, nazwa manifestu zasobu jest generowany na podstawie pełnej nazwy pierwszego typu w pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="d3c44-108">Starting in .NET Core 3.0, when a *.resx* file is colocated with a source file of the same name, for example, in Windows Forms apps, the resource manifest name is generated from the full name of the first type in the source file.</span></span> <span data-ttu-id="d3c44-109">Na przykład jeśli *Type.cs* jest zlokalizowany z *Type.resx*, wygenerowana nazwa manifestu to *Namespace.Classname.resources*.</span><span class="sxs-lookup"><span data-stu-id="d3c44-109">For example, if *Type.cs* is colocated with *Type.resx*, the generated manifest name is *Namespace.Classname.resources*.</span></span> <span data-ttu-id="d3c44-110">Jeśli jednak zmodyfikujesz którykolwiek `EmbeddedResource` z atrybutów właściwości pliku *.resx,* wygenerowana nazwa pliku manifestu może być inna:</span><span class="sxs-lookup"><span data-stu-id="d3c44-110">However, if you modify any of the attributes on the `EmbeddedResource` property for the *.resx* file, the generated manifest file name may be different:</span></span>

- <span data-ttu-id="d3c44-111">Jeśli `LogicalName` atrybut we `EmbeddedResource` właściwości jest ustawiony, ta wartość jest używana jako nazwa pliku manifestu zasobu.</span><span class="sxs-lookup"><span data-stu-id="d3c44-111">If the `LogicalName` attribute on the `EmbeddedResource` property is set, that value is used as the resource manifest file name.</span></span>

  <span data-ttu-id="d3c44-112">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="d3c44-112">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  <span data-ttu-id="d3c44-113">**Nazwa pliku manifestu wygenerowanego zasobu**: *SomeName.resources* (niezależnie od nazwy pliku *.resx* lub kultury lub innych metadanych).</span><span class="sxs-lookup"><span data-stu-id="d3c44-113">**Generated resource manifest file name**: *SomeName.resources* (regardless of the *.resx* file name or culture or any other metadata).</span></span>

- <span data-ttu-id="d3c44-114">Jeśli `LogicalName` nie jest ustawiona, `ManifestResourceName` ale `EmbeddedResource` atrybut we właściwości jest ustawiona, jego wartość, w połączeniu z rozszerzeniem pliku *.resources*, jest używany jako nazwa pliku manifestu zasobu.</span><span class="sxs-lookup"><span data-stu-id="d3c44-114">If `LogicalName` is not set, but the `ManifestResourceName` attribute on the `EmbeddedResource` property is set, its value, combined with the file extension *.resources*, is used as the resource manifest file name.</span></span>

  <span data-ttu-id="d3c44-115">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="d3c44-115">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  <span data-ttu-id="d3c44-116">**Nazwa pliku manifestu wygenerowanego zasobu:** *SomeName.resources* lub *SomeName.fr-FR.resources*.</span><span class="sxs-lookup"><span data-stu-id="d3c44-116">**Generated resource manifest file name**: *SomeName.resources* or *SomeName.fr-FR.resources*.</span></span>

- <span data-ttu-id="d3c44-117">Jeśli poprzednie reguły nie mają zastosowania, `DependentUpon` a `EmbeddedResource` atrybut elementu jest ustawiony na plik źródłowy, nazwa typu pierwszej klasy w pliku źródłowym jest używana w nazwie pliku manifestu zasobu.</span><span class="sxs-lookup"><span data-stu-id="d3c44-117">If the previous rules don't apply, and the `DependentUpon` attribute on the `EmbeddedResource` element is set to a source file, the type name of the first class in the source file is used in the resource manifest file name.</span></span> <span data-ttu-id="d3c44-118">Dokładniej, wygenerowana nazwa pliku to *\[Namespace.Classname . Kultura].zasoby*.</span><span class="sxs-lookup"><span data-stu-id="d3c44-118">More specifically, the generated file name is *Namespace.Classname\[.Culture].resources*.</span></span>

  <span data-ttu-id="d3c44-119">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="d3c44-119">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  <span data-ttu-id="d3c44-120">**Nazwa pliku manifestu wygenerowanego zasobu**: *Namespace.Classname.resources* lub *Namespace.Classname.fr-FR.resources* (gdzie `Namespace.Classname` jest nazwą pierwszej klasy w *MyTypes.cs).*</span><span class="sxs-lookup"><span data-stu-id="d3c44-120">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="d3c44-121">Jeśli poprzednie reguły nie mają `EmbeddedResourceUseDependentUponConvention` `true` zastosowania, jest (domyślnie dla .NET Core) i istnieje plik źródłowy colocated z plikiem *.resx,* który ma tę samą nazwę pliku podstawowego, plik *.resx* jest zależny od pasującego pliku źródłowego, a wygenerowana nazwa jest taka sama jak w poprzedniej regule.</span><span class="sxs-lookup"><span data-stu-id="d3c44-121">If the previous rules don't apply, `EmbeddedResourceUseDependentUponConvention` is `true` (the default for .NET Core), and there's a source file colocated with a *.resx* file that has the same base file name, the *.resx* file is made dependent upon the matching source file, and the generated name is the same as in the previous rule.</span></span> <span data-ttu-id="d3c44-122">Jest to reguła "ustawień domyślnych" dla projektów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d3c44-122">This is the "default settings" rule for .NET Core projects.</span></span>
  
  <span data-ttu-id="d3c44-123">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="d3c44-123">Examples:</span></span>
  
  <span data-ttu-id="d3c44-124">Pliki *MyTypes.cs* i *MyTypes.resx* lub *MyTypes.fr-FR.resx* istnieją w tym samym folderze.</span><span class="sxs-lookup"><span data-stu-id="d3c44-124">Files *MyTypes.cs* and *MyTypes.resx* or *MyTypes.fr-FR.resx* exist in the same folder.</span></span>
  
  <span data-ttu-id="d3c44-125">**Nazwa pliku manifestu wygenerowanego zasobu**: *Namespace.Classname.resources* lub *Namespace.Classname.fr-FR.resources* (gdzie `Namespace.Classname` jest nazwą pierwszej klasy w *MyTypes.cs).*</span><span class="sxs-lookup"><span data-stu-id="d3c44-125">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="d3c44-126">Jeśli żadna z poprzednich reguł nie ma zastosowania, wygenerowaną nazwą pliku manifestu zasobu jest *RootNamespace.RelativePathWithDotsForSlashes.\[ Kultura.] zasobów*.</span><span class="sxs-lookup"><span data-stu-id="d3c44-126">If none of the previous rules apply, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="d3c44-127">Ścieżka względna jest `Link` wartością `EmbeddedResource` atrybutu elementu, jeśli jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="d3c44-127">The relative path is the value of the `Link` attribute of the `EmbeddedResource` element if it's set.</span></span> <span data-ttu-id="d3c44-128">W przeciwnym razie ścieżka względna jest wartością `Identity` atrybutu `EmbeddedResource` elementu.</span><span class="sxs-lookup"><span data-stu-id="d3c44-128">Otherwise, the relative path is the value of the `Identity` attribute of the `EmbeddedResource` element.</span></span> <span data-ttu-id="d3c44-129">W programie Visual Studio jest to ścieżka od katalogu głównego projektu do pliku w Eksploratorze rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="d3c44-129">In Visual Studio, this is the path from the project root to the file in Solution Explorer.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d3c44-130">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="d3c44-130">Recommended action</span></span>

<span data-ttu-id="d3c44-131">Jeśli nie jesteś zadowolony z wygenerowanych nazw manifestów, możesz:</span><span class="sxs-lookup"><span data-stu-id="d3c44-131">If you're unsatisfied with the generated manifest names, you can:</span></span>

- <span data-ttu-id="d3c44-132">Zmodyfikuj metadane pliku zasobów zgodnie z jedną z wcześniej opisanych reguł nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="d3c44-132">Modify your resource file metadata according to one of the previously described naming rules.</span></span>

- <span data-ttu-id="d3c44-133">Ustaw `EmbeddedResourceUseDependentUponConvention` `false` w pliku projektu, aby całkowicie zrezygnować z nowej konwencji:</span><span class="sxs-lookup"><span data-stu-id="d3c44-133">Set `EmbeddedResourceUseDependentUponConvention` to `false` in your project file to opt out of the new convention entirely:</span></span>

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > <span data-ttu-id="d3c44-134">Jeśli `LogicalName` lub `ManifestResourceName` atrybuty są obecne, ich wartości będą nadal używane dla wygenerowanej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="d3c44-134">If the `LogicalName` or `ManifestResourceName` attributes are present, their values will still be used for the generated file name.</span></span>

#### <a name="category"></a><span data-ttu-id="d3c44-135">Kategoria</span><span class="sxs-lookup"><span data-stu-id="d3c44-135">Category</span></span>

<span data-ttu-id="d3c44-136">MSBuild</span><span class="sxs-lookup"><span data-stu-id="d3c44-136">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d3c44-137">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d3c44-137">Affected APIs</span></span>

<span data-ttu-id="d3c44-138">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="d3c44-138">N/A</span></span>
