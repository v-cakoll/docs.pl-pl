---
title: "Dodatki i rozszerzalność"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extensibility [.NET Framework], add-ins
- add-ins [.NET Framework]
- add-ins [.NET Framework], about
- hosts [.NET Framework], compared to add-ins
- .NET Framework, add-ins
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], compared to hosts
- .NET Framework, extensibility
- versioning [.NET Framework], add-ins
ms.assetid: 8dd45b02-7218-40f9-857d-40d7b98b850b
caps.latest.revision: "42"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9bd09d0da70869ba193b414d8a2ce6c25cbb6b38
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2017
---
# <a name="add-ins-and-extensibility"></a><span data-ttu-id="e4a8b-102">Dodatki i rozszerzalność</span><span class="sxs-lookup"><span data-stu-id="e4a8b-102">Add-ins and Extensibility</span></span>
<a name="top"></a><span data-ttu-id="e4a8b-103">Dodatki Podaj rozszerzonych funkcji lub usług dla aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-103">Add-ins provide extended features or services for a host application.</span></span> <span data-ttu-id="e4a8b-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Zapewnia model programowania, w której deweloperzy mogą używać w celu opracowywania dodatków i aktywować je w aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides a programming model that developers can use to develop add-ins and activate them in their host application.</span></span> <span data-ttu-id="e4a8b-105">Model osiąga to, tworząc potok komunikacji między hostem a dodatku.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-105">The model achieves this by constructing a communication pipeline between the host and the add-in.</span></span> <span data-ttu-id="e4a8b-106">Model jest zaimplementowana przy użyciu typów w <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, i <xref:System.AddIn.Contract> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-106">The model is implemented by using the types in the <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, and <xref:System.AddIn.Contract> namespaces.</span></span>  
  
 <span data-ttu-id="e4a8b-107">Ten przegląd zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="e4a8b-107">This overview contains the following sections:</span></span>  
  
