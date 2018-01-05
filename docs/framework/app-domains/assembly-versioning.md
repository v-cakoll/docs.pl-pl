---
title: Przechowywanie wersji zestawu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 327ef282c23fc02791eb7c531fd1ae25c6700fd4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-versioning"></a><span data-ttu-id="5f89b-102">Przechowywanie wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="5f89b-102">Assembly Versioning</span></span>
<span data-ttu-id="5f89b-103">Zarządzanie wszystkimi wersjami zestawów używających środowiska uruchomieniowego języka wspólnego odbywa się na poziomie zestawów.</span><span class="sxs-lookup"><span data-stu-id="5f89b-103">All versioning of assemblies that use the common language runtime is done at the assembly level.</span></span> <span data-ttu-id="5f89b-104">Konkretna wersja zestawu oraz wersje zestawów zależnych są rejestrowane w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="5f89b-104">The specific version of an assembly and the versions of dependent assemblies are recorded in the assembly's manifest.</span></span> <span data-ttu-id="5f89b-105">Domyślna zasada dotycząca wersji środowiska dla środowiska uruchomieniowego stanowi, że aplikacje są uruchamiane tylko w wersjach, w których zostały skompilowane i przetestowane, chyba że inaczej stanowią jawnie zasady dotyczące wersji określone w plikach konfiguracji (plik konfiguracji aplikacji, plik zasad wydawcy i plik konfiguracji administratora komputera).</span><span class="sxs-lookup"><span data-stu-id="5f89b-105">The default version policy for the runtime is that applications run only with the versions they were built and tested with, unless overridden by explicit version policy in configuration files (the application configuration file, the publisher policy file, and the computer's administrator configuration file).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f89b-106">Zarządzanie wersjami dotyczy wyłącznie zestawów o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="5f89b-106">Versioning is done only on assemblies with strong names.</span></span>  
  
 <span data-ttu-id="5f89b-107">W celu rozpoznania żądania powiązania zestawu środowisko uruchomieniowe wykonuje kilka czynności:</span><span class="sxs-lookup"><span data-stu-id="5f89b-107">The runtime performs several steps to resolve an assembly binding request:</span></span>  
  
1.  <span data-ttu-id="5f89b-108">Sprawdza oryginalne odwołanie do zestawu w celu ustalenia wersji zestawu, którą należy powiązać.</span><span class="sxs-lookup"><span data-stu-id="5f89b-108">Checks the original assembly reference to determine the version of the assembly to be bound.</span></span>  
  
2.  <span data-ttu-id="5f89b-109">Szuka wszystkich właściwych plików konfiguracji, do których trzeba zastosować zasady dotyczące wersji.</span><span class="sxs-lookup"><span data-stu-id="5f89b-109">Checks for all applicable configuration files to apply version policy.</span></span>  
  
3.  <span data-ttu-id="5f89b-110">Na podstawie oryginalnego odwołania do zestawu ustala poprawny zestaw oraz wszelkie przekierowania określone w plikach konfiguracji, po czym ustala wersję, która ma zostać powiązana z wywołującym zestawem.</span><span class="sxs-lookup"><span data-stu-id="5f89b-110">Determines the correct assembly from the original assembly reference and any redirection specified in the configuration files, and determines the version that should be bound to the calling assembly.</span></span>  
  
