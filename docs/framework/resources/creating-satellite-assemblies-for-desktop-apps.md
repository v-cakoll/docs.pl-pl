---
title: Tworzenie zestawów satelickich dla aplikacji klasycznych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- public keys, obtaining
- satellite assemblies
- assemblies [.NET Framework], signing
- application resources, deploying
- Al.exe
- GAC (global assembly cache), satellite assemblies
- Assembly Linker
- directory locations for satellite assemblies
- global assembly cache, satellite assemblies
- packaging application resources
- compiling satellite assemblies
- re-signing assemblies
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
ms.openlocfilehash: 5efc5001a1a9756e09053d684a2f6673d15fadcf
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458015"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a><span data-ttu-id="c87cf-102">Tworzenie zestawów satelickich dla aplikacji klasycznych</span><span class="sxs-lookup"><span data-stu-id="c87cf-102">Creating Satellite Assemblies for Desktop Apps</span></span>

<span data-ttu-id="c87cf-103">Pliki zasobów odgrywają centralną rolę w zlokalizowanych aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="c87cf-103">Resource files play a central role in localized applications.</span></span> <span data-ttu-id="c87cf-104">Umożliwiają one aplikacji wyświetlanie ciągów, obrazów i innych danych w własnym języku i kulturze użytkownika oraz dostarczanie alternatywnych danych, jeśli zasoby dla własnego języka lub kultury użytkownika są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="c87cf-104">They enable an application to display strings, images, and other data in the user's own language and culture, and to provide alternate data if resources for the user's own language or culture are unavailable.</span></span> <span data-ttu-id="c87cf-105">.NET Framework używa modelu gwiazdy, aby zlokalizować i pobrać zlokalizowane zasoby.</span><span class="sxs-lookup"><span data-stu-id="c87cf-105">The .NET Framework uses a hub-and-spoke model to locate and retrieve localized resources.</span></span> <span data-ttu-id="c87cf-106">Koncentrator jest głównym zestawem zawierającym nielokalizowalny kod wykonywalny i zasoby dla jednej kultury, która jest nazywana kulturą neutralną lub domyślną.</span><span class="sxs-lookup"><span data-stu-id="c87cf-106">The hub is the main assembly that contains the non-localizable executable code and the resources for a single culture, which is called the neutral or default culture.</span></span> <span data-ttu-id="c87cf-107">Domyślna kultura jest kulturą rezerwową dla aplikacji; jest on używany, gdy nie są dostępne żadne zlokalizowane zasoby.</span><span class="sxs-lookup"><span data-stu-id="c87cf-107">The default culture is the fallback culture for the application; it is used when no localized resources are available.</span></span> <span data-ttu-id="c87cf-108">Użyj atrybutu, <xref:System.Resources.NeutralResourcesLanguageAttribute> aby wyznaczyć kulturę domyślnej kultury aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c87cf-108">You use the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute to designate the culture of the application's default culture.</span></span> <span data-ttu-id="c87cf-109">Każdy szprych nawiązuje połączenie z zestawem satelickim zawierającym zasoby dla jednej zlokalizowanej kultury, ale nie zawiera kodu.</span><span class="sxs-lookup"><span data-stu-id="c87cf-109">Each spoke connects to a satellite assembly that contains the resources for a single localized culture but does not contain any code.</span></span> <span data-ttu-id="c87cf-110">Ponieważ zestawy satelickie nie są częścią głównego zestawu, można łatwo aktualizować lub zastępować zasoby, które odpowiadają określonej kulturze, bez zastępowania głównego zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c87cf-110">Because the satellite assemblies are not part of the main assembly, you can easily update or replace resources that correspond to a specific culture without replacing the main assembly for the application.</span></span>

> [!NOTE]
> <span data-ttu-id="c87cf-111">Zasoby domyślnej kultury aplikacji mogą być również przechowywane w zestawie satelickim.</span><span class="sxs-lookup"><span data-stu-id="c87cf-111">The resources of an application's default culture can also be stored in a satellite assembly.</span></span> <span data-ttu-id="c87cf-112">W tym celu należy przypisać <xref:System.Resources.NeutralResourcesLanguageAttribute> atrybut o wartości. <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="c87cf-112">To do this, you assign the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute a value of <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.</span></span>

## <a name="satellite-assembly-name-and-location"></a><span data-ttu-id="c87cf-113">Nazwa i lokalizacja zestawu satelickiego</span><span class="sxs-lookup"><span data-stu-id="c87cf-113">Satellite Assembly Name and Location</span></span>

<span data-ttu-id="c87cf-114">Model gwiazdy i gwiazdy wymaga umieszczenia zasobów w określonych lokalizacjach, aby można je było łatwo zlokalizować i wykorzystać.</span><span class="sxs-lookup"><span data-stu-id="c87cf-114">The hub-and-spoke model requires that you place resources in specific locations so that they can be easily located and used.</span></span> <span data-ttu-id="c87cf-115">Jeśli nie kompilujesz zasobów i nie nazywasz ich w oczekiwany sposób lub jeśli nie umieścisz ich w prawidłowych lokalizacjach, środowisko uruchomieniowe języka wspólnego nie będzie w stanie go zlokalizować i będzie używać zasobów kultury domyślnej.</span><span class="sxs-lookup"><span data-stu-id="c87cf-115">If you do not compile and name resources as expected, or if you do not place them in the correct locations, the common language runtime will not be able to locate them and will use the resources of the default culture instead.</span></span> <span data-ttu-id="c87cf-116">.NET Framework Menedżer zasobów reprezentowane przez <xref:System.Resources.ResourceManager> obiekt jest używany do automatycznego uzyskiwania dostępu do zlokalizowanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="c87cf-116">The .NET Framework Resource Manager, represented by a <xref:System.Resources.ResourceManager> object, is used to automatically access localized resources.</span></span> <span data-ttu-id="c87cf-117">Menedżer zasobów wymaga następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c87cf-117">The Resource Manager requires the following:</span></span>

- <span data-ttu-id="c87cf-118">Pojedynczy zestaw satelicki musi zawierać wszystkie zasoby dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="c87cf-118">A single satellite assembly must include all the resources for a particular culture.</span></span> <span data-ttu-id="c87cf-119">Innymi słowy, należy skompilować wiele plików *txt* lub *resx* do jednego pliku binarnego *resources* .</span><span class="sxs-lookup"><span data-stu-id="c87cf-119">In other words, you should compile multiple *.txt* or *.resx* files into a single binary *.resources* file.</span></span>

