---
title: Przegląd tworzenia punktów końcowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], overview
ms.assetid: f4dce0fb-6f54-47e6-8054-86d7f574b91c
ms.openlocfilehash: 0b0c22737e9407ebe2cb56c15fb7ff75d16b50a4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040309"
---
# <a name="endpoint-creation-overview"></a>Przegląd tworzenia punktów końcowych

Cała komunikacja z usługą Windows Communication Foundation (WCF) odbywa się za pomocą *punktów końcowych* usługi. Punkty końcowe zapewniają klientom dostęp do funkcji oferowanych przez usługę WCF. W tej sekcji opisano strukturę punktu końcowego i przedstawiono sposób definiowania punktu końcowego w konfiguracji i w kodzie.

## <a name="the-structure-of-an-endpoint"></a>Struktura punktu końcowego

Każdy punkt końcowy zawiera adres wskazujący, gdzie znaleźć punkt końcowy, powiązanie, które określa, jak klient może komunikować się z punktem końcowym, oraz umowę, która identyfikuje dostępne metody.

- **Adres**. Adres jednoznacznie identyfikuje punkt końcowy i informuje potencjalnych klientów, w których znajduje się usługa. Jest reprezentowana w modelu obiektów WCF przez <xref:System.ServiceModel.EndpointAddress> adres, który zawiera Uniform Resource Identifier (URI) i właściwości adresu, które obejmują tożsamość, niektóre elementy Web Services Description Language (WSDL) i kolekcję opcjonalną nagłówka. Opcjonalne nagłówki zawierają dodatkowe informacje o adresach, które identyfikują lub współpracują z punktem końcowym. Aby uzyskać więcej informacji, zobacz [Określanie adresu punktu końcowego](../../../docs/framework/wcf/specifying-an-endpoint-address.md).

- **Powiązanie**. Powiązanie określa sposób komunikacji z punktem końcowym. Powiązanie określa, w jaki sposób punkt końcowy komunikuje się z całym świecie, w tym który protokół transportowy do użycia (na przykład TCP lub HTTP), którego kodowanie ma być używane dla komunikatów (na przykład tekst lub binarny), a wymagania dotyczące zabezpieczeń są niezbędne (dla przykład SSL [SSL] lub zabezpieczenia komunikatów SOAP). Aby uzyskać więcej informacji, zobacz [using bindings to configure Services and clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).

- **Kontrakt usługi**. Kontrakt usługi zawiera opis funkcji, które punkt końcowy uwidacznia dla klienta. Kontrakt określa operacje, które klient może wywołać, formę komunikatu oraz typ parametrów wejściowych lub danych wymaganych do wywołania operacji oraz rodzaj przetwarzania lub komunikatów odpowiedzi, których może oczekiwać klient. Trzy podstawowe typy kontraktów odnoszą się do podstawowych wzorców wymiany komunikatów (MEPs): datagram (jednokierunkowe), żądanie/odpowiedź i dupleks (dwukierunkowe). Kontrakt usługi może również korzystać z kontraktów danych i komunikatów w celu wymagania określonych typów danych i formatów komunikatów podczas uzyskiwania dostępu do nich. Aby uzyskać więcej informacji na temat sposobu definiowania kontraktu usługi, zobacz [Projektowanie kontraktów usług](../../../docs/framework/wcf/designing-service-contracts.md). Należy pamiętać, że klient może być również wymagany do wdrożenia kontraktu zdefiniowanego przez usługę, zwanego kontraktem wywołania zwrotnego, aby odbierać komunikaty z usługi w trybie dupleksu unikatowy MEP. Aby uzyskać więcej informacji, zobacz [usługi dupleksowe](../../../docs/framework/wcf/feature-details/duplex-services.md).

Punkt końcowy usługi można określić samodzielnie za pomocą kodu lub deklaratywnie za pośrednictwem konfiguracji. Jeśli nie określono żadnych punktów końcowych, środowisko uruchomieniowe zapewnia domyślne punkty końcowe, dodając jeden domyślny punkt końcowy dla każdego adresu podstawowego dla każdego kontraktu usługi zaimplementowanego przez usługę. Definiowanie punktów końcowych w kodzie zazwyczaj nie jest praktyczne, ponieważ powiązania i adresy dla wdrożonej usługi są zwykle inne niż te używane podczas tworzenia usługi. Ogólnie rzecz biorąc, bardziej praktyczne jest zdefiniowanie punktów końcowych usługi przy użyciu konfiguracji zamiast kodu. Przechowywanie informacji o powiązaniach i adresowaniu poza kodem pozwala im zmieniać bez konieczności ponownego kompilowania i wdrażania aplikacji.

