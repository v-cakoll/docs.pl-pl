---
title: Rozszerzanie hostingu za pomocą elementu ServiceHostFactory
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: e553fe161ffc5b50850d916cf1cef6b38dd5c1a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991318"
---
# <a name="extending-hosting-using-servicehostfactory"></a><span data-ttu-id="f6eba-102">Rozszerzanie hostingu za pomocą elementu ServiceHostFactory</span><span class="sxs-lookup"><span data-stu-id="f6eba-102">Extending Hosting Using ServiceHostFactory</span></span>
<span data-ttu-id="f6eba-103">Standardowa <xref:System.ServiceModel.ServiceHost> interfejsu API do obsługi usług w Windows Communication Foundation (WCF) jest punktem rozszerzalność w architekturze WCF.</span><span class="sxs-lookup"><span data-stu-id="f6eba-103">The standard <xref:System.ServiceModel.ServiceHost> API for hosting services in Windows Communication Foundation (WCF) is an extensibility point in the WCF architecture.</span></span> <span data-ttu-id="f6eba-104">Użytkownicy mogą pochodzić własnych klas hosta z <xref:System.ServiceModel.ServiceHost>, zazwyczaj w celu zastąpienia <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> używać <xref:System.ServiceModel.Description.ServiceDescription> do dodawania domyślnych punktów końcowych obowiązkowo lub modyfikowania zachowania, przed otwarciem usługi.</span><span class="sxs-lookup"><span data-stu-id="f6eba-104">Users can derive their own host classes from <xref:System.ServiceModel.ServiceHost>, usually to override <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> to use <xref:System.ServiceModel.Description.ServiceDescription> to add default endpoints imperatively or modify behaviors, prior to opening the service.</span></span>  
  
 <span data-ttu-id="f6eba-105">W środowisku hosta samodzielnego jest konieczne utworzenie niestandardowego <xref:System.ServiceModel.ServiceHost> ponieważ napisać kod, który tworzy wystąpienie hosta, a następnie wywołać <xref:System.ServiceModel.ICommunicationObject.Open> na nim po tworzenia jego instancji.</span><span class="sxs-lookup"><span data-stu-id="f6eba-105">In the self-host environment, you do not have to create a custom <xref:System.ServiceModel.ServiceHost> because you write the code that instantiates the host and then call <xref:System.ServiceModel.ICommunicationObject.Open> on it after you instantiate it.</span></span> <span data-ttu-id="f6eba-106">Między te dwa kroki można wykonać, co tylko chcesz.</span><span class="sxs-lookup"><span data-stu-id="f6eba-106">Between those two steps you can do whatever you want.</span></span> <span data-ttu-id="f6eba-107">Na przykład można dodać nowego <xref:System.ServiceModel.Description.IServiceBehavior>:</span><span class="sxs-lookup"><span data-stu-id="f6eba-107">You could, for example, add a new <xref:System.ServiceModel.Description.IServiceBehavior>:</span></span>  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="f6eba-108">To podejście nie jest wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="f6eba-108">This approach is not reusable.</span></span> <span data-ttu-id="f6eba-109">Kod, który obsługuje opis kanonicznej zakodowanej w hoście programu (w tym przypadku funkcji Main()), dzięki czemu jest trudny do ponownego użycia tej logiki w innych kontekstach.</span><span class="sxs-lookup"><span data-stu-id="f6eba-109">The code that manipulates the description is coded into the host program (in this case, the Main() function), so it is difficult to reuse that logic in other contexts.</span></span> <span data-ttu-id="f6eba-110">Dostępne są także inne sposoby dodawania <xref:System.ServiceModel.Description.IServiceBehavior> nie wymagają kodu imperatywnego.</span><span class="sxs-lookup"><span data-stu-id="f6eba-110">There are also other ways of adding an <xref:System.ServiceModel.Description.IServiceBehavior> that do not require imperative code.</span></span> <span data-ttu-id="f6eba-111">Można uzyskać atrybutu z <xref:System.ServiceModel.ServiceBehaviorAttribute> i umieścić czy dla implementacji usługi typu lub można utworzyć niestandardowe zachowanie można skonfigurować i narzędzia compose dynamicznie przy użyciu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f6eba-111">You can derive an attribute from <xref:System.ServiceModel.ServiceBehaviorAttribute> and put that on your service implementation type or you can make a custom behavior configurable and compose it dynamically using configuration.</span></span>  
  
 <span data-ttu-id="f6eba-112">Jednak niewielkie zmiany przykładu można również rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="f6eba-112">However, a slight variation of the example can also be used to solve this problem.</span></span> <span data-ttu-id="f6eba-113">Jednym z podejść jest można przenieść kod, który dodaje ServiceBehavior poza `Main()` do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metoda niestandardowe utworów zależnych od <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="f6eba-113">One approach is to move the code that adds the ServiceBehavior out of `Main()` and into the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method of a custom derivative of <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
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
  
 <span data-ttu-id="f6eba-114">Następnie wewnątrz elementu `Main()` można użyć:</span><span class="sxs-lookup"><span data-stu-id="f6eba-114">Then, inside of `Main()` you can use:</span></span>  
  