- <span data-ttu-id="c87cf-120">W katalogu aplikacji musi znajdować się oddzielny podkatalog dla każdej zlokalizowanej kultury, która przechowuje zasoby danej kultury.</span><span class="sxs-lookup"><span data-stu-id="c87cf-120">There must be a separate subdirectory in the application directory for each localized culture that stores that culture's resources.</span></span> <span data-ttu-id="c87cf-121">Nazwa podkatalogu musi być taka sama jak nazwa kultury.</span><span class="sxs-lookup"><span data-stu-id="c87cf-121">The subdirectory name must be the same as the culture name.</span></span> <span data-ttu-id="c87cf-122">Alternatywnie można przechowywać zestawy satelickie w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="c87cf-122">Alternately, you can store your satellite assemblies in the global assembly cache.</span></span> <span data-ttu-id="c87cf-123">W takim przypadku składnik informacji o kulturze silnej nazwy zestawu musi wskazywać jego kulturę.</span><span class="sxs-lookup"><span data-stu-id="c87cf-123">In this case, the culture information component of the assembly's strong name must indicate its culture.</span></span> <span data-ttu-id="c87cf-124">(Zobacz [Instalowanie zestawów satelickich w globalnej pamięci podręcznej zestawów w](#SN) dalszej części tego tematu).</span><span class="sxs-lookup"><span data-stu-id="c87cf-124">(See the [Installing Satellite Assemblies in the Global Assembly Cache](#SN) section later in this topic.)</span></span>

  > [!NOTE]
  > <span data-ttu-id="c87cf-125">Jeśli aplikacja zawiera zasoby dla podkultur, umieść każdą podkulturę w osobnym podkatalogu w katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c87cf-125">If your application includes resources for subcultures, place each subculture in a separate subdirectory under the application directory.</span></span> <span data-ttu-id="c87cf-126">Nie należy umieszczać podkultur w podkatalogach w katalogu kultury głównej.</span><span class="sxs-lookup"><span data-stu-id="c87cf-126">Do not place subcultures in subdirectories under their main culture's directory.</span></span>

- <span data-ttu-id="c87cf-127">Zestaw satelicki musi mieć taką samą nazwę jak aplikacja i musi używać rozszerzenia nazwy pliku ". resources. dll".</span><span class="sxs-lookup"><span data-stu-id="c87cf-127">The satellite assembly must have the same name as the application, and must use the file name extension ".resources.dll".</span></span> <span data-ttu-id="c87cf-128">Na przykład jeśli aplikacja ma nazwę *example. exe*, Nazwa każdego zestawu satelickiego powinna być *przykładem. resources. dll*.</span><span class="sxs-lookup"><span data-stu-id="c87cf-128">For example, if an application is named *Example.exe*, the name of each satellite assembly should be *Example.resources.dll*.</span></span> <span data-ttu-id="c87cf-129">Należy zauważyć, że nazwa zestawu satelickiego nie wskazuje kultury plików zasobów.</span><span class="sxs-lookup"><span data-stu-id="c87cf-129">Note that the satellite assembly name does not indicate the culture of its resource files.</span></span> <span data-ttu-id="c87cf-130">Jednak zestaw satelicki pojawia się w katalogu, który określa kulturę.</span><span class="sxs-lookup"><span data-stu-id="c87cf-130">However, the satellite assembly appears in a directory that does specify the culture.</span></span>

- <span data-ttu-id="c87cf-131">Informacje o kulturze zestawu satelickiego muszą być zawarte w metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="c87cf-131">Information about the culture of the satellite assembly must be included in the assembly's metadata.</span></span> <span data-ttu-id="c87cf-132">Aby zapisać nazwę kultury w metadanych zestawu satelickiego, należy określić `/culture` opcję przy użyciu [konsolidatora zestawu](../tools/al-exe-assembly-linker.md) do osadzenia zasobów w zestawie satelickim.</span><span class="sxs-lookup"><span data-stu-id="c87cf-132">To store the culture name in the satellite assembly's metadata, you specify the `/culture` option when you use [Assembly Linker](../tools/al-exe-assembly-linker.md) to embed resources in the satellite assembly.</span></span>

<span data-ttu-id="c87cf-133">Na poniższej ilustracji przedstawiono przykładową strukturę katalogów i wymagania dotyczące lokalizacji dla aplikacji, które nie są instalowane w [globalnej pamięci podręcznej zestawów](../app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="c87cf-133">The following illustration shows a sample directory structure and location requirements for applications that you are not installing in the [global assembly cache](../app-domains/gac.md).</span></span> <span data-ttu-id="c87cf-134">Elementy z rozszerzeniami. txt i. resources nie będą dostarczane z aplikacją końcową.</span><span class="sxs-lookup"><span data-stu-id="c87cf-134">The items with .txt and .resources extensions will not ship with the final application.</span></span> <span data-ttu-id="c87cf-135">Są to pośrednie pliki zasobów używane do tworzenia końcowych zestawów zasobów satelitarnych.</span><span class="sxs-lookup"><span data-stu-id="c87cf-135">These are the intermediate resource files used to create the final satellite resource assemblies.</span></span> <span data-ttu-id="c87cf-136">W tym przykładzie można zastąpić pliki RESX dla plików txt.</span><span class="sxs-lookup"><span data-stu-id="c87cf-136">In this example, you could substitute .resx files for the .txt files.</span></span> <span data-ttu-id="c87cf-137">Aby uzyskać więcej informacji, zobacz [pakowanie i wdrażanie zasobów](packaging-and-deploying-resources-in-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="c87cf-137">For more information, see [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md).</span></span>

<span data-ttu-id="c87cf-138">Na poniższej ilustracji przedstawiono katalog zestawu satelickiego:</span><span class="sxs-lookup"><span data-stu-id="c87cf-138">The following image shows the satellite assembly directory:</span></span>

![Katalog zestawu satelickiego ze zlokalizowanymi podkatalogami kultury.](./media/creating-satellite-assemblies-for-desktop-apps/satellite-assembly-directory.gif)

## <a name="compiling-satellite-assemblies"></a><span data-ttu-id="c87cf-140">Kompilowanie zestawów satelickich</span><span class="sxs-lookup"><span data-stu-id="c87cf-140">Compiling Satellite Assemblies</span></span>

<span data-ttu-id="c87cf-141">Używasz [generatora plików zasobów (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) do kompilowania plików tekstowych lub plików XML (*. resx*) zawierających zasoby do plików binarnych *. resources* .</span><span class="sxs-lookup"><span data-stu-id="c87cf-141">You use [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) to compile text files or XML (*.resx*) files that contain resources to binary *.resources* files.</span></span> <span data-ttu-id="c87cf-142">Następnie należy użyć [konsolidatora zestawu (Al. exe)](../tools/al-exe-assembly-linker.md) do kompilowania plików *resources* do zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="c87cf-142">You then use [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to compile *.resources* files into satellite assemblies.</span></span> <span data-ttu-id="c87cf-143">*Al. exe* tworzy zestaw z plików *resources* , które określisz.</span><span class="sxs-lookup"><span data-stu-id="c87cf-143">*Al.exe* creates an assembly from the *.resources* files that you specify.</span></span> <span data-ttu-id="c87cf-144">Zestawy satelickie mogą zawierać tylko zasoby; nie mogą zawierać żadnego kodu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="c87cf-144">Satellite assemblies can contain only resources; they cannot contain any executable code.</span></span>

<span data-ttu-id="c87cf-145">Następujące polecenie *Al. exe* tworzy zestaw satelicki dla aplikacji `Example` z ciągów plików zasobów niemieckich *. de. resources*.</span><span class="sxs-lookup"><span data-stu-id="c87cf-145">The following *Al.exe* command creates a satellite assembly for the application `Example` from the German resources file *strings.de.resources*.</span></span>

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll
```

<span data-ttu-id="c87cf-146">Następujące polecenie *Al. exe* tworzy również zestaw satelicki dla aplikacji `Example` z ciągów plików *. de. resources*.</span><span class="sxs-lookup"><span data-stu-id="c87cf-146">The following *Al.exe* command also creates a satellite assembly for the application `Example` from the file *strings.de.resources*.</span></span> <span data-ttu-id="c87cf-147">Opcja **/Template** powoduje, że zestaw satelicki dziedziczy wszystkie metadane zestawu, z wyjątkiem informacji o kulturze z zestawu nadrzędnego (*przykład. dll*).</span><span class="sxs-lookup"><span data-stu-id="c87cf-147">The **/template** option causes the satellite assembly to inherit all assembly metadata except for its culture information from the parent assembly (*Example.dll*).</span></span>

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll
```  
  
<span data-ttu-id="c87cf-148">W poniższej tabeli opisano opcje *Al. exe* używane w tych poleceniach bardziej szczegółowo:</span><span class="sxs-lookup"><span data-stu-id="c87cf-148">The following table describes the *Al.exe* options used in these commands in more detail:</span></span>
  
|<span data-ttu-id="c87cf-149">Opcja</span><span class="sxs-lookup"><span data-stu-id="c87cf-149">Option</span></span>|<span data-ttu-id="c87cf-150">Opis</span><span class="sxs-lookup"><span data-stu-id="c87cf-150">Description</span></span>|
|------------|-----------------|
|`-target:lib`|<span data-ttu-id="c87cf-151">Określa, że zestaw satelicki jest kompilowany do pliku biblioteki (. dll).</span><span class="sxs-lookup"><span data-stu-id="c87cf-151">Specifies that your satellite assembly is compiled to a library (.dll) file.</span></span> <span data-ttu-id="c87cf-152">Ponieważ zestaw satelicki nie zawiera kodu wykonywalnego i nie jest głównym zestawem aplikacji, należy zapisać zestawy satelickie jako biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="c87cf-152">Because a satellite assembly does not contain executable code and is not an application's main assembly, you must save satellite assemblies as DLLs.</span></span>|
|`-embed:strings.de.resources`|<span data-ttu-id="c87cf-153">Określa nazwę pliku zasobu do osadzenia, gdy *Al. exe* kompiluje zestaw.</span><span class="sxs-lookup"><span data-stu-id="c87cf-153">Specifies the name of the resource file to embed when *Al.exe* compiles the assembly.</span></span> <span data-ttu-id="c87cf-154">Można osadzić wiele plików Resources w zestawie satelickim, ale jeśli korzystasz z modelu gwiazdy i szprych, musisz skompilować jeden zestaw satelicki dla każdej kultury.</span><span class="sxs-lookup"><span data-stu-id="c87cf-154">You can embed multiple .resources files in a satellite assembly, but if you are following the hub-and-spoke model, you must compile one satellite assembly for each culture.</span></span> <span data-ttu-id="c87cf-155">Można jednak tworzyć oddzielne pliki resources dla ciągów i obiektów.</span><span class="sxs-lookup"><span data-stu-id="c87cf-155">However, you can create separate .resources files for strings and objects.</span></span>|
|`-culture:de`|<span data-ttu-id="c87cf-156">Określa kulturę zasobu do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="c87cf-156">Specifies the culture of the resource to compile.</span></span> <span data-ttu-id="c87cf-157">Środowisko uruchomieniowe języka wspólnego używa tych informacji podczas wyszukiwania zasobów dla określonej kultury.</span><span class="sxs-lookup"><span data-stu-id="c87cf-157">The common language runtime uses this information when it searches for the resources for a specified culture.</span></span> <span data-ttu-id="c87cf-158">W przypadku pominięcia tej opcji *Al. exe* będzie nadal kompilować zasób, ale środowisko uruchomieniowe nie będzie mogło go znaleźć, gdy użytkownik zażąda.</span><span class="sxs-lookup"><span data-stu-id="c87cf-158">If you omit this option, *Al.exe* will still compile the resource, but the runtime will not be able to find it when a user requests it.</span></span>|
|`-out:Example.resources.dll`|<span data-ttu-id="c87cf-159">Określa nazwę pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="c87cf-159">Specifies the name of the output file.</span></span> <span data-ttu-id="c87cf-160">Nazwa musi następować po nazewnictwie standard *basename*. resources. *rozszerzenie*, gdzie *basename* jest nazwą głównego zestawu, a *rozszerzenie* jest prawidłowym rozszerzeniem nazwy pliku (np. dll).</span><span class="sxs-lookup"><span data-stu-id="c87cf-160">The name must follow the naming standard *baseName*.resources.*extension*, where *baseName* is the name of the main assembly and *extension* is a valid file name extension (such as .dll).</span></span> <span data-ttu-id="c87cf-161">Należy pamiętać, że środowisko uruchomieniowe nie może określić kultury zestawu satelickiego na podstawie jego nazwy pliku wyjściowego; Aby to określić, należy użyć opcji **/Culture** .</span><span class="sxs-lookup"><span data-stu-id="c87cf-161">Note that the runtime is not able to determine the culture of a satellite assembly based on its output file name; you must use the **/culture** option to specify it.</span></span>|
|`-template:Example.dll`|<span data-ttu-id="c87cf-162">Określa zestaw, z którego zestaw satelicki będzie dziedziczyć wszystkie metadane zestawu z wyjątkiem pola kultury.</span><span class="sxs-lookup"><span data-stu-id="c87cf-162">Specifies an assembly from which the satellite assembly will inherit all assembly metadata except the culture field.</span></span> <span data-ttu-id="c87cf-163">Ta opcja ma wpływ na zestawy satelickie tylko w przypadku określenia zestawu o [silnej nazwie](../../standard/assembly/strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="c87cf-163">This option affects satellite assemblies only if you specify an assembly that has a [strong name](../../standard/assembly/strong-named.md).</span></span>|
  
 <span data-ttu-id="c87cf-164">Aby zapoznać się z pełną listą opcji dostępnych w programie *Al. exe*, zobacz [konsolidator zestawu (Al. exe)](../tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="c87cf-164">For a complete list of options available with *Al.exe*, see [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span>
  
## <a name="satellite-assemblies-an-example"></a><span data-ttu-id="c87cf-165">Zestawy satelickie: przykład</span><span class="sxs-lookup"><span data-stu-id="c87cf-165">Satellite Assemblies: An Example</span></span>

<span data-ttu-id="c87cf-166">Poniżej znajduje się prosty przykład "Hello World", który wyświetla okno komunikatu zawierające zlokalizowane powitanie.</span><span class="sxs-lookup"><span data-stu-id="c87cf-166">The following is a simple "Hello world" example that displays a message box containing a localized greeting.</span></span> <span data-ttu-id="c87cf-167">W przykładzie uwzględniono zasoby dla kultur angielskiej (Stany Zjednoczone), francuski (Francja) i rosyjski (Rosja), a jej kultura rezerwowa jest w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="c87cf-167">The example includes resources for the English (United States), French (France), and Russian (Russia) cultures, and its fallback culture is English.</span></span> <span data-ttu-id="c87cf-168">Aby utworzyć przykład, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c87cf-168">To create the example, do the following:</span></span>
  
1. <span data-ttu-id="c87cf-169">Utwórz plik zasobów o nazwie *Greetings. resx* lub *Greeting. txt* , aby zawierał zasób dla kultury domyślnej.</span><span class="sxs-lookup"><span data-stu-id="c87cf-169">Create a resource file named *Greeting.resx* or *Greeting.txt* to contain the resource for the default culture.</span></span> <span data-ttu-id="c87cf-170">Przechowywanie pojedynczego ciągu o nazwie `HelloString` "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c87cf-170">Store a single string named `HelloString` whose value is "Hello world!"</span></span> <span data-ttu-id="c87cf-171">w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="c87cf-171">in this file.</span></span>

2. <span data-ttu-id="c87cf-172">Aby wskazać, że angielski (EN) jest kulturą domyślną aplikacji, Dodaj następujący <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atrybut do pliku AssemblyInfo aplikacji lub do głównego pliku kodu źródłowego, który zostanie skompilowany do głównego zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c87cf-172">To indicate that English (en) is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly.</span></span>

    [!code-csharp[Conceptual.Resources.Locating#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
    [!code-vb[Conceptual.Resources.Locating#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3. <span data-ttu-id="c87cf-173">Dodaj obsługę dodatkowych kultur (EN-US, fr-FR i ru-RU) do aplikacji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c87cf-173">Add support for additional cultures (en-US, fr-FR, and ru-RU) to the application as follows:</span></span>  
  
    - <span data-ttu-id="c87cf-174">Aby zapewnić obsługę kultury en-US lub English (Stany Zjednoczone), Utwórz plik zasobów o nazwie *greetingd. en-us. resx* lub *Greetings. en-us. txt*i Zapisz w nim w tym samym ciągu o `HelloString` nazwie "Witaj świecie!".</span><span class="sxs-lookup"><span data-stu-id="c87cf-174">To support the en-US or English (United States) culture, create a resource file named *Greeting.en-US.resx* or *Greeting.en-US.txt*, and store in it a single string named `HelloString` whose value is "Hi world!".</span></span>
  
    - <span data-ttu-id="c87cf-175">Aby zapewnić obsługę kultury fr-FR lub francuski (Francja), Utwórz plik zasobów o nazwie *Greeting.fr-fr. resx* lub *Greeting.fr-fr. txt*, a następnie zapisz go w tym samym ciągu `HelloString` o nazwie, którego wartość to "Salut Tout Le Monde!".</span><span class="sxs-lookup"><span data-stu-id="c87cf-175">To support the fr-FR or French (France) culture, create a resource file named *Greeting.fr-FR.resx* or *Greeting.fr-FR.txt*, and store in it a single string named `HelloString` whose value is "Salut tout le monde!".</span></span>
  
    - <span data-ttu-id="c87cf-176">Aby zapewnić obsługę kultury ru-RU lub rosyjski (Rosja), Utwórz plik zasobów o nazwie *Greeting.ru-RU. resx* lub *Greeting.ru-RU. txt*, a następnie zapisz go w tym samym ciągu `HelloString` o nazwie, którego wartość to "Всем Привет!".</span><span class="sxs-lookup"><span data-stu-id="c87cf-176">To support the ru-RU or Russian (Russia) culture, create a resource file named *Greeting.ru-RU.resx* or *Greeting.ru-RU.txt*, and store in it a single string named `HelloString` whose value is "Всем привет!".</span></span>
  
4. <span data-ttu-id="c87cf-177">Użyj programu [Resgen. exe](../tools/resgen-exe-resource-file-generator.md) , aby skompilować każdy plik tekstowy lub XML do pliku binarnego *. resources* .</span><span class="sxs-lookup"><span data-stu-id="c87cf-177">Use [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary *.resources* file.</span></span> <span data-ttu-id="c87cf-178">Dane wyjściowe to zestaw plików, które mają taką samą nazwę pliku głównego jak pliki *resx* lub *txt* , ale rozszerzenie *. resources* .</span><span class="sxs-lookup"><span data-stu-id="c87cf-178">The output is a set of files that have the same root file name as the *.resx* or *.txt* files, but a *.resources* extension.</span></span> <span data-ttu-id="c87cf-179">Jeśli utworzysz przykład w programie Visual Studio, proces kompilacji jest obsługiwany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c87cf-179">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="c87cf-180">Jeśli nie korzystasz z programu Visual Studio, uruchom następujące polecenia, aby skompilować pliki. *resx* do plików *resources* :</span><span class="sxs-lookup"><span data-stu-id="c87cf-180">If you aren't using Visual Studio, run the following commands to compile the *.resx* files into *.resources* files:</span></span>  
  
    ```console
    resgen Greeting.resx
    resgen Greeting.en-us.resx
    resgen Greeting.fr-FR.resx
    resgen Greeting.ru-RU.resx
    ```

    <span data-ttu-id="c87cf-181">Jeśli zasoby znajdują się w plikach tekstowych zamiast plików XML, Zastąp rozszerzenie *resx* rozszerzeniem *. txt*.</span><span class="sxs-lookup"><span data-stu-id="c87cf-181">If your resources are in text files instead of XML files, replace the *.resx* extension with *.txt*.</span></span>

5. <span data-ttu-id="c87cf-182">Skompiluj następujący kod źródłowy wraz z zasobami dla domyślnej kultury w zestawie głównym aplikacji:</span><span class="sxs-lookup"><span data-stu-id="c87cf-182">Compile the following source code along with the resources for the default culture into the application's main assembly:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="c87cf-183">Jeśli używasz wiersza polecenia zamiast programu Visual Studio do utworzenia przykładu, należy zmodyfikować wywołanie konstruktora <xref:System.Resources.ResourceManager> klasy w następujący sposób:`ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span><span class="sxs-lookup"><span data-stu-id="c87cf-183">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to the following: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span></span>

    [!code-csharp[Conceptual.Resources.Locating#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
    [!code-vb[Conceptual.Resources.Locating#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]

    <span data-ttu-id="c87cf-184">Jeśli aplikacja jest przykładowa i jest kompilowana z wiersza polecenia, polecenie dla kompilatora C# jest następujące:</span><span class="sxs-lookup"><span data-stu-id="c87cf-184">If the application is named Example and you are compiling from the command-line, the command for the C# compiler is:</span></span>

    ```console
    csc Example.cs -res:Greeting.resources
    ```

    <span data-ttu-id="c87cf-185">Odpowiednie polecenie kompilatora Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="c87cf-185">The corresponding Visual Basic compiler command is:</span></span>

    ```console
    vbc Example.vb -res:Greeting.resources
    ```

6. <span data-ttu-id="c87cf-186">Utwórz podkatalog w katalogu głównym aplikacji dla każdej zlokalizowanej kultury obsługiwanej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="c87cf-186">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="c87cf-187">Należy utworzyć podkatalog *en-us*, *fr-fr*i *ru-RU* .</span><span class="sxs-lookup"><span data-stu-id="c87cf-187">You should create an *en-US*, an *fr-FR*, and an *ru-RU* subdirectory.</span></span> <span data-ttu-id="c87cf-188">Program Visual Studio automatycznie tworzy te podkatalogi w ramach procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c87cf-188">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span>

7. <span data-ttu-id="c87cf-189">Osadź poszczególne pliki *zasobów* specyficzne dla kultury w zestawach satelickich i Zapisz je w odpowiednim katalogu.</span><span class="sxs-lookup"><span data-stu-id="c87cf-189">Embed the individual culture-specific *.resources* files into satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="c87cf-190">Polecenie to zrób dla każdego pliku *resources* :</span><span class="sxs-lookup"><span data-stu-id="c87cf-190">The command to do this for each *.resources* file is:</span></span>

    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll
    ```

     <span data-ttu-id="c87cf-191">gdzie *Culture* to nazwa kultury, której zasoby zawierają zestaw satelicki.</span><span class="sxs-lookup"><span data-stu-id="c87cf-191">where *culture* is the name of the culture whose resources the satellite assembly contains.</span></span> <span data-ttu-id="c87cf-192">Program Visual Studio obsługuje ten proces automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c87cf-192">Visual Studio handles this process automatically.</span></span>

<span data-ttu-id="c87cf-193">Następnie można uruchomić przykład.</span><span class="sxs-lookup"><span data-stu-id="c87cf-193">You can then run the example.</span></span> <span data-ttu-id="c87cf-194">Spowoduje to losowo przetworzenie jednej z obsługiwanych kultur w bieżącej kulturze i wyświetlenie zlokalizowanego powitania.</span><span class="sxs-lookup"><span data-stu-id="c87cf-194">It will randomly make one of the supported cultures the current culture and display a localized greeting.</span></span>

<a name="SN"></a>

## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="c87cf-195">Instalowanie zestawów satelickich w globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="c87cf-195">Installing Satellite Assemblies in the Global Assembly Cache</span></span>

<span data-ttu-id="c87cf-196">Zamiast instalować zestawy w lokalnym podkatalogu aplikacji, można je zainstalować w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="c87cf-196">Instead of installing assemblies in a local application subdirectory, you can install them in the global assembly cache.</span></span> <span data-ttu-id="c87cf-197">Jest to szczególnie przydatne, jeśli dysponujesz bibliotekami klas i zestawami zasobów biblioteki klas, które są używane przez wiele aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c87cf-197">This is particularly useful if you have class libraries and class library resource assemblies that are used by multiple applications.</span></span>
  
<span data-ttu-id="c87cf-198">Instalowanie zestawów w globalnej pamięci podręcznej zestawów wymaga posiadania silnych nazw.</span><span class="sxs-lookup"><span data-stu-id="c87cf-198">Installing assemblies in the global assembly cache requires that they have strong names.</span></span> <span data-ttu-id="c87cf-199">Zestawy o silnych nazwach są podpisane przy użyciu prawidłowej pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="c87cf-199">Strong-named assemblies are signed with a valid public/private key pair.</span></span> <span data-ttu-id="c87cf-200">Zawierają informacje o wersji używane przez środowisko uruchomieniowe do określenia zestawu, który ma być używany w celu spełnienia żądania powiązania.</span><span class="sxs-lookup"><span data-stu-id="c87cf-200">They contain version information that the runtime uses to determine which assembly to use to satisfy a binding request.</span></span> <span data-ttu-id="c87cf-201">Aby uzyskać więcej informacji na temat silnych nazw i wersji, zobacz [wersja zestawu](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="c87cf-201">For more information about strong names and versioning, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span> <span data-ttu-id="c87cf-202">Aby uzyskać więcej informacji o silnych nazwach, zobacz [zestawy o silnych nazwach](../../standard/assembly/strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="c87cf-202">For more information about strong names, see [Strong-Named Assemblies](../../standard/assembly/strong-named.md).</span></span>

<span data-ttu-id="c87cf-203">Podczas tworzenia aplikacji jest mało prawdopodobne, że będziesz mieć dostęp do ostatniej pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="c87cf-203">When you are developing an application, it is unlikely that you will have access to the final public/private key pair.</span></span> <span data-ttu-id="c87cf-204">W celu zainstalowania zestawu satelickiego w globalnej pamięci podręcznej zestawów i upewnienia się, że działa zgodnie z oczekiwaniami, można użyć techniki o nazwie opóźnione podpisywanie.</span><span class="sxs-lookup"><span data-stu-id="c87cf-204">In order to install a satellite assembly in the global assembly cache and ensure that it works as expected, you can use a technique called delayed signing.</span></span> <span data-ttu-id="c87cf-205">Gdy opóźniasz podpisywanie zestawu w czasie kompilacji, Zarezerwuj miejsce w pliku dla sygnatury silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="c87cf-205">When you delay sign an assembly, at build time you reserve space in the file for the strong name signature.</span></span> <span data-ttu-id="c87cf-206">Rzeczywiste podpisywanie jest opóźnione aż do późniejszego momentu udostępnienia ostatniej pary kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="c87cf-206">The actual signing is delayed until later, when the final public/private key pair is available.</span></span> <span data-ttu-id="c87cf-207">Aby uzyskać więcej informacji na temat opóźnionego podpisywania, zobacz [opóźnienie podpisywania zestawu](../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="c87cf-207">For more information about delayed signing, see [Delay Signing an Assembly](../../standard/assembly/delay-sign.md).</span></span>

### <a name="obtaining-the-public-key"></a><span data-ttu-id="c87cf-208">Uzyskiwanie klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="c87cf-208">Obtaining the Public Key</span></span>

<span data-ttu-id="c87cf-209">Aby opóźnić podpisywanie zestawu, musisz mieć dostęp do klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="c87cf-209">To delay sign an assembly, you must have access to the public key.</span></span> <span data-ttu-id="c87cf-210">Możesz uzyskać rzeczywisty klucz publiczny z organizacji w firmie, który będzie podpisywać ostateczne lub utworzyć klucz publiczny za pomocą [Narzędzia silnej nazwy (SN. exe)](../tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="c87cf-210">You can either obtain the real public key from the organization in your company that will do the eventual signing, or create a public key by using the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md).</span></span>

<span data-ttu-id="c87cf-211">Następujące polecenie *SN. exe* tworzy parę kluczy publiczny/prywatny.</span><span class="sxs-lookup"><span data-stu-id="c87cf-211">The following *Sn.exe* command creates a test public/private key pair.</span></span> <span data-ttu-id="c87cf-212">Opcja **– k** określa, że *SN. exe* powinien utworzyć nową parę kluczy i zapisać ją w pliku o nazwie *TestKeyPair. snk*.</span><span class="sxs-lookup"><span data-stu-id="c87cf-212">The **–k** option specifies that *Sn.exe* should create a new key pair and save it in a file named *TestKeyPair.snk*.</span></span>
  
```console
sn –k TestKeyPair.snk
```

<span data-ttu-id="c87cf-213">Klucz publiczny można wyodrębnić z pliku, który zawiera parę kluczy testowych.</span><span class="sxs-lookup"><span data-stu-id="c87cf-213">You can extract the public key from the file that contains the test key pair.</span></span> <span data-ttu-id="c87cf-214">Następujące polecenie wyodrębnia klucz publiczny z *TestKeyPair. snk* i zapisuje go w *PublicKey. snk*:</span><span class="sxs-lookup"><span data-stu-id="c87cf-214">The following command extracts the public key from *TestKeyPair.snk* and saves it in *PublicKey.snk*:</span></span>

```console
sn –p TestKeyPair.snk PublicKey.snk
```

### <a name="delay-signing-an-assembly"></a><span data-ttu-id="c87cf-215">Opóźnione podpisywanie zestawu</span><span class="sxs-lookup"><span data-stu-id="c87cf-215">Delay Signing an Assembly</span></span>

<span data-ttu-id="c87cf-216">Po uzyskaniu lub utworzeniu klucza publicznego należy użyć [konsolidatora zestawu (Al. exe)](../tools/al-exe-assembly-linker.md) do skompilowania zestawu i określić opóźnione podpisywanie.</span><span class="sxs-lookup"><span data-stu-id="c87cf-216">After you obtain or create the public key, you use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to compile the assembly and specify delayed signing.</span></span>

<span data-ttu-id="c87cf-217">Następujące polecenie *Al. exe* tworzy zestaw o silnej nazwie satelicki dla aplikacji StringLibrary z pliku *String. ja. resources* :</span><span class="sxs-lookup"><span data-stu-id="c87cf-217">The following *Al.exe* command creates a strong-named satellite assembly for the application StringLibrary from the *strings.ja.resources* file:</span></span>

```console
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk
```

<span data-ttu-id="c87cf-218">Opcja **-delay +** określa, że konsolidator zestawu powinien opóźnić podpisywanie zestawu.</span><span class="sxs-lookup"><span data-stu-id="c87cf-218">The **-delay+** option specifies that the Assembly Linker should delay sign the assembly.</span></span> <span data-ttu-id="c87cf-219">Opcja **-KeyFile** określa nazwę pliku klucza, który zawiera klucz publiczny używany do opóźniania podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="c87cf-219">The **-keyfile** option specifies the name of the key file that contains the public key to use to delay sign the assembly.</span></span>

### <a name="re-signing-an-assembly"></a><span data-ttu-id="c87cf-220">Ponowne podpisywanie zestawu</span><span class="sxs-lookup"><span data-stu-id="c87cf-220">Re-signing an Assembly</span></span>

<span data-ttu-id="c87cf-221">Przed wdrożeniem aplikacji należy ponownie podpisać Wbudowany zestaw satelicki z opóźnieniem przy użyciu pary kluczy rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="c87cf-221">Before you deploy your application, you must re-sign the delay signed satellite assembly with the real key pair.</span></span> <span data-ttu-id="c87cf-222">Można to zrobić za pomocą *SN. exe*.</span><span class="sxs-lookup"><span data-stu-id="c87cf-222">You can do this by using *Sn.exe*.</span></span>

<span data-ttu-id="c87cf-223">Następujące polecenie *SN. exe* znakuje *StringLibrary. resources. dll* z parą kluczy przechowywaną w pliku *RealKeyPair. snk*.</span><span class="sxs-lookup"><span data-stu-id="c87cf-223">The following *Sn.exe* command signs *StringLibrary.resources.dll* with the key pair stored in the file *RealKeyPair.snk*.</span></span> <span data-ttu-id="c87cf-224">Opcja **– R** określa, że wcześniej podpisany lub opóźniony zestaw podpisany z opóźnieniem ma być podpisywany.</span><span class="sxs-lookup"><span data-stu-id="c87cf-224">The **–R** option specifies that a previously signed or delay signed assembly is to be re-signed.</span></span>

```console
sn –R StringLibrary.resources.dll RealKeyPair.snk
```

### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a><span data-ttu-id="c87cf-225">Instalowanie zestawu satelickiego w globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="c87cf-225">Installing a Satellite Assembly in the Global Assembly Cache</span></span>

<span data-ttu-id="c87cf-226">Gdy środowisko uruchomieniowe wyszukuje zasoby w procesie rezerwowym zasobów, najpierw przeszukuje [globalną pamięć podręczną zestawów](../app-domains/gac.md) .</span><span class="sxs-lookup"><span data-stu-id="c87cf-226">When the runtime searches for resources in the resource fallback process, it looks in the [global assembly cache](../app-domains/gac.md) first.</span></span> <span data-ttu-id="c87cf-227">(Aby uzyskać więcej informacji, zobacz sekcję "proces rezerwowy zasobów" tematu [pakowanie i wdrażanie zasobów](packaging-and-deploying-resources-in-desktop-apps.md) ). Gdy tylko zestaw satelicki zostanie podpisany przy użyciu silnej nazwy, można go zainstalować w globalnej pamięci podręcznej zestawów przy użyciu [Global Assembly Cache Tool (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="c87cf-227">(For more information, see the "Resource Fallback Process" section of the [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md) topic.) As soon as a satellite assembly is signed with a strong name, it can be installed in the global assembly cache by using the [Global Assembly Cache Tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span></span>

<span data-ttu-id="c87cf-228">Następujące polecenie *Gacutil. exe* instaluje *StringLibrary. resources. dll*\* w globalnej pamięci podręcznej zestawów:</span><span class="sxs-lookup"><span data-stu-id="c87cf-228">The following *Gacutil.exe* command installs *StringLibrary.resources.dll*\* in the global assembly cache:</span></span>

```console
gacutil -i:StringLibrary.resources.dll
```

<span data-ttu-id="c87cf-229">**/I** opcja określa, że *Gacutil. exe* powinien zainstalować określony zestaw w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="c87cf-229">The **/i** option specifies that *Gacutil.exe* should install the specified assembly into the global assembly cache.</span></span> <span data-ttu-id="c87cf-230">Po zainstalowaniu zestawu satelickiego w pamięci podręcznej zasoby, które zawiera, staną się dostępne dla wszystkich aplikacji, które są przeznaczone do korzystania z zestawu satelickiego.</span><span class="sxs-lookup"><span data-stu-id="c87cf-230">After the satellite assembly is installed in the cache, the resources it contains become available to all applications that are designed to use the satellite assembly.</span></span>

### <a name="resources-in-the-global-assembly-cache-an-example"></a><span data-ttu-id="c87cf-231">Zasoby w globalnej pamięci podręcznej zestawów: przykład</span><span class="sxs-lookup"><span data-stu-id="c87cf-231">Resources in the Global Assembly Cache: An Example</span></span>

<span data-ttu-id="c87cf-232">Poniższy przykład używa metody w bibliotece klas .NET Framework, aby wyodrębnić i zwrócić zlokalizowane powitanie z pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="c87cf-232">The following example uses a method in a .NET Framework class library to extract and return a localized greeting from a resource file.</span></span> <span data-ttu-id="c87cf-233">Biblioteka i jej zasoby są zarejestrowane w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="c87cf-233">The library and its resources are registered in the global assembly cache.</span></span> <span data-ttu-id="c87cf-234">Przykład zawiera zasoby dla angielskiej wersji językowej (Stany Zjednoczone), francuski (Francja), rosyjski (Rosja) i kulturę w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="c87cf-234">The example includes resources for the English (United States), French (France), Russian (Russia), and English cultures.</span></span> <span data-ttu-id="c87cf-235">Język angielski jest kulturą domyślną; jego zasoby są przechowywane w zestawie głównym.</span><span class="sxs-lookup"><span data-stu-id="c87cf-235">English is the default culture; its resources are stored in the main assembly.</span></span> <span data-ttu-id="c87cf-236">Przykładowe opóźnienie polega na podpisaniu biblioteki i jej zestawów satelickich za pomocą klucza publicznego, a następnie ponowne podpisanie ich za pomocą pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="c87cf-236">The example initially delay signs the library and its satellite assemblies with a public key, then re-signs them with a public/private key pair.</span></span> <span data-ttu-id="c87cf-237">Aby utworzyć przykład, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c87cf-237">To create the example, do the following:</span></span>

1. <span data-ttu-id="c87cf-238">Jeśli nie używasz programu Visual Studio, użyj następującego polecenia [silnej nazwy (SN. exe)](../tools/sn-exe-strong-name-tool.md) , aby utworzyć parę kluczy publiczny/prywatny o nazwie *ResKey. snk*:</span><span class="sxs-lookup"><span data-stu-id="c87cf-238">If you are not using Visual Studio, use the following [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) command to create a public/private key pair named *ResKey.snk*:</span></span>

    ```console
    sn –k ResKey.snk
    ```

    <span data-ttu-id="c87cf-239">Jeśli używasz programu Visual Studio, Użyj karty **podpisywanie** okna dialogowego **Właściwości** projektu, aby wygenerować plik klucza.</span><span class="sxs-lookup"><span data-stu-id="c87cf-239">If you are using Visual Studio, use the **Signing** tab of the project **Properties** dialog box to generate the key file.</span></span>

2. <span data-ttu-id="c87cf-240">Użyj poniższego polecenia [silnej nazwy (SN. exe)](../tools/sn-exe-strong-name-tool.md) , aby utworzyć plik klucza publicznego o nazwie *PublicKey. snk*:</span><span class="sxs-lookup"><span data-stu-id="c87cf-240">Use the following [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) command to create a public key file named *PublicKey.snk*:</span></span>

    ```console
    sn –p ResKey.snk PublicKey.snk
    ```

3. <span data-ttu-id="c87cf-241">Utwórz plik zasobów o nazwie *Strings. resx* , aby zawierał zasób domyślnej kultury.</span><span class="sxs-lookup"><span data-stu-id="c87cf-241">Create a resource file named *Strings.resx* to contain the resource for the default culture.</span></span> <span data-ttu-id="c87cf-242">Przechowaj pojedynczy ciąg o `Greeting` nazwie, którego wartość to "jak to zrobić"?</span><span class="sxs-lookup"><span data-stu-id="c87cf-242">Store a single string named `Greeting` whose value is "How do you do?"</span></span> <span data-ttu-id="c87cf-243">w tym pliku.</span><span class="sxs-lookup"><span data-stu-id="c87cf-243">in that file.</span></span>

4. <span data-ttu-id="c87cf-244">Aby wskazać, że "en" jest kulturą domyślną aplikacji, Dodaj następujący <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> atrybut do pliku AssemblyInfo aplikacji lub do głównego pliku kodu źródłowego, który zostanie skompilowany do głównego zestawu aplikacji:</span><span class="sxs-lookup"><span data-stu-id="c87cf-244">To indicate that "en" is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly:</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
    [!code-vb[Conceptual.Resources.Satellites#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]

5. <span data-ttu-id="c87cf-245">Dodanie obsługi dodatkowych kultur (kultur en-US, fr-FR i ru-RU) do aplikacji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c87cf-245">Add support for additional cultures (the en-US, fr-FR, and ru-RU cultures) to the application as follows:</span></span>

    - <span data-ttu-id="c87cf-246">Aby zapewnić obsługę kultury "en-US" lub angielski (Stany Zjednoczone), Utwórz plik zasobów o nazwie *Strings. en-us. resx* lub *String. en-us. txt*i Zapisz w nim pojedynczy ciąg o nazwie `Greeting` "Hello!".</span><span class="sxs-lookup"><span data-stu-id="c87cf-246">To support the "en-US" or English (United States) culture, create a resource file named *Strings.en-US.resx* or *Strings.en-US.txt*, and store in it a single string named `Greeting` whose value is "Hello!".</span></span>

    - <span data-ttu-id="c87cf-247">Aby zapewnić kulturę "fr-FR" lub francuski (Francja), Utwórz plik zasobów o nazwie *Strings.fr-fr. resx* lub *Strings.fr-fr. txt* i Zapisz w nim pojedynczy ciąg o nazwie `Greeting` "szczęśliwe jour!".</span><span class="sxs-lookup"><span data-stu-id="c87cf-247">To support the "fr-FR" or French (France) culture, create a resource file named *Strings.fr-FR.resx* or *Strings.fr-FR.txt* and store in it a single string named `Greeting` whose value is "Bon jour!".</span></span>

    - <span data-ttu-id="c87cf-248">Aby zapewnić obsługę kultury "ru-RU" lub rosyjski (Rosja), Utwórz plik zasobów o nazwie *Strings.ru-RU. resx* lub *Strings.ru-RU. txt* i Zapisz w nim pojedynczy ciąg o nazwie `Greeting` "Привет!".</span><span class="sxs-lookup"><span data-stu-id="c87cf-248">To support the "ru-RU" or Russian (Russia) culture, create a resource file named *Strings.ru-RU.resx* or *Strings.ru-RU.txt* and store in it a single string named `Greeting` whose value is "Привет!".</span></span>

6. <span data-ttu-id="c87cf-249">Użyj programu [Resgen. exe](../tools/resgen-exe-resource-file-generator.md) , aby skompilować każdy plik tekstowy lub XML do pliku binarnego. resources.</span><span class="sxs-lookup"><span data-stu-id="c87cf-249">Use [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary .resources file.</span></span> <span data-ttu-id="c87cf-250">Dane wyjściowe to zestaw plików, które mają taką samą nazwę pliku głównego jak pliki *resx* lub *txt* , ale rozszerzenie *. resources* .</span><span class="sxs-lookup"><span data-stu-id="c87cf-250">The output is a set of files that have the same root file name as the *.resx* or *.txt* files, but a *.resources* extension.</span></span> <span data-ttu-id="c87cf-251">Jeśli utworzysz przykład w programie Visual Studio, proces kompilacji jest obsługiwany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c87cf-251">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="c87cf-252">Jeśli nie korzystasz z programu Visual Studio, uruchom następujące polecenie, aby skompilować pliki. *resx* do plików *resources* :</span><span class="sxs-lookup"><span data-stu-id="c87cf-252">If you aren't using Visual Studio, run the following command to compile the *.resx* files into *.resources* files:</span></span>

    ```console
    resgen filename
    ```

    <span data-ttu-id="c87cf-253">Gdzie *filename* to opcjonalna ścieżka, nazwa pliku i rozszerzenie pliku *resx* lub tekstu.</span><span class="sxs-lookup"><span data-stu-id="c87cf-253">Where *filename* is the optional path, file name, and extension of the *.resx* or text file.</span></span>

7. <span data-ttu-id="c87cf-254">Skompiluj następujący kod źródłowy dla *StringLibrary. vb* lub *StringLibrary.cs* wraz z zasobami dla kultury domyślnej w zestawie bibliotek podpisanych z opóźnieniem o nazwie *StringLibrary. dll*:</span><span class="sxs-lookup"><span data-stu-id="c87cf-254">Compile the following source code for *StringLibrary.vb* or *StringLibrary.cs* along with the resources for the default culture into a delay signed library assembly named *StringLibrary.dll*:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="c87cf-255">Jeśli używasz wiersza polecenia zamiast programu Visual Studio do utworzenia przykładu, należy zmodyfikować wywołanie konstruktora <xref:System.Resources.ResourceManager> klasy do. `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`</span><span class="sxs-lookup"><span data-stu-id="c87cf-255">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
    [!code-vb[Conceptual.Resources.Satellites#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]

    <span data-ttu-id="c87cf-256">Polecenie dla kompilatora C# jest następujące:</span><span class="sxs-lookup"><span data-stu-id="c87cf-256">The command for the C# compiler is:</span></span>

    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs
    ```

    <span data-ttu-id="c87cf-257">Odpowiednie polecenie kompilatora Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="c87cf-257">The corresponding Visual Basic compiler command is:</span></span>

    ```console
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb
    ```

8. <span data-ttu-id="c87cf-258">Utwórz podkatalog w katalogu głównym aplikacji dla każdej zlokalizowanej kultury obsługiwanej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="c87cf-258">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="c87cf-259">Należy utworzyć podkatalog *en-us*, *fr-fr*i *ru-RU* .</span><span class="sxs-lookup"><span data-stu-id="c87cf-259">You should create an *en-US*, an *fr-FR*, and an *ru-RU* subdirectory.</span></span> <span data-ttu-id="c87cf-260">Program Visual Studio automatycznie tworzy te podkatalogi w ramach procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c87cf-260">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span> <span data-ttu-id="c87cf-261">Ponieważ wszystkie zestawy satelickie mają taką samą nazwę pliku, podkatalogi są używane do przechowywania poszczególnych zestawów satelickich specyficznych dla kultury, dopóki nie zostaną podpisane przy użyciu pary kluczy publicznych/prywatnych.</span><span class="sxs-lookup"><span data-stu-id="c87cf-261">Because all satellite assemblies have the same file name, the subdirectories are used to store individual culture-specific satellite assemblies until they are signed with a public/private key pair.</span></span>

9. <span data-ttu-id="c87cf-262">Osadź poszczególne pliki *zasobów* specyficznych dla kultury w celu opóźniania podpisanych zestawów satelickich i Zapisz je w odpowiednim katalogu.</span><span class="sxs-lookup"><span data-stu-id="c87cf-262">Embed the individual culture-specific *.resources* files into delay signed satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="c87cf-263">Polecenie to zrób dla każdego pliku *resources* :</span><span class="sxs-lookup"><span data-stu-id="c87cf-263">The command to do this for each *.resources* file is:</span></span>

    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk
    ```

    <span data-ttu-id="c87cf-264">gdzie *Culture* jest nazwą kultury.</span><span class="sxs-lookup"><span data-stu-id="c87cf-264">where *culture* is the name of a culture.</span></span> <span data-ttu-id="c87cf-265">W tym przykładzie nazwy kultur to en-US, fr-FR i ru-RU.</span><span class="sxs-lookup"><span data-stu-id="c87cf-265">In this example, the culture names are en-US, fr-FR, and ru-RU.</span></span>

10. <span data-ttu-id="c87cf-266">Podpisz *StringLibrary. dll* przy użyciu [Narzędzia silnej nazwy (SN. exe)](../tools/sn-exe-strong-name-tool.md) w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c87cf-266">Re-sign *StringLibrary.dll* by using the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) as follows:</span></span>

    ```console
    sn –R StringLibrary.dll RealKeyPair.snk
    ```

11. <span data-ttu-id="c87cf-267">Ponowne podpisywanie poszczególnych zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="c87cf-267">Re-sign the individual satellite assemblies.</span></span> <span data-ttu-id="c87cf-268">W tym celu należy użyć [Narzędzia silnej nazwy (SN. exe)](../tools/sn-exe-strong-name-tool.md) w następujący sposób dla każdego zestawu satelickiego:</span><span class="sxs-lookup"><span data-stu-id="c87cf-268">To do this, use the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) as follows for each satellite assembly:</span></span>

    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk
    ```

12. <span data-ttu-id="c87cf-269">Zarejestruj *StringLibrary. dll* i każdy z jej zestawów satelickich w globalnej pamięci podręcznej zestawów przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="c87cf-269">Register *StringLibrary.dll* and each of its satellite assemblies in the global assembly cache by using the following command:</span></span>

    ```console
    gacutil -i filename
    ```

    <span data-ttu-id="c87cf-270">gdzie *filename* jest nazwą pliku do zarejestrowania.</span><span class="sxs-lookup"><span data-stu-id="c87cf-270">where *filename* is the name of the file to register.</span></span>

13. <span data-ttu-id="c87cf-271">Jeśli używasz programu Visual Studio, Utwórz nowy projekt **aplikacji konsoli** o nazwie `Example`, Dodaj odwołanie do *StringLibrary. dll* i Poniższy kod źródłowy, a następnie Skompiluj.</span><span class="sxs-lookup"><span data-stu-id="c87cf-271">If you are using Visual Studio, create a new **Console Application** project named `Example`, add a reference to *StringLibrary.dll* and the following source code to it, and compile.</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
    [!code-vb[Conceptual.Resources.Satellites#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]

    <span data-ttu-id="c87cf-272">Aby skompilować z wiersza polecenia, użyj następującego polecenia dla kompilatora C#:</span><span class="sxs-lookup"><span data-stu-id="c87cf-272">To compile from the command line, use the following command for the C# compiler:</span></span>

    ```console
    csc Example.cs -r:StringLibrary.dll
    ```

    <span data-ttu-id="c87cf-273">Wiersz polecenia dla kompilatora Visual Basic jest:</span><span class="sxs-lookup"><span data-stu-id="c87cf-273">The command line for the Visual Basic compiler is:</span></span>

    ```console
    vbc Example.vb -r:StringLibrary.dll
    ```

14. <span data-ttu-id="c87cf-274">Uruchom *przykład. exe*.</span><span class="sxs-lookup"><span data-stu-id="c87cf-274">Run *Example.exe*.</span></span>

## <a name="see-also"></a><span data-ttu-id="c87cf-275">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c87cf-275">See also</span></span>

- [<span data-ttu-id="c87cf-276">Opakowanie i wdrażanie zasobów</span><span class="sxs-lookup"><span data-stu-id="c87cf-276">Packaging and Deploying Resources</span></span>](packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="c87cf-277">Opóźnione podpisywanie zestawu</span><span class="sxs-lookup"><span data-stu-id="c87cf-277">Delay Signing an Assembly</span></span>](../../standard/assembly/delay-sign.md)
- [<span data-ttu-id="c87cf-278">Al. exe (Konsolidator zestawu)</span><span class="sxs-lookup"><span data-stu-id="c87cf-278">Al.exe (Assembly Linker)</span></span>](../tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="c87cf-279">SN. exe (Narzędzie silnej nazwy)</span><span class="sxs-lookup"><span data-stu-id="c87cf-279">Sn.exe (Strong Name Tool)</span></span>](../tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="c87cf-280">Gacutil. exe (Global Assembly Cache Tool)</span><span class="sxs-lookup"><span data-stu-id="c87cf-280">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="c87cf-281">Zasoby w aplikacjach klasycznych</span><span class="sxs-lookup"><span data-stu-id="c87cf-281">Resources in Desktop Apps</span></span>](index.md)
