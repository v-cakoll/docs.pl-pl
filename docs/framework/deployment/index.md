---
title: Wdrażanie programu .NET Framework i aplikacji
description: Zacznij od wdrożenia platformy .NET przy użyciu aplikacji. Platforma .NET udostępnia aplikacje bez wpływu na składniki prywatne, domyślnie kontrolowane udostępnianie kodu i nie tylko.
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
ms.openlocfilehash: cce888c962c9ab83c13cce4040eb9ba50270972d
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803505"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="8c1bd-104">Wdrażanie programu .NET Framework i aplikacji</span><span class="sxs-lookup"><span data-stu-id="8c1bd-104">Deploying the .NET Framework and Applications</span></span>

<span data-ttu-id="8c1bd-105">Ten artykuł pomoże Ci rozpocząć wdrażanie .NET Framework przy użyciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-105">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="8c1bd-106">Większość informacji jest przeznaczona dla deweloperów, producentów OEM i administratorów przedsiębiorstwa.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-106">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="8c1bd-107">Użytkownicy, którzy chcą zainstalować .NET Framework na swoich komputerach, powinni przeczytać [instalowanie .NET Framework](../install/index.md).</span><span class="sxs-lookup"><span data-stu-id="8c1bd-107">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](../install/index.md).</span></span>

## <a name="key-deployment-resources"></a><span data-ttu-id="8c1bd-108">Zasoby wdrażania kluczy</span><span class="sxs-lookup"><span data-stu-id="8c1bd-108">Key Deployment Resources</span></span>

<span data-ttu-id="8c1bd-109">Skorzystaj z poniższych linków do innych tematów MSDN, aby uzyskać szczegółowe informacje na temat wdrażania i obsługi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-109">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>

<span data-ttu-id="8c1bd-110">**Instalacja i wdrożenie**</span><span class="sxs-lookup"><span data-stu-id="8c1bd-110">**Setup and deployment**</span></span>

