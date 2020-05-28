---
title: Przykład migracji do programu .NET Core 3.1
description: Przedstawiamy sposób migrowania przykładowych aplikacji przeznaczonych dla .NET Framework do programu .NET Core 3,1.
ms.date: 05/12/2020
ms.openlocfilehash: 5e8b1219cf4bd89ada5b71a60ef27eaabb94997c
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144271"
---
# <a name="example-of-migrating-to-net-core-31"></a><span data-ttu-id="a7c7d-103">Przykład migracji do programu .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="a7c7d-103">Example of migrating to .NET Core 3.1</span></span>

<span data-ttu-id="a7c7d-104">W tym rozdziale przedstawimy praktyczne wskazówki ułatwiające przeprowadzenie migracji istniejącej aplikacji z .NET Framework na platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-104">In this chapter, we present practical guidelines to help you perform a migration of your existing application from .NET Framework to .NET Core.</span></span>

<span data-ttu-id="a7c7d-105">Oferujemy dobrze strukturalny proces, który można wykonać, i najważniejsze zagadnienia, które należy wziąć pod uwagę w każdym kroku.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-105">We present a well-structured process you can follow and the most important things to consider on each step.</span></span>

<span data-ttu-id="a7c7d-106">Następnie należy udokumentować proces migracji krok po kroku dla przykładowej aplikacji klasycznej, zarówno z WinForms, jak i wersji WPF.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-106">We then document a step-by-step migration process for a sample desktop application, both from WinForms and WPF versions.</span></span>

## <a name="migration-process-overview"></a><span data-ttu-id="a7c7d-107">Przegląd procesu migracji</span><span class="sxs-lookup"><span data-stu-id="a7c7d-107">Migration process overview</span></span>

<span data-ttu-id="a7c7d-108">Proces migracji składa się z czterech kolejnych kroków:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-108">The migration process consists of four sequential steps:</span></span>

1. <span data-ttu-id="a7c7d-109">**Przygotowanie**: zrozumienie zależności, dla których projekt musi mieć pomysł dotyczący tego, co dzieje się z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-109">**Preparation**: Understand the dependencies the project has to have an idea of what's ahead.</span></span> <span data-ttu-id="a7c7d-110">W tym kroku przeniesiesz bieżący projekt do stanu, który upraszcza punkt startowy migracji.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-110">In this step, you take the current project into a state that simplifies the startup point for the migration.</span></span>

2. <span data-ttu-id="a7c7d-111">**Migruj plik projektu:** projekty platformy .NET Core używają nowego formatu projektu w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-111">**Migrate Project File:** .NET Core projects use the new SDK-style project format.</span></span> <span data-ttu-id="a7c7d-112">Utwórz nowy plik projektu o tym formacie lub zaktualizuj go, aby użyć stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-112">Create a new project file with this format or update the one you have to use the SDK style.</span></span>

3. <span data-ttu-id="a7c7d-113">**Napraw kod i skompiluj:** Kompilowanie kodu w programie .NET Core — różnice na poziomie interfejsu API między .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-113">**Fix code and build:** Build the code in .NET Core addressing API-level differences between .NET Framework and .NET Core.</span></span> <span data-ttu-id="a7c7d-114">W razie potrzeby zaktualizuj pakiety innych firm do tych, które obsługują platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-114">If needed, update third-party packages to the ones that support .NET Core.</span></span>

4. <span data-ttu-id="a7c7d-115">**Uruchom i Testuj:** Mogą występować różnice, które nie są wyświetlane do czasu uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-115">**Run and test:** There might be differences that don't show up until run time.</span></span> <span data-ttu-id="a7c7d-116">Dlatego nie zapomnij uruchomić aplikacji i przetestuj, że wszystko działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-116">So, don't forget to run the application and test that everything works as expected.</span></span>

### <a name="preparation"></a><span data-ttu-id="a7c7d-117">Przygotowanie</span><span class="sxs-lookup"><span data-stu-id="a7c7d-117">Preparation</span></span>

#### <a name="migrate-packagesconfig-file"></a><span data-ttu-id="a7c7d-118">Migruj plik Packages. config</span><span class="sxs-lookup"><span data-stu-id="a7c7d-118">Migrate packages.config file</span></span>

<span data-ttu-id="a7c7d-119">W aplikacji .NET Framework wszystkie odwołania do pakietów zewnętrznych są deklarowane w pliku *Packages. config* .</span><span class="sxs-lookup"><span data-stu-id="a7c7d-119">In a .NET Framework application, all references to external packages are declared in the *packages.config* file.</span></span> <span data-ttu-id="a7c7d-120">W programie .NET Core nie ma już potrzeby używania pliku *Packages. config* .</span><span class="sxs-lookup"><span data-stu-id="a7c7d-120">In .NET Core, there's no longer the need to use the *packages.config* file.</span></span> <span data-ttu-id="a7c7d-121">Zamiast tego należy użyć właściwości [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) wewnątrz pliku projektu, aby określić pakiety NuGet dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-121">Instead, use the [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) property inside the project file to specify the NuGet packages for your app.</span></span>

