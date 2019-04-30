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
ms.openlocfilehash: 7124b6b234601e3afc27109ac318f47e3fe40c35
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675354"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="ffe4b-102">Programowanie przy użyciu zestawów i domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="ffe4b-102">Programming with Application Domains and Assemblies</span></span>
<span data-ttu-id="ffe4b-103">Tworzenie hostów, takich jak Microsoft Internet Explorer, ASP.NET i ładowanie powłoki Windows środowiska uruchomieniowego języka wspólnego w procesie [domeny aplikacji](../../../docs/framework/app-domains/application-domains.md) tego przetwarzania i następnie załadować i wykonywanie kodu użytkownika w tej domenie aplikacji podczas uruchamiania aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ffe4b-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](../../../docs/framework/app-domains/application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="ffe4b-104">W większości przypadków nie trzeba martwić się o sposobie tworzenia domeny aplikacji i ładowanie zestawów do nich, ponieważ host środowiska uruchomieniowego wykonuje te zadania.</span><span class="sxs-lookup"><span data-stu-id="ffe4b-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
 <span data-ttu-id="ffe4b-105">Jednak jeśli tworzysz aplikację, która będzie obsługiwać środowisko uruchomieniowe języka wspólnego, utworzenie narzędzi lub kod, który chcesz zwolnić programowo, lub podłączanych składników, które może być zwolniony i ponownie załadowany na bieżąco, zostanie utworzona własne domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ffe4b-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="ffe4b-106">Nawet wtedy, gdy host środowiska uruchomieniowego są nietworzenie, ta sekcja zawiera ważne informacje na temat pracy z domenami aplikacji i zestawy, ładowane w tych domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ffe4b-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ffe4b-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ffe4b-107">In This Section</span></span>  
 [<span data-ttu-id="ffe4b-108">Instrukcje dotyczące zestawów i domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="ffe4b-108">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 <span data-ttu-id="ffe4b-109">Zawiera łącza do wszystkich tematów instrukcje w dokumentacji koncepcyjnego dla programowania, korzystając z domeny aplikacji i zestawy.</span><span class="sxs-lookup"><span data-stu-id="ffe4b-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
 [<span data-ttu-id="ffe4b-110">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="ffe4b-110">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)  
 <span data-ttu-id="ffe4b-111">Przykłady tworzenia, konfigurowania i używania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ffe4b-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
 [<span data-ttu-id="ffe4b-112">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="ffe4b-112">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="ffe4b-113">W tym artykule opisano sposób tworzenia, zaloguj się i ustawianie atrybutów zestawów.</span><span class="sxs-lookup"><span data-stu-id="ffe4b-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ffe4b-114">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ffe4b-114">Related Sections</span></span>  
 [<span data-ttu-id="ffe4b-115">Emitowanie dynamicznych metod i zestawów</span><span class="sxs-lookup"><span data-stu-id="ffe4b-115">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="ffe4b-116">W tym artykule opisano sposób tworzenia zestawów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="ffe4b-116">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="ffe4b-117">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="ffe4b-117">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="ffe4b-118">Omówienie koncepcyjne zestawów.</span><span class="sxs-lookup"><span data-stu-id="ffe4b-118">Provides a conceptual overview of assemblies.</span></span>  
  
 [<span data-ttu-id="ffe4b-119">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="ffe4b-119">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="ffe4b-120">Omówienie koncepcyjne domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ffe4b-120">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="ffe4b-121">Omówienie odbicia</span><span class="sxs-lookup"><span data-stu-id="ffe4b-121">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="ffe4b-122">Opisuje sposób używania **odbicia** klasy, aby uzyskać informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="ffe4b-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
