---
title: Programowanie przy użyciu zestawów i domen aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84d674f7ae8e80d7a5e6a40539e3330fcfa9b563
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053116"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="87d8e-102">Programowanie przy użyciu zestawów i domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="87d8e-102">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="87d8e-103">Hosty, takie jak Microsoft Internet Explorer, ASP.NET i powłoka systemu Windows, ładują środowisko uruchomieniowe języka wspólnego do procesu, tworzą w tym procesie [domenę aplikacji](application-domains.md) , a następnie ładują i wykonują kod użytkownika w tej domenie aplikacji podczas uruchamiania programu .NET Aplikacja struktury.</span><span class="sxs-lookup"><span data-stu-id="87d8e-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="87d8e-104">W większości przypadków nie trzeba martwić się o tworzenie domen aplikacji i ładowaniem do nich zestawów, ponieważ host środowiska uruchomieniowego wykonuje te zadania.</span><span class="sxs-lookup"><span data-stu-id="87d8e-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="87d8e-105">Jeśli jednak tworzysz aplikację, która będzie hostować środowisko uruchomieniowe języka wspólnego, tworzysz narzędzia lub kod, który chcesz usunąć programowo, lub utworzyć podłączane składniki, które mogą zostać zwolnione i ponownie załadowane na bieżąco, będziesz tworzyć własne domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87d8e-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="87d8e-106">Nawet jeśli nie tworzysz hosta środowiska uruchomieniowego, ta sekcja zawiera ważne informacje dotyczące pracy z domenami i zestawami aplikacji załadowanymi w tych domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87d8e-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="87d8e-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="87d8e-107">In This Section</span></span>  

[<span data-ttu-id="87d8e-108">Instrukcje dotyczące zestawów i domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="87d8e-108">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="87d8e-109">Zawiera łącza do wszystkich tematów, które znajdują się w dokumentacji koncepcyjnej dotyczącej programowania przy użyciu domen i zestawów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87d8e-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="87d8e-110">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="87d8e-110">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="87d8e-111">Zawiera przykłady tworzenia, konfigurowania i używania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87d8e-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="87d8e-112">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="87d8e-112">Programming with Assemblies</span></span>](../../standard/assembly/program.md)  
<span data-ttu-id="87d8e-113">Opisuje sposób tworzenia, podpisywania i ustawiania atrybutów dla zestawów.</span><span class="sxs-lookup"><span data-stu-id="87d8e-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="87d8e-114">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="87d8e-114">Related Sections</span></span>  

[<span data-ttu-id="87d8e-115">Emitowanie dynamicznych metod i zestawów</span><span class="sxs-lookup"><span data-stu-id="87d8e-115">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="87d8e-116">Opisuje sposób tworzenia zestawów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="87d8e-116">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="87d8e-117">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="87d8e-117">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="87d8e-118">Omówienie koncepcyjne zestawów.</span><span class="sxs-lookup"><span data-stu-id="87d8e-118">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="87d8e-119">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="87d8e-119">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="87d8e-120">Omówienie koncepcyjne domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="87d8e-120">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="87d8e-121">Przegląd odbicia</span><span class="sxs-lookup"><span data-stu-id="87d8e-121">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="87d8e-122">Opisuje sposób użycia klasy **odbicia** w celu uzyskania informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="87d8e-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
