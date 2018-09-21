---
title: 'Instrukcje: Hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: b79c3246b7c12a3a99a5c68586387fc30573dcb6
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46481926"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="f3fd1-102">Instrukcje: Hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f3fd1-102">How to: Host and Run a Basic Windows Communication Foundation Service</span></span>

<span data-ttu-id="f3fd1-103">Jest to trzecia sześciu zadań podrzędnych, wymagane do utworzenia aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f3fd1-103">This is the third of six tasks required to create a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="f3fd1-104">Omówienie wszystkich sześciu zadań, zobacz [Samouczek wprowadzający](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="f3fd1-105">W tym temacie opisano, jak hostować usługi Windows Communication Foundation (WCF) w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-105">This topic describes how to host a Windows Communication Foundation (WCF) service in a console application.</span></span> <span data-ttu-id="f3fd1-106">Ta procedura obejmuje następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="f3fd1-106">This procedure consists of the following steps:</span></span>

- <span data-ttu-id="f3fd1-107">Utwórz projekt aplikacji konsoli do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-107">Create a console application project to host the service.</span></span>

- <span data-ttu-id="f3fd1-108">Utwórz hosta usługi dla usługi.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-108">Create a service host for the service.</span></span>

- <span data-ttu-id="f3fd1-109">Włącz wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-109">Enable metadata exchange.</span></span>

- <span data-ttu-id="f3fd1-110">Otworzyć hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-110">Open the service host.</span></span>

<span data-ttu-id="f3fd1-111">Pełną listę kod napisany w ramach tego zadania jest dostępna w przykładzie zamieszczonym po procedurze.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-111">A complete listing of the code written in this task is provided in the example following the procedure.</span></span>

## <a name="create-a-new-console-application-to-host-the-service"></a><span data-ttu-id="f3fd1-112">Utwórz nową aplikację konsoli do obsługi usługi</span><span class="sxs-lookup"><span data-stu-id="f3fd1-112">Create a new console application to host the service</span></span>

1. <span data-ttu-id="f3fd1-113">Utwórz nowy projekt aplikacji konsoli w programie Visual Studio, klikając prawym przyciskiem myszy na wprowadzenie do rozwiązań i wybierając **Dodaj** > **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-113">Create a new Console Application project in Visual Studio by right-clicking on the Getting Started solution and selecting **Add** > **New Project**.</span></span> <span data-ttu-id="f3fd1-114">W **Dodaj nowy projekt** okna dialogowego po lewej stronie wybierz **pulpitu Windows** kategorię w obszarze **Visual C#** lub **języka Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-114">In the **Add New Project** dialog, on the left-hand side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> <span data-ttu-id="f3fd1-115">Wybierz **Aplikacja konsoli (.NET Framework)** szablonu, a następnie nazwę projektu **GettingStartedHost**.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-115">Select the **Console App (.NET Framework)** template, and then name the project **GettingStartedHost**.</span></span>

2. <span data-ttu-id="f3fd1-116">Dodaj odwołanie do projektu GettingStartedLib do projektu GettingStartedHost.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-116">Add a reference to the GettingStartedLib project to the GettingStartedHost project.</span></span> <span data-ttu-id="f3fd1-117">Kliknij prawym przyciskiem myszy **odwołania** folderu w projekcie GettingStartedHost w **Eksploratora rozwiązań**, a następnie wybierz pozycję **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-117">Right-click on the **References** folder under the GettingStartedHost project in **Solution Explorer**, and then select **Add Reference**.</span></span> <span data-ttu-id="f3fd1-118">W **Dodaj odwołanie** okno dialogowe, wybierz opcję **rozwiązania** w lewej części okna dialogowego Wybierz GettingStartedLib w górnej części okna dialogowego, a następnie wybierz **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-118">In the **Add Reference** dialog, select **Solution** on the left-hand side of the dialog, select GettingStartedLib in the center section of the dialog, and then choose **Add**.</span></span> <span data-ttu-id="f3fd1-119">To sprawia, że typy zdefiniowane w GettingStartedLib GettingStartedHost projektowi.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-119">This makes the types defined in GettingStartedLib available to the GettingStartedHost project.</span></span>

3. <span data-ttu-id="f3fd1-120">Dodaj odwołanie do System.ServiceModel do projektu GettingStartedHost.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-120">Add a reference to System.ServiceModel to the GettingStartedHost project.</span></span> <span data-ttu-id="f3fd1-121">Kliknij prawym przyciskiem myszy **odwołania** folderu w projekcie GettingStartedHost w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-121">Right-click the **References** folder under the GettingStartedHost project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="f3fd1-122">W **Dodaj odwołanie** okno dialogowe, wybierz opcję **Framework** po lewej stronie okna dialogowego, w obszarze **zestawy**.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-122">In the **Add Reference** dialog, select **Framework** on the left-hand side of the dialog under **Assemblies**.</span></span> <span data-ttu-id="f3fd1-123">Znajdź i zaznacz **System.ServiceModel**, a następnie wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-123">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> <span data-ttu-id="f3fd1-124">Zapisz rozwiązanie, wybierając **pliku** > **Zapisz wszystko**.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-124">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="host-the-service"></a><span data-ttu-id="f3fd1-125">Host usługi</span><span class="sxs-lookup"><span data-stu-id="f3fd1-125">Host the service</span></span>