> [!NOTE]
> Podczas dodawania punktu końcowego usługi, który wykonuje personifikację, należy użyć jednej z <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metod <xref:System.ServiceModel.Description.ContractDescription.GetContract%28System.Type%2CSystem.Type%29> lub metody w celu poprawnego załadowania kontraktu do nowego <xref:System.ServiceModel.Description.ServiceDescription> obiektu.

## <a name="defining-endpoints-in-code"></a>Definiowanie punktów końcowych w kodzie

Poniższy przykład ilustruje sposób określania punktu końcowego w kodzie przy użyciu następujących metod:

- Zdefiniuj kontrakt dla `IEcho` typu usługi, który akceptuje nazwę i echo kogoś z odpowiedzi "Hello \<Name >!".

- `IEcho` Implementowanie `Echo` usługi typu zdefiniowanej przez kontrakt.

- Określ adres `http://localhost:8000/Echo` punktu końcowego dla usługi.

- `Echo` Skonfiguruj usługę <xref:System.ServiceModel.WSHttpBinding> przy użyciu powiązania.

```csharp
namespace Echo
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
> Host usługi jest tworzony przy użyciu adresu podstawowego, a następnie pozostała część adresu względem adresu podstawowego jest określana jako część punktu końcowego. Takie partycjonowanie adresu pozwala na bardziej wygodne definiowanie wielu punktów końcowych dla usług na hoście.

> [!NOTE]
> Właściwości w aplikacji usługi nie mogą być modyfikowane po <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> metodzie <xref:System.ServiceModel.ServiceHostBase>. <xref:System.ServiceModel.Description.ServiceDescription> Niektóre elementy członkowskie, takie jak <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> Właściwość `AddServiceEndpoint` i metody w <xref:System.ServiceModel.ServiceHostBase> i <xref:System.ServiceModel.ServiceHost>, zgłaszają wyjątek, jeśli zostały zmodyfikowane po tym punkcie. Inne umożliwiają modyfikowanie ich, ale wynik jest niezdefiniowany.
>
> Analogicznie, na kliencie <xref:System.ServiceModel.Description.ServiceEndpoint> wartości nie mogą być modyfikowane po <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> wywołaniu metody <xref:System.ServiceModel.ChannelFactory>. <xref:System.ServiceModel.ChannelFactory.Credentials%2A> Właściwość zgłasza wyjątek, jeśli został zmodyfikowany poza tym punktem. Inne wartości opisu klienta można modyfikować bez błędu, ale wynik jest niezdefiniowany.
>
> Niezależnie od tego, czy dla usługi lub klienta zaleca się zmodyfikowanie opisu przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.

## <a name="defining-endpoints-in-configuration"></a>Definiowanie punktów końcowych w konfiguracji

Podczas tworzenia aplikacji często chcesz odroczyć decyzje administratora, który wdraża aplikację. Na przykład często nie ma możliwości znajomości informacji o adresie usługi (URI). Zamiast kodowania adresu, preferowane jest umożliwienie administratorowi wykonania tej czynności po utworzeniu usługi. Ta elastyczność jest realizowana przy użyciu konfiguracji. Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).

> [!NOTE]
> Użyj [Narzędzia metadanych ServiceModel (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) z przełącznikiem filename `/config:`nazwy*pliku* `]` ,`[,`aby szybko utworzyć pliki konfiguracyjne.

## <a name="using-default-endpoints"></a>Używanie domyślnych punktów końcowych

Jeśli w kodzie lub w konfiguracji nie określono żadnych punktów końcowych, środowisko uruchomieniowe zapewnia domyślne punkty końcowe, dodając jeden domyślny punkt końcowy dla każdego adresu podstawowego dla każdego kontraktu usługi zaimplementowanego przez usługę. Adres podstawowy może być określony w kodzie lub w konfiguracji, a domyślne punkty końcowe są dodawane, gdy <xref:System.ServiceModel.ICommunicationObject.Open> jest wywoływana <xref:System.ServiceModel.ServiceHost>na. Ten przykład jest taki sam jak w poprzedniej sekcji, ale ponieważ nie określono żadnych punktów końcowych, dodawane są domyślne punkty końcowe.

```csharp
namespace Echo
{
   // Define the contract for the IEcho service
   [ServiceContract]
   public interface IEcho
   {
       [OperationContract]
       String Hello(string name)
   }

   // Create an Echo service that implements IEcho contract
   public class Echo : IEcho
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

 Jeśli punkty końcowe są podane jawnie, można nadal dodawać domyślne punkty końcowe, wywołując <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> <xref:System.ServiceModel.ServiceHost> dla przed wywołaniem <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>metody. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [Uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

## <a name="see-also"></a>Zobacz także

- [Implementowanie kontraktów usług](../../../docs/framework/wcf/implementing-service-contracts.md)
