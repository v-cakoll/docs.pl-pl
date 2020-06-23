---
title: Uzyskiwanie dostępu do usług za pomocą klienta WCF
description: Dowiedz się, jak utworzyć serwer proxy klienta WCF dla usługi WCF. Aplikacja kliencka komunikuje się z usługą za pomocą serwera proxy klienta.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 25446a89a0b5657d32d77e2d0d57f58f36bed71b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245547"
---
# <a name="accessing-services-using-a-wcf-client"></a>Uzyskiwanie dostępu do usług za pomocą klienta WCF

Następnym krokiem po utworzeniu usługi jest utworzenie serwera proxy klienta programu WCF. Aplikacja kliencka używa serwera proxy klienta WCF do komunikowania się z usługą. Aplikacje klienckie zazwyczaj importują metadane usługi w celu wygenerowania kodu klienta WCF, którego można użyć do wywołania usługi.

 Podstawowe kroki tworzenia klienta WCF są następujące:

1. Skompiluj kod usługi.

2. Generuj serwer proxy klienta WCF.

3. Tworzenie wystąpienia serwera proxy klienta WCF.

Serwer proxy klienta WCF można wygenerować ręcznie przy użyciu narzędzia metadanych modelu usługi (SvcUtil.exe), aby uzyskać więcej informacji, zobacz [Narzędzie narzędzia metadanych ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md). Serwer proxy klienta WCF można również wygenerować w programie Visual Studio przy użyciu funkcji **Dodaj odwołanie do usługi** . Aby wygenerować serwer proxy klienta WCF przy użyciu dowolnej metody, musi być uruchomiona usługa. Jeśli usługa jest samoobsługowa, należy uruchomić hosta. Jeśli usługa jest hostowana w programie IIS/nie trzeba wykonywać żadnych innych czynności.

## <a name="servicemodel-metadata-utility-tool"></a>Narzędzie do przesyłania metadanych ServiceModel
 [Narzędzie do przesyłania metadanych modelu ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) jest narzędziem wiersza polecenia do generowania kodu z metadanych. Poniżej przedstawiono przykład polecenia Basic Svcutil.exe.

```console
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 Alternatywnie, można użyć Svcutil.exe z Web Services Description Language (WSDL) i plików języka definicji schematu XML (XSD) w systemie plików.

```console
Svcutil.exe <list of WSDL and XSD files on file system>
```

 Wynikiem jest plik kodu, który zawiera kod klienta WCF, którego aplikacja kliencka może użyć do wywołania usługi.

 Możesz również użyć narzędzia do generowania plików konfiguracji.

```console
Svcutil.exe <file1 [,file2]>
```

 Jeśli podano tylko jedną nazwę pliku, która jest nazwą pliku wyjściowego. Jeśli podano dwie nazwy plików, pierwszy plik jest plikiem konfiguracji wejściowej, którego zawartość jest scalana z wygenerowaną konfiguracją i zapisywana w drugim pliku. Aby uzyskać więcej informacji na temat konfiguracji, zobacz [Konfigurowanie powiązań dla usług](configuring-bindings-for-wcf-services.md).

> [!IMPORTANT]
> Niezabezpieczone żądania metadanych stanowią pewne zagrożenia w taki sam sposób, w jaki wszystkie niezabezpieczone żądania sieciowe: Jeśli nie masz pewności, że punkt końcowy, z którym nawiązujesz połączenie, jest to, że informacje pobierane mogą być metadanymi ze złośliwej usługi.

## <a name="add-service-reference-in-visual-studio"></a>Dodaj odwołanie do usługi w programie Visual Studio

 Po uruchomieniu usługi kliknij prawym przyciskiem myszy projekt, który będzie zawierać serwer proxy klienta WCF i wybierz polecenie **Dodaj**  >  **odwołanie do usługi**. W **oknie dialogowym Dodaj odwołanie do usługi**wpisz adres URL usługi, którą chcesz wywołać, a następnie kliknij przycisk **Przejdź** . W oknie dialogowym zostanie wyświetlona lista usług dostępnych pod określonym adresem. Kliknij dwukrotnie usługę, aby wyświetlić dostępne kontrakty i operacje, określ przestrzeń nazw dla wygenerowanego kodu, a następnie kliknij przycisk **OK** .

## <a name="example"></a>Przykład
 Poniższy przykład kodu przedstawia kontrakt usługi utworzony dla usługi.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    // Other methods are not shown here.
}
```

