---
ms.openlocfilehash: 276268d31670b5e7dcd0ae9c0b7a61c3c38ca663
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451898"
---
### <a name="resource-manifest-file-names"></a><span data-ttu-id="258aa-101">Nazwy plików manifestu zasobów</span><span class="sxs-lookup"><span data-stu-id="258aa-101">Resource manifest file names</span></span>

<span data-ttu-id="258aa-102">Począwszy od platformy .NET Core 3,0, wygenerowana nazwa pliku manifestu zasobu została zmieniona.</span><span class="sxs-lookup"><span data-stu-id="258aa-102">Starting in .NET Core 3.0, the generated resource manifest file name has changed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="258aa-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="258aa-103">Version introduced</span></span>

<span data-ttu-id="258aa-104">3.0</span><span class="sxs-lookup"><span data-stu-id="258aa-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="258aa-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="258aa-105">Change description</span></span>

<span data-ttu-id="258aa-106">Przed platformą .NET Core 3,0, gdy [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadane zostały ustawione dla pliku zasobu ( *. resx*) w pliku projektu MSBuild, wygenerowana nazwa manifestu to *Namespace. ClassName. resources*.</span><span class="sxs-lookup"><span data-stu-id="258aa-106">Prior to .NET Core 3.0, when [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) metadata was set for a resource (*.resx*) file in the MSBuild project file, the generated manifest name was *Namespace.Classname.resources*.</span></span> <span data-ttu-id="258aa-107">Gdy [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) nie została ustawiona, wygenerowana nazwa manifestu to *Namespace. ClassName. FolderPathRelativeToRoot. Culture. resources*.</span><span class="sxs-lookup"><span data-stu-id="258aa-107">When [DependentUpon](/visualstudio/msbuild/common-msbuild-project-items#compile) was not set, the generated manifest name was *Namespace.Classname.FolderPathRelativeToRoot.Culture.resources*.</span></span>

<span data-ttu-id="258aa-108">Począwszy od platformy .NET Core 3,0, gdy plik *. resx* znajduje się w pliku źródłowym o tej samej nazwie, na przykład w aplikacjach Windows Forms, nazwa manifestu zasobu jest generowana na podstawie pełnej nazwy pierwszego typu w pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="258aa-108">Starting in .NET Core 3.0, when a *.resx* file is colocated with a source file of the same name, for example, in Windows Forms apps, the resource manifest name is generated from the full name of the first type in the source file.</span></span> <span data-ttu-id="258aa-109">Na przykład, jeśli *Type.cs* jest wspólnie z *typem Type. resx*, wygenerowana nazwa manifestu to *Namespace. ClassName. resources*.</span><span class="sxs-lookup"><span data-stu-id="258aa-109">For example, if *Type.cs* is colocated with *Type.resx*, the generated manifest name is *Namespace.Classname.resources*.</span></span> <span data-ttu-id="258aa-110">Jednak w przypadku zmodyfikowania dowolnego atrybutu właściwości `EmbeddedResource` pliku *resx* wygenerowana nazwa pliku manifestu może być różna:</span><span class="sxs-lookup"><span data-stu-id="258aa-110">However, if you modify any of the attributes on the `EmbeddedResource` property for the *.resx* file, the generated manifest file name may be different:</span></span>

- <span data-ttu-id="258aa-111">Jeśli atrybut `LogicalName` właściwości `EmbeddedResource` jest ustawiony, ta wartość jest używana jako nazwa pliku manifestu zasobu.</span><span class="sxs-lookup"><span data-stu-id="258aa-111">If the `LogicalName` attribute on the `EmbeddedResource` property is set, that value is used as the resource manifest file name.</span></span>

  <span data-ttu-id="258aa-112">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="258aa-112">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
  ```

  <span data-ttu-id="258aa-113">**Wygenerowana nazwa pliku manifestu zasobu**: *częśćname. resources* (niezależnie od nazwy pliku *resx* lub kultury lub innych metadanych).</span><span class="sxs-lookup"><span data-stu-id="258aa-113">**Generated resource manifest file name**: *SomeName.resources* (regardless of the *.resx* file name or culture or any other metadata).</span></span>

- <span data-ttu-id="258aa-114">Jeśli `LogicalName` nie jest ustawiona, ale atrybut `ManifestResourceName` właściwości `EmbeddedResource` jest ustawiony, jego wartość, łącznie z rozszerzeniem pliku *. resources*, jest używana jako nazwa pliku manifestu zasobu.</span><span class="sxs-lookup"><span data-stu-id="258aa-114">If `LogicalName` is not set, but the `ManifestResourceName` attribute on the `EmbeddedResource` property is set, its value, combined with the file extension *.resources*, is used as the resource manifest file name.</span></span>

  <span data-ttu-id="258aa-115">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="258aa-115">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
  ```

  <span data-ttu-id="258aa-116">**Wygenerowana nazwa pliku manifestu zasobu**: *częśćname. resources* lub *SomeName.fr-fr. resources*.</span><span class="sxs-lookup"><span data-stu-id="258aa-116">**Generated resource manifest file name**: *SomeName.resources* or *SomeName.fr-FR.resources*.</span></span>

- <span data-ttu-id="258aa-117">Jeśli poprzednie reguły nie mają zastosowania, a atrybut `DependentUpon` w elemencie `EmbeddedResource` jest ustawiony na plik źródłowy, nazwa typu pierwszej klasy w pliku źródłowym zostanie użyta w nazwie pliku manifestu zasobu.</span><span class="sxs-lookup"><span data-stu-id="258aa-117">If the previous rules don't apply, and the `DependentUpon` attribute on the `EmbeddedResource` element is set to a source file, the type name of the first class in the source file is used in the resource manifest file name.</span></span> <span data-ttu-id="258aa-118">Dokładniej mówiąc, wygenerowana nazwa pliku to *Namespace. Classname\[. Culture]. resources*.</span><span class="sxs-lookup"><span data-stu-id="258aa-118">More specifically, the generated file name is *Namespace.Classname\[.Culture].resources*.</span></span>

  <span data-ttu-id="258aa-119">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="258aa-119">Examples:</span></span>

  ```xml
  <EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
  -or-
  <EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
  ```

  <span data-ttu-id="258aa-120">**Wygenerowana nazwa pliku manifestu zasobu**: *Namespace. ClassName. resources* lub *Namespace.ClassName.fr-fr. resources* (gdzie `Namespace.Classname` jest nazwą pierwszej klasy w *MyTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="258aa-120">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>

- <span data-ttu-id="258aa-121">Jeśli poprzednie reguły nie mają zastosowania, `EmbeddedResourceUseDependentUponConvention` jest `true` (domyślnie w przypadku platformy .NET Core) i istnieje plik źródłowy współpracujący z plikiem *resx* , który ma taką samą nazwę pliku podstawowego, plik *. resx* jest uzależniony od pasującego pliku źródłowego, a wygenerowana nazwa jest taka sama jak w poprzedniej regule.</span><span class="sxs-lookup"><span data-stu-id="258aa-121">If the previous rules don't apply, `EmbeddedResourceUseDependentUponConvention` is `true` (the default for .NET Core), and there's a source file colocated with a *.resx* file that has the same base file name, the *.resx* file is made dependent upon the matching source file, and the generated name is the same as in the previous rule.</span></span> <span data-ttu-id="258aa-122">To jest reguła "ustawienia domyślne" dla projektów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="258aa-122">This is the "default settings" rule for .NET Core projects.</span></span>
  
  <span data-ttu-id="258aa-123">Przykłady:</span><span class="sxs-lookup"><span data-stu-id="258aa-123">Examples:</span></span>
  
  <span data-ttu-id="258aa-124">Pliki *MyTypes.cs* i *MyTypes.fr-fr. resx* istnieją w tym samym *folderze.*</span><span class="sxs-lookup"><span data-stu-id="258aa-124">Files *MyTypes.cs* and *MyTypes.resx* or *MyTypes.fr-FR.resx* exist in the same folder.</span></span>
  
  <span data-ttu-id="258aa-125">**Wygenerowana nazwa pliku manifestu zasobu**: *Namespace. ClassName. resources* lub *Namespace.ClassName.fr-fr. resources* (gdzie `Namespace.Classname` jest nazwą pierwszej klasy w *MyTypes.cs*).</span><span class="sxs-lookup"><span data-stu-id="258aa-125">**Generated resource manifest file name**: *Namespace.Classname.resources* or *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the name of the first class in *MyTypes.cs*).</span></span>
    
- <span data-ttu-id="258aa-126">Jeśli żadna z poprzednich reguł nie zostanie zastosowana, wygenerowana nazwa pliku manifestu zasobu to *RootNamespace. RelativePathWithDotsForSlashes.\[Culture.] zasoby*.</span><span class="sxs-lookup"><span data-stu-id="258aa-126">If none of the previous rules apply, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="258aa-127">Ścieżka względna jest wartością atrybutu `Link` elementu `EmbeddedResource`, jeśli jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="258aa-127">The relative path is the value of the `Link` attribute of the `EmbeddedResource` element if it's set.</span></span> <span data-ttu-id="258aa-128">W przeciwnym razie ścieżka względna jest wartością atrybutu `Identity` elementu `EmbeddedResource`.</span><span class="sxs-lookup"><span data-stu-id="258aa-128">Otherwise, the relative path is the value of the `Identity` attribute of the `EmbeddedResource` element.</span></span> <span data-ttu-id="258aa-129">W programie Visual Studio jest to ścieżka z katalogu głównego projektu do pliku w Eksplorator rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="258aa-129">In Visual Studio, this is the path from the project root to the file in Solution Explorer.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="258aa-130">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="258aa-130">Recommended action</span></span>

<span data-ttu-id="258aa-131">Jeśli wygenerowane nazwy manifestów nie są zadowalające, można:</span><span class="sxs-lookup"><span data-stu-id="258aa-131">If you're unsatisfied with the generated manifest names, you can:</span></span>

- <span data-ttu-id="258aa-132">Zmodyfikuj metadane pliku zasobów zgodnie z jedną z wcześniej opisanymi regułami nazewnictwa.</span><span class="sxs-lookup"><span data-stu-id="258aa-132">Modify your resource file metadata according to one of the previously described naming rules.</span></span>

- <span data-ttu-id="258aa-133">Ustaw `EmbeddedResourceUseDependentUponConvention` na `false` w pliku projektu, aby zrezygnować z nowej konwencji w całości:</span><span class="sxs-lookup"><span data-stu-id="258aa-133">Set `EmbeddedResourceUseDependentUponConvention` to `false` in your project file to opt out of the new convention entirely:</span></span>

   ```xml
   <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
   ```

   > [!NOTE]
   > <span data-ttu-id="258aa-134">Jeśli atrybuty `LogicalName` lub `ManifestResourceName` są obecne, ich wartości będą nadal używane dla wygenerowanej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="258aa-134">If the `LogicalName` or `ManifestResourceName` attributes are present, their values will still be used for the generated file name.</span></span>

#### <a name="category"></a><span data-ttu-id="258aa-135">Kategoria</span><span class="sxs-lookup"><span data-stu-id="258aa-135">Category</span></span>

<span data-ttu-id="258aa-136">MSBuild</span><span class="sxs-lookup"><span data-stu-id="258aa-136">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="258aa-137">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="258aa-137">Affected APIs</span></span>

<span data-ttu-id="258aa-138">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="258aa-138">N/A</span></span>
