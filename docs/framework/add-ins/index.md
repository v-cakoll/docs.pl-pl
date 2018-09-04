---
title: Dodatki i rozszerzalność
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb2485f2ecf0426360dba80d443500a92b5a7af6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510057"
---
# <a name="add-ins-and-extensibility"></a><span data-ttu-id="d9276-102">Dodatki i rozszerzalność</span><span class="sxs-lookup"><span data-stu-id="d9276-102">Add-ins and Extensibility</span></span>
<a name="top"></a> <span data-ttu-id="d9276-103">Dodatki zapewniają rozszerzone funkcje lub usługi dla aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="d9276-103">Add-ins provide extended features or services for a host application.</span></span> <span data-ttu-id="d9276-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Zapewnia model programowania, które deweloperzy mogą używać do tworzenia dodatków i ich aktywowania w aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="d9276-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides a programming model that developers can use to develop add-ins and activate them in their host application.</span></span> <span data-ttu-id="d9276-105">Model osiąga to, tworząc potok komunikacji między hostem a dodatkiem.</span><span class="sxs-lookup"><span data-stu-id="d9276-105">The model achieves this by constructing a communication pipeline between the host and the add-in.</span></span> <span data-ttu-id="d9276-106">Model jest implementowany przy użyciu typów w <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, i <xref:System.AddIn.Contract> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d9276-106">The model is implemented by using the types in the <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, and <xref:System.AddIn.Contract> namespaces.</span></span>  
  
 <span data-ttu-id="d9276-107">Ten przegląd zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="d9276-107">This overview contains the following sections:</span></span>  
  
