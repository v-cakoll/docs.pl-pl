---
title: Wdrażanie programu .NET Framework i aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2686d0db966192606656167d6e505f34ded333f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="daeb4-102">Wdrażanie programu .NET Framework i aplikacji</span><span class="sxs-lookup"><span data-stu-id="daeb4-102">Deploying the .NET Framework and Applications</span></span>
<span data-ttu-id="daeb4-103">Ten artykuł pomoże rozpocząć wdrażanie programu .NET Framework z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="daeb4-103">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="daeb4-104">Większość informacji jest przeznaczony dla deweloperów, OEM i Administratorzy przedsiębiorstwa.</span><span class="sxs-lookup"><span data-stu-id="daeb4-104">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="daeb4-105">Użytkownicy chcący zainstalować program .NET Framework na swoich komputerach należy przeczytać [Instalowanie programu .NET Framework](~/docs/framework/install/index.md).</span><span class="sxs-lookup"><span data-stu-id="daeb4-105">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](~/docs/framework/install/index.md).</span></span>  
  
## <a name="key-deployment-resources"></a><span data-ttu-id="daeb4-106">Zasoby dotyczące wdrażania klucza</span><span class="sxs-lookup"><span data-stu-id="daeb4-106">Key Deployment Resources</span></span>  
 <span data-ttu-id="daeb4-107">Informacje na temat wdrażania i obsługi programu .NET Framework, użyj następujących łączy do innych tematów w witrynie MSDN.</span><span class="sxs-lookup"><span data-stu-id="daeb4-107">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>  
  
 <span data-ttu-id="daeb4-108">**Instalacji i wdrażania**</span><span class="sxs-lookup"><span data-stu-id="daeb4-108">**Setup and deployment**</span></span>  
  
