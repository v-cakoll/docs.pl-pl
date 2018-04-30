---
title: Uzyskiwanie dostępu do usług za pomocą klienta WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
caps.latest.revision: 36
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69352ba5c12267f5075ae38c5bdcc0665b3fe050
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="accessing-services-using-a-wcf-client"></a>Uzyskiwanie dostępu do usług za pomocą klienta WCF
Po utworzeniu usługi, następnym krokiem jest utworzenie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] proxy klienta. Aplikacja kliencka używa [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] proxy klienta do komunikowania się z usługą. Aplikacje klienckie zwykle Importowanie metadanych usługi do generowania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kodu klienta, który może służyć do wywołania usługi.  
  
 Podstawowe kroki tworzenia [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta są następujące:  
  
1.  Kompilowanie kodu usługi.  
  
2.  Generowanie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] proxy klienta.  
  
3.  Utwórz wystąpienie serwera proxy klienta WCF.  
  
 Serwer proxy klienta WCF można wygenerować ręcznie przy użyciu modelu metadanych narzędzie narzędzia usługi (SvcUtil.exe) Aby uzyskać więcej informacji, zobacz [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Serwer proxy klienta WCF może być również generowany w programie Visual Studio za pomocą funkcji Dodaj odwołanie do usługi. Aby wygenerować proxy klienta WCF, za pomocą jednej z metod usługi musi być uruchomiona. Jeśli usługa jest samodzielnie hostowana należy uruchomić hosta. Jeśli usługa jest obsługiwana w programie IIS / WAS, nie trzeba nic robić.  
  
## <a name="servicemodel-metadata-utility-tool"></a>Narzędzie do obsługi metadanych elementu ServiceModel  
 [Narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to narzędzie wiersza polecenia dla generowania kodu z metadanych. Użyj następujących jest przykładem podstawowe polecenia Svcutil.exe.  
  
```  
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
```  
  
 Alternatywnie można użyć Svcutil.exe przy użyciu usługi sieci Web Services Description Language (WSDL) i schemat XML definicji języka (XSD) plików w systemie plików.  
  
```  
Svcutil.exe <list of WSDL and XSD files on file system>  
```  
  
 Wynik jest plik kodu zawierający [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kodu klienta, który aplikacja kliencka można użyć do wywołania usługi.  
  
 Można również użyć narzędzia do generowania plików konfiguracyjnych.  
  
```  
Svcutil.exe <file1 [,file2]>  
```  
  
 Jeśli tylko jedną nazwę pliku, jest to nazwa pliku wyjściowego. Jeśli są podane dwie nazwy pliku, plik jest plik wejściowy konfiguracji, których zawartość jest scalany z wygenerowanym konfiguracji i zapisywane w pliku drugie. Aby uzyskać więcej informacji o konfiguracji, zobacz [konfigurowanie powiązań dla usług](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).  
  
> [!IMPORTANT]
>  Żądania metadanych niezabezpieczona stanowić zagrożenie niektórych w taki sam sposób, który wykonuje każde żądanie sieć niezabezpieczona: Jeśli nie masz pewność, że punkt końcowy komunikują się z jest tożsamości jest, można pobrać informacji mogą być metadanych z złośliwe usługi.  
  
## <a name="add-service-reference-in-visual-studio"></a>Dodaj odwołanie do usługi w programie Visual Studio  
 Z uruchomioną usługę, kliknij prawym przyciskiem myszy projekt, który będzie zawierać serwer proxy klienta WCF i wybierz **Dodaj odwołanie do usługi**. W **Dodaj usługi okna dialogowego odwołania** typem w adresie URL do usługi, aby wywołać i kliknij przycisk **Przejdź** przycisku. Okno dialogowe wyświetli listę usług, które są dostępne pod adresem, które określisz. Kliknij dwukrotnie usługę, aby wyświetlić Umowy i dostępne operacje, określać przestrzeń nazw dla wygenerowanego kodu i kliknij przycisk **OK** przycisku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje kontrakt usługi utworzone dla usług.  
  
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
  
 Narzędzie do metadanych elementu ServiceModel i Dodaj odwołanie do usługi w programie Visual Studio generuje następujące [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klasy klienta. Klasa dziedziczy ogólnego <xref:System.ServiceModel.ClientBase%601> klasy i implementuje `ICalculator` interfejsu. Narzędzie generuje również `ICalculator` interfejsu (nie jest tutaj widoczny).  
  
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
 Aby użyć [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta, Utwórz wystąpienie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta, a następnie wywołać jej metod, jak pokazano w poniższym kodzie.  
  
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
  
## <a name="debugging-exceptions-thrown-by-a-client"></a>Debugowanie wyjątków zgłaszanych przez klienta  
 Wiele wyjątków zgłaszanych przez [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta są spowodowane przez wyjątek w usłudze. Przedstawiono kilka przykładów:  
  
-   <xref:System.Net.Sockets.SocketException>: Istniejące połączenie zostało zamknięte przez hosta zdalnego.  
  
-   <xref:System.ServiceModel.CommunicationException>Połączenie podstawowe zostało nieoczekiwanie zakończone.  
  
-   <xref:System.ServiceModel.CommunicationObjectAbortedException>: Połączenie gniazda zostało przerwane. Przyczyną może być błąd podczas przetwarzania komunikatu, limit czasu odbioru przekroczenia przez hosta zdalnego lub podstawowej problemem z zasobami sieciowymi.  
  
 W przypadku wystąpienia tego typu wyjątki najlepszy sposób, aby umożliwić rozwiązanie tego problemu jest Włącz śledzenie po stronie usługi, a także określenie, jakie wyjątek wystąpił brak. Aby uzyskać więcej informacji dotyczących śledzenia, zobacz [śledzenie](../../../docs/framework/wcf/diagnostics/tracing/index.md) i [przy użyciu śledzenie, aby rozwiązać Twoja aplikacja](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [Instrukcje: asynchroniczne wywoływanie operacji usługi](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)  
 [Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktów jednokierunkowych i kontraktów „żądanie-odpowiedź”](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)  
 [Instrukcje: dostęp do usługi WSE 3.0](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)  
 [Opis wygenerowanego kodu klienta](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)  
 [Instrukcje: skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)  
 [Określanie zachowania klienta w czasie wykonywania](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [Konfigurowanie zachowań klienta](../../../docs/framework/wcf/configuring-client-behaviors.md)