-   [<span data-ttu-id="e4a8b-108">Dodatek modelu</span><span class="sxs-lookup"><span data-stu-id="e4a8b-108">Add-in Model</span></span>](#addin_model)  
  
-   [<span data-ttu-id="e4a8b-109">Dodatki i hostów</span><span class="sxs-lookup"><span data-stu-id="e4a8b-109">Distinguishing Between Add-ins and Hosts</span></span>](#distinguishing_between_addins_and_hosts)  
  
-   [<span data-ttu-id="e4a8b-110">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="e4a8b-110">Related Topics</span></span>](#related_topics)  
  
-   [<span data-ttu-id="e4a8b-111">Odwołanie</span><span class="sxs-lookup"><span data-stu-id="e4a8b-111">Reference</span></span>](#reference)  
  
> [!NOTE]
>  <span data-ttu-id="e4a8b-112">Dla budynku potoków dodatku, można znaleźć dodatkowe przykładowy kod i wersji zapoznawczych platformy technologię klienta narzędzi w [zarządzanych rozszerzeń i Dodaj w ramach lokacji w witrynie CodePlex](http://go.microsoft.com/fwlink/?LinkId=121190).</span><span class="sxs-lookup"><span data-stu-id="e4a8b-112">You can find additional sample code, and customer technology previews of tools for building add-in pipelines, at the [Managed Extensibility and Add-In Framework site on CodePlex](http://go.microsoft.com/fwlink/?LinkId=121190).</span></span>  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a><span data-ttu-id="e4a8b-113">Dodatek modelu</span><span class="sxs-lookup"><span data-stu-id="e4a8b-113">Add-in Model</span></span>  
 <span data-ttu-id="e4a8b-114">Model dodatku składa się z szeregu segmentów, które tworzą dodatku potoku (znanej także jako potok komunikacji), która jest odpowiedzialna za całą komunikację między dodatek i hostem.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-114">The add-in model consists of a series of segments that make up the add-in pipeline (also known as the communication pipeline), that is responsible for all communication between the add-in and the host.</span></span> <span data-ttu-id="e4a8b-115">Potok to model symetryczny komunikacji segmentów, które wymiany danych między dodatek i jej hosta.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-115">The pipeline is a symmetrical communication model of segments that exchange data between an add-in and its host.</span></span> <span data-ttu-id="e4a8b-116">Tworzenie te segmenty między hostem a dodatek zawiera wymagane warstwy abstrakcji, które obsługuje przechowywanie wersji i izolacja dodatku.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-116">Developing these segments between the host and the add-in provides the required layers of abstraction that support versioning and isolation of the add-in.</span></span>  
  
 <span data-ttu-id="e4a8b-117">Na poniższej ilustracji przedstawiono potoku.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-117">The following illustration shows the pipeline.</span></span>  
  
 <span data-ttu-id="e4a8b-118">![Dodaj &#45; w modelu procesu. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span><span class="sxs-lookup"><span data-stu-id="e4a8b-118">![Add&#45;in pipeline model.](../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span></span>  
<span data-ttu-id="e4a8b-119">Potok dodatku</span><span class="sxs-lookup"><span data-stu-id="e4a8b-119">Add-in pipeline</span></span>  
  
 <span data-ttu-id="e4a8b-120">Zestawy dla te segmenty nie są wymagane w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-120">The assemblies for these segments are not required to be in the same application domain.</span></span> <span data-ttu-id="e4a8b-121">Można załadować dodatku do jego własnej nowej domeny aplikacji, do istniejącej domeny aplikacji lub nawet w domenie aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-121">You can load an add-in into its own new application domain, into an existing application domain, or even into the host's application domain.</span></span> <span data-ttu-id="e4a8b-122">Do tej samej domenie aplikacji, umożliwiający dodatki współużytkowanie zasobów i kontekstów zabezpieczeń można załadować wiele dodatków.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-122">You can load multiple add-ins into the same application domain, which enables the add-ins to share resources and security contexts.</span></span>  
  
 <span data-ttu-id="e4a8b-123">Obsługuje modelu dodatku i zaleca, opcjonalne granicę między hostem a dodatku, nazywanego granica izolacji (znanej także jako granic zdalnych).</span><span class="sxs-lookup"><span data-stu-id="e4a8b-123">The add-in model supports, and recommends, an optional boundary between the host and the add-in, which is called the isolation boundary (also known as a remoting boundary).</span></span> <span data-ttu-id="e4a8b-124">Tę granicę można granice domeny lub procesu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-124">This boundary can be an application domain or process boundary.</span></span>  
  
 <span data-ttu-id="e4a8b-125">Segment kontraktu w środku potoku jest ładowany do zarówno domeny aplikacji hosta, jak i dodatku domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-125">The contract segment in the middle of the pipeline is loaded into both the host's application domain and the add-in's application domain.</span></span> <span data-ttu-id="e4a8b-126">Kontrakt definiuje metody wirtualne który hoście i Użyj dodatku do programu exchange typów ze sobą.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-126">The contract defines the virtual methods that the host and the add-in use to exchange types with each other.</span></span>  
  
 <span data-ttu-id="e4a8b-127">Do przekazywania granica izolacji, typy muszą być umów lub typów możliwych do serializacji.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-127">To pass through the isolation boundary, types must be either contracts or serializable types.</span></span> <span data-ttu-id="e4a8b-128">Typy, które nie umów lub typów możliwych do serializacji muszą zostać skonwertowane do kontraktów segmentami karty w potoku.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-128">Types that are not contracts or serializable types must be converted to contracts by the adapter segments in the pipeline.</span></span>  
  
 <span data-ttu-id="e4a8b-129">Widok segmentów potoku są abstrakcyjnych klas podstawowych lub interfejsów, które dostarczają hosta i Dodaj w widoku metody, które mają, zgodnie z umową.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-129">The view segments of the pipeline are abstract base classes or interfaces that provide the host and the add-in with a view of the methods that they share, as defined by the contract.</span></span>  
  
 <span data-ttu-id="e4a8b-130">Aby uzyskać więcej informacji o tworzeniu segmentów potoku, zobacz [rozwój potoku](../../../docs/framework/add-ins/pipeline-development.md).</span><span class="sxs-lookup"><span data-stu-id="e4a8b-130">For more information about developing pipeline segments, see [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md).</span></span>  
  
 <span data-ttu-id="e4a8b-131">W kolejnych sekcjach opisano funkcje modelu dodatku.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-131">The sections that follow describe the features of the add-in model.</span></span>  
  
### <a name="independent-versioning"></a><span data-ttu-id="e4a8b-132">Niezależnie od wersji</span><span class="sxs-lookup"><span data-stu-id="e4a8b-132">Independent Versioning</span></span>  
 <span data-ttu-id="e4a8b-133">Model dodatku pozwala niezależnie hostów i dodatki do wersji.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-133">The add-in model allows hosts and add-ins to version independently.</span></span> <span data-ttu-id="e4a8b-134">W związku z tym modelem dodatku umożliwia następujące scenariusze:</span><span class="sxs-lookup"><span data-stu-id="e4a8b-134">As a result, the add-in model enables the following scenarios:</span></span>  
  
-   <span data-ttu-id="e4a8b-135">Tworzenie kart, które umożliwia hosta dodatku skompilowany dla wcześniejszych wersji programu host.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-135">Creating an adapter that enables a host to use an add-in built for a previous version of the host.</span></span>  
  
-   <span data-ttu-id="e4a8b-136">Tworzenie adaptera, które umożliwia hosta dodatku utworzony przy użyciu nowszej wersji hosta.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-136">Creating an adapter that enables a host to use an add-in built for a later version of the host.</span></span>  
  
-   <span data-ttu-id="e4a8b-137">Tworzenie adaptera hosta do użycia dodatków umożliwia skompilowany dla innego hosta.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-137">Creating an adapter that enables a host to use add-ins built for a different host.</span></span>  
  
### <a name="discovery-and-activation"></a><span data-ttu-id="e4a8b-138">Odnajdywanie i aktywacji</span><span class="sxs-lookup"><span data-stu-id="e4a8b-138">Discovery and Activation</span></span>  
 <span data-ttu-id="e4a8b-139">Dodatek można aktywować przy użyciu tokenu z kolekcji, reprezentująca dodatki znaleziono z magazynu informacji.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-139">You can activate an add-in by using a token from a collection that represents the add-ins found from an information store.</span></span> <span data-ttu-id="e4a8b-140">Dodatki są znaleziony podczas przeszukiwania dla typu, który definiuje widoku hosta dodatku.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-140">Add-ins are found by searching for the type that defines the host's view of the add-in.</span></span> <span data-ttu-id="e4a8b-141">Można również znaleźć określonego dodatku według typu, który definiuje dodatku.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-141">You can also find a specific add-in by the type that defines the add-in.</span></span> <span data-ttu-id="e4a8b-142">Magazyn informacji składa się z dwóch plików pamięci podręcznej: Magazyn potoku i Magazyn dodatków.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-142">The information store consists of two cache files: the pipeline store and the add-in store.</span></span>  
  
 <span data-ttu-id="e4a8b-143">Aby uzyskać informacji na temat aktualizowania i ponowne kompilowanie magazynu informacji, zobacz [dodatku odnajdywania](http://msdn.microsoft.com/en-us/5d268dde-11df-4c4d-a022-f58d88bbc421).</span><span class="sxs-lookup"><span data-stu-id="e4a8b-143">For information about updating and rebuilding the information store, see [Add-in Discovery](http://msdn.microsoft.com/en-us/5d268dde-11df-4c4d-a022-f58d88bbc421).</span></span> <span data-ttu-id="e4a8b-144">Uzyskać informacji o aktywacji dodatków, zobacz [dodatku aktywacji](http://msdn.microsoft.com/en-us/bedcbcdf-5964-4215-b5f3-3299798b2b3f) i [porady: uaktywnić dodatki z różnych izolacji i zabezpieczeń](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="e4a8b-144">For information about activating add-ins, see [Add-in Activation](http://msdn.microsoft.com/en-us/bedcbcdf-5964-4215-b5f3-3299798b2b3f) and [How to: Activate Add-ins with Different Isolation and Security](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="isolation-levels-and-external-processes"></a><span data-ttu-id="e4a8b-145">Poziom izolacji i procesów zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="e4a8b-145">Isolation Levels and External Processes</span></span>  
 <span data-ttu-id="e4a8b-146">Model dodatku obsługuje kilka poziomów izolacji między dodatek i jej hosta lub dodatków. Te poziomy od najmniej izolowanym, są następujące:</span><span class="sxs-lookup"><span data-stu-id="e4a8b-146">The add-in model supports several levels of isolation between an add-in and its host or between add-ins. Starting from the least isolated, these levels are as follows:</span></span>  
  
-   <span data-ttu-id="e4a8b-147">Dodatek jest uruchamiany w tej samej domenie aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-147">The add-in runs in the same application domain as the host.</span></span> <span data-ttu-id="e4a8b-148">Nie jest to zalecane, ponieważ utratę izolacji i zwalniania możliwości, które można uzyskać, korzystając z różnych domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-148">This is not recommended because you lose the isolation and unloading capabilities that you get when you use different application domains.</span></span>  
  
-   <span data-ttu-id="e4a8b-149">Wiele dodatki są ładowane do tej samej domenie aplikacji, która różni się od domeny aplikacji używana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-149">Multiple add-ins are loaded into the same application domain that is different from the application domain used by the host.</span></span>  
  
-   <span data-ttu-id="e4a8b-150">Każdy dodatek jest załadowany wyłącznie do własnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-150">Each add-in is loaded exclusively into its own application domain.</span></span> <span data-ttu-id="e4a8b-151">Jest to najbardziej typowe poziom izolacji.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-151">This is the most common level of isolation.</span></span>  
  
-   <span data-ttu-id="e4a8b-152">Wiele dodatki są ładowane do tej samej domeny aplikacji w procesie zewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-152">Multiple add-ins are loaded into the same application domain in an external process.</span></span>  
  
-   <span data-ttu-id="e4a8b-153">Każdy dodatek jest załadowany wyłącznie do własnej domeny aplikacji w procesie zewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-153">Each add-in is loaded exclusively into its own application domain in an external process.</span></span> <span data-ttu-id="e4a8b-154">Jest to najbardziej izolowanego scenariusz.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-154">This is the most isolated scenario.</span></span>  
  
 <span data-ttu-id="e4a8b-155">Aby uzyskać więcej informacji o używaniu procesów zewnętrznych, zobacz [porady: uaktywnić dodatki z różnych izolacji i zabezpieczeń](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="e4a8b-155">For more information about using external processes, see [How to: Activate Add-ins with Different Isolation and Security](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="lifetime-management"></a><span data-ttu-id="e4a8b-156">Zarządzanie okresem istnienia</span><span class="sxs-lookup"><span data-stu-id="e4a8b-156">Lifetime Management</span></span>  
 <span data-ttu-id="e4a8b-157">Ponieważ model dodatku obejmuje granic domeny i procesu aplikacji, wyrzucanie elementów bezużytecznych przez samego siebie nie wystarcza do wydania i odzyskiwanie obiektów.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-157">Because the add-in model spans application domain and process boundaries, garbage collection by itself is not sufficient to release and reclaim objects.</span></span> <span data-ttu-id="e4a8b-158">Model dodatku zapewnia mechanizm zarządzania okresu istnienia, który korzysta z tokenów i liczenie odwołań i zwykle nie wymaga dodatkowego programowania.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-158">The add-in model provides a lifetime management mechanism that uses tokens and reference counting, and usually does not require additional programming.</span></span> <span data-ttu-id="e4a8b-159">Aby uzyskać więcej informacji, zobacz [Zarządzanie okresem istnienia](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="e4a8b-159">For more information, see [Lifetime Management](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
 [<span data-ttu-id="e4a8b-160">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="e4a8b-160">Back to top</span></span>](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a><span data-ttu-id="e4a8b-161">Dodatki i hostów</span><span class="sxs-lookup"><span data-stu-id="e4a8b-161">Distinguishing Between Add-ins and Hosts</span></span>  
 <span data-ttu-id="e4a8b-162">Różnica między dodatek i hosta jest jedynie, że host jest taki, który uaktywnia dodatku.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-162">The difference between an add-in and a host is merely that the host is the one that activates the add-in.</span></span> <span data-ttu-id="e4a8b-163">Host może być większy dwóch, takie jak aplikacja edytora i jego pisowni; lub hosta może być mniejszy z dwóch, takich jak klientem obsługi wiadomości błyskawicznych osadza odtwarzacza multimedialnego.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-163">The host can be the larger of the two, such as a word processing application and its spell checkers; or the host can be the smaller of the two, such as an instant messaging client that embeds a media player.</span></span> <span data-ttu-id="e4a8b-164">Model dodatku obsługuje dodatki w scenariuszach klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-164">The add-in model supports add-ins in both client and server scenarios.</span></span> <span data-ttu-id="e4a8b-165">Przykładami dodatki serwera dodatków, które dostarczają serwerów poczty antywirusowym, filtry i ochrony IP.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-165">Examples of server add-ins include add-ins that provide mail servers with virus scanning, spam filters, and IP protection.</span></span> <span data-ttu-id="e4a8b-166">Klient dodatku przykładami odwołanie dodatków dla edytory tekstów, specjalne funkcje dla programów grafiki i gry i antywirusowe dla klientów lokalnych poczty e-mail.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-166">Client add-in examples include reference add-ins for word processors, specialized features for graphics programs and games, and virus scanning for local e-mail clients.</span></span>  
  
 [<span data-ttu-id="e4a8b-167">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="e4a8b-167">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="e4a8b-168">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="e4a8b-168">Related Topics</span></span>  
  
|<span data-ttu-id="e4a8b-169">Tytuł</span><span class="sxs-lookup"><span data-stu-id="e4a8b-169">Title</span></span>|<span data-ttu-id="e4a8b-170">Opis</span><span class="sxs-lookup"><span data-stu-id="e4a8b-170">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e4a8b-171">Rozwój potoku</span><span class="sxs-lookup"><span data-stu-id="e4a8b-171">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)|<span data-ttu-id="e4a8b-172">W tym artykule opisano potok komunikacji segmentów z aplikacji hosta do dodatku.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-172">Describes the communication pipeline of segments from the host application to the add-in.</span></span> <span data-ttu-id="e4a8b-173">Przykłady kodu w wskazówki tematach opisano sposób tworzenia potoku i sposobu wdrażania segmentów potoku w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e4a8b-173">Provides code examples in walkthrough topics that describe how to construct the pipeline and how to deploy segments to the pipeline in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>|  
|[<span data-ttu-id="e4a8b-174">Zestawów i domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="e4a8b-174">Application Domains and Assemblies</span></span>](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)|<span data-ttu-id="e4a8b-175">Opisuje relację między domenami aplikacji, które zapewniają granica izolacji zabezpieczeń, niezawodności i przechowywanie wersji i zestawów.</span><span class="sxs-lookup"><span data-stu-id="e4a8b-175">Describes the relationship between application domains, which provide an isolation boundary for security, reliability, and versioning, and assemblies.</span></span>|  
  
 [<span data-ttu-id="e4a8b-176">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="e4a8b-176">Back to top</span></span>](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a><span data-ttu-id="e4a8b-177">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="e4a8b-177">Reference</span></span>  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [<span data-ttu-id="e4a8b-178">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="e4a8b-178">Back to top</span></span>](#top)