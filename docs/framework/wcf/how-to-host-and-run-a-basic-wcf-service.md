---
title: Jak hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 73633c2c6119204f2fb608b32ae794a2e07b27d0
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747077"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>Jak hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation

Jest to trzecia sześciu zadań podrzędnych, wymagane do utworzenia aplikacji Windows Communication Foundation (WCF). Omówienie wszystkich sześciu zadań, zobacz [Samouczek wprowadzający](getting-started-tutorial.md) tematu.

W tym temacie opisano, jak hostować usługi Windows Communication Foundation (WCF) w aplikacji konsoli. Ta procedura obejmuje następujące kroki:

- Utwórz projekt aplikacji konsoli do obsługi usługi.

- Utwórz hosta usługi dla usługi.

- Włącz wymiany metadanych.

- Otworzyć hosta usługi.

Pełną listę kod napisany w ramach tego zadania jest dostępna w przykładzie zamieszczonym po procedurze.

## <a name="create-a-new-console-application-to-host-the-service"></a>Utwórz nową aplikację konsoli do obsługi usługi

1. Utwórz nowy projekt aplikacji konsoli w programie Visual Studio, klikając prawym przyciskiem myszy na wprowadzenie do rozwiązań i wybierając **Dodaj** > **nowy projekt**. W **Dodaj nowy projekt** okna dialogowego po lewej stronie wybierz **pulpitu Windows** kategorię w obszarze **Visual C#** lub **języka Visual Basic**. Wybierz **Aplikacja konsoli (.NET Framework)** szablonu, a następnie nazwę projektu **GettingStartedHost**.

2. Dodaj odwołanie do projektu GettingStartedLib do projektu GettingStartedHost. Kliknij prawym przyciskiem myszy **odwołania** folderu w projekcie GettingStartedHost w **Eksploratora rozwiązań**, a następnie wybierz pozycję **Dodaj odwołanie**. W **Dodaj odwołanie** okno dialogowe, wybierz opcję **rozwiązania** w lewej części okna dialogowego Wybierz GettingStartedLib w górnej części okna dialogowego, a następnie wybierz **Dodaj**. To sprawia, że typy zdefiniowane w GettingStartedLib GettingStartedHost projektowi.

3. Dodaj odwołanie do System.ServiceModel do projektu GettingStartedHost. Kliknij prawym przyciskiem myszy **odwołania** folderu w projekcie GettingStartedHost w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie**. W **Dodaj odwołanie** okno dialogowe, wybierz opcję **Framework** po lewej stronie okna dialogowego, w obszarze **zestawy**. Znajdź i zaznacz **System.ServiceModel**, a następnie wybierz **OK**. Zapisz rozwiązanie, wybierając **pliku** > **Zapisz wszystko**.

## <a name="host-the-service"></a>Host usługi

Otwórz plik Program.cs lub Module.vb i wprowadź następujący kod:

```csharp
using System;
using System.ServiceModel;
using System.ServiceModel.Description;
using GettingStartedLib;

namespace GettingStartedHost
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1 Create a URI to serve as the base address.
            Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

            // Step 2 Create a ServiceHost instance
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

            try
            {
                // Step 3 Add a service endpoint.
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                // Step 4 Enable metadata exchange.
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                smb.HttpGetEnabled = true;
                selfHost.Description.Behaviors.Add(smb);

                // Step 5 Start the service.
                selfHost.Open();
                Console.WriteLine("The service is ready.");
                Console.WriteLine("Press <ENTER> to terminate service.");
                Console.WriteLine();
                Console.ReadLine();

                // Close the ServiceHostBase to shutdown the service.
                selfHost.Close();
            }
            catch (CommunicationException ce)
            {
                Console.WriteLine("An exception occurred: {0}", ce.Message);
                selfHost.Abort();
            }
        }
    }
}
```

```vb
Imports System.ServiceModel
Imports System.ServiceModel.Description
Imports GettingStartedLibVB.GettingStartedLib

Module Service

    Class Program
        Shared Sub Main()
            ' Step 1 Create a URI to serve as the base address
            Dim baseAddress As New Uri("http://localhost:8000/GettingStarted")

            ' Step 2 Create a ServiceHost instance
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
           Try

                ' Step 3 Add a service endpoint
                ' Add a service endpoint
                selfHost.AddServiceEndpoint( _
                    GetType(ICalculator), _
                    New WSHttpBinding(), _
                    "CalculatorService")

                ' Step 4 Enable metadata exchange.
                Dim smb As New ServiceMetadataBehavior()
                smb.HttpGetEnabled = True
                selfHost.Description.Behaviors.Add(smb)

                ' Step 5 Start the service
                selfHost.Open()
                Console.WriteLine("The service is ready.")
                Console.WriteLine("Press <ENTER> to terminate service.")
                Console.WriteLine()
                Console.ReadLine()

                ' Close the ServiceHostBase to shutdown the service.
                selfHost.Close()
            Catch ce As CommunicationException
                Console.WriteLine("An exception occurred: {0}", ce.Message)
                selfHost.Abort()
            End Try
        End Sub
    End Class

End Module
```

