---
ms.openlocfilehash: f24a29a00a1bff34a452c43716d76bf72ef277b5
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206210"
---
### <a name="resource-manifest-file-name-change"></a><span data-ttu-id="ea6f3-101">Zmiana nazwy pliku manifestu zasobu</span><span class="sxs-lookup"><span data-stu-id="ea6f3-101">Resource manifest file name change</span></span>

<span data-ttu-id="ea6f3-102">Począwszy od platformy .NET Core 3,0, w domyślnym przypadku MSBuild generuje inną nazwę pliku manifestu dla plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="ea6f3-102">Starting in .NET Core 3.0, in the default case, MSBuild generates a different manifest file name for resource files.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ea6f3-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="ea6f3-103">Version introduced</span></span>

<span data-ttu-id="ea6f3-104">3.0</span><span class="sxs-lookup"><span data-stu-id="ea6f3-104">3.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="ea6f3-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="ea6f3-105">Change description</span></span>

<span data-ttu-id="ea6f3-106">Przed platformą .NET Core 3,0, jeśli nie `LogicalName` , `ManifestResourceName` lub `DependentUpon` określono metadane dla `EmbeddedResource` elementu w pliku projektu, MSBuild wygenerował nazwę pliku manifestu w wzorcu `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources` .</span><span class="sxs-lookup"><span data-stu-id="ea6f3-106">Prior to .NET Core 3.0, if no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata was specified for an `EmbeddedResource` item in the project file, MSBuild generated a manifest file name in the pattern `<RootNamespace>.<ResourceFilePathFromProjectRoot>.resources`.</span></span> <span data-ttu-id="ea6f3-107">Jeśli `RootNamespace` nie jest zdefiniowana w pliku projektu, domyślnie jest to nazwa projektu.</span><span class="sxs-lookup"><span data-stu-id="ea6f3-107">If `RootNamespace` is not defined in the project file, it defaults to the project name.</span></span> <span data-ttu-id="ea6f3-108">Na przykład wygenerowana nazwa manifestu dla pliku zasobów o nazwie *Form1. resx* w katalogu głównym projektu miały wartość *WebProject. Form1. resources*.</span><span class="sxs-lookup"><span data-stu-id="ea6f3-108">For example, the generated manifest name for a resource file named *Form1.resx* in the root project directory was *MyProject.Form1.resources*.</span></span>

<span data-ttu-id="ea6f3-109">Począwszy od platformy .NET Core 3,0, jeśli plik zasobów znajduje się w pliku źródłowym o tej samej nazwie (na przykład *Form1. resx* i *Form1.cs*), MSBuild używa informacji o typie z pliku źródłowego do wygenerowania nazwy pliku manifestu w wzorcu `<Namespace>.<ClassName>.resources` .</span><span class="sxs-lookup"><span data-stu-id="ea6f3-109">Starting in .NET Core 3.0, if a resource file is colocated with a source file of the same name (for example, *Form1.resx* and *Form1.cs*), MSBuild uses type information from the source file to generate the manifest file name in the pattern `<Namespace>.<ClassName>.resources`.</span></span> <span data-ttu-id="ea6f3-110">Przestrzeń nazw i nazwa klasy są wyodrębniane z pierwszego typu w umieszczonym w nim pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="ea6f3-110">The namespace and class name are extracted from the first type in the colocated source file.</span></span> <span data-ttu-id="ea6f3-111">Na przykład wygenerowana nazwa manifestu dla pliku zasobów o nazwie *Form1. resx* , który znajduje się w pliku źródłowym o nazwie *Form1.cs* , to moja *przestrzeń nazw. Form1. resources*.</span><span class="sxs-lookup"><span data-stu-id="ea6f3-111">For example, the generated manifest name for a resource file named *Form1.resx* that's colocated with a source file named *Form1.cs* is *MyNamespace.Form1.resources*.</span></span> <span data-ttu-id="ea6f3-112">Kluczową kwestią jest to, że pierwsza część nazwy pliku różni się od wcześniejszych wersji platformy .NET Core (*przestrzeń nazw* , a nie *projekt*).</span><span class="sxs-lookup"><span data-stu-id="ea6f3-112">The key thing to note is that the first part of the file name is different to prior versions of .NET Core (*MyNamespace* instead of *MyProject*).</span></span>