-   [<span data-ttu-id="d9276-108">Model dodatku</span><span class="sxs-lookup"><span data-stu-id="d9276-108">Add-in Model</span></span>](#addin_model)  
  
-   [<span data-ttu-id="d9276-109">Dodatki i hostów</span><span class="sxs-lookup"><span data-stu-id="d9276-109">Distinguishing Between Add-ins and Hosts</span></span>](#distinguishing_between_addins_and_hosts)  
  
-   [<span data-ttu-id="d9276-110">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="d9276-110">Related Topics</span></span>](#related_topics)  
  
-   [<span data-ttu-id="d9276-111">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="d9276-111">Reference</span></span>](#reference)  
  
> [!NOTE]
>  <span data-ttu-id="d9276-112">Do tworzenia potoków dodatku, można znaleźć dodatkowe przykłady kodu i narzędzia klienta z podglądem technologii w [zarządzanych rozszerzeń i Dodaj w ramach lokacji w witrynie CodePlex](https://go.microsoft.com/fwlink/?LinkId=121190).</span><span class="sxs-lookup"><span data-stu-id="d9276-112">You can find additional sample code, and customer technology previews of tools for building add-in pipelines, at the [Managed Extensibility and Add-In Framework site on CodePlex](https://go.microsoft.com/fwlink/?LinkId=121190).</span></span>  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a><span data-ttu-id="d9276-113">Model dodatku</span><span class="sxs-lookup"><span data-stu-id="d9276-113">Add-in Model</span></span>  
 <span data-ttu-id="d9276-114">Model dodatku składa się z szeregu segmentów, które tworzą dodatku potoku (znany także jako potok komunikacji), który jest odpowiedzialny za całej komunikacji między dodatkiem a hostem.</span><span class="sxs-lookup"><span data-stu-id="d9276-114">The add-in model consists of a series of segments that make up the add-in pipeline (also known as the communication pipeline), that is responsible for all communication between the add-in and the host.</span></span> <span data-ttu-id="d9276-115">Potok jest model symetryczne komunikacji segmenty wymianę danych między dodatek i jej hostem.</span><span class="sxs-lookup"><span data-stu-id="d9276-115">The pipeline is a symmetrical communication model of segments that exchange data between an add-in and its host.</span></span> <span data-ttu-id="d9276-116">Tworzenie te segmenty między hostem a dodatkiem zapewnia wymagane warstwy abstrakcji, które obsługuje przechowywanie wersji i izolacji dodatku.</span><span class="sxs-lookup"><span data-stu-id="d9276-116">Developing these segments between the host and the add-in provides the required layers of abstraction that support versioning and isolation of the add-in.</span></span>  
  
 <span data-ttu-id="d9276-117">Poniższa ilustracja przedstawia potoku.</span><span class="sxs-lookup"><span data-stu-id="d9276-117">The following illustration shows the pipeline.</span></span>  
  
 <span data-ttu-id="d9276-118">![Dodaj&#45;w modelu potoku. ](../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span><span class="sxs-lookup"><span data-stu-id="d9276-118">![Add&#45;in pipeline model.](../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span></span>  
<span data-ttu-id="d9276-119">Potok dodatku</span><span class="sxs-lookup"><span data-stu-id="d9276-119">Add-in pipeline</span></span>  
  
 <span data-ttu-id="d9276-120">Zestawy dla te segmenty nie są wymagane w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d9276-120">The assemblies for these segments are not required to be in the same application domain.</span></span> <span data-ttu-id="d9276-121">Możesz załadować dodatek do jego własnej nowej domeny aplikacji, do istniejącej domeny aplikacji lub nawet do domeny aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="d9276-121">You can load an add-in into its own new application domain, into an existing application domain, or even into the host's application domain.</span></span> <span data-ttu-id="d9276-122">W tej samej domenie aplikacji, która umożliwia dodatków udostępnić zasoby obliczeniowe i konteksty zabezpieczeń, należy załadować wielu dodatków.</span><span class="sxs-lookup"><span data-stu-id="d9276-122">You can load multiple add-ins into the same application domain, which enables the add-ins to share resources and security contexts.</span></span>  
  
 <span data-ttu-id="d9276-123">Obsługuje model dodatku, a zaleceniem, opcjonalnie granic między hostem a dodatek, który nazywa się granic izolacji (znany także jako granic wywołaniem funkcji zdalnych).</span><span class="sxs-lookup"><span data-stu-id="d9276-123">The add-in model supports, and recommends, an optional boundary between the host and the add-in, which is called the isolation boundary (also known as a remoting boundary).</span></span> <span data-ttu-id="d9276-124">Tą granicą może być granic domeny lub procesu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d9276-124">This boundary can be an application domain or process boundary.</span></span>  
  
 <span data-ttu-id="d9276-125">Segment umowy w trakcie wykonywania potoku są ładowane do zarówno w domenie aplikacji hosta, jak i dodatku w domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d9276-125">The contract segment in the middle of the pipeline is loaded into both the host's application domain and the add-in's application domain.</span></span> <span data-ttu-id="d9276-126">Kontrakt definiuje metody wirtualnej, hosta i Użyj dodatku do programu exchange typy ze sobą.</span><span class="sxs-lookup"><span data-stu-id="d9276-126">The contract defines the virtual methods that the host and the add-in use to exchange types with each other.</span></span>  
  
 <span data-ttu-id="d9276-127">Aby przekazać za pośrednictwem granic izolacji, typy muszą być kontraktów lub typów możliwych do serializacji.</span><span class="sxs-lookup"><span data-stu-id="d9276-127">To pass through the isolation boundary, types must be either contracts or serializable types.</span></span> <span data-ttu-id="d9276-128">Typy, które są nie kontraktów lub typów możliwych do serializacji, muszą zostać skonwertowane do umów segmentami karty w potoku.</span><span class="sxs-lookup"><span data-stu-id="d9276-128">Types that are not contracts or serializable types must be converted to contracts by the adapter segments in the pipeline.</span></span>  
  
 <span data-ttu-id="d9276-129">Widok segmenty potoku są abstrakcyjne klasy bazowe lub interfejsów, które umożliwiają hosta i dodatek przy użyciu widoku metody, które współużytkują one zgodnie z definicją w umowie.</span><span class="sxs-lookup"><span data-stu-id="d9276-129">The view segments of the pipeline are abstract base classes or interfaces that provide the host and the add-in with a view of the methods that they share, as defined by the contract.</span></span>  
  
 <span data-ttu-id="d9276-130">Aby uzyskać więcej informacji o tworzeniu potoku segmentów, zobacz [opracowywanie potoku](../../../docs/framework/add-ins/pipeline-development.md).</span><span class="sxs-lookup"><span data-stu-id="d9276-130">For more information about developing pipeline segments, see [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md).</span></span>  
  
 <span data-ttu-id="d9276-131">W kolejnych sekcjach opisano funkcje modelu dodatków.</span><span class="sxs-lookup"><span data-stu-id="d9276-131">The sections that follow describe the features of the add-in model.</span></span>  
  
### <a name="independent-versioning"></a><span data-ttu-id="d9276-132">Niezależnie od wersji</span><span class="sxs-lookup"><span data-stu-id="d9276-132">Independent Versioning</span></span>  
 <span data-ttu-id="d9276-133">Model dodatku pozwala niezależnie hostów i dodatki do wersji.</span><span class="sxs-lookup"><span data-stu-id="d9276-133">The add-in model allows hosts and add-ins to version independently.</span></span> <span data-ttu-id="d9276-134">W rezultacie modelu dodatków umożliwia następujące scenariusze:</span><span class="sxs-lookup"><span data-stu-id="d9276-134">As a result, the add-in model enables the following scenarios:</span></span>  
  
-   <span data-ttu-id="d9276-135">Tworzenie adaptera, który umożliwia hosta do użycia dodatku stworzona z myślą o poprzednią wersję hosta.</span><span class="sxs-lookup"><span data-stu-id="d9276-135">Creating an adapter that enables a host to use an add-in built for a previous version of the host.</span></span>  
  
-   <span data-ttu-id="d9276-136">Tworzenie adaptera, który umożliwia hosta do użycia dodatku stworzona z myślą o późniejszą wersję hosta.</span><span class="sxs-lookup"><span data-stu-id="d9276-136">Creating an adapter that enables a host to use an add-in built for a later version of the host.</span></span>  
  
-   <span data-ttu-id="d9276-137">Tworzenie karty, która umożliwia hosta na używanie dodatków stworzona z myślą o innego hosta.</span><span class="sxs-lookup"><span data-stu-id="d9276-137">Creating an adapter that enables a host to use add-ins built for a different host.</span></span>  
  
### <a name="discovery-and-activation"></a><span data-ttu-id="d9276-138">Odnajdywanie i aktywacja</span><span class="sxs-lookup"><span data-stu-id="d9276-138">Discovery and Activation</span></span>  
 <span data-ttu-id="d9276-139">Dodatek można aktywować przy użyciu tokenu z kolekcji, reprezentująca dodatki znalezione na podstawie magazynu informacji.</span><span class="sxs-lookup"><span data-stu-id="d9276-139">You can activate an add-in by using a token from a collection that represents the add-ins found from an information store.</span></span> <span data-ttu-id="d9276-140">Dodatki można znaleźć, wyszukując typ, który definiuje widok hosta dodatków.</span><span class="sxs-lookup"><span data-stu-id="d9276-140">Add-ins are found by searching for the type that defines the host's view of the add-in.</span></span> <span data-ttu-id="d9276-141">Można również znaleźć określonego dodatku, typ, który definiuje dodatku.</span><span class="sxs-lookup"><span data-stu-id="d9276-141">You can also find a specific add-in by the type that defines the add-in.</span></span> <span data-ttu-id="d9276-142">Magazyn informacji składa się z dwóch plików w pamięci podręcznej: store potoku i sklepie dodatku.</span><span class="sxs-lookup"><span data-stu-id="d9276-142">The information store consists of two cache files: the pipeline store and the add-in store.</span></span>  
  
 <span data-ttu-id="d9276-143">Aby uzyskać informacji na temat aktualizowania i ponownie skompilować Magazyn informacji, zobacz [dodatku odnajdywania](https://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421).</span><span class="sxs-lookup"><span data-stu-id="d9276-143">For information about updating and rebuilding the information store, see [Add-in Discovery](https://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421).</span></span> <span data-ttu-id="d9276-144">Aby dowiedzieć się, jak uaktywnianie dodatków, zobacz [dodatku aktywacji](https://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f) i [jak: Aktywacja dodatków z różnymi ustawieniami izolacji i zabezpieczeń](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="d9276-144">For information about activating add-ins, see [Add-in Activation](https://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f) and [How to: Activate Add-ins with Different Isolation and Security](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="isolation-levels-and-external-processes"></a><span data-ttu-id="d9276-145">Poziomy izolacji i procesy zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="d9276-145">Isolation Levels and External Processes</span></span>  
 <span data-ttu-id="d9276-146">Model dodatku obsługuje kilka poziomy izolacji między dodatek i jej hostem lub między dodatków. Począwszy od najmniej izolowane, te poziomy są następujące:</span><span class="sxs-lookup"><span data-stu-id="d9276-146">The add-in model supports several levels of isolation between an add-in and its host or between add-ins. Starting from the least isolated, these levels are as follows:</span></span>  
  
-   <span data-ttu-id="d9276-147">Dodatek jest uruchamiany w tej samej domenie aplikacji hosta.</span><span class="sxs-lookup"><span data-stu-id="d9276-147">The add-in runs in the same application domain as the host.</span></span> <span data-ttu-id="d9276-148">Nie jest to zalecane, ponieważ utracisz izolacji i zwalnianie możliwości, które można uzyskać, korzystając z różnych domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d9276-148">This is not recommended because you lose the isolation and unloading capabilities that you get when you use different application domains.</span></span>  
  
-   <span data-ttu-id="d9276-149">Wielu dodatków są ładowane do tej samej domenie aplikacji, która jest inna niż domena aplikacji używana przez hosta.</span><span class="sxs-lookup"><span data-stu-id="d9276-149">Multiple add-ins are loaded into the same application domain that is different from the application domain used by the host.</span></span>  
  
-   <span data-ttu-id="d9276-150">Każdy dodatek jest ładowany wyłącznie do własnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d9276-150">Each add-in is loaded exclusively into its own application domain.</span></span> <span data-ttu-id="d9276-151">Jest to najbardziej typowe poziom izolacji.</span><span class="sxs-lookup"><span data-stu-id="d9276-151">This is the most common level of isolation.</span></span>  
  
-   <span data-ttu-id="d9276-152">Wielu dodatków są ładowane do tej samej domenie aplikacji w procesie zewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="d9276-152">Multiple add-ins are loaded into the same application domain in an external process.</span></span>  
  
-   <span data-ttu-id="d9276-153">Każdy dodatek jest ładowany wyłącznie do własnej domeny aplikacji w procesie zewnętrznym.</span><span class="sxs-lookup"><span data-stu-id="d9276-153">Each add-in is loaded exclusively into its own application domain in an external process.</span></span> <span data-ttu-id="d9276-154">Jest to najbardziej izolowane scenariusz.</span><span class="sxs-lookup"><span data-stu-id="d9276-154">This is the most isolated scenario.</span></span>  
  
 <span data-ttu-id="d9276-155">Aby uzyskać więcej informacji o korzystaniu z zewnętrznego procesów, zobacz [jak: Aktywacja dodatków z różnymi ustawieniami izolacji i zabezpieczeń](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="d9276-155">For more information about using external processes, see [How to: Activate Add-ins with Different Isolation and Security](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="lifetime-management"></a><span data-ttu-id="d9276-156">Zarządzanie okresem istnienia</span><span class="sxs-lookup"><span data-stu-id="d9276-156">Lifetime Management</span></span>  
 <span data-ttu-id="d9276-157">Ponieważ model dodatku obejmuje granic domeny i procesu aplikacji, wyrzucanie elementów bezużytecznych samodzielnie nie jest wystarczające, aby zwolnić i odzyskać obiekty.</span><span class="sxs-lookup"><span data-stu-id="d9276-157">Because the add-in model spans application domain and process boundaries, garbage collection by itself is not sufficient to release and reclaim objects.</span></span> <span data-ttu-id="d9276-158">Model dodatku zapewnia mechanizm zarządzania okresem istnienia, który używa tokenów i zliczanie odwołań i zazwyczaj nie wymaga dodatkowego programowania.</span><span class="sxs-lookup"><span data-stu-id="d9276-158">The add-in model provides a lifetime management mechanism that uses tokens and reference counting, and usually does not require additional programming.</span></span> <span data-ttu-id="d9276-159">Aby uzyskać więcej informacji, zobacz [Zarządzanie okresem istnienia](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="d9276-159">For more information, see [Lifetime Management](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
 [<span data-ttu-id="d9276-160">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="d9276-160">Back to top</span></span>](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a><span data-ttu-id="d9276-161">Dodatki i hostów</span><span class="sxs-lookup"><span data-stu-id="d9276-161">Distinguishing Between Add-ins and Hosts</span></span>  
 <span data-ttu-id="d9276-162">Różnica między dodatek i hosta jest jedynie, że host jest taki, który aktywuje dodatek.</span><span class="sxs-lookup"><span data-stu-id="d9276-162">The difference between an add-in and a host is merely that the host is the one that activates the add-in.</span></span> <span data-ttu-id="d9276-163">Host może być większy z nich, takie jak aplikacja edytora tekstów i jego pisowni; lub host może być mniejszy z nich, takich jak klient wiadomości błyskawicznych, który uwzględnia Windows media player.</span><span class="sxs-lookup"><span data-stu-id="d9276-163">The host can be the larger of the two, such as a word processing application and its spell checkers; or the host can be the smaller of the two, such as an instant messaging client that embeds a media player.</span></span> <span data-ttu-id="d9276-164">Model dodatku obsługuje dodatków w scenariuszach klienta i serwera.</span><span class="sxs-lookup"><span data-stu-id="d9276-164">The add-in model supports add-ins in both client and server scenarios.</span></span> <span data-ttu-id="d9276-165">Przykładami dodatki serwera dodatki, które dostarczają serwerów poczty skanowania antywirusowego, filtry i ochrona.</span><span class="sxs-lookup"><span data-stu-id="d9276-165">Examples of server add-ins include add-ins that provide mail servers with virus scanning, spam filters, and IP protection.</span></span> <span data-ttu-id="d9276-166">Klient dodatku przykładami dodatki odwołania dla edytorów tekstów specjalne funkcje dla programów grafika i gry i antywirusowe dla klientów poczty e-mail lokalnego.</span><span class="sxs-lookup"><span data-stu-id="d9276-166">Client add-in examples include reference add-ins for word processors, specialized features for graphics programs and games, and virus scanning for local email clients.</span></span>  
  
 [<span data-ttu-id="d9276-167">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="d9276-167">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="d9276-168">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="d9276-168">Related Topics</span></span>  
  
|<span data-ttu-id="d9276-169">Tytuł</span><span class="sxs-lookup"><span data-stu-id="d9276-169">Title</span></span>|<span data-ttu-id="d9276-170">Opis</span><span class="sxs-lookup"><span data-stu-id="d9276-170">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d9276-171">Opracowywanie potoku</span><span class="sxs-lookup"><span data-stu-id="d9276-171">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)|<span data-ttu-id="d9276-172">W tym artykule opisano potok komunikacji segmentów aplikacji hosta, aby dodatek.</span><span class="sxs-lookup"><span data-stu-id="d9276-172">Describes the communication pipeline of segments from the host application to the add-in.</span></span> <span data-ttu-id="d9276-173">Przykłady kodu w tematach wskazówki, które opisują jak do budowy potoku oraz jak wdrożyć segmentów potoku w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d9276-173">Provides code examples in walkthrough topics that describe how to construct the pipeline and how to deploy segments to the pipeline in Visual Studio.</span></span>|  
|[<span data-ttu-id="d9276-174">Domeny aplikacji i zestawy</span><span class="sxs-lookup"><span data-stu-id="d9276-174">Application Domains and Assemblies</span></span>](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)|<span data-ttu-id="d9276-175">W tym artykule opisano relację między domenami aplikacji, które umożliwiają wyznaczanie granic izolacji zabezpieczeń, niezawodności i przechowywanie wersji i zestawy.</span><span class="sxs-lookup"><span data-stu-id="d9276-175">Describes the relationship between application domains, which provide an isolation boundary for security, reliability, and versioning, and assemblies.</span></span>|  
  
 [<span data-ttu-id="d9276-176">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="d9276-176">Back to top</span></span>](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a><span data-ttu-id="d9276-177">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d9276-177">Reference</span></span>  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [<span data-ttu-id="d9276-178">Powrót do początku</span><span class="sxs-lookup"><span data-stu-id="d9276-178">Back to top</span></span>](#top)