```  
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="f6eba-115">Teraz ma hermetyzowany niestandardowej logiki do czystego abstrakcji, który można łatwo ponownie wykorzystać w odniesieniu wielu aplikacji wykonywalnych innego hosta.</span><span class="sxs-lookup"><span data-stu-id="f6eba-115">Now you have encapsulated the custom logic into a clean abstraction that can be easily reused across many different host executables.</span></span>  
  
 <span data-ttu-id="f6eba-116">Nie jest natychmiast oczywisty sposób użycia tego niestandardowego <xref:System.ServiceModel.ServiceHost> z wewnątrz usługi Internet Information Services (IIS) lub Windows Process Activation Service (WAS).</span><span class="sxs-lookup"><span data-stu-id="f6eba-116">It is not immediately obvious how to use this custom <xref:System.ServiceModel.ServiceHost> from inside of Internet Information Services (IIS) or Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="f6eba-117">Tych środowisk różnią się od samodzielnego hostowania środowiska, ponieważ Środowisko hostingu jest utworzenie jednego wystąpienia <xref:System.ServiceModel.ServiceHost> imieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f6eba-117">Those environments are different than the self-host environment, because the hosting environment is the one instantiating the <xref:System.ServiceModel.ServiceHost> on behalf of the application.</span></span> <span data-ttu-id="f6eba-118">Usługi IIS i WAS infrastruktury hostingu wiesz nic o niestandardowych <xref:System.ServiceModel.ServiceHost> utworów zależnych.</span><span class="sxs-lookup"><span data-stu-id="f6eba-118">The IIS and WAS hosting infrastructure does not know anything about your custom <xref:System.ServiceModel.ServiceHost> derivative.</span></span>  
  
 <span data-ttu-id="f6eba-119"><xref:System.ServiceModel.Activation.ServiceHostFactory> Zaprojektowano tak, aby rozwiązać ten problem, uzyskiwania dostępu do niestandardowego <xref:System.ServiceModel.ServiceHost> z w ramach usług IIS i WAS.</span><span class="sxs-lookup"><span data-stu-id="f6eba-119">The <xref:System.ServiceModel.Activation.ServiceHostFactory> was designed to solve this problem of accessing your custom <xref:System.ServiceModel.ServiceHost> from within IIS or WAS.</span></span> <span data-ttu-id="f6eba-120">Ponieważ niestandardowego hosta, który jest tworzony na podstawie <xref:System.ServiceModel.ServiceHost> dynamicznie skonfigurowano i potencjalnie różnych typów, środowisko hostingu nigdy nie uruchamia go bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="f6eba-120">Because a custom host that is derived from <xref:System.ServiceModel.ServiceHost> is dynamically configured and potentially of various types, the hosting environment never instantiates it directly.</span></span> <span data-ttu-id="f6eba-121">Zamiast tego WCF korzysta ze wzorca fabryki, aby zapewnić warstwę pośredników między środowiskiem hostingu i konkretny typ usługi.</span><span class="sxs-lookup"><span data-stu-id="f6eba-121">Instead, WCF uses a factory pattern to provide a layer of indirection between the hosting environment and the concrete type of the service.</span></span> <span data-ttu-id="f6eba-122">O ile nie zostanie stwierdzenie, w przeciwnym razie, używa ona domyślną implementację elementu <xref:System.ServiceModel.Activation.ServiceHostFactory> która zwraca wystąpienie <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="f6eba-122">Unless you tell it otherwise, it uses a default implementation of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="f6eba-123">Ale możesz też podać własne fabryka, która zwraca pochodnej hosta, określając nazwę typu CLR fabryki implementacji w @ServiceHost dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="f6eba-123">But you can also provide your own factory that returns your derived host by specifying the CLR type name of your factory implementation in the @ServiceHost directive.</span></span>  
  
 <span data-ttu-id="f6eba-124">Celem jest, że w przypadkach, podstawowa, implementowanie własnych fabryki powinny być proste wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f6eba-124">The intent is that for basic cases, implementing your own factory should be a straight forward exercise.</span></span> <span data-ttu-id="f6eba-125">Na przykład, w tym miejscu jest niestandardowy <xref:System.ServiceModel.Activation.ServiceHostFactory> zwracającego pochodnej <xref:System.ServiceModel.ServiceHost>:</span><span class="sxs-lookup"><span data-stu-id="f6eba-125">For example, here is a custom <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns a derived <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 <span data-ttu-id="f6eba-126">Aby użyć tej fabryce, zamiast domyślną fabrykę, należy podać nazwę typu w @ServiceHost dyrektywy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f6eba-126">To use this factory instead of the default factory, provide the type name in the @ServiceHost directive as follows:</span></span>  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="f6eba-127">Gdy nie ma żadnego limitu Technical Preview, w sposób, co chcesz <xref:System.ServiceModel.ServiceHost> zwracanie z <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, zalecamy pozostawienie swojej implementacji fabryki tak proste, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="f6eba-127">While there is no technical limit on doing what you want to the <xref:System.ServiceModel.ServiceHost> you return from <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, we suggest that you keep your factory implementations as simple as possible.</span></span> <span data-ttu-id="f6eba-128">Jeśli masz wiele logikę niestandardową, lepiej jest umieścić tej logiki wewnątrz hosta zamiast wewnątrz fabryki, tak aby mogły być wielokrotnego użytku.</span><span class="sxs-lookup"><span data-stu-id="f6eba-128">If you have lots of custom logic, it is better to put that logic inside of you host instead of inside the factory so that it can be reusable.</span></span>  
  
 <span data-ttu-id="f6eba-129">Ma więcej warstw do obsługi interfejsu API, który powinna zostać wymieniona.</span><span class="sxs-lookup"><span data-stu-id="f6eba-129">There is one more layer to the hosting API that should be mentioned here.</span></span> <span data-ttu-id="f6eba-130">Ma również WCF <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, z którego <xref:System.ServiceModel.ServiceHost> i <xref:System.ServiceModel.Activation.ServiceHostFactory> odpowiednio pochodnych.</span><span class="sxs-lookup"><span data-stu-id="f6eba-130">WCF also has <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, from which <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.Activation.ServiceHostFactory> respectively derive.</span></span> <span data-ttu-id="f6eba-131">Dla bardziej zaawansowanych scenariuszach, gdzie należy zamienić dużej części systemu metadanych przy użyciu własnych dostosowanych operacje tworzenia tych istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6eba-131">Those exist for more advanced scenarios where you must swap out large parts of the metadata system with your own customized creations.</span></span>