4.  <span data-ttu-id="5f89b-111">Sprawdza globalnej pamięci podręcznej zestawów, codebases określony w pliki konfiguracji, a następnie kontroli katalogu i jego podkatalogach, przy użyciu sondowania reguł aplikacji wyjaśniono w [jak zestawy środowiska wykonawczego lokalizuje](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="5f89b-111">Checks the global assembly cache, codebases specified in configuration files, and then checks the application's directory and subdirectories using the probing rules explained in [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="5f89b-112">Poniższa ilustracja przedstawia te kroki.</span><span class="sxs-lookup"><span data-stu-id="5f89b-112">The following illustration shows these steps.</span></span>  
  
 <span data-ttu-id="5f89b-113">![Deklaracja myAssembly extern](../../../docs/framework/app-domains/media/versioningover.gif "versioningover")</span><span class="sxs-lookup"><span data-stu-id="5f89b-113">![.assembly extern myAssembly](../../../docs/framework/app-domains/media/versioningover.gif "versioningover")</span></span>  
<span data-ttu-id="5f89b-114">Rozpoznawanie żądania powiązania zestawu</span><span class="sxs-lookup"><span data-stu-id="5f89b-114">Resolving an assembly binding request</span></span>  
  
 <span data-ttu-id="5f89b-115">Aby uzyskać więcej informacji dotyczących konfigurowania aplikacji, zobacz [konfigurowania aplikacji](../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="5f89b-115">For more information about configuring applications, see [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="5f89b-116">Aby uzyskać więcej informacji na temat powiązania zasad, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="5f89b-116">For more information about binding policy, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="5f89b-117">Informacje o wersji</span><span class="sxs-lookup"><span data-stu-id="5f89b-117">Version Information</span></span>  
 <span data-ttu-id="5f89b-118">Każdy zestaw może przedstawiać informacje o wersji na dwa odrębne sposoby:</span><span class="sxs-lookup"><span data-stu-id="5f89b-118">Each assembly has two distinct ways of expressing version information:</span></span>  
  
-   <span data-ttu-id="5f89b-119">Numer wersji zestawu, który razem z nazwą zestawu i informacjami o kulturze jest częścią tożsamości zestawu.</span><span class="sxs-lookup"><span data-stu-id="5f89b-119">The assembly's version number, which, together with the assembly name and culture information, is part of the assembly's identity.</span></span> <span data-ttu-id="5f89b-120">Numer jest wykorzystywany przez środowisko uruchomieniowe do wymuszania zasad dotyczących wersji oraz odgrywa kluczową rolę w procesie rozpoznawania typów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5f89b-120">This number is used by the runtime to enforce version policy and plays a key part in the type resolution process at run time.</span></span>  
  
-   <span data-ttu-id="5f89b-121">Dane informacyjne wersji, czyli ciąg tekstowy reprezentujący dodatkowe informacje o wersji dołączane są wyłącznie w celach informacyjnych.</span><span class="sxs-lookup"><span data-stu-id="5f89b-121">An informational version, which is a string that represents additional version information included for informational purposes only.</span></span>  
  
### <a name="assembly-version-number"></a><span data-ttu-id="5f89b-122">Numer wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="5f89b-122">Assembly Version Number</span></span>  
 <span data-ttu-id="5f89b-123">Elementem tożsamości każdego zestawu jest jego numer wersji.</span><span class="sxs-lookup"><span data-stu-id="5f89b-123">Each assembly has a version number as part of its identity.</span></span> <span data-ttu-id="5f89b-124">W związku z tym dwa zestawy, które różnią się numerem wersji, są przez środowisko uruchomieniowe uznawane za całkowicie różne zestawy.</span><span class="sxs-lookup"><span data-stu-id="5f89b-124">As such, two assemblies that differ by version number are considered by the runtime to be completely different assemblies.</span></span> <span data-ttu-id="5f89b-125">Numer wersji jest fizycznie reprezentowany jako czteroczęściowy ciąg tekstowy o następującym formacie:</span><span class="sxs-lookup"><span data-stu-id="5f89b-125">This version number is physically represented as a four-part string with the following format:</span></span>  
  
 <span data-ttu-id="5f89b-126">\<*Wersja główna*>.\< *wersja pomocnicza*>.\< *numer kompilacji*>.\< *poprawki*></span><span class="sxs-lookup"><span data-stu-id="5f89b-126">\<*major version*>.\<*minor version*>.\<*build number*>.\<*revision*></span></span>  
  
 <span data-ttu-id="5f89b-127">Na przykład wersja 1.5.1254.0 określa „1” jako wersję główną, „5” jako wersję pomocniczą, „1254” jako numer kompilacji i „0” jako numer poprawki.</span><span class="sxs-lookup"><span data-stu-id="5f89b-127">For example, version 1.5.1254.0 indicates 1 as the major version, 5 as the minor version, 1254 as the build number, and 0 as the revision number.</span></span>  
  
 <span data-ttu-id="5f89b-128">Numer wersji jest przechowywany w manifeście zestawu razem z innymi informacjami tożsamości, takimi jak nazwa zestawu i klucz publiczny, a także informacjami dotyczącymi relacji i tożsamości innych zestawów połączonych z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="5f89b-128">The version number is stored in the assembly manifest along with other identity information, including the assembly name and public key, as well as information on relationships and identities of other assemblies connected with the application.</span></span>  
  
 <span data-ttu-id="5f89b-129">Podczas kompilowania zestawu narzędzie programistyczne zapisuje informacje o zależnościach każdego zestawu, do którego istnieje odwołanie w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="5f89b-129">When an assembly is built, the development tool records dependency information for each assembly that is referenced in the assembly manifest.</span></span> <span data-ttu-id="5f89b-130">Na podstawie numerów wersji oraz innych informacji konfiguracyjnych wprowadzonych przez administratora, aplikację lub wydawcę środowisko uruchomieniowe ładuje odpowiednią wersję przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="5f89b-130">The runtime uses these version numbers, in conjunction with configuration information set by an administrator, an application, or a publisher, to load the proper version of a referenced assembly.</span></span>  
  
 <span data-ttu-id="5f89b-131">Na potrzeby zarządzania wersjami środowisko uruchomieniowe rozróżnia między zestawami zwykłymi i o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="5f89b-131">The runtime distinguishes between regular and strong-named assemblies for the purposes of versioning.</span></span> <span data-ttu-id="5f89b-132">Sprawdzanie wersji dotyczy tylko zestawów o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="5f89b-132">Version checking only occurs with strong-named assemblies.</span></span>  
  
 <span data-ttu-id="5f89b-133">Informacji o określaniu wersji powiązania zasad, zobacz [konfigurowania aplikacji](../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="5f89b-133">For information about specifying version binding policies, see [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="5f89b-134">Aby dowiedzieć się jak używa informacje o wersji środowiska uruchomieniowego można znaleźć określonego zestawu, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="5f89b-134">For information about how the runtime uses version information to find a particular assembly, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
### <a name="assembly-informational-version"></a><span data-ttu-id="5f89b-135">Informacje o wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="5f89b-135">Assembly Informational Version</span></span>  
 <span data-ttu-id="5f89b-136">Informacje o wersji zestawu to ciąg tekstowy, który dołącza do zestawu dodatkowe informacje o wersji jedynie w celach informacyjnych. Informacje te nie są używane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5f89b-136">The informational version is a string that attaches additional version information to an assembly for informational purposes only; this information is not used at run time.</span></span> <span data-ttu-id="5f89b-137">Tekstowe informacje o wersji nawiązują do materiałów marketingowych, opakowania lub nazwy produktu.</span><span class="sxs-lookup"><span data-stu-id="5f89b-137">The text-based informational version corresponds to the product's marketing literature, packaging, or product name and is not used by the runtime.</span></span> <span data-ttu-id="5f89b-138">Informacjami o wersji mogą być na przykład ciągi „Środowisko uruchomieniowe języka wspólnego w wersji 1.0” lub „NET Control z dodatkiem SP 2”.</span><span class="sxs-lookup"><span data-stu-id="5f89b-138">For example, an informational version could be "Common Language Runtime version 1.0" or "NET Control SP 2".</span></span> <span data-ttu-id="5f89b-139">W systemie Microsoft Windows w oknie dialogowym właściwości pliku na karcie Wersja informacje te są wyświetlane w polu „Wersja produktu”.</span><span class="sxs-lookup"><span data-stu-id="5f89b-139">On the Version tab of the file properties dialog in Microsoft Windows, this information appears in the item "Product Version".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f89b-140">Można podać dowolny tekst, ale jeśli ciąg tekstowy nie będzie w formacie używanym przez numer wersji zestawu albo jeśli będzie w tym formacie, ale będzie zawierać symbole wieloznaczne, podczas kompilacji pojawi się komunikat ostrzegawczy.</span><span class="sxs-lookup"><span data-stu-id="5f89b-140">Although you can specify any text, a warning message appears on compilation if the string is not in the format used by the assembly version number, or if it is in that format but contains wildcards.</span></span> <span data-ttu-id="5f89b-141">Ostrzeżenie to jest nieszkodliwe.</span><span class="sxs-lookup"><span data-stu-id="5f89b-141">This warning is harmless.</span></span>  
  
 <span data-ttu-id="5f89b-142">Informacje o wersji są reprezentowane za pomocą niestandardowego atrybutu <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5f89b-142">The informational version is represented using the custom attribute <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5f89b-143">Aby uzyskać więcej informacji na temat atrybutu wersji informacyjny zobacz [ustawienie atrybutów zestawu](../../../docs/framework/app-domains/set-assembly-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5f89b-143">For more information about the informational version attribute, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f89b-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f89b-144">See Also</span></span>  
 [<span data-ttu-id="5f89b-145">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="5f89b-145">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="5f89b-146">Konfigurowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="5f89b-146">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)  
 [<span data-ttu-id="5f89b-147">Ustawienie atrybutów zestawu</span><span class="sxs-lookup"><span data-stu-id="5f89b-147">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 [<span data-ttu-id="5f89b-148">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="5f89b-148">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
