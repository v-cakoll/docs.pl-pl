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
ms.openlocfilehash: f38ed31748560292753789e38595a5e30f6ea08a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509657"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="d0cd3-102">Wdrażanie programu .NET Framework i aplikacji</span><span class="sxs-lookup"><span data-stu-id="d0cd3-102">Deploying the .NET Framework and Applications</span></span>
<span data-ttu-id="d0cd3-103">Ten artykuł pomoże rozpocząć wdrażanie programu .NET Framework z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-103">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="d0cd3-104">Większość informacji jest przeznaczona dla deweloperów, producentów OEM i Administratorzy przedsiębiorstwa.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-104">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="d0cd3-105">Użytkownicy, którzy chcą zainstalować program .NET Framework na swoich komputerach powinni przeczytać [Instalowanie programu .NET Framework](~/docs/framework/install/index.md).</span><span class="sxs-lookup"><span data-stu-id="d0cd3-105">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](~/docs/framework/install/index.md).</span></span>  
  
## <a name="key-deployment-resources"></a><span data-ttu-id="d0cd3-106">Zasoby dotyczące wdrażania klucza</span><span class="sxs-lookup"><span data-stu-id="d0cd3-106">Key Deployment Resources</span></span>  
 <span data-ttu-id="d0cd3-107">Informacje na temat wdrażania i obsługi programu .NET Framework, należy użyć następujących łączy do innych tematów MSDN.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-107">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>  
  
 <span data-ttu-id="d0cd3-108">**Instalacja i wdrożenie**</span><span class="sxs-lookup"><span data-stu-id="d0cd3-108">**Setup and deployment**</span></span>  
  