```vb
' Define a service contract.
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```

 Narzędzie do przesyłania metadanych ServiceModel i **Dodaj odwołanie do usługi** w programie Visual Studio generuje następujące klasy klienta WCF. Klasa dziedziczy z klasy generycznej <xref:System.ServiceModel.ClientBase%601> i implementuje `ICalculator` interfejs. Narzędzie generuje również `ICalculator` interfejs (nie pokazano tutaj).

```csharp
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator
{
    public CalculatorClient()
    {}

    public CalculatorClient(string endpointConfigurationName) :
            base(endpointConfigurationName)
    {}

    public CalculatorClient(string endpointConfigurationName, string remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(string endpointConfigurationName,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(System.ServiceModel.Channels.Binding binding,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(binding, remoteAddress)
    {}

    public double Add(double n1, double n2)
    {
        return base.Channel.Add(n1, n2);
    }
}
```

```vb
Partial Public Class CalculatorClient
    Inherits System.ServiceModel.ClientBase(Of ICalculator)
    Implements ICalculator

    Public Sub New()
        MyBase.New
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String)
        MyBase.New(endpointConfigurationName)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String, ByVal remoteAddress As String)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal binding As System.ServiceModel.Channels.Binding,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(binding, remoteAddress)
    End Sub

    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        Implements ICalculator.Add
        Return MyBase.Channel.Add(n1, n2)
    End Function
End Class
```

## <a name="using-the-wcf-client"></a>Korzystanie z klienta WCF
 Aby użyć klienta WCF, Utwórz wystąpienie klienta WCF, a następnie Wywołaj jego metody, jak pokazano w poniższym kodzie.

```csharp
// Create a client object with the given client endpoint configuration.
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = calcClient.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

```vb
' Create a client object with the given client endpoint configuration.
Dim calcClient As CalculatorClient = _
New CalculatorClient("CalculatorEndpoint")

' Call the Add service operation.
Dim value1 As Double = 100.00D
Dim value2 As Double = 15.99D
Dim result As Double = calcClient.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)
```

## <a name="debugging-exceptions-thrown-by-a-client"></a>Debugowanie wyjątków zgłoszonych przez klienta

Wiele wyjątków zgłoszonych przez klienta WCF jest spowodowanych przez wyjątek w usłudze. Oto kilka przykładów:

- <xref:System.Net.Sockets.SocketException>: Wykryto, że istniejące połączenie zostało wymuszone przez hosta zdalnego.

- <xref:System.ServiceModel.CommunicationException>: Połączenie bazowe zostało nieoczekiwanie zamknięte.

- <xref:System.ServiceModel.CommunicationObjectAbortedException>: Połączenie gniazda zostało przerwane. Może to być spowodowane błędem przetwarzania komunikatu, przekroczeniem limitu czasu odbierania przez hosta zdalnego lub problemem związanym z zasobami sieciowymi.

W przypadku wystąpienia tego typu wyjątków najlepszym sposobem rozwiązania problemu jest włączenie śledzenia po stronie usługi i określenie, który wyjątek wystąpił. Aby uzyskać więcej informacji na temat śledzenia, zobacz [śledzenie](./diagnostics/tracing/index.md) i [Używanie śledzenia w celu rozwiązywania problemów z aplikacją](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="see-also"></a>Zobacz też

- [Instrukcje: tworzenie klienta](how-to-create-a-wcf-client.md)
- [Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego](./feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Instrukcje: Asynchroniczne wywoływanie operacji usługi](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktów jednokierunkowych i kontraktów „żądanie-odpowiedź”](./feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Instrukcje: dostęp do usługi WSE 3.0](./feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Opis wygenerowanego kodu klienta](./feature-details/understanding-generated-client-code.md)
- [Instrukcje: skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [Określanie zachowania klienta w czasie wykonywania](specifying-client-run-time-behavior.md)
- [Konfigurowanie zachowań klienta](configuring-client-behaviors.md)