<span data-ttu-id="f3fd1-126">Otwórz plik Program.cs lub Module.vb i wprowadź następujący kod:</span><span class="sxs-lookup"><span data-stu-id="f3fd1-126">Open the Program.cs or Module.vb file and enter the following code:</span></span>

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

<span data-ttu-id="f3fd1-127">**Krok 1** — tworzy wystąpienie klasy Uri do przechowywania adres podstawowy usługi.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-127">**Step 1** - Creates an instance of the Uri class to hold the base address of the service.</span></span> <span data-ttu-id="f3fd1-128">Usługi są identyfikowane przez adres URL, który zawiera adres podstawowy i opcjonalnie identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-128">Services are identified by a URL which contains a base address and an optional URI.</span></span> <span data-ttu-id="f3fd1-129">Adres podstawowy jest sformatowany w następujący sposób: [transportu] :// [nazwa komputera lub domeny] [: opcjonalne # portu] / [opcjonalne segmentem identyfikatora URI] adres podstawowy usługi Kalkulator używa protokołu HTTP, localhost, port 8000 i identyfikator URI segmentu "GettingStarted"</span><span class="sxs-lookup"><span data-stu-id="f3fd1-129">The base address is formatted as follows:[transport]://[machine-name or domain][:optional port #]/[optional URI segment]The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment "GettingStarted"</span></span>

<span data-ttu-id="f3fd1-130">**Krok 2** — tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> klasy do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-130">**Step 2** – Creates an instance of the <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="f3fd1-131">Konstruktor przyjmuje dwa parametry typu klasy, który implementuje ten kontrakt usługi i podstawowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-131">The constructor takes two parameters, the type of the class that implements the service contract, and the base address of the service.</span></span>

<span data-ttu-id="f3fd1-132">**Krok 3** — tworzy <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-132">**Step 3** – Creates a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="f3fd1-133">Punkt końcowy usługi składa się z adresu, powiązanie i kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-133">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="f3fd1-134"><xref:System.ServiceModel.Description.ServiceEndpoint> Konstruktor przyjmuje w związku z tym typem interfejsu kontraktu usługi, powiązanie i adres.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-134">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor therefore takes the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="f3fd1-135">Umowa serwisowa jest `ICalculator`, zdefiniowane przez użytkownika, która implementuje typu usługi.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-135">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="f3fd1-136">Wiązanie używane w tym przykładzie jest <xref:System.ServiceModel.WSHttpBinding> czyli wbudowane powiązania, które służy do nawiązywania połączenia z punktami końcowymi, które odpowiadają WS-\* specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-136">The binding used in this sample is <xref:System.ServiceModel.WSHttpBinding> which is a built-in binding that is used for connecting to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="f3fd1-137">Aby uzyskać więcej informacji na temat wiązania WCF, zobacz [omówienie powiązań WCF](../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f3fd1-137">For more information about WCF bindings, see [WCF Bindings Overview](../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="f3fd1-138">Adres jest dołączany do podstawowego adresu do identyfikowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-138">The address is appended to the base address to identify the endpoint.</span></span> <span data-ttu-id="f3fd1-139">Adres podany w tym kodzie jest "CalculatorService", dlatego jest w pełni kwalifikowany adres punktu końcowego `"http://localhost:8000/GettingStarted/CalculatorService"`.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-139">The address specified in this code is "CalculatorService" so the fully qualified address for the endpoint is `"http://localhost:8000/GettingStarted/CalculatorService"`.</span></span>

    > [!IMPORTANT]
    > Adding a service endpoint is optional when using .NET Framework 4 or later. In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service. For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md). For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

