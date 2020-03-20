---
title: Programowanie przy użyciu zestawów i domen aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
- application domains, programming
- programming application domains
ms.assetid: 96d3b8e3-bef8-4da0-9a81-9841e23a94e9
ms.openlocfilehash: 2c849d27c70971d17bf4359ee7ae1081ee976a5f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73119821"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="58ac6-102">Programowanie przy użyciu zestawów i domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="58ac6-102">Programming with Application Domains and Assemblies</span></span>

<span data-ttu-id="58ac6-103">Hosty, takie jak Microsoft Internet Explorer, ASP.NET i powłoki systemu Windows, ładują środowisko uruchomieniowe wspólnego języka do procesu, tworzą [domenę aplikacji](application-domains.md) w tym procesie, a następnie ładują i wykonaj kod użytkownika w tej domenie aplikacji podczas uruchamiania aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="58ac6-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="58ac6-104">W większości przypadków nie trzeba się martwić o tworzenie domen aplikacji i ładowanie zestawów do nich, ponieważ host środowiska wykonawczego wykonuje te zadania.</span><span class="sxs-lookup"><span data-stu-id="58ac6-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
<span data-ttu-id="58ac6-105">Jeśli jednak tworzysz aplikację, która będzie obsługiwać środowisko uruchomieniowe języka wspólnego, tworzenie narzędzi lub kodu, które chcesz rozładować programowo, lub tworzenie podłączanych składników, które mogą być rozładowywane i przeładowywane na bieżąco, będziesz tworzyć własne domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="58ac6-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="58ac6-106">Nawet jeśli nie tworzysz hosta środowiska uruchomieniowego, ta sekcja zawiera ważne informacje dotyczące sposobu pracy z domenami aplikacji i zestawami załadowanymi w tych domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="58ac6-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="58ac6-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="58ac6-107">In This Section</span></span>  

[<span data-ttu-id="58ac6-108">Porady dotyczące zestawów i domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="58ac6-108">Application Domains and Assemblies How-to Topics</span></span>](application-domains-and-assemblies-how-to-topics.md)  
<span data-ttu-id="58ac6-109">Zawiera łącza do wszystkich tematów inkoncesjowych znalezionych w dokumentacji koncepcyjnej do programowania z domen aplikacji i zestawów.</span><span class="sxs-lookup"><span data-stu-id="58ac6-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
[<span data-ttu-id="58ac6-110">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="58ac6-110">Using Application Domains</span></span>](use.md)  
<span data-ttu-id="58ac6-111">Zawiera przykłady tworzenia, konfigurowania i używania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="58ac6-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
[<span data-ttu-id="58ac6-112">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="58ac6-112">Programming with Assemblies</span></span>](../../standard/assembly/program.md)  
<span data-ttu-id="58ac6-113">W tym artykule opisano sposób tworzenia, podpisywania i ustawiania atrybutów w zestawach.</span><span class="sxs-lookup"><span data-stu-id="58ac6-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="58ac6-114">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="58ac6-114">Related Sections</span></span>  

[<span data-ttu-id="58ac6-115">Emitowanie dynamicznych metod i zestawów</span><span class="sxs-lookup"><span data-stu-id="58ac6-115">Emitting Dynamic Methods and Assemblies</span></span>](../reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
<span data-ttu-id="58ac6-116">Opisuje sposób tworzenia zestawów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="58ac6-116">Describes how to create dynamic assemblies.</span></span>  
  
[<span data-ttu-id="58ac6-117">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="58ac6-117">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="58ac6-118">Omówienie koncepcyjne zestawów.</span><span class="sxs-lookup"><span data-stu-id="58ac6-118">Provides a conceptual overview of assemblies.</span></span>  
  
[<span data-ttu-id="58ac6-119">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="58ac6-119">Application Domains</span></span>](application-domains.md)  
<span data-ttu-id="58ac6-120">Omówienie koncepcyjne domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="58ac6-120">Provides a conceptual overview of application domains.</span></span>  
  
[<span data-ttu-id="58ac6-121">Przegląd refleksji</span><span class="sxs-lookup"><span data-stu-id="58ac6-121">Reflection Overview</span></span>](../reflection-and-codedom/reflection.md)  
<span data-ttu-id="58ac6-122">Opisuje sposób korzystania **z Reflection** klasy, aby uzyskać informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="58ac6-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
