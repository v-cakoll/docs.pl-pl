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
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742435"
---
# <a name="programming-with-application-domains-and-assemblies"></a><span data-ttu-id="adf0c-102">Programowanie przy użyciu zestawów i domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="adf0c-102">Programming with Application Domains and Assemblies</span></span>
<span data-ttu-id="adf0c-103">Hosty, takich jak Microsoft Internet Explorer, ASP.NET i obciążenia powłoki Windows środowisko uruchomieniowe języka wspólnego do procesu tworzenia [domeny aplikacji](../../../docs/framework/app-domains/application-domains.md) w tym przetwarzania i następnie załadowanie i wykonanie kodu użytkownika w tej domenie aplikacji podczas uruchamiania aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="adf0c-103">Hosts such as Microsoft Internet Explorer, ASP.NET, and the Windows shell load the common language runtime into a process, create an [application domain](../../../docs/framework/app-domains/application-domains.md) in that process, and then load and execute user code in that application domain when running a .NET Framework application.</span></span> <span data-ttu-id="adf0c-104">W większości przypadków nie trzeba martwić tworzenia domeny aplikacji i ładowanie zestawów do nich, ponieważ host czasu wykonywania wykonuje te zadania.</span><span class="sxs-lookup"><span data-stu-id="adf0c-104">In most cases, you do not have to worry about creating application domains and loading assemblies into them because the runtime host performs those tasks.</span></span>  
  
 <span data-ttu-id="adf0c-105">Jednak w przypadku tworzenia aplikacji, która będzie obsługiwać środowiska CLR, utworzenie narzędzia lub kod, który chcesz zwolnić programowo, lub podłączany składników, które może być zwolnione i ponownie załadowany na bieżąco, zostanie utworzony własne domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="adf0c-105">However, if you are creating an application that will host the common language runtime, creating tools or code you want to unload programmatically, or creating pluggable components that can be unloaded and reloaded on the fly, you will be creating your own application domains.</span></span> <span data-ttu-id="adf0c-106">Nawet jeśli host czasu wykonywania nie są tworzone, ta sekcja zawiera ważne informacje na temat pracy z zestawów załadowanych w tych domenach aplikacji i domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="adf0c-106">Even if you are not creating a runtime host, this section provides important information on how to work with application domains and assemblies loaded in these application domains.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="adf0c-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="adf0c-107">In This Section</span></span>  
 [<span data-ttu-id="adf0c-108">Instrukcje dotyczące zestawów i domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="adf0c-108">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 <span data-ttu-id="adf0c-109">Zawiera łącza do wszystkich — tematy porad znajdującego się w dokumentacji koncepcyjnego do programowania za pomocą zestawów i domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="adf0c-109">Provides links to all How-to topics found in the conceptual documentation for programming with application domains and assemblies.</span></span>  
  
 [<span data-ttu-id="adf0c-110">Używanie domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="adf0c-110">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)  
 <span data-ttu-id="adf0c-111">Przykłady tworzenie, konfigurowanie i używanie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="adf0c-111">Provides examples of creating, configuring, and using application domains.</span></span>  
  
 [<span data-ttu-id="adf0c-112">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="adf0c-112">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="adf0c-113">Opisuje sposób tworzenia, zaloguj się i ustawić atrybuty zestawów.</span><span class="sxs-lookup"><span data-stu-id="adf0c-113">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="adf0c-114">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="adf0c-114">Related Sections</span></span>  
 [<span data-ttu-id="adf0c-115">Emitowanie dynamicznych metod i zestawów</span><span class="sxs-lookup"><span data-stu-id="adf0c-115">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="adf0c-116">Opisuje sposób tworzenia zestawów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="adf0c-116">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="adf0c-117">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="adf0c-117">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="adf0c-118">Omówienie koncepcyjne zestawów.</span><span class="sxs-lookup"><span data-stu-id="adf0c-118">Provides a conceptual overview of assemblies.</span></span>  
  
 [<span data-ttu-id="adf0c-119">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="adf0c-119">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="adf0c-120">Omówienie koncepcyjne domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="adf0c-120">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="adf0c-121">Odbicie — omówienie</span><span class="sxs-lookup"><span data-stu-id="adf0c-121">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="adf0c-122">Informacje dotyczące używania **odbicia** klasę, aby uzyskać informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="adf0c-122">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