<span data-ttu-id="f3fd1-140">**Krok 4** — Włączanie wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-140">**Step 4** – Enable metadata exchange.</span></span> <span data-ttu-id="f3fd1-141">Klienci będą używać wymiany metadanych do Generowanie serwerów proxy, które będą używane do wywoływania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-141">Clients will use metadata exchange to generate proxies that will be used to call the service operations.</span></span> <span data-ttu-id="f3fd1-142">Umożliwia tworzenie wymiany metadanych <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienia, należy ustawić go w <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwości `true`i dodać zachowanie, aby <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` zbiór <xref:System.ServiceModel.ServiceHost> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-142">To enable metadata exchange create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set it’s <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, and add the behavior to the <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

<span data-ttu-id="f3fd1-143">**Krok 5** — Otwórz <xref:System.ServiceModel.ServiceHost> do nasłuchiwania pod kątem przychodzących wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-143">**Step 5** – Open the <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="f3fd1-144">Zauważ, że kod oczekuje na użytkownika trafić wprowadzić.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-144">Notice the code waits for the user to hit enter.</span></span> <span data-ttu-id="f3fd1-145">Jeśli nie tego zrobić, aplikacja zostanie natychmiast zamknięta i usługa zostanie zamknięta. Zwróć również uwagę bloku try/catch używane.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-145">If you do not do this, the app will close immediately and the service will shut down.Also notice a  try/catch block used.</span></span> <span data-ttu-id="f3fd1-146">Po <xref:System.ServiceModel.ServiceHost> został uruchomiony, inny kod znajduje się w bloku try/catch.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-146">After the <xref:System.ServiceModel.ServiceHost> has been instantiated, all other code is placed in a try/catch block.</span></span> <span data-ttu-id="f3fd1-147">Aby uzyskać więcej informacji na temat bezpiecznego przechwytywanie wyjątków zgłaszanych przez <xref:System.ServiceModel.ServiceHost>, zobacz [unikanie problemów z instrukcją Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="f3fd1-147">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f3fd1-148">Edytowanie pliku App.config w GettingStartedLib w celu odzwierciedlenia zmian w kodzie:</span><span class="sxs-lookup"><span data-stu-id="f3fd1-148">Edit App.config in GettingStartedLib to reflect the changes made in code:</span></span>
> 1. <span data-ttu-id="f3fd1-149">Zmień wiersz 14 `<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="f3fd1-149">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
> 2. <span data-ttu-id="f3fd1-150">Zmień wiersz 17 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="f3fd1-150">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
> 3. <span data-ttu-id="f3fd1-151">Zmień wiersz 22 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="f3fd1-151">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="f3fd1-152">Sprawdź, czy usługa działa</span><span class="sxs-lookup"><span data-stu-id="f3fd1-152">Verify the service is working</span></span>

1. <span data-ttu-id="f3fd1-153">Uruchom konsolę GettingStartedHost aplikacji z poziomu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-153">Run the GettingStartedHost console application from inside Visual Studio.</span></span>

   <span data-ttu-id="f3fd1-154">Usługa musi być uruchamiane z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-154">The service must be run with administrator privileges.</span></span> <span data-ttu-id="f3fd1-155">Ponieważ program Visual Studio została otwarta z uprawnieniami administratora, GettingStartedHost również jest uruchamiane z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-155">Because Visual Studio was opened with administrator privileges, GettingStartedHost is also run with administrator privileges.</span></span> <span data-ttu-id="f3fd1-156">Możesz również otworzyć nowego przy użyciu wiersza polecenia **Uruchom jako administrator** i uruchom service.exe znajdujący się w nim.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-156">You can also open a new command prompt using **Run as administrator** and run service.exe within it.</span></span>

2. <span data-ttu-id="f3fd1-157">Otwórz przeglądarkę internetową i przejdź do strony debugowania usługi na `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-157">Open a web browser and browse to the service's debug page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

## <a name="example"></a><span data-ttu-id="f3fd1-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3fd1-158">Example</span></span>

<span data-ttu-id="f3fd1-159">Poniższy przykład zawiera kontrakt usługi i implementację z poprzednich kroków samouczka i hostuje usługę w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-159">The following example includes the service contract and implementation from previous steps in the tutorial and hosts the service in a console application.</span></span>

<span data-ttu-id="f3fd1-160">Aby skompilować to za pomocą kompilatora wiersza polecenia, należy skompilować do biblioteki klas, który odwołuje się do IService1.cs i Service1.cs `System.ServiceModel.dll`.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-160">To compile this with a command-line compiler, compile IService1.cs and Service1.cs into a class library that references `System.ServiceModel.dll`.</span></span> <span data-ttu-id="f3fd1-161">Kompiluj plik Program.cs jako aplikację konsolową w języku.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-161">Compile Program.cs as a console application.</span></span>

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
> <span data-ttu-id="f3fd1-162">Usługi, takie jak tego wymaga uprawnienia do rejestrowania adresy HTTP na komputerze w celu nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-162">Services such as this one require permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="f3fd1-163">Administrator konta mają to uprawnienie, ale konta bez uprawnień administratora musi mieć uprawnienie dla przestrzeni nazw protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-163">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="f3fd1-164">Aby uzyskać więcej informacji o sposobie konfigurowania rezerwacji przestrzeni nazw, zobacz [Konfigurowanie protokołów HTTP i HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="f3fd1-164">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="f3fd1-165">Podczas uruchamiania w programie Visual Studio, service.exe muszą być uruchomione z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-165">When running under Visual Studio, the service.exe must be run with administrator privileges.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f3fd1-166">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="f3fd1-166">Next steps</span></span>

<span data-ttu-id="f3fd1-167">Teraz usługa jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-167">Now the service is running.</span></span> <span data-ttu-id="f3fd1-168">Następne zadanie tworzenia klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="f3fd1-168">In the next task, you create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f3fd1-169">Porady: Tworzenie klienta WCF</span><span class="sxs-lookup"><span data-stu-id="f3fd1-169">How to: Create a WCF client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)

<span data-ttu-id="f3fd1-170">Aby uzyskać informacje dotyczące rozwiązywania problemów, zobacz [Rozwiązywanie problemów z samouczka Wprowadzenie](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f3fd1-170">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3fd1-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3fd1-171">See also</span></span>

- [<span data-ttu-id="f3fd1-172">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f3fd1-172">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="f3fd1-173">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="f3fd1-173">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)