- <span data-ttu-id="8c1bd-111">Ogólne informacje o instalacji i wdrożeniu:</span><span class="sxs-lookup"><span data-stu-id="8c1bd-111">General installer and deployment information:</span></span>

  - <span data-ttu-id="8c1bd-112">Opcje Instalatora:</span><span class="sxs-lookup"><span data-stu-id="8c1bd-112">Installer options:</span></span>

    - [<span data-ttu-id="8c1bd-113">Instalator sieci Web</span><span class="sxs-lookup"><span data-stu-id="8c1bd-113">Web installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [<span data-ttu-id="8c1bd-114">Instalator w trybie offline</span><span class="sxs-lookup"><span data-stu-id="8c1bd-114">Offline installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - <span data-ttu-id="8c1bd-115">Tryby instalacji:</span><span class="sxs-lookup"><span data-stu-id="8c1bd-115">Installation modes:</span></span>

    - [<span data-ttu-id="8c1bd-116">Instalacja w trybie dyskretnym</span><span class="sxs-lookup"><span data-stu-id="8c1bd-116">Silent installation</span></span>](deployment-guide-for-developers.md#chaining_custom)

    - [<span data-ttu-id="8c1bd-117">Wyświetlanie interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="8c1bd-117">Displaying a UI</span></span>](deployment-guide-for-developers.md#chaining_default)

  - [<span data-ttu-id="8c1bd-118">Zmniejszenie liczby ponownych uruchomień systemu podczas instalacji .NET Framework 4,5</span><span class="sxs-lookup"><span data-stu-id="8c1bd-118">Reducing system restarts during .NET Framework 4.5 installations</span></span>](reducing-system-restarts.md)

  - [<span data-ttu-id="8c1bd-119">Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8c1bd-119">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- <span data-ttu-id="8c1bd-120">Wdrażanie .NET Framework za pomocą aplikacji klienckiej (dla deweloperów):</span><span class="sxs-lookup"><span data-stu-id="8c1bd-120">Deploying the .NET Framework with a client application (for developers):</span></span>

  - <span data-ttu-id="8c1bd-121">[Korzystanie z InstallShield](deployment-guide-for-developers.md#installshield-deployment) w projekcie instalacji i wdrażania</span><span class="sxs-lookup"><span data-stu-id="8c1bd-121">[Using InstallShield](deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>

  - [<span data-ttu-id="8c1bd-122">Korzystanie z aplikacji ClickOnce programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8c1bd-122">Using a Visual Studio ClickOnce application</span></span>](deployment-guide-for-developers.md#clickonce-deployment)

  - [<span data-ttu-id="8c1bd-123">Tworzenie pakietu instalacyjnego WiX</span><span class="sxs-lookup"><span data-stu-id="8c1bd-123">Creating a WiX installation package</span></span>](deployment-guide-for-developers.md#wix)

  - [<span data-ttu-id="8c1bd-124">Używanie instalatora niestandardowego</span><span class="sxs-lookup"><span data-stu-id="8c1bd-124">Using a custom installer</span></span>](deployment-guide-for-developers.md#chaining)

  - <span data-ttu-id="8c1bd-125">[Dodatkowe informacje](deployment-guide-for-developers.md) dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="8c1bd-125">[Additional information](deployment-guide-for-developers.md) for developers</span></span>

- <span data-ttu-id="8c1bd-126">Wdrażanie .NET Framework (dla producentów OEM i administratorów):</span><span class="sxs-lookup"><span data-stu-id="8c1bd-126">Deploying the .NET Framework (for OEMs and administrators):</span></span>

  - [<span data-ttu-id="8c1bd-127">Zestaw Windows Assessment and Deployment Kit (ADK)</span><span class="sxs-lookup"><span data-stu-id="8c1bd-127">Windows Assessment and Deployment Kit (ADK)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [<span data-ttu-id="8c1bd-128">Podręcznik administratora</span><span class="sxs-lookup"><span data-stu-id="8c1bd-128">Administrator's guide</span></span>](guide-for-administrators.md)

<span data-ttu-id="8c1bd-129">**Obsługa techniczna**</span><span class="sxs-lookup"><span data-stu-id="8c1bd-129">**Servicing**</span></span>

- <span data-ttu-id="8c1bd-130">Aby uzyskać ogólne informacje, zobacz [blog .NET Framework](https://devblogs.microsoft.com/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="8c1bd-130">For general information, see the [.NET Framework blog](https://devblogs.microsoft.com/dotnet/).</span></span>

- [<span data-ttu-id="8c1bd-131">Wykrywanie wersji</span><span class="sxs-lookup"><span data-stu-id="8c1bd-131">Detecting versions</span></span>](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [<span data-ttu-id="8c1bd-132">Wykrywanie pakietów usług i aktualizacji</span><span class="sxs-lookup"><span data-stu-id="8c1bd-132">Detecting service packs and updates</span></span>](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a><span data-ttu-id="8c1bd-133">Funkcje upraszczające wdrażanie</span><span class="sxs-lookup"><span data-stu-id="8c1bd-133">Features That Simplify Deployment</span></span>

<span data-ttu-id="8c1bd-134">.NET Framework udostępnia wiele podstawowych funkcji, które ułatwiają wdrażanie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="8c1bd-134">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>

- <span data-ttu-id="8c1bd-135">Aplikacje bez wpływu.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-135">No-impact applications.</span></span>

     <span data-ttu-id="8c1bd-136">Ta funkcja zapewnia izolację aplikacji i eliminuje konflikty bibliotek DLL.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-136">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="8c1bd-137">Domyślnie składniki nie wpływają na inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-137">By default, components do not affect other applications.</span></span>

- <span data-ttu-id="8c1bd-138">Składniki prywatne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-138">Private components by default.</span></span>

     <span data-ttu-id="8c1bd-139">Domyślnie składniki są wdrażane w katalogu aplikacji i są widoczne tylko dla aplikacji zawierającej.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-139">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>

- <span data-ttu-id="8c1bd-140">Kontrolowane udostępnianie kodu.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-140">Controlled code sharing.</span></span>

     <span data-ttu-id="8c1bd-141">Udostępnianie kodu wymaga jawnego udostępnienia kodu do udostępnienia zamiast zachowania domyślnego.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-141">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>

- <span data-ttu-id="8c1bd-142">Przechowywanie wersji równoległych.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-142">Side-by-side versioning.</span></span>

     <span data-ttu-id="8c1bd-143">Wiele wersji składnika lub aplikacji może współistnieć, możesz wybrać wersje, które mają być używane, a środowisko uruchomieniowe języka wspólnego wymusza zasady przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-143">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>

- <span data-ttu-id="8c1bd-144">Wdrażanie i replikacja polecenia XCOPY.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-144">XCOPY deployment and replication.</span></span>

     <span data-ttu-id="8c1bd-145">Samodzielne i samodzielne składniki i aplikacje można wdrażać bez wpisów lub zależności rejestru.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-145">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>

- <span data-ttu-id="8c1bd-146">Aktualizacje na bieżąco.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-146">On-the-fly updates.</span></span>

     <span data-ttu-id="8c1bd-147">Administratorzy mogą używać hostów, takich jak ASP.NET, do aktualizowania bibliotek DLL programu, nawet na komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-147">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>

- <span data-ttu-id="8c1bd-148">Integracja z Instalator Windows.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-148">Integration with the Windows Installer.</span></span>

     <span data-ttu-id="8c1bd-149">Podczas wdrażania aplikacji są dostępne anonse, publikowanie, naprawa i instalacja na żądanie.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-149">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>

- <span data-ttu-id="8c1bd-150">Wdrażanie w przedsiębiorstwie.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-150">Enterprise deployment.</span></span>

     <span data-ttu-id="8c1bd-151">Ta funkcja zapewnia łatwą dystrybucję oprogramowania, w tym za pomocą Active Directory.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-151">This feature provides easy software distribution, including using Active Directory.</span></span>

- <span data-ttu-id="8c1bd-152">Pobieranie i buforowanie.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-152">Downloading and caching.</span></span>

     <span data-ttu-id="8c1bd-153">Pobieranie przyrostowe zachowuje mniejsze ilości plików, a składniki mogą być izolowane do użytku tylko przez aplikację w przypadku wdrożenia o niskim wpływie.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-153">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>

- <span data-ttu-id="8c1bd-154">Kod częściowo zaufany.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-154">Partially trusted code.</span></span>

     <span data-ttu-id="8c1bd-155">Tożsamość jest oparta na kodzie zamiast użytkownika i nie pojawiają się okna dialogowe certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-155">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>

## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="8c1bd-156">Pakowanie i dystrybucja .NET Framework aplikacji</span><span class="sxs-lookup"><span data-stu-id="8c1bd-156">Packaging and Distributing .NET Framework Applications</span></span>

<span data-ttu-id="8c1bd-157">Niektóre informacje dotyczące pakowania i wdrażania dla .NET Framework są opisane w innych sekcjach dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-157">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="8c1bd-158">Te sekcje zawierają informacje o samoopisywanych jednostkach nazywanych [zestawami](../../standard/assembly/index.md), które nie wymagają żadnych wpisów rejestru, [zestawów o silnych nazwach](../../standard/assembly/strong-named.md), które zapewniają unikatowość nazw i uniemożliwiają fałszowanie nazw oraz [przechowywanie wersji zestawu](../../standard/assembly/versioning.md), który dotyczy wielu problemów związanych z konfliktami dll.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-158">Those sections provide information about the self-describing units called [assemblies](../../standard/assembly/index.md), which require no registry entries, [strong-named assemblies](../../standard/assembly/strong-named.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../standard/assembly/versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="8c1bd-159">Poniższe sekcje zawierają informacje o pakowaniu i dystrybucji aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-159">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>

### <a name="packaging"></a><span data-ttu-id="8c1bd-160">Packaging</span><span class="sxs-lookup"><span data-stu-id="8c1bd-160">Packaging</span></span>

<span data-ttu-id="8c1bd-161">.NET Framework udostępnia następujące opcje dla aplikacji pakietów:</span><span class="sxs-lookup"><span data-stu-id="8c1bd-161">The .NET Framework provides the following options for packaging applications:</span></span>

- <span data-ttu-id="8c1bd-162">Jako pojedynczy zestaw lub zbiór zestawów.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-162">As a single assembly or as a collection of assemblies.</span></span>

     <span data-ttu-id="8c1bd-163">Po wybraniu tej opcji wystarczy użyć plików. dll lub. exe, ponieważ zostały one skompilowane.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-163">With this option, you simply use the .dll or .exe files as they were built.</span></span>

- <span data-ttu-id="8c1bd-164">Jako pliki cabinet (CAB).</span><span class="sxs-lookup"><span data-stu-id="8c1bd-164">As cabinet (CAB) files.</span></span>

     <span data-ttu-id="8c1bd-165">W przypadku tej opcji kompresujesz pliki do plików CAB, aby dokonać dystrybucji lub pobrać mniej czasochłonne.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-165">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>

- <span data-ttu-id="8c1bd-166">Jako pakiet Instalator Windows lub w innych formatach Instalatora.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-166">As a Windows Installer package or in other installer formats.</span></span>

     <span data-ttu-id="8c1bd-167">Za pomocą tej opcji można tworzyć pliki MSI do użycia w Instalator Windows lub spakować aplikację do użycia z innym instalatorem.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-167">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>

### <a name="distribution"></a><span data-ttu-id="8c1bd-168">Dystrybucja</span><span class="sxs-lookup"><span data-stu-id="8c1bd-168">Distribution</span></span>

<span data-ttu-id="8c1bd-169">.NET Framework udostępnia następujące opcje dystrybucji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="8c1bd-169">The .NET Framework provides the following options for distributing applications:</span></span>

- <span data-ttu-id="8c1bd-170">Użyj polecenia XCOPY lub FTP.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-170">Use XCOPY or FTP.</span></span>

     <span data-ttu-id="8c1bd-171">Ponieważ aplikacje środowiska uruchomieniowego języka wspólnego nie opisują ani nie wymagają żadnych wpisów rejestru, można użyć polecenia XCOPY lub FTP, aby po prostu skopiować aplikację do odpowiedniego katalogu.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-171">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="8c1bd-172">Aplikację można następnie uruchomić z tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-172">The application can then be run from that directory.</span></span>

- <span data-ttu-id="8c1bd-173">Użyj pobierania kodu.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-173">Use code download.</span></span>

     <span data-ttu-id="8c1bd-174">Jeśli aplikacja jest dystrybuowana przez Internet lub za pośrednictwem firmowej sieci intranet, można po prostu pobrać kod na komputer i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-174">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>

- <span data-ttu-id="8c1bd-175">Użyj programu Instalatora, takiego jak Instalator Windows 2,0.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-175">Use an installer program such as Windows Installer 2.0.</span></span>

     <span data-ttu-id="8c1bd-176">Instalator Windows 2,0 może instalować, naprawiać lub usuwać zestawy .NET Framework w globalnej pamięci podręcznej zestawów i w katalogach prywatnych.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-176">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>

### <a name="installation-location"></a><span data-ttu-id="8c1bd-177">Lokalizacja instalacji</span><span class="sxs-lookup"><span data-stu-id="8c1bd-177">Installation Location</span></span>

<span data-ttu-id="8c1bd-178">Aby określić, gdzie wdrożyć zestawy aplikacji, aby można je było znaleźć w środowisku uruchomieniowym, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="8c1bd-178">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](how-the-runtime-locates-assemblies.md).</span></span>

<span data-ttu-id="8c1bd-179">Zagadnienia dotyczące zabezpieczeń mogą również mieć wpływ na sposób wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-179">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="8c1bd-180">Uprawnienia zabezpieczeń są udzielane do kodu zarządzanego zgodnie z miejscem, w którym znajduje się kod.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-180">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="8c1bd-181">Wdrożenie aplikacji lub składnika w lokalizacji, w której odbierze małe zaufanie, takie jak Internet, ogranicza działanie aplikacji lub składnika.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-181">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="8c1bd-182">Aby uzyskać więcej informacji na temat zagadnień dotyczących wdrażania i zabezpieczeń, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="8c1bd-182">For more information about deployment and security considerations, see [Code Access Security Basics](../misc/code-access-security-basics.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="8c1bd-183">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="8c1bd-183">Related Topics</span></span>

|<span data-ttu-id="8c1bd-184">Tytuł</span><span class="sxs-lookup"><span data-stu-id="8c1bd-184">Title</span></span>|<span data-ttu-id="8c1bd-185">Opis</span><span class="sxs-lookup"><span data-stu-id="8c1bd-185">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="8c1bd-186">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="8c1bd-186">How the Runtime Locates Assemblies</span></span>](how-the-runtime-locates-assemblies.md)|<span data-ttu-id="8c1bd-187">Opisuje, jak środowisko uruchomieniowe języka wspólnego określa zestaw, który ma być używany do realizacji żądania powiązania.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-187">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|
|[<span data-ttu-id="8c1bd-188">Najlepsze praktyki dotyczące ładowania zestawu</span><span class="sxs-lookup"><span data-stu-id="8c1bd-188">Best Practices for Assembly Loading</span></span>](best-practices-for-assembly-loading.md)|<span data-ttu-id="8c1bd-189">Omawia sposoby, aby uniknąć problemów z tożsamością typu, które mogą prowadzić do <xref:System.InvalidCastException> <xref:System.MissingMethodException> innych błędów.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-189">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|
|[<span data-ttu-id="8c1bd-190">Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="8c1bd-190">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)|<span data-ttu-id="8c1bd-191">Opisuje Menedżera ponownego uruchamiania, który uniemożliwia ponowne uruchomienie w miarę możliwości, i wyjaśnia, jak aplikacje instalujące .NET Framework mogą korzystać z tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-191">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|
|[<span data-ttu-id="8c1bd-192">Przewodnik wdrażania dla administratorów</span><span class="sxs-lookup"><span data-stu-id="8c1bd-192">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)|<span data-ttu-id="8c1bd-193">Wyjaśnia, w jaki sposób administrator systemu może wdrożyć .NET Framework i zależności systemu w sieci za pomocą usługi Microsoft Endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-193">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>|
|[<span data-ttu-id="8c1bd-194">Przewodnik wdrażania dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="8c1bd-194">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)|<span data-ttu-id="8c1bd-195">Wyjaśnia, w jaki sposób deweloperzy mogą instalować .NET Framework na komputerach użytkowników przy użyciu ich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-195">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|
|[<span data-ttu-id="8c1bd-196">Wdrażanie aplikacji, usług i składników</span><span class="sxs-lookup"><span data-stu-id="8c1bd-196">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="8c1bd-197">W tym artykule omówiono opcje wdrażania w programie Visual Studio, w tym instrukcje dotyczące publikowania aplikacji przy użyciu technologii ClickOnce i Instalator Windows.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-197">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>|
|[<span data-ttu-id="8c1bd-198">Publikowanie aplikacji ClickOnce</span><span class="sxs-lookup"><span data-stu-id="8c1bd-198">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="8c1bd-199">Opisuje sposób tworzenia pakietów aplikacji Windows Forms i wdrażania jej przy użyciu technologii ClickOnce na komputerach klienckich w sieci.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-199">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|
|[<span data-ttu-id="8c1bd-200">Opakowanie i wdrażanie zasobów</span><span class="sxs-lookup"><span data-stu-id="8c1bd-200">Packaging and Deploying Resources</span></span>](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="8c1bd-201">Opisuje model gwiazdy, którego .NET Framework używa do pakowania i wdrażania zasobów; obejmuje konwencje nazewnictwa zasobów, proces rezerwowy i alternatywy pakietów.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-201">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|
|[<span data-ttu-id="8c1bd-202">Wdrażanie aplikacji międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="8c1bd-202">Deploying an Interop Application</span></span>](../interop/deploying-an-interop-application.md)|<span data-ttu-id="8c1bd-203">Wyjaśnia sposób dostarczania i instalowania aplikacji międzyoperacyjnych, które zwykle zawierają zestaw .NET Framework klienta, co najmniej jeden zestaw międzyoperacyjny reprezentujący różne biblioteki typów modelu COM oraz co najmniej jeden zarejestrowany składnik COM.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-203">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|
|[<span data-ttu-id="8c1bd-204">Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="8c1bd-204">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="8c1bd-205">Opisuje sposób dyskretnego uruchamiania i śledzenia procesu instalacji .NET Framework podczas wyświetlania własnego widoku postępu instalacji.</span><span class="sxs-lookup"><span data-stu-id="8c1bd-205">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|

## <a name="see-also"></a><span data-ttu-id="8c1bd-206">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c1bd-206">See also</span></span>

- [<span data-ttu-id="8c1bd-207">Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="8c1bd-207">Development Guide</span></span>](../development-guide.md)
