---
title: "Przegląd tworzenia punktów końcowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa20edd8fa43fb1e6a28f7b1ec18f83fedd96bca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="endpoint-creation-overview"></a>Przegląd tworzenia punktów końcowych
Cała komunikacja z [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usługi odbywa się przez *punkty końcowe* usługi. Punkty końcowe zapewnić klientom dostęp do funkcji [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] oferty usługi. W tej sekcji opisano strukturę punktu końcowego i opisano sposób definiowania punkt końcowy w konfiguracji i w kodzie.  
  
## <a name="the-structure-of-an-endpoint"></a>Struktura punktu końcowego  
 Każdy punkt końcowy zawiera adres, który wskazuje, gdzie można znaleźć punktu końcowego, powiązanie, które określa, jak klient może komunikować się z punktem końcowym i kontraktu, który identyfikuje dostępne metody.  
  
-   **Adres**. Adres unikatowo identyfikuje punkt końcowy i informuje potencjalnych klientów, w którym znajduje się usługa. Jest reprezentowana w [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] model obiektów przez <xref:System.ServiceModel.EndpointAddress> adresu, który zawiera jednolity identyfikator zasobów (URI) i właściwości adresów, które obejmują tożsamości, niektóre elementy sieci Web Services Description Language (WSDL) i kolekcję opcjonalne nagłówki. Opcjonalne nagłówki zawierają dodatkowe szczegółowe informacje adresowania do identyfikacji użytkownika lub interakcji z punktem końcowym. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Określanie adresu punktu końcowego](../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   **Powiązanie**. Powiązanie określa sposób komunikowania się z punktem końcowym. Określa powiązanie, jak punkt końcowy komunikuje się innym osobom, które protokół transportu do użycia w tym (np. TCP lub HTTP), które kodowanie do użycia dla wiadomości (na przykład tekst lub binarny) i wymagania zabezpieczeń, które są niezbędne (dla przykład protokołu Secure Sockets Layer [SSL] lub zabezpieczenia komunikatów SOAP). [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Konfigurowanie usług i klientów za pomocą powiązania](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
-   **Kontrakt usługi**. Kontrakt usługi przedstawiono funkcje punktu końcowego udostępnia do klienta. Kontrakt określa operacje, które klient może wywoływać, formularz wiadomości i typ parametrów wejściowych lub danych wymaganych do wywołania operacji i rodzaj przetwarzania lub komunikat odpowiedzi, który klient może spodziewać się. Trzy podstawowe typy kontraktów odpowiadają wzorce wymiany wiadomości podstawowe (MEPs): (jednokierunkowe), protokół datagram żądań i odpowiedzi oraz dupleks (dwukierunkowe). Kontrakt usługi można również użyć kontraktów danych i wiadomości wymaga konkretnych typów danych i formaty wiadomości, gdy uzyskiwany. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Definiowanie kontraktu usługi, zobacz [projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md). Należy pamiętać, że klient może również konieczne przeprowadzenie Implementowanie kontraktu usługa zdefiniowana, o nazwie kontrakt wywołania zwrotnego do odbierania wiadomości z usługi w MEP dupleksowych. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 Imperatively przy użyciu kodu lub deklaratywnie przy użyciu konfiguracji można określić punktu końcowego usługi. Jeśli nie określono żadnych punktów końcowych następnie środowiska uruchomieniowego zawiera domyślne punkty końcowe, dodając jeden domyślny punkt końcowy dla każdego adresu podstawowego dla każdej umowy serwisowej zaimplementowanych przez usługę. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie opracowywane. Ogólnie rzecz biorąc lepiej jest punkty końcowe usługi przy użyciu konfiguracji zamiast kodu. Utrzymywanie powiązania i adresowanie poza kod pozwala na zmianę bez konieczności ponowne skompilowanie i wdrożenie aplikacji.  
  
> [!NOTE]
>  Podczas dodawania punktu końcowego usługi, który przeprowadza personifikacji, należy użyć jednej z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody lub <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> metody poprawnie załadować umowy do nowej <xref:System.ServiceModel.Description.ServiceDescription> obiektu.  
  
## <a name="defining-endpoints-in-code"></a>Definiowanie punktów końcowych w kodzie  
 Poniższy przykład przedstawia sposób określania punktu końcowego w kodzie z następujących czynności:  
  
-   Definiowanie kontraktu dla `IEcho` typu usługi, która przyjmuje nazwę i echo z odpowiedzią innego użytkownika "Hello \<name >!".  
  
-   Implementowanie `Echo` usługi określone przez `IEcho` kontraktu.  
  
-   Podaj adres punktu końcowego http://localhost: 8000/Echo dla usługi.  
  
-   Skonfiguruj `Echo` usługi przy użyciu <xref:System.ServiceModel.WSHttpBinding> powiązania.  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   public interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   class Echo : IEcho  
   {  
      public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      public static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Use a predefined WSHttpBinding to configure the service.  
          WSHttpBinding binding = new WSHttpBinding();  
  
          // Add the endpoint for this service to the service host.  
          serviceHost.AddServiceEndpoint(  
             typeof(IEcho),   
             binding,   
             echoUri  
           );  
  
          // Open the service host to run it.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Create a ServiceHost for the Echo service.  
Dim svcHost As ServiceHost = New ServiceHost(GetType(HelloWorld), echoUri)  
  
' Use a predefined WSHttpBinding to configure the service.  
Dim binding As New WSHttpBinding()  
  
' Add the endpoint for this service to the service host.  
serviceHost.AddServiceEndpoint(GetType(IEcho), binding, echoUri)  
  
' Open the service host to run it.  
serviceHost.Open()  
```  
  
> [!NOTE]
>  Host usługi jest tworzony przy użyciu podstawowego adresu, a następnie pozostałą część adresu, określany względem adresu podstawowego jest określony jako część punktu końcowego. Ta partycjonowania adres umożliwia wiele punktów końcowych do zdefiniowania ułatwia dla usług na hoście.  
  
> [!NOTE]
>  Właściwości <xref:System.ServiceModel.Description.ServiceDescription> w usłudze aplikacji nie można modyfikować subsequent do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metoda <xref:System.ServiceModel.ServiceHostBase>. Niektóre elementy, takie jak <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości i `AddServiceEndpoint` metod <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.ServiceHost>, Zgłoś wyjątek, jeśli zmodyfikowane poza tym punktem. Inne pozwala na ich modyfikacji, ale wynik jest niezdefiniowany.  
>   
>  Podobnie, na kliencie <xref:System.ServiceModel.Description.ServiceEndpoint> nie można modyfikować wartości po wywołaniu <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Właściwość zgłasza wyjątek, jeśli zmodyfikowane poza tego punktu. Inne wartości klienta opis można zmodyfikować bez błędów, ale wynik jest niezdefiniowany.  
>   
>  Czy dla usługi lub klienta, zalecane jest zmodyfikowanie opis przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="defining-endpoints-in-configuration"></a>Definiowanie punktów końcowych w konfiguracji  
 Podczas tworzenia aplikacji, ma często mają być odroczone decyzje administratorowi, który jest wdrożenie aplikacji. Na przykład jest często będą żaden sposób uzyskać z wyprzedzeniem jakie usługi adresów (URI). Zamiast kodować adres, zaleca się pozwalają administratorowi zrobić po utworzeniu usługi. Tego rodzaju elastyczności odbywa się za pośrednictwem konfiguracji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).  
  
> [!NOTE]
>  Użyj [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z `/config:` *filename*`[,`*filename* `]` przełączyć się do Szybkie tworzenie plików konfiguracyjnych.  
  
## <a name="using-default-endpoints"></a>Przy użyciu domyślnych punktów końcowych  
 Jeśli nie określono żadnych punktów końcowych w kodzie, lub w konfiguracji następnie środowiska uruchomieniowego zawiera domyślne punkty końcowe, dodając jeden domyślny punkt końcowy dla każdego adresu podstawowego dla każdej umowy serwisowej zaimplementowanych przez usługę. Adres podstawowy można określić w kodzie, lub w konfiguracji i domyślne punkty końcowe są dodawane, gdy <xref:System.ServiceModel.ICommunicationObject.Open> jest wywoływana na <xref:System.ServiceModel.ServiceHost>. W tym przykładzie jest tym samym przykładzie z poprzedniej sekcji, ale ponieważ nie określono żadnych punktów końcowych, domyślne punkty końcowe są dodawane.  
  
```csharp  
Namespace Echo  
{  
   // Define the contract for the IEcho service   
   [ServiceContract]  
   Interface IEcho  
   {  
       [OperationContract]  
       String Hello(string name)  
   }  
  
   // Create an Echo service that implements IEcho contract  
   Class Echo : IEcho  
   {  
      Public string Hello(string name)  
      {  
         return "Hello" + name + "!";  
      }  
      static void Main ()  
      {  
          //Specify the base address for Echo service.  
          Uri echoUri = new Uri("http://localhost:8000/");  
  
          //Create a ServiceHost for the Echo service.  
          ServiceHost serviceHost = new ServiceHost(typeof(Echo),echoUri);  
  
          // Open the service host to run it. Default endpoints  
          // are added when the service is opened.  
          serviceHost.Open();  
     }  
  }  
}  
```  
  
```vb  
' Define the contract for the IEcho service  
    <ServiceContract()> _  
    Public Interface IEcho  
        <OperationContract()> _  
        Function Hello(ByVal name As String) As String  
    End Interface  
  
' Create an Echo service that implements IEcho contract  
    Public Class Echo   
        Implements IEcho  
        Public Function Hello(ByVal name As String) As String _  
 Implements ICalculator.Hello  
            Dim result As String = "Hello" + name + "!"  
            Return result  
        End Function  
  
' Specify the base address for Echo service.  
Dim echoUri As Uri = New Uri("http://localhost:8000/")  
  
' Open the service host to run it. Default endpoints  
' are added when the service is opened.  
serviceHost.Open()  
```  
  
 W przypadku punktów końcowych są jawnie, nadal można dodać domyślne punkty końcowe przez wywołanie metody <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. [!INCLUDE[crabout](../../../includes/crabout-md.md)]domyślne punkty końcowe, zobacz [uproszczony konfiguracji](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md)
