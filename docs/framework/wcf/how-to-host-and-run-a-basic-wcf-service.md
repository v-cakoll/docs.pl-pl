---
title: 'Instrukcje: Hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a13e5a0044c51700acce6b123688868443f635ae
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>Instrukcje: Hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation
To trzeci sześciu zadania wymagane do utworzenia [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikacji. Omówienie sześciu wszystkich zadań, zobacz [Wprowadzenie — samouczek](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.  
  
 W tym temacie opisano, jak udostępniać [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] w aplikacji konsoli. Ta procedura obejmuje następujące kroki:  
  
-   Utwórz projekt aplikacji konsoli do obsługi usługi.  
  
-   Utwórz hosta usługi dla usługi.  
  
-   Włącz wymiany metadanych.  
  
-   Otworzyć hosta usługi.  
  
 Pełna lista kod napisany w tym zadaniu podano w przykładzie poniżej procedury.  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a>Aby utworzyć nową aplikację konsoli do obsługi usługi  
  
1.  Utwórz nowy projekt aplikacji konsoli, klikając prawym przyciskiem myszy na wprowadzenie rozwiązanie, jeśli zostanie wybrana, **Dodaj**, **nowy projekt**. W **Dodawanie nowego projektu** dialog w lewej strony okna dialogowego wyboru **Windows** w obszarze **C#** lub **VB**. W górnej części okna dialogowego wybierz **aplikacji konsoli**. Nazwa projektu GettingStartedHost.  
  
2.  Ustaw docelową platformę projektu GettingStartedHost .NET Framework 4.5, klikając prawym przyciskiem myszy **GettingStartedHost** w Eksploratorze rozwiązań i wybierając **właściwości**. W polu listy rozwijanej etykietą **platformy docelowej** wybierz **.NET Framework 4.5**. Ustawienie platformy docelowej dla projektu VB różni się nieco, w oknie dialogowym właściwości projektu GettingStartedHost, kliknij przycisk **skompilować** po lewej stronie ekranu, a następnie kliknij pozycję **zaawansowane kompilacji Opcje** przycisk w lewym dolnym rogu okna dialogowego. Następnie wybierz **.NET Framework 4.5** w polu listy rozwijanej etykietą **platformy docelowej**.  
  
     Platforma docelowa spowoduje, że ustawienie [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ponowne załadowanie rozwiązania, naciśnij klawisz **OK** po wyświetleniu monitu.  
  
3.  Dodaj odwołanie do projektu GettingStartedLib do projektu GettingStartedHost, klikając prawym przyciskiem myszy **odwołania** GettingStartedHost projekt w Eksploratorze rozwiązań i wybierz folder **Dodaj odwołanie** . W **Dodaj odwołanie** okno dialogowe, wybierz opcję **rozwiązania** po lewej stronie okna dialogowego i wybierz GettingStartedLib w w górnej części okna dialogowego i kliknij przycisk **Dodaj**. Dzięki temu typów zdefiniowanych w GettingStartedLib dostępne do projektu GettingStartedHost.  
  
4.  Dodaj odwołanie do System.ServiceModel do projektu GettingStartedHost, klikając prawym przyciskiem myszy **odwołania** GettingStartedHost projekt w Eksploratorze rozwiązań i wybierz folder **Dodaj** Odwołanie. W **Dodaj odwołanie** oknie dialogowym wybierz pozycję **Framework** po lewej stronie okna dialogowego. W polu tekstowym wyszukiwania zestawów, wpisz w `System.ServiceModel`. W górnej części okna dialogowego wybierz **System.ServiceModel**, kliknij przycisk **Dodaj** przycisk **Zamknij** przycisku. Zapisz rozwiązania przez kliknięcie przycisku Zapisz wszystko pod menu głównego.  
  
### <a name="to-host-the-service"></a>Do obsługi usługi  
  
-   Otwórz plik Program.cs lub Module.vb i wprowadź następujący kod:  
  
    ```csharp
    // program.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
    using GettingStartedLib;  
    using System.ServiceModel.Description;   
  
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
    'Module1.vb  
    Imports System  
    Imports System.ServiceModel  
    Imports System.ServiceModel.Description  
    Imports GettingStartedLibVB.GettingStartedLib  
  
    Module Service  
  
        Class Program  
            Shared Sub Main()  
                ' Step 1 Create a URI to serve as the base address  
                Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
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
  
    1.  Krok 1 — tworzy wystąpienie klasy identyfikatora Uri, aby pomieścić adres podstawowy usługi. Usługi są identyfikowane przez adres URL, który zawiera adres podstawowy i opcjonalnie identyfikatora URI. Adres podstawowy jest sformatowany w następujący sposób: [transportu] :// [nazwa komputera lub domeny] [: opcjonalny # portu] / [Opcjonalny identyfikator URI segmentu] adres podstawowy usługi Kalkulator używa transportu HTTP, localhost, port 8000 i identyfikator URI segmentu "GettingStarted"  
  
    2.  Krok 2 — tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> klasy do obsługi usługi. Konstruktor przyjmuje dwa parametry typu klasy, która implementuje kontraktu usługi, a adres podstawowy usługi.  
  
    3.  Krok 3 — tworzy <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` wystąpienia. Punkt końcowy usługi składa się z adresu, powiązania i kontrakt usługi. <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` Konstruktor ma w związku z tym typem interfejsu kontraktu usługi, powiązanie i adres. Kontrakt usługi jest `ICalculator`, co zdefiniowany i implementować typ usługi. Powiązanie używane w tym przykładzie jest <xref:System.ServiceModel.WSHttpBinding> czyli wbudowane powiązania, które jest używane do łączenia z punktów końcowych, które odpowiadają WS-* specyfikacji. Aby uzyskać więcej informacji na temat wiązania WCF, zobacz [omówienie powiązań WCF](../../../docs/framework/wcf/bindings-overview.md). Ten adres jest dołączany do adres podstawowy do identyfikowania punktu końcowego. Adres podany w ten kod jest "CalculatorService", dlatego pełny adres punktu końcowego jest `"http://localhost:8000/GettingStarted/CalculatorService"` Dodawanie punktu końcowego usługi jest opcjonalne, korzystając z programu .NET Framework 4.0 lub nowszy. W tych wersjach Jeśli punkty końcowe nie są dodawane w konfiguracji, lub kod WCF dodaje jeden domyślny punkt końcowy dla każdej kombinacji adresu podstawowego i kontraktu zaimplementowanych przez usługę. Aby uzyskać więcej informacji na temat domyślne punkty końcowe zobacz [Określanie adresu punktu końcowego](../../../docs/framework/wcf/specifying-an-endpoint-address.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)] domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
        > [!IMPORTANT]
        >  Dodawanie punktu końcowego usługi jest opcjonalne, korzystając z programu .NET Framework 4 lub nowszej. W tych wersjach Jeśli punkty końcowe nie są dodawane w konfiguracji, lub kod WCF dodaje jeden domyślny punkt końcowy dla każdej kombinacji adresu podstawowego i kontraktu zaimplementowanych przez usługę. Aby uzyskać więcej informacji na temat domyślne punkty końcowe zobacz [Określanie adresu punktu końcowego](../../../docs/framework/wcf/specifying-an-endpoint-address.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)] domyślne punkty końcowe, powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
    4.  Krok 4 — Włączanie wymiany metadanych. Klienci będą używać wymiany metadanych do generowania serwerów proxy, które będą używane do wywołania operacji usługi. Umożliwia tworzenie wymiany metadanych <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienia, ustaw go w <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwości `true`i Dodaj zachowanie w <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` Kolekcja <xref:System.ServiceModel.ServiceHost> wystąpienia.  
  
    5.  Krok 5 — Otwórz <xref:System.ServiceModel.ServiceHost> nasłuchiwanie dla komunikatów przychodzących. Wprowadź powiadomienia kod czeka na użytkownikowi trafień. Jeśli nie zrobisz, aplikacja zostanie natychmiast zamknięta i usługa zostanie zamknięta. Również ogłoszeniu bloku try/catch. Po <xref:System.ServiceModel.ServiceHost> został uruchomiony, inny kod znajduje się w bloku try/catch. Aby uzyskać więcej informacji na temat bezpiecznego przechwytywanie wyjątków zgłaszanych przez <xref:System.ServiceModel.ServiceHost>, zobacz [unikanie problemów z instrukcją Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)  
  
### <a name="to-verify-the-service-is-working"></a>Aby sprawdzić, czy usługa działa  
  
1.  Uruchom aplikację konsolową GettingStartedHost z wewnątrz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]. Podczas uruchamiania [!INCLUDE[wv](../../../includes/wv-md.md)] i nowszych systemów operacyjnych, usługi musi być uruchomiony z uprawnieniami administratora. Ponieważ program Visual Studio zostało uruchomione z uprawnieniami administratora, GettingStartedHost jest również uruchamiane z uprawnieniami administratora. Można również uruchomić wiersz polecenia uruchomiony z uprawnieniami administratora i uruchom service.exe znajdujące się w nim.  
  
2.  Otwórz program Internet Explorer i przejdź do debugowania usługi strony na `http://localhost:8000/GettingStarted/CalculatorService`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera kontrakt usługi i implementację z poprzednich kroków samouczka i hostuje usługę w aplikacji konsoli.  
  
 Aby skompilować to z wiersza polecenia kompilatora, kompilowanie IService1.cs i Service1.cs do biblioteki klasy odwołujące się do `System.ServiceModel.dll`. I skompiluj plik Program.cs aplikacji konsoli.  
  
```csharp
// IService1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
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
// Service1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
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
//Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
using GettingStartedLib;  
using System.ServiceModel.Description;   
  
namespace GettingStartedHost  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Uri baseAddress = new Uri("http://localhost:8000/ServiceModelSamples/Service");  
  
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
'IService1.vb  
Imports System  
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
'Service1.vb  
Imports System  
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
'Module1.vb  
Imports System  
Imports System.ServiceModel  
Imports System.ServiceModel.Description  
Imports GettingStartedLibVB.GettingStartedLib  
  
Module Service  
  
    Class Program  
        Shared Sub Main()  
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
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
>  Usługi, takie jak ta wymaga uprawnienia do rejestrowania adresów HTTP na komputerze w celu nasłuchiwania. To uprawnienie mają kont administratorów, ale konta bez uprawnień administratora musi mieć uprawnienie dla przestrzeni nazw protokołu HTTP. [!INCLUDE[crabout](../../../includes/crabout-md.md)] jak skonfigurować rezerwacji przestrzeni nazw, zobacz [Konfigurowanie protokołów HTTP i HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Podczas uruchamiania programu Visual Studio, service.exe musi zostać uruchomione z uprawnieniami administratora.  
  
 Obecnie usługa jest uruchomiona. Przejdź do [porady: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Aby uzyskać informacje dotyczące rozwiązywania problemów, zobacz [Rozwiązywanie problemów z Samouczek wprowadzający](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Host samodzielny](../../../docs/framework/wcf/samples/self-host.md)