<span data-ttu-id="a7c7d-122">Dlatego należy przejść z jednego formatu na inny.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-122">So, you need to transition from one format to another.</span></span> <span data-ttu-id="a7c7d-123">Aktualizację można wykonać ręcznie, biorąc pod uwagę zależności zawarte w pliku *Packages. config* i migruje je do pliku projektu `PackageReference` .</span><span class="sxs-lookup"><span data-stu-id="a7c7d-123">You can do the update manually, taking the dependencies contained in the *packages.config* file and migrating them to the project file with the `PackageReference` format.</span></span> <span data-ttu-id="a7c7d-124">Możesz również pozwolić programowi Visual Studio na wykonywanie zadań: kliknij prawym przyciskiem myszy plik *Packages. config* i wybierz opcję **Migruj pakiety. config do PackageReference** .</span><span class="sxs-lookup"><span data-stu-id="a7c7d-124">Or, you can let Visual Studio do the work for you: right-click on the *packages.config* file and select the **Migrate packages.config to PackageReference** option.</span></span>

#### <a name="verify-every-dependency-compatibility-in-net-core"></a><span data-ttu-id="a7c7d-125">Weryfikowanie każdej zgodności zależności w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="a7c7d-125">Verify every dependency compatibility in .NET Core</span></span>

