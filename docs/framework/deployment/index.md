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
ms.openlocfilehash: b1ba9810b4b0d5a1688318db1093a9ce9bdf8fda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716463"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="caa0a-102">Wdrażanie programu .NET Framework i aplikacji</span><span class="sxs-lookup"><span data-stu-id="caa0a-102">Deploying the .NET Framework and Applications</span></span>

<span data-ttu-id="caa0a-103">Ten artykuł ułatwia rozpoczęcie wdrażania programu .NET Framework za pomocą aplikacji.</span><span class="sxs-lookup"><span data-stu-id="caa0a-103">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="caa0a-104">Większość informacji jest przeznaczona dla deweloperów, producentów OEM i administratorów przedsiębiorstwa.</span><span class="sxs-lookup"><span data-stu-id="caa0a-104">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="caa0a-105">Użytkownicy, którzy chcą zainstalować program .NET Framework na swoich komputerach, powinni przeczytać artykuł [Instalowanie programu .NET Framework](../install/index.md).</span><span class="sxs-lookup"><span data-stu-id="caa0a-105">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](../install/index.md).</span></span>

## <a name="key-deployment-resources"></a><span data-ttu-id="caa0a-106">Kluczowe zasoby wdrażania</span><span class="sxs-lookup"><span data-stu-id="caa0a-106">Key Deployment Resources</span></span>

<span data-ttu-id="caa0a-107">Skorzystaj z poniższych łączy do innych tematów msdn, aby uzyskać szczegółowe informacje na temat wdrażania i obsługi programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="caa0a-107">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>

<span data-ttu-id="caa0a-108">**Konfiguracja i wdrażanie**</span><span class="sxs-lookup"><span data-stu-id="caa0a-108">**Setup and deployment**</span></span>

