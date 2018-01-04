---
title: "Rozszerzanie hostingu za pomocą elementu ServiceHostFactory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4a7bcd2e0ba68499cad63ec47918fd2bd6bd80d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="extending-hosting-using-servicehostfactory"></a><span data-ttu-id="0d85e-102">Rozszerzanie hostingu za pomocą elementu ServiceHostFactory</span><span class="sxs-lookup"><span data-stu-id="0d85e-102">Extending Hosting Using ServiceHostFactory</span></span>
<span data-ttu-id="0d85e-103">Standardowe <xref:System.ServiceModel.ServiceHost> interfejsu API do obsługi usług w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] punkt rozszerzalności w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] architektury.</span><span class="sxs-lookup"><span data-stu-id="0d85e-103">The standard <xref:System.ServiceModel.ServiceHost> API for hosting services in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is an extensibility point in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] architecture.</span></span> <span data-ttu-id="0d85e-104">Użytkownicy mogą pochodzić własnych klas hosta z <xref:System.ServiceModel.ServiceHost>, zazwyczaj w celu zastąpienia <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> do używania <xref:System.ServiceModel.Description.ServiceDescription> do dodawania domyślnych punktów końcowych imperatively lub modyfikowania zachowania, przed otwarciem usługi.</span><span class="sxs-lookup"><span data-stu-id="0d85e-104">Users can derive their own host classes from <xref:System.ServiceModel.ServiceHost>, usually to override <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> to use <xref:System.ServiceModel.Description.ServiceDescription> to add default endpoints imperatively or modify behaviors, prior to opening the service.</span></span>  
  
 <span data-ttu-id="0d85e-105">W środowisku hosta samodzielnego jest konieczne utworzenie niestandardowego <xref:System.ServiceModel.ServiceHost> ponieważ pisania kodu, który tworzy wystąpienie hosta, a następnie wywołać <xref:System.ServiceModel.ICommunicationObject.Open> na nim po jego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0d85e-105">In the self-host environment, you do not have to create a custom <xref:System.ServiceModel.ServiceHost> because you write the code that instantiates the host and then call <xref:System.ServiceModel.ICommunicationObject.Open> on it after you instantiate it.</span></span> <span data-ttu-id="0d85e-106">Między tymi dwa kroki można wykonać dowolne.</span><span class="sxs-lookup"><span data-stu-id="0d85e-106">Between those two steps you can do whatever you want.</span></span> <span data-ttu-id="0d85e-107">Można na przykład dodać nowy <xref:System.ServiceModel.Description.IServiceBehavior>:</span><span class="sxs-lookup"><span data-stu-id="0d85e-107">You could, for example, add a new <xref:System.ServiceModel.Description.IServiceBehavior>:</span></span>  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="0d85e-108">Ta metoda nie jest wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="0d85e-108">This approach is not reusable.</span></span> <span data-ttu-id="0d85e-109">Kod, który manipuluje opis zakodowanej w hoście programu (w tym przypadku funkcja Main()), dlatego jest trudne do ponownego użycia tej logiki w innych kontekstach.</span><span class="sxs-lookup"><span data-stu-id="0d85e-109">The code that manipulates the description is coded into the host program (in this case, the Main() function), so it is difficult to reuse that logic in other contexts.</span></span> <span data-ttu-id="0d85e-110">Istnieją także inne sposoby dodawania <xref:System.ServiceModel.Description.IServiceBehavior> nie wymagają kodu nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="0d85e-110">There are also other ways of adding an <xref:System.ServiceModel.Description.IServiceBehavior> that do not require imperative code.</span></span> <span data-ttu-id="0d85e-111">Może pochodzić z atrybutu <xref:System.ServiceModel.ServiceBehaviorAttribute> i umieszcza w implementacji usługi typ lub użytkownik może wprowadzić można skonfigurować niestandardowe zachowanie i tworzą dynamicznie za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0d85e-111">You can derive an attribute from <xref:System.ServiceModel.ServiceBehaviorAttribute> and put that on your service implementation type or you can make a custom behavior configurable and compose it dynamically using configuration.</span></span>  
  
 <span data-ttu-id="0d85e-112">Jednak niewielkie zmiany przykładu można również aby rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="0d85e-112">However, a slight variation of the example can also be used to solve this problem.</span></span> <span data-ttu-id="0d85e-113">Jednym z podejść jest przeniesienie kod, który dodaje ServiceBehavior poza `Main()` i do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metody niestandardowe pochodną <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="0d85e-113">One approach is to move the code that adds the ServiceBehavior out of `Main()` and into the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method of a custom derivative of <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```  
public class DerivedHost : ServiceHost  
{  
   public DerivedHost( Type t, params Uri baseAddresses ) :  
      base( t, baseAddresses ) {}  
  
   public override void OnOpening()  
   {  
  this.Description.Add( new MyServiceBehavior() );  
   }  
}  
```  
  
 <span data-ttu-id="0d85e-114">Następnie wewnątrz elementu `Main()` można użyć:</span><span class="sxs-lookup"><span data-stu-id="0d85e-114">Then, inside of `Main()` you can use:</span></span>  
  