<span data-ttu-id="a7c7d-126">Po przeprowadzeniu migracji odwołań do pakietów należy sprawdzić wszystkie odwołania w celu zapewnienia zgodności.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-126">Once you've migrated the package references, you must check each reference for compatibility.</span></span> <span data-ttu-id="a7c7d-127">Możesz zapoznać się z zależnościami poszczególnych pakietów NuGet, których aplikacja używa w [NuGet.org](https://www.nuget.org/). Jeśli pakiet ma .NET Standard zależności, wówczas będzie działał w środowisku .NET Core, ponieważ program .NET Core 3,1 [obsługuje](../../standard/net-standard.md#net-implementation-support) wszystkie wersje .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-127">You can explore the dependencies of each NuGet package your application is using on [nuget.org](https://www.nuget.org/). If the package has .NET Standard dependencies, then it's going to work on .NET Core because .NET Core 3.1 [supports](../../standard/net-standard.md#net-implementation-support) all versions of .NET Standard.</span></span> <span data-ttu-id="a7c7d-128">Na poniższej ilustracji przedstawiono zależności `Castle.Windsor` pakietu:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-128">The following image shows the dependencies for the `Castle.Windsor` package:</span></span>

![Zrzut ekranu przedstawiający zależności NuGet dla pakietu Castle. Windsor](./media/example-migration-core/nuget-dependencies.png)

<span data-ttu-id="a7c7d-130">Aby sprawdzić zgodność pakietu, można użyć narzędzia <https://fuget.org> oferującego bardziej szczegółowe informacje o wersjach i zależnościach.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-130">To check the package compatibility, you can use the tool <https://fuget.org> that offers a more detailed information about versions and dependencies.</span></span>

<span data-ttu-id="a7c7d-131">Być może projekt odwołuje się do starszych wersji pakietu, które nie obsługują platformy .NET Core, ale mogą znaleźć nowsze wersje, które je obsługują.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-131">Maybe the project is referencing older package versions that don't support .NET Core, but you might find newer versions that do support it.</span></span> <span data-ttu-id="a7c7d-132">Dlatego aktualizowanie pakietów do nowszych wersji jest generalnie dobrym zaleceniem.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-132">So, updating packages to newer versions is generally a good recommendation.</span></span> <span data-ttu-id="a7c7d-133">Należy jednak wziąć pod uwagę, że aktualizacja wersji pakietu może wprowadzić pewne istotne zmiany, które wymusić zaktualizowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-133">However, you should consider that updating the package version can introduce some breaking changes that would force you to update your code.</span></span>

<span data-ttu-id="a7c7d-134">Co się stanie, jeśli nie znajdziesz zgodnej wersji?</span><span class="sxs-lookup"><span data-stu-id="a7c7d-134">What happens if you don't find a compatible version?</span></span> <span data-ttu-id="a7c7d-135">Co zrobić, jeśli nie chcesz zaktualizować wersji pakietu ze względu na te zmiany?</span><span class="sxs-lookup"><span data-stu-id="a7c7d-135">What if you just don't want to update the version of a package because of these breaking changes?</span></span> <span data-ttu-id="a7c7d-136">Nie martw się, ponieważ można zależeć od .NET Framework pakietów z aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-136">Don't worry because it's possible to depend on .NET Framework packages from a .NET Core application.</span></span> <span data-ttu-id="a7c7d-137">Nie zapomnij go przetestować w szerokim stopniu, ponieważ może to spowodować błędy w czasie wykonywania, jeśli pakiet zewnętrzny wywoła interfejs API, który nie jest dostępny w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-137">Don't forget to test it extensively because it can cause run-time errors if the external package calls an API that isn't available on .NET Core.</span></span> <span data-ttu-id="a7c7d-138">Jest to doskonałe rozwiązanie w przypadku korzystania ze starego pakietu, który nie zostanie zaktualizowany i można go przekierować do pracy z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-138">This is great for when you're using an old package that isn't going to be updated and you can just retarget to work on the .NET Core.</span></span>

#### <a name="check-for-api-compatibility"></a><span data-ttu-id="a7c7d-139">Sprawdź zgodność interfejsu API</span><span class="sxs-lookup"><span data-stu-id="a7c7d-139">Check for API compatibility</span></span>

<span data-ttu-id="a7c7d-140">Ze względu na to, że powierzchnia interfejsu API w .NET Framework i .NET Core jest podobna, ale nie identyczna, należy sprawdzić, które interfejsy API są dostępne w środowisku .NET Core, a które nie.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-140">Since the API surface in .NET Framework and .NET Core is similar but not identical, you must check which APIs are available on .NET Core and which aren't.</span></span> <span data-ttu-id="a7c7d-141">Można użyć narzędzia analizatora przenośności platformy .NET do wykorzystania interfejsów API, które nie są dostępne w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-141">You can use the .NET Portability Analyzer tool to surface APIs used that aren't present on .NET Core.</span></span> <span data-ttu-id="a7c7d-142">Sprawdza on poziom binarny swojej aplikacji, wyodrębnia wszystkie interfejsy API, które są wywoływane, a następnie wyświetla listę interfejsów API, które nie są dostępne w ramach platformy docelowej (w tym przypadku .NET Core 3,1).</span><span class="sxs-lookup"><span data-stu-id="a7c7d-142">It looks at the binary level of your app, extracts all the APIs that are called, and then lists which APIs aren't available on your target framework (.NET Core 3.1 in this case).</span></span>

<span data-ttu-id="a7c7d-143">Więcej informacji o tym narzędziu można znaleźć pod adresem:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-143">You can find more information about this tool at:</span></span>

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

<span data-ttu-id="a7c7d-144">Interesujący aspekt tego narzędzia polega na tym, że tylko prezentuje różnice wynikające z własnego kodu, a nie kodu z pakietów zewnętrznych, których nie można zmienić.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-144">An interesting aspect of this tool is that it only surfaces the differences from your own code and not code from external packages, which you can't change.</span></span> <span data-ttu-id="a7c7d-145">Należy pamiętać, że należy zaktualizować większość z tych pakietów, aby działały one z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-145">Remember you should have updated most of these packages to make them work with .NET Core.</span></span>

### <a name="migrate-project-file"></a><span data-ttu-id="a7c7d-146">Migruj plik projektu</span><span class="sxs-lookup"><span data-stu-id="a7c7d-146">Migrate project file</span></span>

#### <a name="create-the-new-net-core-project"></a><span data-ttu-id="a7c7d-147">Utwórz nowy projekt platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="a7c7d-147">Create the new .NET Core project</span></span>

<span data-ttu-id="a7c7d-148">W większości przypadków należy zaktualizować istniejący projekt do nowego formatu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-148">In most of the cases, you'll want to update your existing project to the new .NET Core format.</span></span> <span data-ttu-id="a7c7d-149">Można jednak również utworzyć nowy projekt przy zachowaniu Starego.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-149">However, you can also create a new project while maintaining the old one.</span></span> <span data-ttu-id="a7c7d-150">Główną wadą z aktualizacji starego projektu jest utrata wsparcia projektanta, co może być dla Ciebie ważne.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-150">The main drawback from updating the old project is that you lose designer support, which may be important for you.</span></span> <span data-ttu-id="a7c7d-151">Jeśli chcesz nadal korzystać z projektanta, musisz utworzyć nowy projekt .NET Core równolegle ze starym i współużytkowanymi zasobami.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-151">If you want to keep using the designer, you must create a new .NET Core project in parallel with the old one and share assets.</span></span> <span data-ttu-id="a7c7d-152">Jeśli musisz zmodyfikować elementy interfejsu użytkownika w projektancie, możesz przełączyć się do starego projektu, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-152">If you need to modify UI elements in the designer, you can switch to the old project to do that.</span></span> <span data-ttu-id="a7c7d-153">Ze względu na to, że zasoby są połączone, zostaną również zaktualizowane w projekcie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-153">And since assets are linked, they'll be updated in the .NET Core project as well.</span></span>

<span data-ttu-id="a7c7d-154">[Projekt w stylu zestawu SDK](../../core/project-sdk/msbuild-props.md) dla platformy .NET Core jest znacznie prostszy niż format projektu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-154">The [SDK-style project](../../core/project-sdk/msbuild-props.md) for .NET Core is a lot simpler than .NET Framework's project format.</span></span> <span data-ttu-id="a7c7d-155">Oprócz powyższych `PackageReference` wpisów nie trzeba robić więcej.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-155">And apart from the previously mentioned `PackageReference` entries, you won't need to do much more.</span></span> <span data-ttu-id="a7c7d-156">Nowy format projektu [Domyślnie](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects)zawiera pewne rozszerzenia plików, takie jak `.cs` i `.xaml` pliki, bez konieczności jawnego umieszczania ich w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-156">The new project format includes certain file extensions [by default](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects), such as `.cs` and `.xaml` files, without the need to explicitly include them in the project file.</span></span>

#### <a name="assemblyinfo-considerations"></a><span data-ttu-id="a7c7d-157">Zagadnienia dotyczące Assembly.info</span><span class="sxs-lookup"><span data-stu-id="a7c7d-157">Assembly.info considerations</span></span>

<span data-ttu-id="a7c7d-158">Atrybuty są generowane automatycznie w projektach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-158">Attributes are autogenerated on .NET Core projects.</span></span> <span data-ttu-id="a7c7d-159">Jeśli projekt zawiera plik *AssemblyInfo.cs* , definicje zostaną zduplikowane, co spowoduje konflikty kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-159">If the project contains an *AssemblyInfo.cs* file, the definitions will be duplicated, which will cause compilation conflicts.</span></span> <span data-ttu-id="a7c7d-160">Możesz usunąć starszy plik *AssemblyInfo.cs* lub wyłączyć automatyczne generowanie, dodając następujący wpis do pliku projektu .NET Core:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-160">You can delete the older *AssemblyInfo.cs* file or disable autogeneration by adding the following entry to the .NET Core project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a><span data-ttu-id="a7c7d-161">Zasoby</span><span class="sxs-lookup"><span data-stu-id="a7c7d-161">Resources</span></span>

<span data-ttu-id="a7c7d-162">Zasoby osadzone są uwzględniane automatycznie, ale zasoby nie są, więc należy przeprowadzić migrację zasobów do nowego pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-162">Embedded resources are included automatically but resources aren't, so you need to migrate the resources to the new project file.</span></span>

#### <a name="package-references"></a><span data-ttu-id="a7c7d-163">Odwołania do pakietu</span><span class="sxs-lookup"><span data-stu-id="a7c7d-163">Package references</span></span>

<span data-ttu-id="a7c7d-164">Za pomocą opcji **Migruj pakiety. config do PackageReference** można łatwo przenieść odwołania do pakietów zewnętrznych do nowego formatu, jak wspomniano wcześniej.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-164">With the **Migrate packages.config to PackageReference** option, you can easily move your external package references to the new format as previously mentioned.</span></span>

#### <a name="update-package-references"></a><span data-ttu-id="a7c7d-165">Aktualizuj odwołania do pakietów</span><span class="sxs-lookup"><span data-stu-id="a7c7d-165">Update package references</span></span>

<span data-ttu-id="a7c7d-166">Zaktualizuj wersje odnalezionych pakietów jako zgodne, jak pokazano w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-166">Update the versions of the packages you've found to be compatible, as shown in the previous section.</span></span>

### <a name="fix-the-code-and-build"></a><span data-ttu-id="a7c7d-167">Popraw kod i skompiluj</span><span class="sxs-lookup"><span data-stu-id="a7c7d-167">Fix the code and build</span></span>

#### <a name="microsoftwindowscompatibility"></a><span data-ttu-id="a7c7d-168">Microsoft. Windows. Compatibility</span><span class="sxs-lookup"><span data-stu-id="a7c7d-168">Microsoft.Windows.Compatibility</span></span>

<span data-ttu-id="a7c7d-169">Jeśli aplikacja jest zależna od interfejsów API, które nie są dostępne w środowisku .NET Core, takich jak rejestr, listy ACL lub WCF, należy dołączyć odwołanie do `Microsoft.Windows.Compatibility` pakietu w celu dodania tych interfejsów API właściwych dla systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-169">If your application depends on APIs that aren't available on .NET Core, such as Registry, ACLs, or WCF, you have to include a reference to the `Microsoft.Windows.Compatibility` package to add these Windows-specific APIs.</span></span> <span data-ttu-id="a7c7d-170">Działają one na platformie .NET Core, ale nie są uwzględniane, ponieważ nie są na wielu platformach.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-170">They work on .NET Core but aren't included as they aren't cross-platform.</span></span>

<span data-ttu-id="a7c7d-171">Istnieje narzędzie o nazwie API Analyzer ( <https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer> ), które pomaga identyfikować interfejsy API, które nie są zgodne z kodem.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-171">There's a tool called API Analyzer (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) that helps you identify APIs that aren't compatible with your code.</span></span>

#### <a name="use-if-directives"></a><span data-ttu-id="a7c7d-172">Użyj \# dyrektywy if</span><span class="sxs-lookup"><span data-stu-id="a7c7d-172">Use \#if directives</span></span>

<span data-ttu-id="a7c7d-173">Jeśli potrzebujesz różnych ścieżek wykonywania podczas określania wartości docelowej .NET Framework i .NET Core, musisz użyć stałych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-173">If you need different execution paths when targeting .NET Framework and .NET Core, you should use compilation constants.</span></span> <span data-ttu-id="a7c7d-174">Dodaj kilka \# dyrektyw if do kodu, aby zachować tę samą bazę kodu dla obu celów.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-174">Add some \#if directives to your code to keep the same code base for both targets.</span></span>

#### <a name="technologies-not-available-on-net-core"></a><span data-ttu-id="a7c7d-175">Technologie niedostępne w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="a7c7d-175">Technologies not available on .NET Core</span></span>

<span data-ttu-id="a7c7d-176">Niektóre technologie nie są dostępne na platformie .NET Core, na przykład:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-176">Some technologies aren't available on .NET Core, such as:</span></span>

* <span data-ttu-id="a7c7d-177">Domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="a7c7d-177">AppDomains</span></span>
* <span data-ttu-id="a7c7d-178">Komunikacji zdalnej</span><span class="sxs-lookup"><span data-stu-id="a7c7d-178">Remoting</span></span>
* <span data-ttu-id="a7c7d-179">Zabezpieczenia dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="a7c7d-179">Code Access Security</span></span>
* <span data-ttu-id="a7c7d-180">Serwer WCF</span><span class="sxs-lookup"><span data-stu-id="a7c7d-180">WCF Server</span></span>
* <span data-ttu-id="a7c7d-181">Przepływ pracy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a7c7d-181">Windows Workflow</span></span>

<span data-ttu-id="a7c7d-182">Dlatego należy znaleźć zamiennik dla tych technologii, jeśli są one używane w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-182">That's why you need to find a replacement for these technologies if you're using them in your application.</span></span> <span data-ttu-id="a7c7d-183">Aby uzyskać więcej informacji, zobacz [technologie .NET Framework niedostępne w artykule .NET Core](../../core/porting/net-framework-tech-unavailable.md) .</span><span class="sxs-lookup"><span data-stu-id="a7c7d-183">For more information, see the [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md) article.</span></span>

#### <a name="regenerate-autogenerated-clients"></a><span data-ttu-id="a7c7d-184">Wygeneruj ponownie generowanych klientów</span><span class="sxs-lookup"><span data-stu-id="a7c7d-184">Regenerate autogenerated clients</span></span>

<span data-ttu-id="a7c7d-185">Jeśli aplikacja używa automatycznie generowanego kodu, takiego jak klient WCF, może być konieczne ponowne wygenerowanie tego kodu dla programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-185">If your application uses autogenerated code, such as a WCF client, you may need to regenerate this code to target .NET Core.</span></span> <span data-ttu-id="a7c7d-186">Czasami można znaleźć brakujące odwołania, ponieważ mogą one nie być dołączone jako część domyślnego zestawu zestawów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-186">Sometimes, you can find some missing references since they may not be included as part of the default .NET Core assemblies set.</span></span> <span data-ttu-id="a7c7d-187">Za pomocą narzędzia takiego jak <https://apisof.net/> , można łatwo zlokalizować zestaw, w którym brakuje brakujące odwołanie, i dodać go z NuGet.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-187">Using a tool like <https://apisof.net/>, you can easily locate the assembly the missing reference lives in and add it from NuGet.</span></span>

#### <a name="rolling-back-package-versions"></a><span data-ttu-id="a7c7d-188">Wycofywanie wersji pakietu</span><span class="sxs-lookup"><span data-stu-id="a7c7d-188">Rolling back package versions</span></span>

<span data-ttu-id="a7c7d-189">Zgodnie z ogólną zasadą zalecamy, aby lepiej zaktualizować każdą wersję pakietu, aby była zgodna z platformą .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-189">As a general rule, we've previously stated that you better update every single package version to be compatible with .NET Core.</span></span> <span data-ttu-id="a7c7d-190">Można jednak znaleźć, że dla zaktualizowanej i zgodnej wersji zestawu nie jest to płatność wyłączona.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-190">However, you can find that targeting an updated and compatible version of an assembly just doesn't pay off.</span></span> <span data-ttu-id="a7c7d-191">Jeśli koszt zmiany nie jest akceptowalny, można rozważyć wycofywanie wersji pakietu, zachowując te, które są używane w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-191">If the cost of change isn't acceptable, you can consider rolling back package versions keeping the ones you use on .NET Framework.</span></span> <span data-ttu-id="a7c7d-192">Chociaż mogą nie być ukierunkowane na platformę .NET Core, powinny one działać prawidłowo, chyba że wywoła nieobsługiwane interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-192">Although they may not be targeting .NET Core, they should work well unless they call some unsupported APIs.</span></span>

### <a name="run-and-test"></a><span data-ttu-id="a7c7d-193">Uruchamianie i testowanie</span><span class="sxs-lookup"><span data-stu-id="a7c7d-193">Run and test</span></span>

<span data-ttu-id="a7c7d-194">Po skompilowaniu aplikacji bez błędów można uruchomić ostatni krok migracji, testując każdą funkcję.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-194">Once you have your application building with no errors, you can start the last step of the migration by testing every functionality.</span></span>

<span data-ttu-id="a7c7d-195">W tym ostatnim kroku można znaleźć kilka różnych problemów w zależności od złożoności aplikacji oraz zależności i interfejsów API, których używasz.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-195">In this final step, you can find several different issues depending on the complexity of your application and the dependencies and APIs you're using.</span></span>

<span data-ttu-id="a7c7d-196">Na przykład w przypadku korzystania z plików konfiguracji (*App. config*) mogą wystąpić błędy w czasie wykonywania, podobnie jak w przypadku nieobecnych sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-196">For example, if you use configuration files (*app.config*), you may find some errors at run time like Configuration Sections not present.</span></span> <span data-ttu-id="a7c7d-197">Korzystanie z `Microsoft.Extensions.Configuration` pakietu NuGet powinno rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-197">Using the `Microsoft.Extensions.Configuration` NuGet package should fix that error.</span></span>

<span data-ttu-id="a7c7d-198">Kolejną przyczyną błędów jest użycie `BeginInvoke` metod i, `EndInvoke` ponieważ nie są one obsługiwane przez platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-198">Another reason for errors is the use of the `BeginInvoke` and `EndInvoke` methods because they aren't supported on .NET Core.</span></span> <span data-ttu-id="a7c7d-199">Nie są one obsługiwane przez platformę .NET Core, ponieważ mają one zależność od komunikacji zdalnej, która nie istnieje w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-199">They aren't supported on .NET Core because they have a dependency on Remoting, which doesn't exist on .NET Core.</span></span> <span data-ttu-id="a7c7d-200">Aby rozwiązać ten problem, spróbuj użyć `await` słowa kluczowego (jeśli jest dostępne) lub <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-200">To solve this issue, try to use the `await` keyword (when available) or the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="a7c7d-201">Analizatory zgodności umożliwiają identyfikowanie interfejsów API i wzorców kodu w kodzie, które mogą powodować problemy w czasie wykonywania za pomocą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-201">You can use compatibility analyzers to let you identify APIs and code patterns in your code that can potentially cause problems at run time with .NET Core.</span></span> <span data-ttu-id="a7c7d-202">Przejdź do programu <https://github.com/dotnet/platform-compat> i użyj analizatora interfejsów API platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-202">Go to <https://github.com/dotnet/platform-compat> and use the .NET API analyzer on your project.</span></span>

## <a name="migrating-a-windows-forms-application"></a><span data-ttu-id="a7c7d-203">Migrowanie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7c7d-203">Migrating a Windows Forms application</span></span>

<span data-ttu-id="a7c7d-204">Aby zaprezentować pełny proces migracji aplikacji Windows Forms, wybrano migrację przykładowej aplikacji eShop <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> .</span><span class="sxs-lookup"><span data-stu-id="a7c7d-204">To showcase a complete migration process of a Windows Forms application, we've chosen to migrate the eShop sample application available at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms>.</span></span> <span data-ttu-id="a7c7d-205">Pełny wynik migracji można znaleźć pod adresem <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> .</span><span class="sxs-lookup"><span data-stu-id="a7c7d-205">You can find the complete result of the migration at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms>.</span></span>

<span data-ttu-id="a7c7d-206">Ta aplikacja pokazuje katalog produktów i umożliwia użytkownikowi nawigację, filtrowanie i wyszukiwanie produktów.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-206">This application shows a product catalog and allows the user to navigate, filter, and search for products.</span></span> <span data-ttu-id="a7c7d-207">Z punktu widzenia architektury aplikacja korzysta z zewnętrznej usługi WCF, która służy jako elewacja bazy danych zaplecza.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-207">From an architecture point of view, the app relies on an external WCF service that serves as a façade to a back-end database.</span></span>

<span data-ttu-id="a7c7d-208">Główne okno aplikacji można zobaczyć na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-208">You can see the main application window in the following picture:</span></span>

![Główne okno aplikacji](./media/example-migration-core/main-application-window.png)

<span data-ttu-id="a7c7d-210">Jeśli otworzysz plik projektu *. csproj* , zobaczysz coś w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-210">If you open the *.csproj* project file, you can see something like this:</span></span>

![Zrzut ekranu przedstawiający zawartość pliku csproj](./media/example-migration-core/csproj-file.png)

<span data-ttu-id="a7c7d-212">Jak wspomniano wcześniej, projekt .NET Core ma bardziej zwarty styl i należy zmigrować strukturę projektu do nowego stylu zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-212">As previously mentioned, .NET Core project has a more compact style and you need to migrate the project structure to the new .NET Core SDK style.</span></span>

<span data-ttu-id="a7c7d-213">W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt Windows Forms i wybierz polecenie **Zwolnij**  >  **edycję**projektu.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-213">In the Solution Explorer, right click on the Windows Forms project and select **Unload Project** > **Edit**.</span></span>

<span data-ttu-id="a7c7d-214">Teraz można zaktualizować plik. csproj.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-214">Now you can update the .csproj file.</span></span> <span data-ttu-id="a7c7d-215">Usuniesz całą zawartość i zastąpisz ją przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-215">You'll delete the entire content and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWindowsForms>true</UseWindowsForms>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

<span data-ttu-id="a7c7d-216">Zapisz i Załaduj ponownie projekt.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-216">Save and reload the project.</span></span> <span data-ttu-id="a7c7d-217">Teraz zakończysz aktualizowanie pliku projektu, a projekt jest przeznaczony dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-217">You're now done updating the project file and the project is targeting the .NET Core.</span></span>

<span data-ttu-id="a7c7d-218">Jeśli kompilujesz projekt w tym momencie, znajdziesz pewne błędy związane z odwołaniem klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-218">If you compile the project at this point, you'll find some errors related to the WCF client reference.</span></span> <span data-ttu-id="a7c7d-219">Ponieważ ten kod jest generowany automatycznie, należy ponownie wygenerować go w celu utworzenia docelowej platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-219">Since this code is autogenerated, you must regenerate it to target .NET Core.</span></span>

![Zrzut ekranu przedstawiający błędy kompilacji w programie Visual Studio](./media/example-migration-core/winforms-compilation-errors.png)

<span data-ttu-id="a7c7d-221">Usuń plik *Reference.cs* i Wygeneruj nowego klienta usługi.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-221">Delete the *Reference.cs* file and generate a new Service Client.</span></span>

<span data-ttu-id="a7c7d-222">Kliknij prawym przyciskiem myszy pozycję **połączone usługi** i wybierz opcję **Dodaj usługę połączoną** .</span><span class="sxs-lookup"><span data-stu-id="a7c7d-222">Right-click on **Connected Services** and select the **Add Connected Service** option.</span></span>

![Zrzut ekranu przedstawiający menu połączone usługi z wybraną opcją Dodaj podłączoną usługę](./media/example-migration-core/add-connected-service.png)

<span data-ttu-id="a7c7d-224">Zostanie otwarte okno połączone usługi.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-224">The Connected Services window opens.</span></span> <span data-ttu-id="a7c7d-225">Wybierz opcję **usługi sieci Web Microsoft WCF** .</span><span class="sxs-lookup"><span data-stu-id="a7c7d-225">Select the **Microsoft WCF Web Service** option.</span></span>

![Zrzut ekranu okna połączone usługi](./media/example-migration-core/connected-services-window.png)

<span data-ttu-id="a7c7d-227">Jeśli masz usługę WCF w tym samym rozwiązaniu, co w tym przykładzie, możesz wybrać opcję **odnajdywania** zamiast określania adresu URL usługi.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-227">If you have the WCF Service in the same solution as we have in this example, you can select the **Discover** option instead of specifying a service URL.</span></span>

![Zrzut ekranu przedstawiający okno Konfigurowanie odwołania do usługi sieci Web WCF](./media/example-migration-core/configure-wcf-reference.png)

<span data-ttu-id="a7c7d-229">Po zlokalizowaniu usługi narzędzie odzwierciedla kontrakt interfejsu API zaimplementowany przez usługę.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-229">Once the service is located, the tool reflects the API contract implemented by the service.</span></span> <span data-ttu-id="a7c7d-230">Zmień nazwę przestrzeni nazw, aby była `eShopServiceReference` wyświetlana na poniższym obrazie:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-230">Change the name of the namespace to be `eShopServiceReference` as shown in the following image:</span></span>

![Zrzut ekranu kontraktu interfejsu API i zmieniono przestrzeń nazw](./media/example-migration-core/api-contract-namespace.png)

<span data-ttu-id="a7c7d-232">Wybierz przycisk **Zakończ** .</span><span class="sxs-lookup"><span data-stu-id="a7c7d-232">Select the **Finish** button.</span></span> <span data-ttu-id="a7c7d-233">Po czasie zobaczysz wygenerowany kod.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-233">After a while, you'll see the generated code.</span></span>

<span data-ttu-id="a7c7d-234">Powinny być widoczne trzy automatycznie generowane pliki:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-234">You should see three autogenerated files:</span></span>

1. <span data-ttu-id="a7c7d-235">*Wprowadzenie*: link do usługi GitHub w celu udostępnienia pewnych informacji na temat usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-235">*Getting Started*: a link to GitHub to provide some information on WCF.</span></span>
2. <span data-ttu-id="a7c7d-236">*Usługę połączoną. JSON*: parametry konfiguracji do nawiązania połączenia z usługą.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-236">*ConnectedService.json*: configuration parameters to connect to the service.</span></span>
3. <span data-ttu-id="a7c7d-237">*Reference.cs*: rzeczywisty kod klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-237">*Reference.cs*: the actual WCF client code.</span></span>

![Zrzut ekranu okna Eksplorator rozwiązań z trzema generowanymi automatycznie plikami](./media/example-migration-core/autogenerated-files.png)

<span data-ttu-id="a7c7d-239">Jeśli kompilujesz ponownie, zobaczysz wiele błędów pochodzących z plików *. cs* w folderze *pomocnika* .</span><span class="sxs-lookup"><span data-stu-id="a7c7d-239">If you compile again, you'll see many errors coming from *.cs* files inside the *Helper* folder.</span></span> <span data-ttu-id="a7c7d-240">Ten folder był obecny w wersji .NET Framework, ale nie znajduje się w starej *csproj*.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-240">This folder was present in the .NET Framework version but not included in the old *.csproj*.</span></span> <span data-ttu-id="a7c7d-241">Ale z nowym projektem w stylu zestawu SDK każdy plik kodu znajdujący się poniżej lokalizacji pliku projektu jest domyślnie uwzględniany.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-241">But with the new SDK-style project, every code file present underneath the project file location is included by default.</span></span> <span data-ttu-id="a7c7d-242">Oznacza to, że nowy projekt .NET Core próbuje skompilować pliki w folderze *pomocnika* .</span><span class="sxs-lookup"><span data-stu-id="a7c7d-242">That is, the new .NET Core project tries to compile the files inside the *Helper* folder.</span></span> <span data-ttu-id="a7c7d-243">Ponieważ ten folder nie jest wymagany, można go bezpiecznie usunąć.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-243">Since that folder isn't needed, you can safely delete it.</span></span>

<span data-ttu-id="a7c7d-244">Po ponownym skompilowaniu projektu i jego wykonaniu nie będą widoczne obrazy produktu.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-244">If you compile the project again and execute it, you won't see the product images.</span></span> <span data-ttu-id="a7c7d-245">Problem polega na tym, że ścieżka do plików jest nieco nieznacznie zmieniana.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-245">The problem is that now the path to the files has slightly changed.</span></span> <span data-ttu-id="a7c7d-246">Aby rozwiązać ten problem, należy dodać kolejny poziom głębokości w ścieżce, a następnie zaktualizować w pliku `CatalogView.cs` wiersz:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-246">To fix this issue, you need to add another level of depth in the path, updating in the file `CatalogView.cs` the line:</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="a7c7d-247">na</span><span class="sxs-lookup"><span data-stu-id="a7c7d-247">to</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="a7c7d-248">Po tej zmianie można sprawdzić, czy aplikacja jest uruchamiana i uruchamiana zgodnie z oczekiwaniami w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-248">After this change, you can check that the application launches and runs as expected on .NET Core.</span></span>

## <a name="migrating-a-wpf-application"></a><span data-ttu-id="a7c7d-249">Migrowanie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="a7c7d-249">Migrating a WPF application</span></span>

<span data-ttu-id="a7c7d-250">Użyjemy `Shop.ClassicWPF` przykładowej aplikacji do przeprowadzenia migracji.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-250">We'll use the `Shop.ClassicWPF` sample application to perform the migration.</span></span> <span data-ttu-id="a7c7d-251">Na poniższej ilustracji przedstawiono zrzut ekranu aplikacji przed migracją:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-251">The following image shows a screenshot of the app before migration:</span></span>

![Przykładowa aplikacja przed migracją](./media/example-migration-core/app-before-migration.png)

<span data-ttu-id="a7c7d-253">Ta aplikacja używa lokalnej bazy danych SQL Server Express do przechowywania informacji o katalogu produktów.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-253">This application uses a local SQL Server Express database to hold the product catalog information.</span></span> <span data-ttu-id="a7c7d-254">Ta baza danych jest dostępna bezpośrednio z aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-254">This database is accessed directly from the WPF application.</span></span>

<span data-ttu-id="a7c7d-255">Najpierw należy zaktualizować plik *. csproj* do nowego stylu zestawu SDK używanego przez aplikacje platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-255">First, you must update the *.csproj* file to the new SDK style used by .NET Core applications.</span></span> <span data-ttu-id="a7c7d-256">Wykonaj te same czynności, które zostały opisane w Windows Forms migracji: spowoduje to zwolnienie projektu, otwarcie pliku *. csproj* , zaktualizowanie jego zawartości i ponowne załadowanie projektu.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-256">You'll follow the same steps described in the Windows Forms migration: you'll unload the project, open the *.csproj* file, update its contents, and reload the project.</span></span>

<span data-ttu-id="a7c7d-257">W takim przypadku Usuń całą zawartość pliku *. csproj* i zastąp go następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-257">In this case, delete all the content of the *.csproj* file and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWPF>true</UseWPF>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

<span data-ttu-id="a7c7d-258">Jeśli załadujesz ponownie projekt i skompilujesz go, zostanie wyświetlony następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-258">If you reload the project and compile it, you'll get the following error:</span></span>

![Zrzut ekranu przedstawiający błędy kompilacji w programie Visual Studio](./media/example-migration-core/wpf-compilation-error.png)

<span data-ttu-id="a7c7d-260">Ze względu na to, że usunięto całą zawartość *. csproj* , w starym projekcie brakuje specyfikacji odwołania do projektu.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-260">Since you've deleted all the *.csproj* contents, you've lost a project reference specification present in the old project.</span></span> <span data-ttu-id="a7c7d-261">Wystarczy dodać ten wiersz do pliku *. csproj* , aby uwzględnić odwołanie do projektu z powrotem:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-261">You just need to add this line to the *.csproj* file to include the project reference back:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

<span data-ttu-id="a7c7d-262">Możesz również pozwolić programowi Visual Studio na pomoc, klikając prawym przyciskiem myszy węzeł **zależności** i wybierając polecenie **Dodaj odwołanie do projektu**.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-262">You can also let Visual Studio help you by right-clicking on the **Dependencies** node and selecting **Add Project Reference**.</span></span> <span data-ttu-id="a7c7d-263">Wybierz projekt z rozwiązania i kliknij przycisk **OK**:</span><span class="sxs-lookup"><span data-stu-id="a7c7d-263">Select the project from the solution and click **OK**:</span></span>

![Zrzut ekranu okna dialogowego Menedżera odwołań z wybranym projektem eshop.](./media/example-migration-core/reference-manager.png)

<span data-ttu-id="a7c7d-265">Po dodaniu brakującego odwołania do projektu aplikacja kompiluje i uruchamia się zgodnie z oczekiwaniami w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a7c7d-265">Once you add the missing project reference, the application compiles and runs as expected on .NET Core.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a7c7d-266">[Poprzedni](windows-migration.md) 
> [Dalej](deploy-modern-applications.md)</span><span class="sxs-lookup"><span data-stu-id="a7c7d-266">[Previous](windows-migration.md)
[Next](deploy-modern-applications.md)</span></span>