- <span data-ttu-id="caa0a-109">Ogólne informacje o instalatorze i wdrożeniu:</span><span class="sxs-lookup"><span data-stu-id="caa0a-109">General installer and deployment information:</span></span>

  - <span data-ttu-id="caa0a-110">Opcje instalatora:</span><span class="sxs-lookup"><span data-stu-id="caa0a-110">Installer options:</span></span>

    - [<span data-ttu-id="caa0a-111">Instalator sieci Web</span><span class="sxs-lookup"><span data-stu-id="caa0a-111">Web installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [<span data-ttu-id="caa0a-112">Instalator w trybie offline</span><span class="sxs-lookup"><span data-stu-id="caa0a-112">Offline installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - <span data-ttu-id="caa0a-113">Tryby instalacji:</span><span class="sxs-lookup"><span data-stu-id="caa0a-113">Installation modes:</span></span>

    - [<span data-ttu-id="caa0a-114">Instalacja w trybie dyskretnym</span><span class="sxs-lookup"><span data-stu-id="caa0a-114">Silent installation</span></span>](deployment-guide-for-developers.md#chaining_custom)

    - [<span data-ttu-id="caa0a-115">Wyświetlanie interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="caa0a-115">Displaying a UI</span></span>](deployment-guide-for-developers.md#chaining_default)

  - [<span data-ttu-id="caa0a-116">Redukcja ponownego uruchamiania systemu podczas instalacji programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="caa0a-116">Reducing system restarts during .NET Framework 4.5 installations</span></span>](reducing-system-restarts.md)

  - [<span data-ttu-id="caa0a-117">Rozwiązywanie problemów z zablokowaną instalacją i odinstalowywaniem programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="caa0a-117">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- <span data-ttu-id="caa0a-118">Wdrażanie programu .NET Framework za pomocą aplikacji klienckiej (dla deweloperów):</span><span class="sxs-lookup"><span data-stu-id="caa0a-118">Deploying the .NET Framework with a client application (for developers):</span></span>

  - <span data-ttu-id="caa0a-119">[Korzystanie z installshield](deployment-guide-for-developers.md#installshield-deployment) w projekcie instalacji i wdrażania</span><span class="sxs-lookup"><span data-stu-id="caa0a-119">[Using InstallShield](deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>

  - [<span data-ttu-id="caa0a-120">Korzystanie z aplikacji ClickOnce programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="caa0a-120">Using a Visual Studio ClickOnce application</span></span>](deployment-guide-for-developers.md#clickonce-deployment)

  - [<span data-ttu-id="caa0a-121">Tworzenie pakietu instalacyjnego WiX</span><span class="sxs-lookup"><span data-stu-id="caa0a-121">Creating a WiX installation package</span></span>](deployment-guide-for-developers.md#wix)

  - [<span data-ttu-id="caa0a-122">Korzystanie z instalatora niestandardowego</span><span class="sxs-lookup"><span data-stu-id="caa0a-122">Using a custom installer</span></span>](deployment-guide-for-developers.md#chaining)

  - <span data-ttu-id="caa0a-123">[Dodatkowe informacje](deployment-guide-for-developers.md) dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="caa0a-123">[Additional information](deployment-guide-for-developers.md) for developers</span></span>

- <span data-ttu-id="caa0a-124">Wdrażanie programu .NET Framework (dla pracowników OEM i administratorów):</span><span class="sxs-lookup"><span data-stu-id="caa0a-124">Deploying the .NET Framework (for OEMs and administrators):</span></span>

  - [<span data-ttu-id="caa0a-125">Zestaw Windows Assessment and Deployment Kit (ADK)</span><span class="sxs-lookup"><span data-stu-id="caa0a-125">Windows Assessment and Deployment Kit (ADK)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [<span data-ttu-id="caa0a-126">Przewodnik administratora</span><span class="sxs-lookup"><span data-stu-id="caa0a-126">Administrator's guide</span></span>](guide-for-administrators.md)

<span data-ttu-id="caa0a-127">**Obsługa techniczna**</span><span class="sxs-lookup"><span data-stu-id="caa0a-127">**Servicing**</span></span>

- <span data-ttu-id="caa0a-128">Aby uzyskać ogólne informacje, zobacz [blog programu .NET Framework](https://devblogs.microsoft.com/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="caa0a-128">For general information, see the [.NET Framework blog](https://devblogs.microsoft.com/dotnet/).</span></span>

- [<span data-ttu-id="caa0a-129">Wykrywanie wersji</span><span class="sxs-lookup"><span data-stu-id="caa0a-129">Detecting versions</span></span>](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [<span data-ttu-id="caa0a-130">Wykrywanie dodatków Service Pack i aktualizacji</span><span class="sxs-lookup"><span data-stu-id="caa0a-130">Detecting service packs and updates</span></span>](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a><span data-ttu-id="caa0a-131">Funkcje, które upraszczają wdrażanie</span><span class="sxs-lookup"><span data-stu-id="caa0a-131">Features That Simplify Deployment</span></span>

<span data-ttu-id="caa0a-132">Program .NET Framework udostępnia szereg podstawowych funkcji ułatwiające wdrażanie aplikacji:</span><span class="sxs-lookup"><span data-stu-id="caa0a-132">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>

- <span data-ttu-id="caa0a-133">Aplikacje bez wpływu.</span><span class="sxs-lookup"><span data-stu-id="caa0a-133">No-impact applications.</span></span>

     <span data-ttu-id="caa0a-134">Ta funkcja zapewnia izolację aplikacji i eliminuje konflikty DLL.</span><span class="sxs-lookup"><span data-stu-id="caa0a-134">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="caa0a-135">Domyślnie składniki nie mają wpływu na inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="caa0a-135">By default, components do not affect other applications.</span></span>

- <span data-ttu-id="caa0a-136">Składniki prywatne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="caa0a-136">Private components by default.</span></span>

     <span data-ttu-id="caa0a-137">Domyślnie składniki są wdrażane w katalogu aplikacji i są widoczne tylko dla aplikacji zawierającej.</span><span class="sxs-lookup"><span data-stu-id="caa0a-137">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>

- <span data-ttu-id="caa0a-138">Kontrolowane udostępnianie kodu.</span><span class="sxs-lookup"><span data-stu-id="caa0a-138">Controlled code sharing.</span></span>

     <span data-ttu-id="caa0a-139">Udostępnianie kodu wymaga jawnego udostępnienia kodu do udostępniania, a nie zachowania domyślnego.</span><span class="sxs-lookup"><span data-stu-id="caa0a-139">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>

- <span data-ttu-id="caa0a-140">Przechowywanie wersji obok siebie.</span><span class="sxs-lookup"><span data-stu-id="caa0a-140">Side-by-side versioning.</span></span>

     <span data-ttu-id="caa0a-141">Wiele wersji składnika lub aplikacji może współistnieć, można wybrać, które wersje do użycia, a środowisko wykonawcze języka wspólnego wymusza zasady przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="caa0a-141">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>

- <span data-ttu-id="caa0a-142">XCOPY wdrożenia i replikacji.</span><span class="sxs-lookup"><span data-stu-id="caa0a-142">XCOPY deployment and replication.</span></span>

     <span data-ttu-id="caa0a-143">Samodzielnie opisane i samodzielne składniki i aplikacje mogą być wdrażane bez wpisów rejestru lub zależności.</span><span class="sxs-lookup"><span data-stu-id="caa0a-143">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>

- <span data-ttu-id="caa0a-144">Aktualizacje w locie.</span><span class="sxs-lookup"><span data-stu-id="caa0a-144">On-the-fly updates.</span></span>

     <span data-ttu-id="caa0a-145">Administratorzy mogą używać hostów, takich jak ASP.NET, do aktualizowania bibliotek DLL programu, nawet na komputerach zdalnych.</span><span class="sxs-lookup"><span data-stu-id="caa0a-145">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>

- <span data-ttu-id="caa0a-146">Integracja z Instalatorem Windows.</span><span class="sxs-lookup"><span data-stu-id="caa0a-146">Integration with the Windows Installer.</span></span>

     <span data-ttu-id="caa0a-147">Anons, publikowanie, naprawa i instalowanie na żądanie są dostępne podczas wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="caa0a-147">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>

- <span data-ttu-id="caa0a-148">Wdrożenie w przedsiębiorstwie.</span><span class="sxs-lookup"><span data-stu-id="caa0a-148">Enterprise deployment.</span></span>

     <span data-ttu-id="caa0a-149">Ta funkcja zapewnia łatwą dystrybucję oprogramowania, w tym korzystanie z usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="caa0a-149">This feature provides easy software distribution, including using Active Directory.</span></span>

- <span data-ttu-id="caa0a-150">Pobieranie i buforowanie.</span><span class="sxs-lookup"><span data-stu-id="caa0a-150">Downloading and caching.</span></span>

     <span data-ttu-id="caa0a-151">Pobieranie przyrostowe zmniejsza pobieranie, a składniki mogą być izolowane do użytku tylko przez aplikację do wdrażania o niskim wpływie.</span><span class="sxs-lookup"><span data-stu-id="caa0a-151">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>

- <span data-ttu-id="caa0a-152">Częściowo zaufany kod.</span><span class="sxs-lookup"><span data-stu-id="caa0a-152">Partially trusted code.</span></span>

     <span data-ttu-id="caa0a-153">Tożsamość jest oparta na kodzie zamiast użytkownika i nie są wyświetlane żadne okna dialogowe certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="caa0a-153">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>

## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="caa0a-154">Pakowanie i dystrybucja aplikacji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="caa0a-154">Packaging and Distributing .NET Framework Applications</span></span>

<span data-ttu-id="caa0a-155">Niektóre informacje o pakowaniu i wdrażaniu programu .NET Framework są opisane w innych sekcjach dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="caa0a-155">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="caa0a-156">Te sekcje zawierają informacje o jednostek samookryzyskujących o nazwie [zestawy](../../standard/assembly/index.md), które nie wymagają wpisów rejestru, [zestawy o silnych nazwach](../../standard/assembly/strong-named.md), które zapewniają unikatowość nazwy i zapobiegają fałszowaniu nazw i [przechowywanie wersji zestawu,](../../standard/assembly/versioning.md)co rozwiązuje wiele problemów związanych z konfliktami biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="caa0a-156">Those sections provide information about the self-describing units called [assemblies](../../standard/assembly/index.md), which require no registry entries, [strong-named assemblies](../../standard/assembly/strong-named.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../standard/assembly/versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="caa0a-157">Poniższe sekcje zawierają informacje dotyczące pakowania i dystrybucji aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="caa0a-157">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>

### <a name="packaging"></a><span data-ttu-id="caa0a-158">Tworzenie pakietów</span><span class="sxs-lookup"><span data-stu-id="caa0a-158">Packaging</span></span>

<span data-ttu-id="caa0a-159">Program .NET Framework udostępnia następujące opcje dla aplikacji do pakowania:</span><span class="sxs-lookup"><span data-stu-id="caa0a-159">The .NET Framework provides the following options for packaging applications:</span></span>

- <span data-ttu-id="caa0a-160">Jako pojedynczy zestaw lub jako zbiór zestawów.</span><span class="sxs-lookup"><span data-stu-id="caa0a-160">As a single assembly or as a collection of assemblies.</span></span>

     <span data-ttu-id="caa0a-161">Dzięki tej opcji wystarczy użyć plików .dll lub .exe, które zostały zbudowane.</span><span class="sxs-lookup"><span data-stu-id="caa0a-161">With this option, you simply use the .dll or .exe files as they were built.</span></span>

- <span data-ttu-id="caa0a-162">Jako szafka (CAB).</span><span class="sxs-lookup"><span data-stu-id="caa0a-162">As cabinet (CAB) files.</span></span>

     <span data-ttu-id="caa0a-163">Ta opcja umożliwia kompresowanie plików do plików cab w celu zmniejszenia czasu dystrybucji lub pobierania.</span><span class="sxs-lookup"><span data-stu-id="caa0a-163">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>

- <span data-ttu-id="caa0a-164">Jako pakiet Instalatora Windows lub w innych formatach instalatora.</span><span class="sxs-lookup"><span data-stu-id="caa0a-164">As a Windows Installer package or in other installer formats.</span></span>

     <span data-ttu-id="caa0a-165">Za pomocą tej opcji można utworzyć pliki msi do użytku z Instalatorem Windows lub spakować aplikację do użycia z innym instalatorem.</span><span class="sxs-lookup"><span data-stu-id="caa0a-165">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>

### <a name="distribution"></a><span data-ttu-id="caa0a-166">Dystrybucja</span><span class="sxs-lookup"><span data-stu-id="caa0a-166">Distribution</span></span>

<span data-ttu-id="caa0a-167">Program .NET Framework udostępnia następujące opcje dystrybucji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="caa0a-167">The .NET Framework provides the following options for distributing applications:</span></span>

- <span data-ttu-id="caa0a-168">Użyj XCOPY lub FTP.</span><span class="sxs-lookup"><span data-stu-id="caa0a-168">Use XCOPY or FTP.</span></span>

     <span data-ttu-id="caa0a-169">Ponieważ aplikacje środowiska wykonawczego języka wspólnego są samoopisujące i nie wymagają żadnych wpisów rejestru, można użyć XCOPY lub FTP, aby po prostu skopiować aplikację do odpowiedniego katalogu.</span><span class="sxs-lookup"><span data-stu-id="caa0a-169">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="caa0a-170">Aplikację można następnie uruchomić z tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="caa0a-170">The application can then be run from that directory.</span></span>

- <span data-ttu-id="caa0a-171">Użyj pobierania kodu.</span><span class="sxs-lookup"><span data-stu-id="caa0a-171">Use code download.</span></span>

     <span data-ttu-id="caa0a-172">Jeśli rozprowadzasz aplikację przez Internet lub za pośrednictwem firmowego intranetu, możesz po prostu pobrać kod na komputer i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="caa0a-172">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>

- <span data-ttu-id="caa0a-173">Użyj programu instalacyjnego, takiego jak Instalator Windows 2.0.</span><span class="sxs-lookup"><span data-stu-id="caa0a-173">Use an installer program such as Windows Installer 2.0.</span></span>

     <span data-ttu-id="caa0a-174">Instalator Windows 2.0 może instalować, naprawiać lub usuwać zestawy programu .NET Framework w globalnej pamięci podręcznej zestawów i w katalogach prywatnych.</span><span class="sxs-lookup"><span data-stu-id="caa0a-174">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>

### <a name="installation-location"></a><span data-ttu-id="caa0a-175">Lokalizacja instalacji</span><span class="sxs-lookup"><span data-stu-id="caa0a-175">Installation Location</span></span>

<span data-ttu-id="caa0a-176">Aby określić, gdzie wdrożyć zestawy aplikacji, aby można je było znaleźć w czasie wykonywania, zobacz [Jak środowisko wykonawcze lokalizuje zestawy](how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="caa0a-176">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](how-the-runtime-locates-assemblies.md).</span></span>

<span data-ttu-id="caa0a-177">Zagadnienia dotyczące zabezpieczeń mogą również mieć wpływ na sposób wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="caa0a-177">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="caa0a-178">Uprawnienia zabezpieczeń są przyznawane kodowi zarządzanego zgodnie z miejscem, w którym znajduje się kod.</span><span class="sxs-lookup"><span data-stu-id="caa0a-178">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="caa0a-179">Wdrażanie aplikacji lub składnika w lokalizacji, w której otrzymuje niewielkie zaufanie, takie jak Internet, ogranicza to, co może zrobić aplikacja lub składnik.</span><span class="sxs-lookup"><span data-stu-id="caa0a-179">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="caa0a-180">Aby uzyskać więcej informacji na temat zagadnień dotyczących wdrażania i zabezpieczeń, zobacz [Podstawy zabezpieczeń dostępu do kodu](../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="caa0a-180">For more information about deployment and security considerations, see [Code Access Security Basics](../misc/code-access-security-basics.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="caa0a-181">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="caa0a-181">Related Topics</span></span>

|<span data-ttu-id="caa0a-182">Tytuł</span><span class="sxs-lookup"><span data-stu-id="caa0a-182">Title</span></span>|<span data-ttu-id="caa0a-183">Opis</span><span class="sxs-lookup"><span data-stu-id="caa0a-183">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="caa0a-184">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="caa0a-184">How the Runtime Locates Assemblies</span></span>](how-the-runtime-locates-assemblies.md)|<span data-ttu-id="caa0a-185">W tym artykule opisano, jak środowisko uruchomieniowe języka wspólnego określa, który zestaw do użycia do spełnienia żądania powiązania.</span><span class="sxs-lookup"><span data-stu-id="caa0a-185">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|
|[<span data-ttu-id="caa0a-186">Najlepsze praktyki dotyczące ładowania zestawu</span><span class="sxs-lookup"><span data-stu-id="caa0a-186">Best Practices for Assembly Loading</span></span>](best-practices-for-assembly-loading.md)|<span data-ttu-id="caa0a-187">W tym artykule omówiono sposoby <xref:System.InvalidCastException>unikania problemów z tożsamością typu, które mogą prowadzić do , <xref:System.MissingMethodException>i innych błędów.</span><span class="sxs-lookup"><span data-stu-id="caa0a-187">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|
|[<span data-ttu-id="caa0a-188">Zmniejszenie liczby ponownych uruchomień systemu podczas instalowania programu .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="caa0a-188">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)|<span data-ttu-id="caa0a-189">W tym artykule opisano Menedżera ponownego uruchamiania, który zapobiega ponownemu uruchomieniu, gdy jest to możliwe, i wyjaśniono, jak aplikacje, które instalują program .NET Framework mogą z niego korzystać.</span><span class="sxs-lookup"><span data-stu-id="caa0a-189">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|
|[<span data-ttu-id="caa0a-190">Przewodnik wdrażania dla administratorów</span><span class="sxs-lookup"><span data-stu-id="caa0a-190">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)|<span data-ttu-id="caa0a-191">W tym artykule wyjaśniono, jak administrator systemu może wdrażać program .NET Framework i jego zależności systemowe w sieci przy użyciu programu Microsoft Endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="caa0a-191">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>|
|[<span data-ttu-id="caa0a-192">Przewodnik wdrażania dla deweloperów</span><span class="sxs-lookup"><span data-stu-id="caa0a-192">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)|<span data-ttu-id="caa0a-193">W tym artykule wyjaśniono, jak deweloperzy mogą instalować program .NET Framework na komputerach swoich użytkowników za pomocą aplikacji.</span><span class="sxs-lookup"><span data-stu-id="caa0a-193">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|
|[<span data-ttu-id="caa0a-194">Wdrażanie aplikacji, usług i składników</span><span class="sxs-lookup"><span data-stu-id="caa0a-194">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="caa0a-195">W tym artykule omówiono opcje wdrażania w programie Visual Studio, w tym instrukcje dotyczące publikowania aplikacji przy użyciu technologii ClickOnce i Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="caa0a-195">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>|
|[<span data-ttu-id="caa0a-196">Publikowanie aplikacji ClickOnce</span><span class="sxs-lookup"><span data-stu-id="caa0a-196">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="caa0a-197">W tym artykule opisano sposób pakowania aplikacji Windows Forms i wdrażania jej za pomocą funkcji ClickOnce na komputerach klienckich w sieci.</span><span class="sxs-lookup"><span data-stu-id="caa0a-197">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|
|[<span data-ttu-id="caa0a-198">Opakowanie i wdrażanie zasobów</span><span class="sxs-lookup"><span data-stu-id="caa0a-198">Packaging and Deploying Resources</span></span>](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="caa0a-199">W tym artykule opisano model koncentratora i szprychy, który jest używany przez program .NET Framework do pakowania i wdrażania zasobów; obejmuje konwencje nazewnictwa zasobów, proces rezerwowy i alternatywy pakowania.</span><span class="sxs-lookup"><span data-stu-id="caa0a-199">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|
|[<span data-ttu-id="caa0a-200">Wdrażanie aplikacji międzyoperacyjnych</span><span class="sxs-lookup"><span data-stu-id="caa0a-200">Deploying an Interop Application</span></span>](../interop/deploying-an-interop-application.md)|<span data-ttu-id="caa0a-201">W tym artykule wyjaśniono, jak wysyłać i instalować aplikacje interop, które zazwyczaj obejmują zestaw klienta .NET Framework, jeden lub więcej zestawów międzyoperacyjnych reprezentujących odrębne biblioteki typu COM i jeden lub więcej zarejestrowanych składników COM.</span><span class="sxs-lookup"><span data-stu-id="caa0a-201">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|
|[<span data-ttu-id="caa0a-202">Porady: pobieranie danych o postępie z Instalatora .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="caa0a-202">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="caa0a-203">W tym artykule opisano sposób dyskretnego uruchamiania i śledzenia procesu instalacji programu .NET Framework, podczas gdy wyświetlany jest własny widok postępu instalacji.</span><span class="sxs-lookup"><span data-stu-id="caa0a-203">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|

## <a name="see-also"></a><span data-ttu-id="caa0a-204">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="caa0a-204">See also</span></span>

- [<span data-ttu-id="caa0a-205">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="caa0a-205">Development Guide</span></span>](../development-guide.md)
