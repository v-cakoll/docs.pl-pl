---
title: Programowanie przy użyciu zestawów i domen aplikacji
description: Poznaj programowanie z domenami i zestawami aplikacji w programie .NET. Zobacz linki do tematów zawierających instrukcje & przykłady tworzenia domen aplikacji & zestawów.
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 1c28fe0abeb279a1dbbc6dcf043c1780c72d79df
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903441"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="d273b-104">Programowanie przy użyciu zestawów i domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="d273b-104">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="d273b-105">Hosty, takie jak Microsoft Internet Explorer, ASP.NET i powłoka systemu Windows, ładują środowisko uruchomieniowe języka wspólnego do procesu, tworzą w tym procesie [domenę aplikacji](application-domains.md) , a następnie ładują i wykonują kod użytkownika w tej domenie aplikacji podczas uruchamiania aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d273b-105">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="d273b-106">W większości przypadków nie trzeba martwić się o tworzenie domen aplikacji i ładowaniem do nich zestawów, ponieważ host środowiska uruchomieniowego wykonuje te zadania.</span><span class="sxs-lookup"><span data-stu-id="d273b-106">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="d273b-107">Jeśli jednak tworzysz aplikację, która będzie hostować środowisko uruchomieniowe języka wspólnego, tworzysz narzędzia lub kod, który chcesz zwolnić programowo, lub tworząc podłączane składniki, które mogą zostać zwolnione i ponownie załadowane na bieżąco, będziesz tworzyć własne domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d273b-107">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="d273b-108">Nawet jeśli nie tworzysz hosta środowiska uruchomieniowego, ta sekcja zawiera ważne informacje dotyczące pracy z domenami i zestawami aplikacji załadowanymi w tych domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d273b-108">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d273b-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d273b-109">In This Section</span></span>  

[<span data-ttu-id="d273b-110">Porady dotyczące zestawów i domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="d273b-110">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="d273b-111">Zawiera łącza do wszystkich tematów, które znajdują się w dokumentacji koncepcyjnej dotyczącej programowania przy użyciu domen i zestawów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d273b-111">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="d273b-112">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="d273b-112">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="d273b-113">Zawiera przykłady tworzenia, konfigurowania i używania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d273b-113">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="d273b-114">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="d273b-114">Programming with Assemblies</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="d273b-115">Opisuje sposób tworzenia, podpisywania i ustawiania atrybutów dla zestawów.</span><span class="sxs-lookup"><span data-stu-id="d273b-115">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d273b-116">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d273b-116">Related Sections</span></span>  

[<span data-ttu-id="d273b-117">Emitowanie dynamicznych metod i zestawów</span><span class="sxs-lookup"><span data-stu-id="d273b-117">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="d273b-118">Opisuje sposób tworzenia zestawów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="d273b-118">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="d273b-119">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="d273b-119">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="d273b-120">Omówienie koncepcyjne zestawów.</span><span class="sxs-lookup"><span data-stu-id="d273b-120">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="d273b-121">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="d273b-121">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="d273b-122">Omówienie koncepcyjne domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d273b-122">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="d273b-123">Przegląd odbicia</span><span class="sxs-lookup"><span data-stu-id="d273b-123">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="d273b-124">Opisuje sposób użycia klasy **odbicia** w celu uzyskania informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="d273b-124">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