**Krok 1** — tworzy wystąpienie klasy Uri do przechowywania adres podstawowy usługi. Usługi są identyfikowane przez adres URL, który zawiera adres podstawowy i opcjonalnie identyfikatora URI. Adres podstawowy jest sformatowany w następujący sposób: [transportu] :// [nazwa komputera lub domeny] [: opcjonalne # portu] / [opcjonalne segmentem identyfikatora URI] adres podstawowy usługi Kalkulator używa protokołu HTTP, localhost, port 8000 i identyfikator URI segmentu "GettingStarted"

**Krok 2** — tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> klasy do obsługi usługi. Konstruktor przyjmuje dwa parametry typu klasy, który implementuje ten kontrakt usługi i podstawowego adresu usługi.

**Krok 3** — tworzy <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienia. Punkt końcowy usługi składa się z adresu, powiązanie i kontraktu usługi. <xref:System.ServiceModel.Description.ServiceEndpoint> Konstruktor przyjmuje w związku z tym typem interfejsu kontraktu usługi, powiązanie i adres. Umowa serwisowa jest `ICalculator`, zdefiniowane przez użytkownika, która implementuje typu usługi. Wiązanie używane w tym przykładzie jest <xref:System.ServiceModel.WSHttpBinding> czyli wbudowane powiązania, które służy do nawiązywania połączenia z punktami końcowymi, które odpowiadają WS-* specyfikacji. Aby uzyskać więcej informacji na temat wiązania WCF, zobacz [omówienie powiązań WCF](bindings-overview.md). Adres jest dołączany do podstawowego adresu do identyfikowania punktu końcowego. Adres podany w tym kodzie jest "CalculatorService", dlatego jest w pełni kwalifikowany adres punktu końcowego `"http://localhost:8000/GettingStarted/CalculatorService"`.

> [!IMPORTANT]
> Dodawanie punktu końcowego usługi jest opcjonalny podczas korzystania z programu .NET Framework 4 lub nowszej. W tych wersjach Jeśli punkty końcowe nie są dodawane w kodzie lub konfiguracji usługi WCF dodaje jeden domyślny punkt końcowy dla każdej kombinacji adresu podstawowego i kontrakt implementowane przez usługę. Aby uzyskać więcej informacji na temat domyślne punkty końcowe zobacz [Określanie adresu punktu końcowego](specifying-an-endpoint-address.md). Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](simplified-configuration.md) i [uproszczona konfiguracja usług WCF](./samples/simplified-configuration-for-wcf-services.md).

**Krok 4** — Włączanie wymiany metadanych. Klienci będą używać wymiany metadanych do Generowanie serwerów proxy, które będą używane do wywoływania operacji usługi. Umożliwia tworzenie wymiany metadanych <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienia, należy ustawić go w <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwości `true`i dodać zachowanie, aby <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> zbiór <xref:System.ServiceModel.ServiceHost> wystąpienia.

**Krok 5** — Otwórz <xref:System.ServiceModel.ServiceHost> do nasłuchiwania pod kątem przychodzących wiadomości. Zauważ, że kod oczekuje na użytkownika trafić wprowadzić. Jeśli nie tego zrobić, aplikacja zostanie natychmiast zamknięta i usługa zostanie zamknięta. Zwróć również uwagę bloku try/catch używane. Po <xref:System.ServiceModel.ServiceHost> został uruchomiony, inny kod znajduje się w bloku try/catch. Aby uzyskać więcej informacji na temat bezpiecznego przechwytywanie wyjątków zgłaszanych przez <xref:System.ServiceModel.ServiceHost>, zobacz [Użyj Zamknij i Abort, aby zwolnić zasoby klienta WCF](samples/use-close-abort-release-wcf-client-resources.md)

> [!IMPORTANT]
> Po dodaniu biblioteki usługi WCF, Visual Studio może obsługiwać go dla Ciebie podczas debugowania przez uruchomienie hosta usługi. Aby uniknąć konfliktów tę opcję można wyłączyć. 
> 1. Otwórz właściwości projektu dla GettingStartedLib.
> 2. Przejdź do **opcje WCF** i usuń zaznaczenie pola wyboru **Start podczas debugowania Host usługi WCF**.

## <a name="verify-the-service-is-working"></a>Sprawdź, czy usługa działa

1. Uruchom konsolę GettingStartedHost aplikacji z poziomu programu Visual Studio.

   Usługa musi być uruchamiane z uprawnieniami administratora. Ponieważ program Visual Studio została otwarta z uprawnieniami administratora, GettingStartedHost również jest uruchamiane z uprawnieniami administratora. Możesz również otworzyć nowego przy użyciu wiersza polecenia **Uruchom jako administrator** i uruchom service.exe znajdujący się w nim.