```  
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="0d85e-115">Teraz ma hermetyzowany niestandardowej logiki do czystej abstrakcji, które mogą być łatwo ponownie używane przez wiele plików wykonywalnych innego hosta.</span><span class="sxs-lookup"><span data-stu-id="0d85e-115">Now you have encapsulated the custom logic into a clean abstraction that can be easily reused across many different host executables.</span></span>  
  
 <span data-ttu-id="0d85e-116">Nie jest od razu widoczne sposobu korzystania z tej niestandardowej <xref:System.ServiceModel.ServiceHost> z wewnątrz usługi Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="0d85e-116">It is not immediately obvious how to use this custom <xref:System.ServiceModel.ServiceHost> from inside of Internet Information Services (IIS) or Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="0d85e-117">Tych środowisk są inne niż środowiska hosta samodzielnego, ponieważ środowisko macierzyste jest utworzenie jednego wystąpienia <xref:System.ServiceModel.ServiceHost> w imieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0d85e-117">Those environments are different than the self-host environment, because the hosting environment is the one instantiating the <xref:System.ServiceModel.ServiceHost> on behalf of the application.</span></span> <span data-ttu-id="0d85e-118">Infrastruktura obsługi usług IIS i WAS nie może określić dowolne niestandardowe <xref:System.ServiceModel.ServiceHost> zależnych.</span><span class="sxs-lookup"><span data-stu-id="0d85e-118">The IIS and WAS hosting infrastructure does not know anything about your custom <xref:System.ServiceModel.ServiceHost> derivative.</span></span>  
  
 <span data-ttu-id="0d85e-119"><xref:System.ServiceModel.Activation.ServiceHostFactory> Zaprojektowano tak, aby rozwiązać ten problem, uzyskiwania dostępu do niestandardowe <xref:System.ServiceModel.ServiceHost> od w usługach IIS lub WAS.</span><span class="sxs-lookup"><span data-stu-id="0d85e-119">The <xref:System.ServiceModel.Activation.ServiceHostFactory> was designed to solve this problem of accessing your custom <xref:System.ServiceModel.ServiceHost> from within IIS or WAS.</span></span> <span data-ttu-id="0d85e-120">Ponieważ niestandardowego hostów, która jest pochodną <xref:System.ServiceModel.ServiceHost> dynamicznie skonfigurowano i potencjalnie różnych typów środowisko macierzyste nigdy nie uruchamia go bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="0d85e-120">Because a custom host that is derived from <xref:System.ServiceModel.ServiceHost> is dynamically configured and potentially of various types, the hosting environment never instantiates it directly.</span></span> <span data-ttu-id="0d85e-121">Zamiast tego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] korzysta ze wzorca fabryki, aby zapewnić warstwę pośredników między środowisko macierzyste i konkretnego typu usługi.</span><span class="sxs-lookup"><span data-stu-id="0d85e-121">Instead, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses a factory pattern to provide a layer of indirection between the hosting environment and the concrete type of the service.</span></span> <span data-ttu-id="0d85e-122">Jeśli nie wiadomo, ją inaczej, używa domyślną implementację <xref:System.ServiceModel.Activation.ServiceHostFactory> która zwraca wystąpienie klasy <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="0d85e-122">Unless you tell it otherwise, it uses a default implementation of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="0d85e-123">Ale można też podać własne fabryka, która zwraca pochodnej hosta, określając nazwę typu CLR fabryki implementacji w @ServiceHost dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="0d85e-123">But you can also provide your own factory that returns your derived host by specifying the CLR type name of your factory implementation in the @ServiceHost directive.</span></span>  
  
 <span data-ttu-id="0d85e-124">Celem jest, że w przypadku podstawowych wdrażanie własnych fabryki powinny być bezpośrednio do przodu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0d85e-124">The intent is that for basic cases, implementing your own factory should be a straight forward exercise.</span></span> <span data-ttu-id="0d85e-125">Na przykład, w tym miejscu jest niestandardowy <xref:System.ServiceModel.Activation.ServiceHostFactory> zwracającą pochodnego <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="0d85e-125">For example, here is a custom <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns a derived <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 <span data-ttu-id="0d85e-126">Aby korzystać z tej fabryki zamiast domyślną fabrykę, podaj nazwę typu w @ServiceHost dyrektywy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0d85e-126">To use this factory instead of the default factory, provide the type name in the @ServiceHost directive as follows:</span></span>  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="0d85e-127">Gdy nie ma żadnego limitu technicznych na ten ma być <xref:System.ServiceModel.ServiceHost> zwróconych z <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, zalecamy pozostawienie implementacjach fabryki użytkownika, wystarczy.</span><span class="sxs-lookup"><span data-stu-id="0d85e-127">While there is no technical limit on doing what you want to the <xref:System.ServiceModel.ServiceHost> you return from <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, we suggest that you keep your factory implementations as simple as possible.</span></span> <span data-ttu-id="0d85e-128">Jeśli masz wiele logiki niestandardowej, lepiej jest umieszczenie tej logiki w ramach hosta zamiast wewnątrz fabryka, aby można go do ponownego użycia.</span><span class="sxs-lookup"><span data-stu-id="0d85e-128">If you have lots of custom logic, it is better to put that logic inside of you host instead of inside the factory so that it can be reusable.</span></span>  
  
 <span data-ttu-id="0d85e-129">Istnieje więcej warstw do obsługi interfejsu API, który powinien być powieść.</span><span class="sxs-lookup"><span data-stu-id="0d85e-129">There is one more layer to the hosting API that should be mentioned here.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="0d85e-130">ma również <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, z którego <xref:System.ServiceModel.ServiceHost> i <xref:System.ServiceModel.Activation.ServiceHostFactory> odpowiednio pochodzi.</span><span class="sxs-lookup"><span data-stu-id="0d85e-130"> also has <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, from which <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.Activation.ServiceHostFactory> respectively derive.</span></span> <span data-ttu-id="0d85e-131">Te istnieje dla bardziej zaawansowanych scenariuszy, w którym musi zamiana dużej części system metadanych z własnych dostosowanych tworzenie.</span><span class="sxs-lookup"><span data-stu-id="0d85e-131">Those exist for more advanced scenarios where you must swap out large parts of the metadata system with your own customized creations.</span></span>