-   <span data-ttu-id="daeb4-109">Ogólne informacje dotyczące Instalatora i wdrażania:</span><span class="sxs-lookup"><span data-stu-id="daeb4-109">General installer and deployment information:</span></span>  
  
    -   <span data-ttu-id="daeb4-110">Opcje Instalatora:</span><span class="sxs-lookup"><span data-stu-id="daeb4-110">Installer options:</span></span>  
  
        -   [<span data-ttu-id="daeb4-111">Instalator sieci Web</span><span class="sxs-lookup"><span data-stu-id="daeb4-111">Web installer</span></span>](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
        -   [<span data-ttu-id="daeb4-112">Instalatora w trybie offline</span><span class="sxs-lookup"><span data-stu-id="daeb4-112">Offline installer</span></span>](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
    -   <span data-ttu-id="daeb4-113">Tryby instalacji:</span><span class="sxs-lookup"><span data-stu-id="daeb4-113">Installation modes:</span></span>  
  
        -   [<span data-ttu-id="daeb4-114">Instalacja w trybie dyskretnym</span><span class="sxs-lookup"><span data-stu-id="daeb4-114">Silent installation</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)  
  
        -   [<span data-ttu-id="daeb4-115">Wyświetlanie interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="daeb4-115">Displaying a UI</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)  
  
    -   [<span data-ttu-id="daeb4-116">Zmniejszenie liczby systemu ponownych uruchomień podczas instalacji programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="daeb4-116">Reducing system restarts during .NET Framework 4.5 installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)  
  
    -   [<span data-ttu-id="daeb4-117">Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="daeb4-117">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
  
-   <span data-ttu-id="daeb4-118">Wdrażanie programu .NET Framework z aplikacją klienta (dla deweloperów):</span><span class="sxs-lookup"><span data-stu-id="daeb4-118">Deploying the .NET Framework with a client application (for developers):</span></span>  
  
    -   <span data-ttu-id="daeb4-119">[Przy użyciu InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) w projekcie instalacji i wdrażania</span><span class="sxs-lookup"><span data-stu-id="daeb4-119">[Using InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>  
  
    -   [<span data-ttu-id="daeb4-120">Przy użyciu aplikacji ClickOnce usługi Visual Studio</span><span class="sxs-lookup"><span data-stu-id="daeb4-120">Using a Visual Studio ClickOnce application</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)  
  
    -   [<span data-ttu-id="daeb4-121">Tworzenie pakietu instalacyjnego WiX</span><span class="sxs-lookup"><span data-stu-id="daeb4-121">Creating a WiX installation package</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)  
  
    -   [<span data-ttu-id="daeb4-122">Za pomocą instalatora niestandardowego</span><span class="sxs-lookup"><span data-stu-id="daeb4-122">Using a custom installer</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)  
  
    -   <span data-ttu-id="daeb4-123">[Dodatkowe informacje](../../../docs/framework/deployment/deployment-guide-for-developers.md) dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="daeb4-123">[Additional information](../../../docs/framework/deployment/deployment-guide-for-developers.md) for developers</span></span>  
  
-   <span data-ttu-id="daeb4-124">Wdrażanie programu .NET Framework (dla producentów OEM i Administratorzy):</span><span class="sxs-lookup"><span data-stu-id="daeb4-124">Deploying the .NET Framework (for OEMs and administrators):</span></span>  
  
    -   [<span data-ttu-id="daeb4-125">Windows Assessment and Deployment Kit (ADK)</span><span class="sxs-lookup"><span data-stu-id="daeb4-125">Windows Assessment and Deployment Kit (ADK)</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=254976)  
  
    -   [<span data-ttu-id="daeb4-126">Podręcznik administratora</span><span class="sxs-lookup"><span data-stu-id="daeb4-126">Administrator's guide</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)  
  
 <span data-ttu-id="daeb4-127">**Obsługa**</span><span class="sxs-lookup"><span data-stu-id="daeb4-127">**Servicing**</span></span>  
  
-   <span data-ttu-id="daeb4-128">Aby uzyskać ogólne informacje, zobacz [blogu .NET Framework](http://go.microsoft.com/fwlink/p/?LinkId=254977)</span><span class="sxs-lookup"><span data-stu-id="daeb4-128">For general information, see the [.NET Framework blog](http://go.microsoft.com/fwlink/p/?LinkId=254977)</span></span>  
  
-   [<span data-ttu-id="daeb4-129">Wykrywanie wersji</span><span class="sxs-lookup"><span data-stu-id="daeb4-129">Detecting versions</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
  
-   [<span data-ttu-id="daeb4-130">Wykrywanie dodatków service pack i aktualizacje</span><span class="sxs-lookup"><span data-stu-id="daeb4-130">Detecting service packs and updates</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
  
## <a name="features-that-simplify-deployment"></a><span data-ttu-id="daeb4-131">Funkcje, które upraszczają proces wdrażania</span><span class="sxs-lookup"><span data-stu-id="daeb4-131">Features That Simplify Deployment</span></span>  
 <span data-ttu-id="daeb4-132">.NET Framework udostępnia wiele podstawowych funkcji, które ułatwiają wdrażanie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="daeb4-132">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>  
  
-   <span data-ttu-id="daeb4-133">Aplikacje nie wpływu.</span><span class="sxs-lookup"><span data-stu-id="daeb4-133">No-impact applications.</span></span>  
  
     <span data-ttu-id="daeb4-134">Ta funkcja zapewnia izolację aplikacji i eliminuje konflikty biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="daeb4-134">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="daeb4-135">Domyślnie składniki nie wpływa na inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="daeb4-135">By default, components do not affect other applications.</span></span>  
  
-   <span data-ttu-id="daeb4-136">Składniki prywatnej domyślnie.</span><span class="sxs-lookup"><span data-stu-id="daeb4-136">Private components by default.</span></span>  
  
     <span data-ttu-id="daeb4-137">Domyślnie składniki są wdrażane do katalogu aplikacji i są widoczne tylko dla aplikacji zawierających.</span><span class="sxs-lookup"><span data-stu-id="daeb4-137">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>  
  
-   <span data-ttu-id="daeb4-138">Udostępnianie kodu kontrolowany.</span><span class="sxs-lookup"><span data-stu-id="daeb4-138">Controlled code sharing.</span></span>  
  
     <span data-ttu-id="daeb4-139">Udostępnianie kodu wymaga jawnie udostępnić kodu do udostępniania zamiast domyślnego zachowania.</span><span class="sxs-lookup"><span data-stu-id="daeb4-139">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>  
  
-   <span data-ttu-id="daeb4-140">Przechowywanie wersji Side-by-side.</span><span class="sxs-lookup"><span data-stu-id="daeb4-140">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="daeb4-141">Wiele wersji składnika lub aplikacji mogą współistnieć, można wybrać, które wersje do użycia i środowisko uruchomieniowe języka wspólnego wymusza zasady przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="daeb4-141">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>  
  
-   <span data-ttu-id="daeb4-142">Wdrażanie XCOPY i replikacji.</span><span class="sxs-lookup"><span data-stu-id="daeb4-142">XCOPY deployment and replication.</span></span>  
  
     <span data-ttu-id="daeb4-143">Składniki własnym opisane, niezależna i aplikacje można wdrożyć bez wpisy rejestru lub zależności.</span><span class="sxs-lookup"><span data-stu-id="daeb4-143">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>  
  
-   <span data-ttu-id="daeb4-144">Aktualizacje na bieżąco.</span><span class="sxs-lookup"><span data-stu-id="daeb4-144">On-the-fly updates.</span></span>  
  
     <span data-ttu-id="daeb4-145">Administratorzy mogą używać hostów, takich jak ASP.NET, aby zaktualizować program bibliotek DLL, nawet na komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="daeb4-145">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>  
  
-   <span data-ttu-id="daeb4-146">Integracja z Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="daeb4-146">Integration with the Windows Installer.</span></span>  
  
     <span data-ttu-id="daeb4-147">Anonsu, publikowania, naprawy i instalacji na żądanie są wszystkie dostępne podczas wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="daeb4-147">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>  
  
-   <span data-ttu-id="daeb4-148">Wdrożenia w przedsiębiorstwie.</span><span class="sxs-lookup"><span data-stu-id="daeb4-148">Enterprise deployment.</span></span>  
  
     <span data-ttu-id="daeb4-149">Ta funkcja zapewnia dystrybucji oprogramowania łatwe, w tym o korzystaniu z usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="daeb4-149">This feature provides easy software distribution, including using Active Directory.</span></span>  
  
-   <span data-ttu-id="daeb4-150">Pobieranie i buforowania.</span><span class="sxs-lookup"><span data-stu-id="daeb4-150">Downloading and caching.</span></span>  
  
     <span data-ttu-id="daeb4-151">Pobieranie przyrostowe Zachowaj mniejsze pliki do pobrania i składniki mogą być izolowane do użycia tylko przez aplikację do wdrożenia niskiego wpływu.</span><span class="sxs-lookup"><span data-stu-id="daeb4-151">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>  
  
-   <span data-ttu-id="daeb4-152">Częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="daeb4-152">Partially trusted code.</span></span>  
  
     <span data-ttu-id="daeb4-153">Tożsamość jest oparty na kodzie zamiast użytkownika, a pola dialogowe certyfikat, nie pojawiają się.</span><span class="sxs-lookup"><span data-stu-id="daeb4-153">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>  
  
## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="daeb4-154">Pakowanie i dystrybucja aplikacji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="daeb4-154">Packaging and Distributing .NET Framework Applications</span></span>  
 <span data-ttu-id="daeb4-155">Niektóre z pakowaniem i informacje na temat wdrażania dla programu .NET Framework jest opisane w innych częściach dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="daeb4-155">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="daeb4-156">Te sekcje zawierają informacje dotyczące samoopisujące jednostki o nazwie [zestawy](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), które nie wymagają żadnych wpisów rejestru [zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md), co zapewnić unikatowość nazwy i zapobiec nazwy fałszowanie zawartości, i [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md), która rozwiązuje wiele problemów związanych z konflikty biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="daeb4-156">Those sections provide information about the self-describing units called [assemblies](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), which require no registry entries, [strong-named assemblies](../../../docs/framework/app-domains/strong-named-assemblies.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../../docs/framework/app-domains/assembly-versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="daeb4-157">Poniższe sekcje zawierają informacje dotyczące tworzenia pakietów i dystrybucja aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="daeb4-157">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>  
  
### <a name="packaging"></a><span data-ttu-id="daeb4-158">Tworzenie pakietów</span><span class="sxs-lookup"><span data-stu-id="daeb4-158">Packaging</span></span>  
 <span data-ttu-id="daeb4-159">.NET Framework udostępnia następujące opcje dla pakietów aplikacji:</span><span class="sxs-lookup"><span data-stu-id="daeb4-159">The .NET Framework provides the following options for packaging applications:</span></span>  
  
-   <span data-ttu-id="daeb4-160">Jako pojedynczy zestaw lub zbiór zestawów.</span><span class="sxs-lookup"><span data-stu-id="daeb4-160">As a single assembly or as a collection of assemblies.</span></span>  
  
     <span data-ttu-id="daeb4-161">Ta opcja służy po prostu plików .dll lub .exe zgodnie z ich zostały skompilowane.</span><span class="sxs-lookup"><span data-stu-id="daeb4-161">With this option, you simply use the .dll or .exe files as they were built.</span></span>  
  
-   <span data-ttu-id="daeb4-162">Jako pliki w formacie cabinet (CAB).</span><span class="sxs-lookup"><span data-stu-id="daeb4-162">As cabinet (CAB) files.</span></span>  
  
     <span data-ttu-id="daeb4-163">Po wybraniu tej opcji należy kompresuje pliki do plików cab dystrybucji lub pobrać szybciej.</span><span class="sxs-lookup"><span data-stu-id="daeb4-163">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>  
  
-   <span data-ttu-id="daeb4-164">Jako pakiet Instalatora systemu Windows lub w innych formatach Instalatora.</span><span class="sxs-lookup"><span data-stu-id="daeb4-164">As a Windows Installer package or in other installer formats.</span></span>  
  
     <span data-ttu-id="daeb4-165">Po wybraniu tej opcji tworzenia pliku .msi do użycia przy użyciu Instalatora Windows lub pakietu aplikacji do użycia z niektórych innych Instalatora.</span><span class="sxs-lookup"><span data-stu-id="daeb4-165">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>  
  
### <a name="distribution"></a><span data-ttu-id="daeb4-166">Dystrybucji</span><span class="sxs-lookup"><span data-stu-id="daeb4-166">Distribution</span></span>  
 <span data-ttu-id="daeb4-167">Platforma .NET Framework zapewnia następujące opcje dystrybucji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="daeb4-167">The .NET Framework provides the following options for distributing applications:</span></span>  
  
-   <span data-ttu-id="daeb4-168">Użyj polecenia XCOPY lub FTP.</span><span class="sxs-lookup"><span data-stu-id="daeb4-168">Use XCOPY or FTP.</span></span>  
  
     <span data-ttu-id="daeb4-169">Ponieważ typowych aplikacji środowiska wykonawczego języka są samoopisujące i wymagają żadnych wpisów rejestru, wystarczy skopiować do odpowiedniego katalogu aplikacji można użyć polecenia XCOPY lub FTP.</span><span class="sxs-lookup"><span data-stu-id="daeb4-169">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="daeb4-170">Aplikacja może następnie uruchamiana z tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="daeb4-170">The application can then be run from that directory.</span></span>  
  
-   <span data-ttu-id="daeb4-171">Użyj Pobieranie kodu.</span><span class="sxs-lookup"><span data-stu-id="daeb4-171">Use code download.</span></span>  
  
     <span data-ttu-id="daeb4-172">Jeśli aplikacja jest rozpowszechniana przez Internet lub przez firmową sieć intranet, można po prostu Pobierz kod na komputer i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="daeb4-172">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>  
  
-   <span data-ttu-id="daeb4-173">Użyj programu instalacyjnego, takich jak Instalator Windows 2.0.</span><span class="sxs-lookup"><span data-stu-id="daeb4-173">Use an installer program such as Windows Installer 2.0.</span></span>  
  
     <span data-ttu-id="daeb4-174">Instalatora systemu Windows w wersji 2.0 można zainstalować, naprawę lub usunięcie zestawy .NET Framework w pamięci podręcznej GAC i prywatnych katalogów.</span><span class="sxs-lookup"><span data-stu-id="daeb4-174">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>  
  
### <a name="installation-location"></a><span data-ttu-id="daeb4-175">Lokalizacja instalacji</span><span class="sxs-lookup"><span data-stu-id="daeb4-175">Installation Location</span></span>  
 <span data-ttu-id="daeb4-176">Aby ustalić, gdzie można wdrażać zestawów aplikacji, tak aby można je znaleźć w czasie wykonywania, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="daeb4-176">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="daeb4-177">Zagadnienia dotyczące zabezpieczeń może wpłynąć na sposób wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="daeb4-177">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="daeb4-178">Kod zarządzany zgodnie z którym znajduje się kod są przyznawane uprawnienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="daeb4-178">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="daeb4-179">Wdrażanie aplikacji lub składnika do lokalizacji, w którym odbiera małego zaufania, na przykład Internet, limity aplikację lub składnik czynności.</span><span class="sxs-lookup"><span data-stu-id="daeb4-179">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="daeb4-180">Aby uzyskać więcej informacji na temat wdrażania i zagadnienia dotyczące zabezpieczeń, zobacz [podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="daeb4-180">For more information about deployment and security considerations, see [Code Access Security Basics](../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="daeb4-181">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="daeb4-181">Related Topics</span></span>  
  
|<span data-ttu-id="daeb4-182">Tytuł</span><span class="sxs-lookup"><span data-stu-id="daeb4-182">Title</span></span>|<span data-ttu-id="daeb4-183">Opis</span><span class="sxs-lookup"><span data-stu-id="daeb4-183">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="daeb4-184">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="daeb4-184">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|<span data-ttu-id="daeb4-185">W tym artykule opisano, jak środowisko uruchomieniowe języka wspólnego Określa, które zestawu do używania w celu spełnienia żądania powiązania.</span><span class="sxs-lookup"><span data-stu-id="daeb4-185">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|  
|[<span data-ttu-id="daeb4-186">Najlepsze praktyki dotyczące ładowania zestawu</span><span class="sxs-lookup"><span data-stu-id="daeb4-186">Best Practices for Assembly Loading</span></span>](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|<span data-ttu-id="daeb4-187">W tym artykule omówiono sposób, aby uniknąć problemów tożsamości typu, który może prowadzić do <xref:System.InvalidCastException>, <xref:System.MissingMethodException>oraz innych błędów.</span><span class="sxs-lookup"><span data-stu-id="daeb4-187">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|  
|[<span data-ttu-id="daeb4-188">Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="daeb4-188">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)|<span data-ttu-id="daeb4-189">Opisano Menedżera ponownego uruchomienia, co uniemożliwia uruchamiany ponownie, jeśli to możliwe i wyjaśniono, jak aplikacje, które Zainstaluj program .NET Framework mogą wykorzystać go.</span><span class="sxs-lookup"><span data-stu-id="daeb4-189">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|  
|[<span data-ttu-id="daeb4-190">Przewodnik wdrażania dla administratorów</span><span class="sxs-lookup"><span data-stu-id="daeb4-190">Deployment Guide for Administrators</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)|<span data-ttu-id="daeb4-191">W tym artykule wyjaśniono, jak administrator systemu może wdrożenia programu .NET Framework i jego zależności systemu w sieci za pomocą programu System Center Configuration Manager (SCCM).</span><span class="sxs-lookup"><span data-stu-id="daeb4-191">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using System Center Configuration Manager (SCCM).</span></span>|  
|[<span data-ttu-id="daeb4-192">Przewodnik wdrażania dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="daeb4-192">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)|<span data-ttu-id="daeb4-193">W tym artykule wyjaśniono, jak deweloperzy można zainstalować środowiska .NET Framework na ich komputerów z ich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="daeb4-193">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|  
|[<span data-ttu-id="daeb4-194">Wdrażanie aplikacji, usług i składników</span><span class="sxs-lookup"><span data-stu-id="daeb4-194">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="daeb4-195">W tym artykule omówiono opcje wdrażania w programie Visual Studio, w tym instrukcje dotyczące publikowania aplikacji przy użyciu technologii ClickOnce i Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="daeb4-195">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>| 
|[<span data-ttu-id="daeb4-196">Publikowanie aplikacji ClickOnce</span><span class="sxs-lookup"><span data-stu-id="daeb4-196">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="daeb4-197">Opisuje sposób pakietu aplikacji formularzy systemu Windows, a następnie wdrożyć go za pomocą technologii ClickOnce do komputerów klienckich w sieci.</span><span class="sxs-lookup"><span data-stu-id="daeb4-197">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|  
|[<span data-ttu-id="daeb4-198">Opakowanie i wdrażanie zasobów</span><span class="sxs-lookup"><span data-stu-id="daeb4-198">Packaging and Deploying Resources</span></span>](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="daeb4-199">W tym artykule opisano model gwiazdy używający programu .NET Framework do pakietu i wdrażanie zasobów; obejmuje zasobów nazewnictwa konwencje, proces rezerwowy i pakowania alternatyw.</span><span class="sxs-lookup"><span data-stu-id="daeb4-199">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|  
|[<span data-ttu-id="daeb4-200">Wdrażanie aplikacji międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="daeb4-200">Deploying an Interop Application</span></span>](../../../docs/framework/interop/deploying-an-interop-application.md)|<span data-ttu-id="daeb4-201">Wyjaśniono, jak wysłać i zainstaluj międzyoperacyjnego aplikacji, które zwykle obejmują zestawu klienta .NET Framework, jeden lub więcej zestawów międzyoperacyjnych reprezentujących różne biblioteki typów COM, i co najmniej jeden zarejestrowany składników COM.</span><span class="sxs-lookup"><span data-stu-id="daeb4-201">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|  
|[<span data-ttu-id="daeb4-202">Instrukcje: Pobieranie danych o postępie z Instalatora .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="daeb4-202">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="daeb4-203">Opisuje sposób dyskretnie uruchamianie i śledzić proces instalacji platformy .NET Framework podczas pokazywania widoku postęp instalacji.</span><span class="sxs-lookup"><span data-stu-id="daeb4-203">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="daeb4-204">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="daeb4-204">See Also</span></span>  
 [<span data-ttu-id="daeb4-205">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="daeb4-205">Development Guide</span></span>](../../../docs/framework/development-guide.md)