-   <span data-ttu-id="d0cd3-109">Informacje ogólne Instalatora i wdrażania:</span><span class="sxs-lookup"><span data-stu-id="d0cd3-109">General installer and deployment information:</span></span>  
  
    -   <span data-ttu-id="d0cd3-110">Opcje Instalatora:</span><span class="sxs-lookup"><span data-stu-id="d0cd3-110">Installer options:</span></span>  
  
        -   [<span data-ttu-id="d0cd3-111">Instalator sieci Web</span><span class="sxs-lookup"><span data-stu-id="d0cd3-111">Web installer</span></span>](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
        -   [<span data-ttu-id="d0cd3-112">Instalator w trybie offline</span><span class="sxs-lookup"><span data-stu-id="d0cd3-112">Offline installer</span></span>](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
    -   <span data-ttu-id="d0cd3-113">Tryby instalacji:</span><span class="sxs-lookup"><span data-stu-id="d0cd3-113">Installation modes:</span></span>  
  
        -   [<span data-ttu-id="d0cd3-114">Instalacja dyskretna</span><span class="sxs-lookup"><span data-stu-id="d0cd3-114">Silent installation</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)  
  
        -   [<span data-ttu-id="d0cd3-115">Wyświetlanie interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="d0cd3-115">Displaying a UI</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)  
  
    -   [<span data-ttu-id="d0cd3-116">Zmniejszenie liczby system ponownych uruchomień podczas instalowania programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="d0cd3-116">Reducing system restarts during .NET Framework 4.5 installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)  
  
    -   [<span data-ttu-id="d0cd3-117">Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d0cd3-117">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
  
-   <span data-ttu-id="d0cd3-118">Wdrażanie programu .NET Framework z aplikacją klienta (dla deweloperów):</span><span class="sxs-lookup"><span data-stu-id="d0cd3-118">Deploying the .NET Framework with a client application (for developers):</span></span>  
  
    -   <span data-ttu-id="d0cd3-119">[Za pomocą programu InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) w projekcie instalacja i wdrożenie</span><span class="sxs-lookup"><span data-stu-id="d0cd3-119">[Using InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>  
  
    -   [<span data-ttu-id="d0cd3-120">Za pomocą aplikacji Visual Studio ClickOnce</span><span class="sxs-lookup"><span data-stu-id="d0cd3-120">Using a Visual Studio ClickOnce application</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)  
  
    -   [<span data-ttu-id="d0cd3-121">Tworzenie pakietu instalacyjnego WiX</span><span class="sxs-lookup"><span data-stu-id="d0cd3-121">Creating a WiX installation package</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)  
  
    -   [<span data-ttu-id="d0cd3-122">Za pomocą niestandardowego Instalatora</span><span class="sxs-lookup"><span data-stu-id="d0cd3-122">Using a custom installer</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)  
  
    -   <span data-ttu-id="d0cd3-123">[Dodatkowe informacje](../../../docs/framework/deployment/deployment-guide-for-developers.md) dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="d0cd3-123">[Additional information](../../../docs/framework/deployment/deployment-guide-for-developers.md) for developers</span></span>  
  
-   <span data-ttu-id="d0cd3-124">Wdrażanie programu .NET Framework (dla producentów OEM i administratorów):</span><span class="sxs-lookup"><span data-stu-id="d0cd3-124">Deploying the .NET Framework (for OEMs and administrators):</span></span>  
  
    -   [<span data-ttu-id="d0cd3-125">Windows Assessment and Deployment Kit (ADK)</span><span class="sxs-lookup"><span data-stu-id="d0cd3-125">Windows Assessment and Deployment Kit (ADK)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=254976)  
  
    -   [<span data-ttu-id="d0cd3-126">Podręcznik administratora</span><span class="sxs-lookup"><span data-stu-id="d0cd3-126">Administrator's guide</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)  
  
 <span data-ttu-id="d0cd3-127">**Obsługa techniczna**</span><span class="sxs-lookup"><span data-stu-id="d0cd3-127">**Servicing**</span></span>  
  
-   <span data-ttu-id="d0cd3-128">Aby uzyskać ogólne informacje, zobacz [blog programu .NET Framework](https://go.microsoft.com/fwlink/p/?LinkId=254977)</span><span class="sxs-lookup"><span data-stu-id="d0cd3-128">For general information, see the [.NET Framework blog](https://go.microsoft.com/fwlink/p/?LinkId=254977)</span></span>  
  
-   [<span data-ttu-id="d0cd3-129">Wykrywania wersji</span><span class="sxs-lookup"><span data-stu-id="d0cd3-129">Detecting versions</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
  
-   [<span data-ttu-id="d0cd3-130">Wykrywanie, dodatki service pack i aktualizacje</span><span class="sxs-lookup"><span data-stu-id="d0cd3-130">Detecting service packs and updates</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
  
## <a name="features-that-simplify-deployment"></a><span data-ttu-id="d0cd3-131">Funkcje, które upraszczają wdrożenia</span><span class="sxs-lookup"><span data-stu-id="d0cd3-131">Features That Simplify Deployment</span></span>  
 <span data-ttu-id="d0cd3-132">.NET Framework oferuje podstawowe funkcje, które ułatwiają wdrażanie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="d0cd3-132">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>  
  
-   <span data-ttu-id="d0cd3-133">Aplikacje bez zakłócania normalnej.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-133">No-impact applications.</span></span>  
  
     <span data-ttu-id="d0cd3-134">Ta funkcja zapewnia izolację aplikacji i eliminuje konflikty biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-134">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="d0cd3-135">Domyślnie składniki nie wpływać na inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-135">By default, components do not affect other applications.</span></span>  
  
-   <span data-ttu-id="d0cd3-136">Składniki prywatnej domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-136">Private components by default.</span></span>  
  
     <span data-ttu-id="d0cd3-137">Domyślnie składniki są wdrażane w katalogu aplikacji i są widoczne tylko dla aplikacji zawierających.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-137">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>  
  
-   <span data-ttu-id="d0cd3-138">Kontrolowane, udostępniania kodu.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-138">Controlled code sharing.</span></span>  
  
     <span data-ttu-id="d0cd3-139">Udostępnianie kodu wymaga jawnego udostępniania kodu na potrzeby udostępniania zamiast domyślnego zachowania.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-139">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>  
  
-   <span data-ttu-id="d0cd3-140">Przechowywanie wersji obok siebie.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-140">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="d0cd3-141">Wiele wersji składnika lub aplikacji mogą współistnieć, można wybrać, które wersje do użycia i środowisko uruchomieniowe języka wspólnego wymusza zasady przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-141">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>  
  
-   <span data-ttu-id="d0cd3-142">Umożliwia wdrażanie XCOPY i replikacji.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-142">XCOPY deployment and replication.</span></span>  
  
     <span data-ttu-id="d0cd3-143">Składniki własnym opisem, niezależna i aplikacje mogą być wdrażane bez wpisów rejestru lub zależności.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-143">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>  
  
-   <span data-ttu-id="d0cd3-144">Aktualizacje na bieżąco.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-144">On-the-fly updates.</span></span>  
  
     <span data-ttu-id="d0cd3-145">Administratorzy mogą używać hostów, takich jak ASP.NET, aby zaktualizować program bibliotek DLL, nawet na komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-145">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>  
  
-   <span data-ttu-id="d0cd3-146">Integracja z Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-146">Integration with the Windows Installer.</span></span>  
  
     <span data-ttu-id="d0cd3-147">Anons, publikowania, naprawy i instalacji na żądanie są dostępne w przypadku wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-147">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>  
  
-   <span data-ttu-id="d0cd3-148">Wdrażanie w przedsiębiorstwie.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-148">Enterprise deployment.</span></span>  
  
     <span data-ttu-id="d0cd3-149">Ta funkcja zapewnia dystrybucja oprogramowania proste, w tym o korzystaniu z usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-149">This feature provides easy software distribution, including using Active Directory.</span></span>  
  
-   <span data-ttu-id="d0cd3-150">Pobieranie i buforowania.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-150">Downloading and caching.</span></span>  
  
     <span data-ttu-id="d0cd3-151">Przyrostowe pobieranie zachować mniejsze pliki do pobrania i składniki mogą być izolowane do użytku tylko przez aplikację na potrzeby o niskim wpływie na wdrożenie.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-151">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>  
  
-   <span data-ttu-id="d0cd3-152">Częściowo zaufanego kodu.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-152">Partially trusted code.</span></span>  
  
     <span data-ttu-id="d0cd3-153">Tożsamość jest oparty na kodzie, zamiast użytkownika, a nie certyfikat okien dialogowych.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-153">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>  
  
## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="d0cd3-154">Pakowanie i rozpowszechnianie aplikacji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d0cd3-154">Packaging and Distributing .NET Framework Applications</span></span>  
 <span data-ttu-id="d0cd3-155">Niektóre pakowania i informacje na temat wdrażania programu .NET Framework jest opisany w innych sekcji dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-155">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="d0cd3-156">Te sekcje zawierają informacje o samoopisujące jednostki o nazwie [zestawy](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), które nie wymagają żadnych wpisów rejestru [zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md), która zapewnić unikatowość nazwy i zapobiec nazwy fałszowanie adresów, a [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md), która rozwiązuje wiele problemów związanych z konflikty biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-156">Those sections provide information about the self-describing units called [assemblies](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), which require no registry entries, [strong-named assemblies](../../../docs/framework/app-domains/strong-named-assemblies.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../../docs/framework/app-domains/assembly-versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="d0cd3-157">Poniższe sekcje zawierają informacje dotyczące tworzenia pakietów i rozpowszechnianie aplikacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-157">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>  
  
### <a name="packaging"></a><span data-ttu-id="d0cd3-158">Tworzenie pakietów</span><span class="sxs-lookup"><span data-stu-id="d0cd3-158">Packaging</span></span>  
 <span data-ttu-id="d0cd3-159">.NET Framework zawiera następujące opcje dla pakietu aplikacji:</span><span class="sxs-lookup"><span data-stu-id="d0cd3-159">The .NET Framework provides the following options for packaging applications:</span></span>  
  
-   <span data-ttu-id="d0cd3-160">Jako pojedynczy zestaw lub kolekcję zestawów.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-160">As a single assembly or as a collection of assemblies.</span></span>  
  
     <span data-ttu-id="d0cd3-161">Po wybraniu tej opcji możesz po prostu użyć pliki .dll i .exe, ponieważ zostały skompilowane.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-161">With this option, you simply use the .dll or .exe files as they were built.</span></span>  
  
-   <span data-ttu-id="d0cd3-162">Jako pliki cabinet (CAB).</span><span class="sxs-lookup"><span data-stu-id="d0cd3-162">As cabinet (CAB) files.</span></span>  
  
     <span data-ttu-id="d0cd3-163">Po wybraniu tej opcji Kompresuj pliki na pliki cab dystrybucji lub pobrać mniej czasochłonne.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-163">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>  
  
-   <span data-ttu-id="d0cd3-164">Jako pakiet Instalatora Windows lub w innych formatach Instalatora.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-164">As a Windows Installer package or in other installer formats.</span></span>  
  
     <span data-ttu-id="d0cd3-165">Po wybraniu tej opcji tworzenia pliku .msi do użycia przy użyciu Instalatora Windows lub pakietu aplikacji do użytku z niektórych innych Instalatora.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-165">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>  
  
### <a name="distribution"></a><span data-ttu-id="d0cd3-166">Dystrybucji</span><span class="sxs-lookup"><span data-stu-id="d0cd3-166">Distribution</span></span>  
 <span data-ttu-id="d0cd3-167">.NET Framework zawiera następujące opcje dystrybucji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="d0cd3-167">The .NET Framework provides the following options for distributing applications:</span></span>  
  
-   <span data-ttu-id="d0cd3-168">Za pomocą polecenia XCOPY lub FTP.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-168">Use XCOPY or FTP.</span></span>  
  
     <span data-ttu-id="d0cd3-169">Ponieważ typowych aplikacji środowiska uruchomieniowego języka są samoopisujące i wymagają żadnych wpisów rejestru, można użyć polecenia XCOPY lub FTP można po prostu skopiować ją do odpowiedniego katalogu.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-169">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="d0cd3-170">Aplikacja może następnie uruchamiana z tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-170">The application can then be run from that directory.</span></span>  
  
-   <span data-ttu-id="d0cd3-171">Za pomocą pobierania kodu.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-171">Use code download.</span></span>  
  
     <span data-ttu-id="d0cd3-172">Jeśli aplikacja jest rozpowszechniana przez Internet lub za pomocą firmowego intranetu, można po prostu pobrać kod na komputerze i uruchamiania aplikacji istnieje.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-172">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>  
  
-   <span data-ttu-id="d0cd3-173">Użyj programu instalacyjnego, takich jak Instalator Windows w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-173">Use an installer program such as Windows Installer 2.0.</span></span>  
  
     <span data-ttu-id="d0cd3-174">Instalator Windows w wersji 2.0 można zainstalować, naprawę lub usunięcie zestawów .NET Framework, w globalnej pamięci podręcznej i prywatne katalogów.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-174">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>  
  
### <a name="installation-location"></a><span data-ttu-id="d0cd3-175">Lokalizacja instalacji</span><span class="sxs-lookup"><span data-stu-id="d0cd3-175">Installation Location</span></span>  
 <span data-ttu-id="d0cd3-176">Aby określić miejsce wdrażania zestawów Twojej aplikacji, dzięki czemu można je znaleźć w czasie wykonywania, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="d0cd3-176">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="d0cd3-177">Zagadnienia dotyczące zabezpieczeń może także mieć wpływ na sposób wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-177">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="d0cd3-178">Uprawnienia zabezpieczeń są przyznawane kodu zarządzanego, zgodnie z którym znajduje się kod.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-178">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="d0cd3-179">Wdrażanie aplikacji lub składnika do lokalizacji, w której otrzymuje nieco zaufania, na przykład Internet, limity aplikacji lub składnika czynności.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-179">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="d0cd3-180">Aby uzyskać więcej informacji dotyczących wdrażania i zagadnienia dotyczące zabezpieczeń, zobacz [podstawy zabezpieczeń dostępu kodu](../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="d0cd3-180">For more information about deployment and security considerations, see [Code Access Security Basics](../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="d0cd3-181">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="d0cd3-181">Related Topics</span></span>  
  
|<span data-ttu-id="d0cd3-182">Tytuł</span><span class="sxs-lookup"><span data-stu-id="d0cd3-182">Title</span></span>|<span data-ttu-id="d0cd3-183">Opis</span><span class="sxs-lookup"><span data-stu-id="d0cd3-183">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d0cd3-184">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d0cd3-184">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|<span data-ttu-id="d0cd3-185">W tym artykule opisano, jak środowisko uruchomieniowe języka wspólnego Określa, które zestawu do używania w celu spełnienia żądania powiązania.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-185">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|  
|[<span data-ttu-id="d0cd3-186">Najlepsze praktyki dotyczące ładowania zestawu</span><span class="sxs-lookup"><span data-stu-id="d0cd3-186">Best Practices for Assembly Loading</span></span>](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|<span data-ttu-id="d0cd3-187">W tym artykule omówiono sposób, aby uniknąć problemów tożsamości typu, który może prowadzić do <xref:System.InvalidCastException>, <xref:System.MissingMethodException>i inne błędy.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-187">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|  
|[<span data-ttu-id="d0cd3-188">Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="d0cd3-188">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)|<span data-ttu-id="d0cd3-189">W tym artykule opisano Menedżera ponownego uruchamiania co uniemożliwia ponowne uruchomienie, jeśli to możliwe i wyjaśniono, jak aplikacje, zainstaluj program .NET Framework, które można z niej korzystać.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-189">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|  
|[<span data-ttu-id="d0cd3-190">Przewodnik wdrażania dla administratorów</span><span class="sxs-lookup"><span data-stu-id="d0cd3-190">Deployment Guide for Administrators</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)|<span data-ttu-id="d0cd3-191">W tym artykule wyjaśniono, jak administrator systemu może wdrożyć środowiska .NET Framework i jego zależności systemowe przez sieć przy użyciu programu System Center Configuration Manager (SCCM).</span><span class="sxs-lookup"><span data-stu-id="d0cd3-191">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using System Center Configuration Manager (SCCM).</span></span>|  
|[<span data-ttu-id="d0cd3-192">Przewodnik wdrażania dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="d0cd3-192">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)|<span data-ttu-id="d0cd3-193">W tym artykule wyjaśniono, jak deweloperzy mogą zainstalować program .NET Framework na komputerach swoich użytkowników przy użyciu swoich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-193">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|  
|[<span data-ttu-id="d0cd3-194">Wdrażanie aplikacji, usług i składników</span><span class="sxs-lookup"><span data-stu-id="d0cd3-194">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="d0cd3-195">W tym artykule omówiono opcje wdrażania w programie Visual Studio, w tym instrukcje dotyczące publikowania aplikacji przy użyciu technologii ClickOnce i Instalator Windows.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-195">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>| 
|[<span data-ttu-id="d0cd3-196">Publikowanie aplikacji ClickOnce</span><span class="sxs-lookup"><span data-stu-id="d0cd3-196">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="d0cd3-197">Opis pakietu aplikacji Windows Forms i wdrożyć ją za pomocą technologii ClickOnce do komputerów klienckich w sieci.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-197">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|  
|[<span data-ttu-id="d0cd3-198">Opakowanie i wdrażanie zasobów</span><span class="sxs-lookup"><span data-stu-id="d0cd3-198">Packaging and Deploying Resources</span></span>](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="d0cd3-199">W tym artykule opisano model gwiazdy, który używa programu .NET Framework w celu pakowanie i wdrażanie zasobów. opisano konwencje nazewnictwa, proces rezerwowy i alternatywne opakowanie zasobów.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-199">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|  
|[<span data-ttu-id="d0cd3-200">Wdrażanie aplikacji międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="d0cd3-200">Deploying an Interop Application</span></span>](../../../docs/framework/interop/deploying-an-interop-application.md)|<span data-ttu-id="d0cd3-201">Wyjaśnia, jak dostarczanie i zainstaluj aplikacje współdziałania, obejmujących zazwyczaj zestawie klienta programu .NET Framework jednego lub więcej zestawów międzyoperacyjnych reprezentująca różne biblioteki typów COM, i co najmniej jeden zarejestrowany składnik COM.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-201">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|  
|[<span data-ttu-id="d0cd3-202">Instrukcje: Pobieranie danych o postępie z Instalatora .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="d0cd3-202">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="d0cd3-203">Opisuje sposób dyskretnie Uruchom i Śledź proces instalacji programu .NET Framework podczas wyświetlania własnego widoku postępu instalacji.</span><span class="sxs-lookup"><span data-stu-id="d0cd3-203">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0cd3-204">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0cd3-204">See Also</span></span>  
 [<span data-ttu-id="d0cd3-205">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="d0cd3-205">Development Guide</span></span>](../../../docs/framework/development-guide.md)
