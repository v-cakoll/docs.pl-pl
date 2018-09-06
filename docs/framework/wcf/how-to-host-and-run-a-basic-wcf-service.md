---
title: 'Instrukcje: Hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: e2bf16bd07c7ac9d918a4ae95d7f4aa185d436ec
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741162"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>Instrukcje: Hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation
Jest to trzecia sześciu zadań podrzędnych, wymagane do utworzenia aplikacji Windows Communication Foundation (WCF). Omówienie wszystkich sześciu zadań, zobacz [Samouczek wprowadzający](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.  
  
 W tym temacie opisano, jak hostować usługi Windows Communication Foundation (WCF) w aplikacji konsoli. Ta procedura obejmuje następujące kroki:  
  
-   Utwórz projekt aplikacji konsoli do obsługi usługi.  
  
-   Utwórz hosta usługi dla usługi.  
  
-   Włącz wymiany metadanych.  
  
-   Otworzyć hosta usługi.  
  
 Pełną listę kod napisany w ramach tego zadania jest dostępna w przykładzie zamieszczonym po procedurze.  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a>Aby utworzyć nową aplikację konsoli do obsługi usługi  
  
1.  Utwórz nowy projekt aplikacji konsoli, klikając prawym przyciskiem myszy na wprowadzenie do rozwiązania, wybierając, **Dodaj**, **nowy projekt**. W **Dodaj nowy projekt** dialog w lewej części okna dialogowego wyboru **Windows** w obszarze **C#** lub **VB**. W górnej części okna dialogowego wybierz **aplikację Konsolową**. Nazwij projekt GettingStartedHost.  
  
2.  Ustaw docelową platformę projektu GettingStartedHost .NET Framework 4.5, klikając prawym przyciskiem myszy **GettingStartedHost** w Eksploratorze rozwiązań i wybierając polecenie **właściwości**. W polu listy rozwijanej etykietą **platformę docelową** wybierz **.NET Framework 4.5**. Platformę docelową dla projektu VB jest nieco inne w oknie dialogowym właściwości projektu GettingStartedHost kliknij opcję **skompilować** karcie po lewej stronie ekranu, a następnie kliknij przycisk **zaawansowane kompilacji Opcje** przycisk w lewym dolnym rogu okna dialogowego. Następnie wybierz pozycję **.NET Framework 4.5** w polu listy rozwijanej etykietą **platformę docelową**.  
  
     Platforma docelowa spowoduje, że ustawienie [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ponowne załadowanie rozwiązania, naciśnij klawisz **OK** po wyświetleniu monitu.  
  
3.  Dodaj odwołanie do projektu GettingStartedLib do projektu GettingStartedHost przez kliknięcie prawym przyciskiem myszy **odwołania** folderu w projekcie GettingStartedHost w Eksploratorze rozwiązań i wybierz pozycję **Dodaj odwołanie** . W **Dodaj odwołanie** okno dialogowe, wybierz opcję **rozwiązania** w lewej części okna dialogowego i wybierz GettingStartedLib w sekcji Centrum okno dialogowe i kliknij przycisk **Dodaj**. To sprawia, że typy zdefiniowane w GettingStartedLib GettingStartedHost projektowi.  
  
4.  Dodaj odwołanie do System.ServiceModel do projektu GettingStartedHost, klikając prawym przyciskiem myszy **odwołania** folderu w projekcie GettingStartedHost w Eksploratorze rozwiązań i wybierz pozycję **Dodaj** Odwołanie. W **Dodaj odwołanie** okna dialogowego wybierz **Framework** po lewej stronie okna dialogowego. W polu tekstowym wyszukiwania zestawów, wpisz `System.ServiceModel`. W górnej części okna dialogowego wybierz **System.ServiceModel**, kliknij przycisk **Dodaj** przycisk, a następnie kliknij przycisk **Zamknij** przycisku. Zapisz rozwiązania, klikając przycisk Zapisz wszystko pod menu głównego.  
  
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
  
    1.  Krok 1 — tworzy wystąpienie klasy Uri do przechowywania adres podstawowy usługi. Usługi są identyfikowane przez adres URL, który zawiera adres podstawowy i opcjonalnie identyfikatora URI. Adres podstawowy jest sformatowany w następujący sposób: [transportu] :// [nazwa komputera lub domeny] [: opcjonalne # portu] / [opcjonalne segmentem identyfikatora URI] adres podstawowy usługi Kalkulator używa protokołu HTTP, localhost, port 8000 i identyfikator URI segmentu "GettingStarted"  
  
    2.  Krok 2 — tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> klasy do obsługi usługi. Konstruktor przyjmuje dwa parametry typu klasy, który implementuje ten kontrakt usługi i podstawowego adresu usługi.  
  
    3.  Krok 3 — tworzy <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienia. Punkt końcowy usługi składa się z adresu, powiązanie i kontraktu usługi. <xref:System.ServiceModel.Description.ServiceEndpoint> Konstruktor przyjmuje w związku z tym typem interfejsu kontraktu usługi, powiązanie i adres. Umowa serwisowa jest `ICalculator`, zdefiniowane przez użytkownika, która implementuje typu usługi. Wiązanie używane w tym przykładzie jest <xref:System.ServiceModel.WSHttpBinding> czyli wbudowane powiązania, które służy do nawiązywania połączenia z punktami końcowymi, które odpowiadają WS-* specyfikacji. Aby uzyskać więcej informacji na temat wiązania WCF, zobacz [omówienie powiązań WCF](../../../docs/framework/wcf/bindings-overview.md). Adres jest dołączany do podstawowego adresu do identyfikowania punktu końcowego. Adres podany w tym kodzie jest "CalculatorService", dlatego jest w pełni kwalifikowany adres punktu końcowego `"http://localhost:8000/GettingStarted/CalculatorService"`.  
  
        > [!IMPORTANT]
        >  Dodawanie punktu końcowego usługi jest opcjonalny podczas korzystania z programu .NET Framework 4 lub nowszej. W tych wersjach Jeśli punkty końcowe nie są dodawane w kodzie lub konfiguracji usługi WCF dodaje jeden domyślny punkt końcowy dla każdej kombinacji adresu podstawowego i kontrakt implementowane przez usługę. Aby uzyskać więcej informacji na temat domyślne punkty końcowe zobacz [Określanie adresu punktu końcowego](../../../docs/framework/wcf/specifying-an-endpoint-address.md). Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
    4.  Krok 4 — Włączanie wymiany metadanych. Klienci będą używać wymiany metadanych do Generowanie serwerów proxy, które będą używane do wywoływania operacji usługi. Umożliwia tworzenie wymiany metadanych <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienia, należy ustawić go w <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwości `true`i dodać zachowanie, aby <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` zbiór <xref:System.ServiceModel.ServiceHost> wystąpienia.  
  
    5.  Krok 5 — Open <xref:System.ServiceModel.ServiceHost> do nasłuchiwania pod kątem przychodzących wiadomości. Zauważ, że kod oczekuje na użytkownika trafić wprowadzić. Jeśli nie tego zrobić, aplikacja zostanie natychmiast zamknięta i usługa zostanie zamknięta. Zwróć również uwagę bloku try/catch używane. Po <xref:System.ServiceModel.ServiceHost> został uruchomiony, inny kod znajduje się w bloku try/catch. Aby uzyskać więcej informacji na temat bezpiecznego przechwytywanie wyjątków zgłaszanych przez <xref:System.ServiceModel.ServiceHost>, zobacz [unikanie problemów z instrukcją Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)  
  
> [!IMPORTANT]
> Edytowanie pliku App.config w GettingStartedLib w celu odzwierciedlenia zmian w kodzie: 
> 1. Zmień wiersz 14 `<service name="GettingStartedLib.CalculatorService">`
> 2. Zmień wiersz 17 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
> 3. Zmień wiersz 22 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`
        
### <a name="to-verify-the-service-is-working"></a>Aby sprawdzić, czy usługa działa  
  
1.  Uruchom aplikację konsolową GettingStartedHost z wewnątrz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]. Podczas uruchamiania na [!INCLUDE[wv](../../../includes/wv-md.md)] i nowszych systemów operacyjnych, usługa musi być uruchomiony z uprawnieniami administratora. Ponieważ program Visual Studio zostało uruchomione z uprawnieniami administratora, GettingStartedHost również jest uruchamiane z uprawnieniami administratora. Można również rozpocząć nowy wiersz polecenia, w których jest on uruchomiony z uprawnieniami administratora i uruchom service.exe znajdujący się w nim.  
  
2.  Otwórz program Internet Explorer i przejdź do usługi debugowania strony na `http://localhost:8000/GettingStarted/CalculatorService`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zawiera kontrakt usługi i implementację z poprzednich kroków samouczka i hostuje usługę w aplikacji konsoli.  
  
 Aby skompilować to za pomocą kompilatora wiersza polecenia, skompilować IService1.cs i Service1.cs do biblioteki klas odwołuje się do `System.ServiceModel.dll`. I skompiluj plik Program.cs aplikacji konsoli.  
  
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
>  Usługi, takie jak tego wymaga uprawnienia do rejestrowania adresy HTTP na komputerze w celu nasłuchiwania. Administrator konta mają to uprawnienie, ale konta bez uprawnień administratora musi mieć uprawnienie dla przestrzeni nazw protokołu HTTP. Aby uzyskać więcej informacji o sposobie konfigurowania rezerwacji przestrzeni nazw, zobacz [Konfigurowanie protokołów HTTP i HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Podczas uruchamiania w programie Visual Studio, service.exe muszą być uruchomione z uprawnieniami administratora.  
  
 Teraz usługa jest uruchomiona. Przejdź do [porady: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md). Aby uzyskać informacje dotyczące rozwiązywania problemów, zobacz [Rozwiązywanie problemów z samouczka Wprowadzenie](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [Host samodzielny](../../../docs/framework/wcf/samples/self-host.md)