> [!NOTE]
> <span data-ttu-id="ea6f3-113">Jeśli masz `LogicalName` `ManifestResourceName` lub `DependentUpon` metadane określone dla `EmbeddedResource` elementu w pliku projektu, ta zmiana nie ma wpływu na ten plik zasobu.</span><span class="sxs-lookup"><span data-stu-id="ea6f3-113">If you have `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata specified on an `EmbeddedResource` item in the project file, then this change does not affect that resource file.</span></span>

<span data-ttu-id="ea6f3-114">Ta nieprzerwana zmiana została wprowadzona wraz z dodaniem `EmbeddedResourceUseDependentUponConvention` właściwości do projektów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ea6f3-114">This breaking change was introduced with the addition of the `EmbeddedResourceUseDependentUponConvention` property to .NET Core projects.</span></span> <span data-ttu-id="ea6f3-115">Domyślnie pliki zasobów nie są jawnie wymienione w pliku projektu .NET Core, dlatego nie zawierają `DependentUpon` metadanych, aby określić, jak należy nazwać wygenerowany plik *resources* .</span><span class="sxs-lookup"><span data-stu-id="ea6f3-115">By default, resource files aren't explicitly listed in a .NET Core project file, so they have no `DependentUpon` metadata to specify how to name the generated *.resources* file.</span></span> <span data-ttu-id="ea6f3-116">Gdy `EmbeddedResourceUseDependentUponConvention` jest ustawiona na `true` , jest to wartość domyślna, program MSBuild szuka współdostępnego pliku źródłowego i wyodrębni przestrzeń nazw i nazwę klasy z tego pliku.</span><span class="sxs-lookup"><span data-stu-id="ea6f3-116">When `EmbeddedResourceUseDependentUponConvention` is set to `true`, which is the default, MSBuild looks for a colocated source file and extracts a namespace and class name from that file.</span></span> <span data-ttu-id="ea6f3-117">Jeśli ustawisz `EmbeddedResourceUseDependentUponConvention` `false` opcję, MSBuild generuje nazwę manifestu zgodnie z poprzednim zachowaniem, które łączy `RootNamespace` i względną ścieżkę pliku.</span><span class="sxs-lookup"><span data-stu-id="ea6f3-117">If you set `EmbeddedResourceUseDependentUponConvention` to `false`, MSBuild generates the manifest name according to the previous behavior, which combines `RootNamespace` and the relative file path.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ea6f3-118">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="ea6f3-118">Recommended action</span></span>

<span data-ttu-id="ea6f3-119">W większości przypadków żadna akcja nie jest wymagana w ramach dewelopera, a aplikacja powinna nadal pracować.</span><span class="sxs-lookup"><span data-stu-id="ea6f3-119">In most cases, no action is required on the part of the developer, and your app should continue to work.</span></span> <span data-ttu-id="ea6f3-120">Jeśli jednak ta zmiana spowoduje przerwanie aplikacji, można:</span><span class="sxs-lookup"><span data-stu-id="ea6f3-120">However, if this change breaks your app, you can either:</span></span>

- <span data-ttu-id="ea6f3-121">Zmień kod, aby oczekiwać nowej nazwy manifestu.</span><span class="sxs-lookup"><span data-stu-id="ea6f3-121">Change your code to expect the new manifest name.</span></span>

- <span data-ttu-id="ea6f3-122">Zrezygnuj z nowej konwencji nazewnictwa, ustawiając wartość `EmbeddedResourceUseDependentUponConvention` `false` w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="ea6f3-122">Opt out of the new naming convention by setting `EmbeddedResourceUseDependentUponConvention` to `false` in your project file.</span></span>

  ```xml
  <PropertyGroup>
    <EmbeddedResourceUseDependentUponConvention>false</EmbeddedResourceUseDependentUponConvention>
  </PropertyGroup>
  ```

#### <a name="category"></a><span data-ttu-id="ea6f3-123">Kategoria</span><span class="sxs-lookup"><span data-stu-id="ea6f3-123">Category</span></span>

<span data-ttu-id="ea6f3-124">MSBuild</span><span class="sxs-lookup"><span data-stu-id="ea6f3-124">MSBuild</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ea6f3-125">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="ea6f3-125">Affected APIs</span></span>

<span data-ttu-id="ea6f3-126">Brak</span><span class="sxs-lookup"><span data-stu-id="ea6f3-126">N/A</span></span>
