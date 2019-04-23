---
title: Przegląd tworzenia punktów końcowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: 6aecad3719fff98a2e834cff6eee9cfe39a699aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106538"
---
# <a name="endpoint-creation-overview"></a>Przegląd tworzenia punktów końcowych
Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się przez *punktów końcowych* usługi. Punkty końcowe zapewniają klientom dostęp do funkcji, która oferuje usługi WCF. W tej sekcji opisuje strukturę punktu końcowego i opisano sposób definiowania punktu końcowego w konfiguracji i w kodzie.  
  
## <a name="the-structure-of-an-endpoint"></a>Struktura punktu końcowego  
 Każdy punkt końcowy zawiera adres który wskazuje, gdzie można znaleźć punktu końcowego, powiązanie, które określa, jak klient może komunikować się z punktem końcowym i kontraktu, który identyfikuje dostępne metody.  
  
-   **Adres**. Adres jednoznacznie identyfikuje punkt końcowy i informuje o potencjalnych klientów, w którym znajduje się usługa. Jest reprezentowana w modelu obiektu programu WCF za <xref:System.ServiceModel.EndpointAddress> adresu, który zawiera jednolity identyfikator zasobów (URI) i właściwości adresu, które obejmują tożsamość, niektóre elementy sieci Web Services Description Language (WSDL) oraz zbiór opcjonalne nagłówki. Opcjonalne nagłówki zawierają dodatkowe szczegółowe informacje adresowania, aby zidentyfikować lub nawiązać kontakt z punktem końcowym. Aby uzyskać więcej informacji, zobacz [Określanie adresu punktu końcowego](../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   **Powiązanie**. Powiązanie Określa, jak komunikować się z punktem końcowym. Powiązanie Określa, jak punkt końcowy komunikuje się z świat, w tym protokół transportu (na przykład, TCP lub HTTP), które kodowanie do użycia dla wiadomości (na przykład tekst lub dane binarne), a wymagania zabezpieczeń, które są niezbędne (dla przykład Secure Sockets Layer [SSL] lub zabezpieczeń wiadomości protokołu SOAP). Aby uzyskać więcej informacji, zobacz [przy użyciu powiązania do konfigurowania usług i klientów](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).  
  
-   **Kontrakt usługi**. Kontrakt usługi opisano, jakie funkcje uwidacznia punkt końcowy, do klienta. Kontrakt określa operacje, które klient może wywołać, formularz wiadomości i typ parametrów wejściowych lub dane wymagane do wywołania operacji i rodzaju przetwarzania lub komunikat odpowiedzi, których można oczekiwać, że klient. Podstawowe wiadomości programu exchange wzorców (MEPs) odpowiadają trzy podstawowe typy kontraktów: datagramów (jednokierunkowe), żądanie/nietypizowana odpowiedź i dupleks (dwukierunkowe). Kontrakt usługi można również używać kontraktów danych i komunikatów wymaga konkretnych typów danych i formaty wiadomości, podczas którego uzyskiwany jest dostęp. Aby uzyskać więcej informacji na temat Definiowanie kontraktu usługi, zobacz [projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md). Należy pamiętać o tym, czy klient może być wymagane do implementowania kontraktu zdefiniowane przez usługę, o nazwie kontrakt wywołania zwrotnego do odbierania komunikatów z usługi w MEP dwukierunkowego. Aby uzyskać więcej informacji, zobacz [usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
 Obowiązkowo przy użyciu kodu lub deklaratywne przy użyciu konfiguracji można określić punktu końcowego usługi. Jeśli nie określono żadnych punktów końcowych następnie środowisko wykonawcze zapewnia domyślne punkty końcowe, dodając jeden domyślny punkt końcowy dla każdego adresu podstawowego dla każdej umowy serwisowej implementowane przez usługę. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne ponieważ powiązań i adresów dla wdrożonej usługi są zazwyczaj inne niż używane, gdy usługa jest obecnie sporządzana. Ogólnie rzecz biorąc lepiej jest punkty końcowe usługi przy użyciu konfiguracji zamiast kodu. Zachowanie powiązania i adresowanie z kodu pozwala zmienić bez konieczności ponownego kompilowania i ponownego wdrażania aplikacji.  
  
> [!NOTE]
>  Podczas dodawania punktu końcowego usługi, który wykonuje personifikacji, należy użyć jednej z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody lub <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> metoda prawidłowo załadować umowy do nowej <xref:System.ServiceModel.Description.ServiceDescription> obiektu.  
  
## <a name="defining-endpoints-in-code"></a>Definiowanie punktów końcowych w kodzie  
 Poniższy przykład ilustruje sposób określania punktu końcowego w kodzie za pomocą następujących czynności:  
  
-   Definiowanie kontraktu w celu `IEcho` typ usługi, który akceptuje nazwy i echa z odpowiedzią innego użytkownika "Hello \<name >!".  
  
-   Implementowanie `Echo` usługi typu zdefiniowanego przez `IEcho` kontraktu.  
  
-   Określ adres punktu końcowego `http://localhost:8000/Echo` dla usługi.  
  
-   Konfigurowanie `Echo` usługi przy użyciu <xref:System.ServiceModel.WSHttpBinding> powiązania.  
  
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
>  Host usługi jest tworzona przy użyciu adres podstawowy, a następnie pozostałą część adresu, określany względem adresu podstawowego jest określone jako część punktu końcowego. Ten podział adres umożliwia wielu punktów końcowych zdefiniowanych w bardzo ułatwia usługi na hoście.  
  
> [!NOTE]
>  Właściwości <xref:System.ServiceModel.Description.ServiceDescription> w usłudze aplikacji nie mogą zostać zmodyfikowane subsequent do <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metody <xref:System.ServiceModel.ServiceHostBase>. Niektóre elementy członkowskie, takie jak <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości i `AddServiceEndpoint` metod <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.ServiceHost>, zgłosić wyjątek, jeśli zmodyfikowane poza tym punktem. Inne pozwala na ich modyfikować, ale wynik jest niezdefiniowany.  
>   
>  Podobnie, na komputerze klienckim <xref:System.ServiceModel.Description.ServiceEndpoint> wartości nie mogą zostać zmodyfikowane po wywołaniu <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> na <xref:System.ServiceModel.ChannelFactory>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Właściwość zgłasza wyjątek, jeśli zmodyfikować ostatnie tego punktu. Inne wartości Opis klienta można zmodyfikować bez błędów, ale wynik jest niezdefiniowany.  
>   
>  Czy usługi lub klienta, zalecane jest zmodyfikowanie opis przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.  
  
## <a name="defining-endpoints-in-configuration"></a>Definiowanie punktów końcowych w konfiguracji  
 Podczas tworzenia aplikacji, często zachodzi potrzeba Odrocz decyzje przez administratora, który jest wdrożenie aplikacji. Na przykład często występuje będzie żadnej możliwość określenia, z wyprzedzeniem, jakie usługi, adresów (URI). Zamiast kodować adresu, jest bardziej pożądane, aby umożliwić administratorowi to zrobić po utworzeniu usługi. Ta elastyczność odbywa się za pośrednictwem konfiguracji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).  
  
> [!NOTE]
>  Użyj [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z `/config:` *filename*`[,`*filename* `]` przejdź do Szybko twórz plików konfiguracyjnych.  
  
## <a name="using-default-endpoints"></a>Przy użyciu domyślnych punktów końcowych  
 Jeśli nie określono żadnych punktów końcowych w kodzie lub w konfiguracji następnie środowisko wykonawcze zapewnia domyślne punkty końcowe, dodając jeden domyślny punkt końcowy dla każdego adresu podstawowego dla każdej umowy serwisowej implementowane przez usługę. Adres podstawowy, można określić w kodzie lub w konfiguracji i domyślne punkty końcowe są dodawane, gdy <xref:System.ServiceModel.ICommunicationObject.Open> jest wywoływana w <xref:System.ServiceModel.ServiceHost>. W tym przykładzie jest tym samym przykładzie w poprzedniej sekcji, ale ponieważ nie określono żadnych punktów końcowych, domyślne punkty końcowe są dodawane.  
  
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
  
 Jeśli punkty końcowe są podane jawnie, nadal można dodać domyślnych punktów końcowych przez wywołanie metody <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> na <xref:System.ServiceModel.ServiceHost> przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md)
