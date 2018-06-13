---
title: Rozszerzanie hostingu za pomocą elementu ServiceHostFactory
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: e553fe161ffc5b50850d916cf1cef6b38dd5c1a9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806211"
---
# <a name="extending-hosting-using-servicehostfactory"></a>Rozszerzanie hostingu za pomocą elementu ServiceHostFactory
Standardowe <xref:System.ServiceModel.ServiceHost> interfejsu API do obsługi usług w systemie Windows Communication Foundation (WCF) jest punktem rozszerzalność architektury WCF. Użytkownicy mogą pochodzić własnych klas hosta z <xref:System.ServiceModel.ServiceHost>, zazwyczaj w celu zastąpienia <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> do używania <xref:System.ServiceModel.Description.ServiceDescription> do dodawania domyślnych punktów końcowych imperatively lub modyfikowania zachowania, przed otwarciem usługi.  
  
 W środowisku hosta samodzielnego jest konieczne utworzenie niestandardowego <xref:System.ServiceModel.ServiceHost> ponieważ pisania kodu, który tworzy wystąpienie hosta, a następnie wywołać <xref:System.ServiceModel.ICommunicationObject.Open> na nim po jego wystąpienia. Między tymi dwa kroki można wykonać dowolne. Można na przykład dodać nowy <xref:System.ServiceModel.Description.IServiceBehavior>:  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 Ta metoda nie jest wielokrotnego użytku. Kod, który manipuluje opis zakodowanej w hoście programu (w tym przypadku funkcja Main()), dlatego jest trudne do ponownego użycia tej logiki w innych kontekstach. Istnieją także inne sposoby dodawania <xref:System.ServiceModel.Description.IServiceBehavior> nie wymagają kodu nadrzędnych. Może pochodzić z atrybutu <xref:System.ServiceModel.ServiceBehaviorAttribute> i umieszcza w implementacji usługi typ lub użytkownik może wprowadzić można skonfigurować niestandardowe zachowanie i tworzą dynamicznie za pomocą konfiguracji.  
  
 Jednak niewielkie zmiany przykładu można również aby rozwiązać ten problem. Jednym z podejść jest przeniesienie kod, który dodaje ServiceBehavior poza `Main()` i do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metody niestandardowe pochodną <xref:System.ServiceModel.ServiceHost>:  
  
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
  
 Następnie wewnątrz elementu `Main()` można użyć:  
  
```  
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 Teraz ma hermetyzowany niestandardowej logiki do czystej abstrakcji, które mogą być łatwo ponownie używane przez wiele plików wykonywalnych innego hosta.  
  
 Nie jest od razu widoczne sposobu korzystania z tej niestandardowej <xref:System.ServiceModel.ServiceHost> z wewnątrz usługi Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS). Tych środowisk są inne niż środowiska hosta samodzielnego, ponieważ środowisko macierzyste jest utworzenie jednego wystąpienia <xref:System.ServiceModel.ServiceHost> w imieniu aplikacji. Infrastruktura obsługi usług IIS i WAS nie może określić dowolne niestandardowe <xref:System.ServiceModel.ServiceHost> zależnych.  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory> Zaprojektowano tak, aby rozwiązać ten problem, uzyskiwania dostępu do niestandardowe <xref:System.ServiceModel.ServiceHost> od w usługach IIS lub WAS. Ponieważ niestandardowego hostów, która jest pochodną <xref:System.ServiceModel.ServiceHost> dynamicznie skonfigurowano i potencjalnie różnych typów środowisko macierzyste nigdy nie uruchamia go bezpośrednio. Zamiast tego WCF korzysta ze wzorca fabryki na udostępnienie warstwy pośredni między środowisko macierzyste i konkretnego typu usługi. Jeśli nie wiadomo, ją inaczej, używa domyślną implementację <xref:System.ServiceModel.Activation.ServiceHostFactory> która zwraca wystąpienie klasy <xref:System.ServiceModel.ServiceHost>. Ale można też podać własne fabryka, która zwraca pochodnej hosta, określając nazwę typu CLR fabryki implementacji w @ServiceHost dyrektywy.  
  
 Celem jest, że w przypadku podstawowych wdrażanie własnych fabryki powinny być bezpośrednio do przodu wykonywania. Na przykład, w tym miejscu jest niestandardowy <xref:System.ServiceModel.Activation.ServiceHostFactory> zwracającą pochodnego <xref:System.ServiceModel.ServiceHost>:  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 Aby korzystać z tej fabryki zamiast domyślną fabrykę, podaj nazwę typu w @ServiceHost dyrektywy w następujący sposób:  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Gdy nie ma żadnego limitu technicznych na ten ma być <xref:System.ServiceModel.ServiceHost> zwróconych z <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, zalecamy pozostawienie implementacjach fabryki użytkownika, wystarczy. Jeśli masz wiele logiki niestandardowej, lepiej jest umieszczenie tej logiki w ramach hosta zamiast wewnątrz fabryka, aby można go do ponownego użycia.  
  
 Istnieje więcej warstw do obsługi interfejsu API, który powinien być powieść. Ma również WCF <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, z którego <xref:System.ServiceModel.ServiceHost> i <xref:System.ServiceModel.Activation.ServiceHostFactory> odpowiednio pochodzi. Te istnieje dla bardziej zaawansowanych scenariuszy, w którym musi zamiana dużej części system metadanych z własnych dostosowanych tworzenie.