2. Otwórz przeglądarkę internetową i przejdź do strony debugowania usługi na `http://localhost:8000/GettingStarted/`. **Uwaga! Końcowy ukośnik jest znaczący.**

## <a name="example"></a>Przykład

Poniższy przykład zawiera kontrakt usługi i implementację z poprzednich kroków samouczka i hostuje usługę w aplikacji konsoli.

Aby skompilować to za pomocą kompilatora wiersza polecenia, należy skompilować do biblioteki klas, który odwołuje się do IService1.cs i Service1.cs `System.ServiceModel.dll`. Kompiluj plik Program.cs jako aplikację konsolową w języku.

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
        [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
        public interface ICalculator
        {
            [OperationContract]
            double Add(double n1, double n2);
            [OperationContract]
            double Subtract(double n1, double n2);
            [OperationContract]
            double Multiply(double n1, double n2);
            [OperationContract]
            double Divide(double n1, double n2);
        }
}
```

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```csharp
using System;
using System.ServiceModel;
using System.ServiceModel.Description;
using GettingStartedLib;

namespace GettingStartedHost
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.
            Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

            // Step 2 of the hosting procedure: Create ServiceHost
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

            try
            {
                // Step 3 of the hosting procedure: Add a service endpoint.
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                // Step 4 of the hosting procedure: Enable metadata exchange.
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                smb.HttpGetEnabled = true;
                selfHost.Description.Behaviors.Add(smb);

                // Step 5 of the hosting procedure: Start (and then stop) the service.
                selfHost.Open();
                Console.WriteLine("The service is ready.");
                Console.WriteLine("Press <ENTER> to terminate service.");
                Console.WriteLine();
                Console.ReadLine();

                // Close the ServiceHostBase to shutdown the service.
                selfHost.Close();
            }
            catch (CommunicationException ce)
            {
                Console.WriteLine("An exception occurred: {0}", ce.Message);
                selfHost.Abort();
            }
        }
    }
}
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
    Public Interface ICalculator

        <OperationContract()> _
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
End Namespace
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

```vb
Imports System.ServiceModel
Imports System.ServiceModel.Description
Imports GettingStartedLibVB.GettingStartedLib

Module Service

    Class Program
        Shared Sub Main()
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.
            Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

            ' Step 2 of the hosting procedure: Create ServiceHost
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
            Try

                ' Step 3 of the hosting procedure: Add a service endpoint.
                ' Add a service endpoint
                selfHost.AddServiceEndpoint( _
                    GetType(ICalculator), _
                    New WSHttpBinding(), _
                    "CalculatorService")

                ' Step 4 of the hosting procedure: Enable metadata exchange.
                ' Enable metadata exchange
                Dim smb As New ServiceMetadataBehavior()
                smb.HttpGetEnabled = True
                selfHost.Description.Behaviors.Add(smb)

                ' Step 5 of the hosting procedure: Start (and then stop) the service.
                selfHost.Open()
                Console.WriteLine("The service is ready.")
                Console.WriteLine("Press <ENTER> to terminate service.")
                Console.WriteLine()
                Console.ReadLine()

                ' Close the ServiceHostBase to shutdown the service.
                selfHost.Close()
            Catch ce As CommunicationException
                Console.WriteLine("An exception occurred: {0}", ce.Message)
                selfHost.Abort()
            End Try
        End Sub
    End Class

End Module
```

> [!NOTE]
> Usługi, takie jak tego wymaga uprawnienia do rejestrowania adresy HTTP na komputerze w celu nasłuchiwania. Administrator konta mają to uprawnienie, ale konta bez uprawnień administratora musi mieć uprawnienie dla przestrzeni nazw protokołu HTTP. Aby uzyskać więcej informacji o sposobie konfigurowania rezerwacji przestrzeni nazw, zobacz [Konfigurowanie protokołów HTTP i HTTPS](feature-details/configuring-http-and-https.md). Podczas uruchamiania w programie Visual Studio, service.exe muszą być uruchomione z uprawnieniami administratora.

## <a name="next-steps"></a>Następne kroki

Teraz usługa jest uruchomiona. Następne zadanie tworzenia klienta programu WCF.

> [!div class="nextstepaction"]
> [Instrukcje: Utworzenie klienta WCF](how-to-create-a-wcf-client.md)

Aby uzyskać informacje dotyczące rozwiązywania problemów, zobacz [Rozwiązywanie problemów z samouczka Wprowadzenie](troubleshooting-the-getting-started-tutorial.md).

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](samples/getting-started-sample.md)
- [Host samodzielny](samples/self-host.md)
- [Usługi hostingowe](hosting-services.md)
