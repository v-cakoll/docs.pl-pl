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
# <a name="extending-hosting-using-servicehostfactory"></a>Rozszerzanie hostingu za pomocą elementu ServiceHostFactory
Standardowa <xref:System.ServiceModel.ServiceHost> interfejsu API do obsługi usług w Windows Communication Foundation (WCF) jest punktem rozszerzalność w architekturze WCF. Użytkownicy mogą pochodzić własnych klas hosta z <xref:System.ServiceModel.ServiceHost>, zazwyczaj w celu zastąpienia <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> używać <xref:System.ServiceModel.Description.ServiceDescription> do dodawania domyślnych punktów końcowych obowiązkowo lub modyfikowania zachowania, przed otwarciem usługi.  
  
 W środowisku hosta samodzielnego jest konieczne utworzenie niestandardowego <xref:System.ServiceModel.ServiceHost> ponieważ napisać kod, który tworzy wystąpienie hosta, a następnie wywołać <xref:System.ServiceModel.ICommunicationObject.Open> na nim po tworzenia jego instancji. Między te dwa kroki można wykonać, co tylko chcesz. Na przykład można dodać nowego <xref:System.ServiceModel.Description.IServiceBehavior>:  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 To podejście nie jest wielokrotnego użytku. Kod, który obsługuje opis kanonicznej zakodowanej w hoście programu (w tym przypadku funkcji Main()), dzięki czemu jest trudny do ponownego użycia tej logiki w innych kontekstach. Dostępne są także inne sposoby dodawania <xref:System.ServiceModel.Description.IServiceBehavior> nie wymagają kodu imperatywnego. Można uzyskać atrybutu z <xref:System.ServiceModel.ServiceBehaviorAttribute> i umieścić czy dla implementacji usługi typu lub można utworzyć niestandardowe zachowanie można skonfigurować i narzędzia compose dynamicznie przy użyciu konfiguracji.  
  
 Jednak niewielkie zmiany przykładu można również rozwiązać ten problem. Jednym z podejść jest można przenieść kod, który dodaje ServiceBehavior poza `Main()` do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metoda niestandardowe utworów zależnych od <xref:System.ServiceModel.ServiceHost>:  
  
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
  
 Teraz ma hermetyzowany niestandardowej logiki do czystego abstrakcji, który można łatwo ponownie wykorzystać w odniesieniu wielu aplikacji wykonywalnych innego hosta.  
  
 Nie jest natychmiast oczywisty sposób użycia tego niestandardowego <xref:System.ServiceModel.ServiceHost> z wewnątrz usługi Internet Information Services (IIS) lub Windows Process Activation Service (WAS). Tych środowisk różnią się od samodzielnego hostowania środowiska, ponieważ Środowisko hostingu jest utworzenie jednego wystąpienia <xref:System.ServiceModel.ServiceHost> imieniu aplikacji. Usługi IIS i WAS infrastruktury hostingu wiesz nic o niestandardowych <xref:System.ServiceModel.ServiceHost> utworów zależnych.  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory> Zaprojektowano tak, aby rozwiązać ten problem, uzyskiwania dostępu do niestandardowego <xref:System.ServiceModel.ServiceHost> z w ramach usług IIS i WAS. Ponieważ niestandardowego hosta, który jest tworzony na podstawie <xref:System.ServiceModel.ServiceHost> dynamicznie skonfigurowano i potencjalnie różnych typów, środowisko hostingu nigdy nie uruchamia go bezpośrednio. Zamiast tego WCF korzysta ze wzorca fabryki, aby zapewnić warstwę pośredników między środowiskiem hostingu i konkretny typ usługi. O ile nie zostanie stwierdzenie, w przeciwnym razie, używa ona domyślną implementację elementu <xref:System.ServiceModel.Activation.ServiceHostFactory> która zwraca wystąpienie <xref:System.ServiceModel.ServiceHost>. Ale możesz też podać własne fabryka, która zwraca pochodnej hosta, określając nazwę typu CLR fabryki implementacji w @ServiceHost dyrektywy.  
  
 Celem jest, że w przypadkach, podstawowa, implementowanie własnych fabryki powinny być proste wykonywania. Na przykład, w tym miejscu jest niestandardowy <xref:System.ServiceModel.Activation.ServiceHostFactory> zwracającego pochodnej <xref:System.ServiceModel.ServiceHost>:  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 Aby użyć tej fabryce, zamiast domyślną fabrykę, należy podać nazwę typu w @ServiceHost dyrektywy w następujący sposób:  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 Gdy nie ma żadnego limitu Technical Preview, w sposób, co chcesz <xref:System.ServiceModel.ServiceHost> zwracanie z <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, zalecamy pozostawienie swojej implementacji fabryki tak proste, jak to możliwe. Jeśli masz wiele logikę niestandardową, lepiej jest umieścić tej logiki wewnątrz hosta zamiast wewnątrz fabryki, tak aby mogły być wielokrotnego użytku.  
  
 Ma więcej warstw do obsługi interfejsu API, który powinna zostać wymieniona. Ma również WCF <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, z którego <xref:System.ServiceModel.ServiceHost> i <xref:System.ServiceModel.Activation.ServiceHostFactory> odpowiednio pochodnych. Dla bardziej zaawansowanych scenariuszach, gdzie należy zamienić dużej części systemu metadanych przy użyciu własnych dostosowanych operacje tworzenia tych istnieje.
