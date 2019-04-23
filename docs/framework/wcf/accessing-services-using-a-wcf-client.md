---
title: Uzyskiwanie dostępu do usług za pomocą klienta WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 6bf683cdd0a03a5d1dbc452c28e7b33911464f09
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59297255"
---
# <a name="accessing-services-using-a-wcf-client"></a>Uzyskiwanie dostępu do usług za pomocą klienta WCF

Po utworzeniu usługi, następnym krokiem jest utworzenie serwer proxy klienta WCF. Aplikacja kliencka używa serwera proxy klienta WCF do komunikowania się z usługą. Aplikacje klienckie zwykle Importowanie metadanych usługi, aby wygenerować kod klienta WCF, który może służyć do wywołania usługi.

 Następujące podstawowe kroki tworzenia klienta programu WCF:

1. Kompilowanie kodu usługi.

2. Generuj proxy klienta WCF.

3. Tworzy serwer proxy klienta WCF.

Serwer proxy klienta WCF można wygenerować ręcznie przy użyciu usługi modelu metadanych narzędzie (SvcUtil.exe) Aby uzyskać więcej informacji, zobacz [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Serwer proxy klienta WCF, mogą być też generowane w programie Visual Studio przy użyciu **Dodaj odwołanie do usługi** funkcji. Aby wygenerować serwer proxy klienta WCF, za pomocą jednej z metod usługi musi być uruchomiona. Jeśli usługa jest samodzielnie hostowana należy uruchomić hosta. Jeśli usługa jest hostowana w programie IIS / WAS, nie trzeba nic robić.

## <a name="servicemodel-metadata-utility-tool"></a>Narzędzie do obsługi metadanych elementu ServiceModel
 [Narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to narzędzie wiersza polecenia, generowanie kodu na podstawie metadanych. Użyj następujących znajduje się przykład podstawowe polecenia Svcutil.exe.

```
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 Alternatywnie można użyć Svcutil.exe plikami Web Services Description Language (WSDL) i schemat XML definicji język (XSD) w systemie plików.

```
Svcutil.exe <list of WSDL and XSD files on file system>
```

 Wynik jest plik kodu, który zawiera kod klienta WCF, używanego przez aplikację klienta do wywołania usługi.

 Umożliwia także narzędzie do generowania plików konfiguracyjnych.

```
Svcutil.exe <file1 [,file2]>
```

 Jeśli tylko jedną nazwę pliku, który jest nazwa pliku wyjściowego. Jeśli są podane dwie nazwy pliku, pierwszy plik jest plikiem konfiguracja danych wejściowych, których zawartość jest scalany z wygenerowaną konfigurację i zapisywane w pliku drugie. Aby uzyskać więcej informacji o konfiguracji, zobacz [konfigurowanie powiązań dla usług](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).

> [!IMPORTANT]
> Żądania metadanych niezabezpieczony stanowić zagrożeniom w taki sam sposób, który wykonuje każde żądanie niezabezpieczonej sieci: Jeśli nie masz pewność, że punkt końcowy, które komunikują się z jest tożsamości jest, informacje, które możesz pobrać może być metadanych usługi złośliwego.

## <a name="add-service-reference-in-visual-studio"></a>Dodaj odwołanie do usługi w programie Visual Studio

 Z uruchomioną usługę, kliknij prawym przyciskiem myszy projekt, który będzie zawierać serwer proxy klienta WCF, a następnie wybrać **Dodaj** > **odwołanie do usługi**. W **Dodaj odwołanie okno dialogowe usługi**, wpisz adres URL usługi, aby wywołać, a następnie kliknij przycisk **Przejdź** przycisku. Okno dialogowe wyświetli listę usług, które są dostępne pod adresem, które określisz. Kliknij dwukrotnie usługę Zobacz kontrakty i operacje dostępne, określ obszar nazw dla wygenerowanego kodu, a następnie kliknij przycisk **OK** przycisku.

## <a name="example"></a>Przykład
 Poniższy przykład kodu pokazuje kontraktu usługi utworzonych dla usługi.

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

 Narzędzie do obsługi metadanych elementu ServiceModel i **Dodaj odwołanie do usługi** w programie Visual Studio generuje następujące klasy klienta programu WCF. Klasa dziedziczy ogólnego <xref:System.ServiceModel.ClientBase%601> klasy i implementuje `ICalculator` interfejsu. Narzędzie generuje również `ICalculator` interfejsu (nie pokazane tutaj).

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

## <a name="using-the-wcf-client"></a>Za pomocą klienta WCF
 Aby używać klienta platformy WCF, Utwórz wystąpienie obiektu klienta WCF, a następnie wywołać jego metody, jak pokazano w poniższym kodzie.

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

## <a name="debugging-exceptions-thrown-by-a-client"></a>Debugowanie wyjątków zgłaszanych przez klientów

Wiele wyjątków wygenerowanych przez klienta programu WCF są spowodowane przez wyjątek w usłudze. Przedstawiono kilka przykładów:

-   <xref:System.Net.Sockets.SocketException>: Istniejące połączenie zostało zamknięte przez hosta zdalnego.

-   <xref:System.ServiceModel.CommunicationException>: Połączenie podstawowe zostało nieoczekiwanie zamknięte.

-   <xref:System.ServiceModel.CommunicationObjectAbortedException>: Połączenie gniazda zostało przerwane. Może to być spowodowane błędnym przetwarzaniem komunikatu, limit czasu odbioru przekroczenia przez hosta zdalnego lub podstawowym problemem z zasobami sieciowymi.

Po wystąpieniu tego rodzaju wyjątków, najlepszym sposobem rozwiązania tego problemu jest włączone jest śledzenie po stronie usługi i określić, jakie wyjątek wystąpił brak. Aby uzyskać więcej informacji na temat śledzenia, zobacz [śledzenia](../../../docs/framework/wcf/diagnostics/tracing/index.md) i [przy użyciu śledzenia do Rozwiązywanie problemów aplikacji](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [Instrukcje: Dostęp do usług za pomocą kontraktu dwukierunkowego](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Instrukcje: Asynchroniczne wywoływanie operacji usługi](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [Instrukcje: Uzyskiwanie dostępu do usług za pomocą jednokierunkowego i kontraktów "żądanie odpowiedź"](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Instrukcje: Dostęp do programu WSE 3.0 usługi](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Opis wygenerowanego kodu klienta](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)
- [Instrukcje: Poprawę czasu uruchamiania programu WCF klienta aplikacji przy użyciu elementu XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [Określanie zachowania klienta w czasie wykonywania](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [Konfigurowanie zachowań klienta](../../../docs/framework/wcf/configuring-client-behaviors.md)
