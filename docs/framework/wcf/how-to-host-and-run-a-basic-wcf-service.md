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
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404674"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="abf3d-102">Instrukcje: Hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="abf3d-102">How to: Host and Run a Basic Windows Communication Foundation Service</span></span>
<span data-ttu-id="abf3d-103">Jest to trzecia sześciu zadań podrzędnych, wymagane do utworzenia aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="abf3d-103">This is the third of six tasks required to create a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="abf3d-104">Omówienie wszystkich sześciu zadań, zobacz [Samouczek wprowadzający](../../../docs/framework/wcf/getting-started-tutorial.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="abf3d-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="abf3d-105">W tym temacie opisano, jak hostować usługi Windows Communication Foundation (WCF) w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="abf3d-105">This topic describes how to host a Windows Communication Foundation (WCF) service in a console application.</span></span> <span data-ttu-id="abf3d-106">Ta procedura obejmuje następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="abf3d-106">This procedure consists of the following steps:</span></span>  
  
-   <span data-ttu-id="abf3d-107">Utwórz projekt aplikacji konsoli do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="abf3d-107">Create a console application project to host the service.</span></span>  
  
-   <span data-ttu-id="abf3d-108">Utwórz hosta usługi dla usługi.</span><span class="sxs-lookup"><span data-stu-id="abf3d-108">Create a service host for the service.</span></span>  
  
-   <span data-ttu-id="abf3d-109">Włącz wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="abf3d-109">Enable metadata exchange.</span></span>  
  
-   <span data-ttu-id="abf3d-110">Otworzyć hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="abf3d-110">Open the service host.</span></span>  
  
 <span data-ttu-id="abf3d-111">Pełną listę kod napisany w ramach tego zadania jest dostępna w przykładzie zamieszczonym po procedurze.</span><span class="sxs-lookup"><span data-stu-id="abf3d-111">A complete listing of the code written in this task is provided in the example following the procedure.</span></span>  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a><span data-ttu-id="abf3d-112">Aby utworzyć nową aplikację konsoli do obsługi usługi</span><span class="sxs-lookup"><span data-stu-id="abf3d-112">To create a new console application to host the service</span></span>  
  
1.  <span data-ttu-id="abf3d-113">Utwórz nowy projekt aplikacji konsoli, klikając prawym przyciskiem myszy na wprowadzenie do rozwiązania, wybierając, **Dodaj**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="abf3d-113">Create a new Console Application project by right-clicking on the Getting Started solution, selecting, **Add**, **New Project**.</span></span> <span data-ttu-id="abf3d-114">W **Dodaj nowy projekt** dialog w lewej części okna dialogowego wyboru **Windows** w obszarze **C#** lub **VB**.</span><span class="sxs-lookup"><span data-stu-id="abf3d-114">In the **Add New Project** dialog on the left hand side of the dialog select **Windows** under **C#** or **VB**.</span></span> <span data-ttu-id="abf3d-115">W górnej części okna dialogowego wybierz **aplikację Konsolową**.</span><span class="sxs-lookup"><span data-stu-id="abf3d-115">In the center section of the dialog select **Console Application**.</span></span> <span data-ttu-id="abf3d-116">Nazwij projekt GettingStartedHost.</span><span class="sxs-lookup"><span data-stu-id="abf3d-116">Name the project GettingStartedHost.</span></span>  
  
2.  <span data-ttu-id="abf3d-117">Ustaw docelową platformę projektu GettingStartedHost .NET Framework 4.5, klikając prawym przyciskiem myszy **GettingStartedHost** w Eksploratorze rozwiązań i wybierając polecenie **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="abf3d-117">Set the target framework of the GettingStartedHost project to .NET Framework 4.5 by right clicking on **GettingStartedHost** in the Solution Explorer and selecting **Properties**.</span></span> <span data-ttu-id="abf3d-118">W polu listy rozwijanej etykietą **platformę docelową** wybierz **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="abf3d-118">In the dropdown box labeled **Target Framework** select **.NET Framework 4.5**.</span></span> <span data-ttu-id="abf3d-119">Platformę docelową dla projektu VB jest nieco inne w oknie dialogowym właściwości projektu GettingStartedHost kliknij opcję **skompilować** karcie po lewej stronie ekranu, a następnie kliknij przycisk **zaawansowane kompilacji Opcje** przycisk w lewym dolnym rogu okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="abf3d-119">Setting the target framework for a VB project is a little different, in the GettingStartedHost project properties dialog, click the **Compile** tab on the left-hand side of the screen, and then click the **Advanced Compile Options** button at the lower left-hand corner of the dialog.</span></span> <span data-ttu-id="abf3d-120">Następnie wybierz pozycję **.NET Framework 4.5** w polu listy rozwijanej etykietą **platformę docelową**.</span><span class="sxs-lookup"><span data-stu-id="abf3d-120">Then select **.NET Framework 4.5** in the dropdown box labeled **Target Framework**.</span></span>  
  
     <span data-ttu-id="abf3d-121">Platforma docelowa spowoduje, że ustawienie [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ponowne załadowanie rozwiązania, naciśnij klawisz **OK** po wyświetleniu monitu.</span><span class="sxs-lookup"><span data-stu-id="abf3d-121">Setting the target framework will cause [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] to reload the solution, press **OK** when prompted.</span></span>  
  
3.  <span data-ttu-id="abf3d-122">Dodaj odwołanie do projektu GettingStartedLib do projektu GettingStartedHost przez kliknięcie prawym przyciskiem myszy **odwołania** folderu w projekcie GettingStartedHost w Eksploratorze rozwiązań i wybierz pozycję **Dodaj odwołanie** .</span><span class="sxs-lookup"><span data-stu-id="abf3d-122">Add a reference to the GettingStartedLib project to the GettingStartedHost project by right clicking on the **References** folder under the GettingStartedHost project in the solution explorer and select **Add Reference**.</span></span> <span data-ttu-id="abf3d-123">W **Dodaj odwołanie** okno dialogowe, wybierz opcję **rozwiązania** w lewej części okna dialogowego i wybierz GettingStartedLib w sekcji Centrum okno dialogowe i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="abf3d-123">In the **Add Reference** dialog, select **Solution** on the left-hand side of the dialog and select GettingStartedLib in the center section of the dialog and click **Add**.</span></span> <span data-ttu-id="abf3d-124">To sprawia, że typy zdefiniowane w GettingStartedLib GettingStartedHost projektowi.</span><span class="sxs-lookup"><span data-stu-id="abf3d-124">This makes the types defined in GettingStartedLib available to the GettingStartedHost project.</span></span>  
  
4.  <span data-ttu-id="abf3d-125">Dodaj odwołanie do System.ServiceModel do projektu GettingStartedHost, klikając prawym przyciskiem myszy **odwołania** folderu w projekcie GettingStartedHost w Eksploratorze rozwiązań i wybierz pozycję **Dodaj** Odwołanie.</span><span class="sxs-lookup"><span data-stu-id="abf3d-125">Add a reference to System.ServiceModel to the GettingStartedHost project by right-clicking the **Reference** folder under the GettingStartedHost project in Solution Explorer and select **Add** Reference.</span></span> <span data-ttu-id="abf3d-126">W **Dodaj odwołanie** okna dialogowego wybierz **Framework** po lewej stronie okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="abf3d-126">In the **Add Reference** dialog select **Framework** on the left-hand side of the dialog.</span></span> <span data-ttu-id="abf3d-127">W polu tekstowym wyszukiwania zestawów, wpisz `System.ServiceModel`.</span><span class="sxs-lookup"><span data-stu-id="abf3d-127">In the Search Assemblies textbox, type in `System.ServiceModel`.</span></span> <span data-ttu-id="abf3d-128">W górnej części okna dialogowego wybierz **System.ServiceModel**, kliknij przycisk **Dodaj** przycisk, a następnie kliknij przycisk **Zamknij** przycisku.</span><span class="sxs-lookup"><span data-stu-id="abf3d-128">In the center section of the dialog select **System.ServiceModel**, click the **Add** button, and click the **Close** button.</span></span> <span data-ttu-id="abf3d-129">Zapisz rozwiązania, klikając przycisk Zapisz wszystko pod menu głównego.</span><span class="sxs-lookup"><span data-stu-id="abf3d-129">Save the solution by clicking the Save All button below the main menu.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="abf3d-130">Do obsługi usługi</span><span class="sxs-lookup"><span data-stu-id="abf3d-130">To host the service</span></span>  
  
-   <span data-ttu-id="abf3d-131">Otwórz plik Program.cs lub Module.vb i wprowadź następujący kod:</span><span class="sxs-lookup"><span data-stu-id="abf3d-131">Open the Program.cs or Module.vb file and enter the following code:</span></span>  
  
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
  
    1.  <span data-ttu-id="abf3d-132">Krok 1 — tworzy wystąpienie klasy Uri do przechowywania adres podstawowy usługi.</span><span class="sxs-lookup"><span data-stu-id="abf3d-132">Step 1 - Creates an instance of the Uri class to hold the base address of the service.</span></span> <span data-ttu-id="abf3d-133">Usługi są identyfikowane przez adres URL, który zawiera adres podstawowy i opcjonalnie identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="abf3d-133">Services are identified by a URL which contains a base address and an optional URI.</span></span> <span data-ttu-id="abf3d-134">Adres podstawowy jest sformatowany w następujący sposób: [transportu] :// [nazwa komputera lub domeny] [: opcjonalne # portu] / [opcjonalne segmentem identyfikatora URI] adres podstawowy usługi Kalkulator używa protokołu HTTP, localhost, port 8000 i identyfikator URI segmentu "GettingStarted"</span><span class="sxs-lookup"><span data-stu-id="abf3d-134">The base address is formatted as follows:[transport]://[machine-name or domain][:optional port #]/[optional URI segment]The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment "GettingStarted"</span></span>  
  
    2.  <span data-ttu-id="abf3d-135">Krok 2 — tworzy wystąpienie <xref:System.ServiceModel.ServiceHost> klasy do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="abf3d-135">Step 2 – Creates an instance of the <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="abf3d-136">Konstruktor przyjmuje dwa parametry typu klasy, który implementuje ten kontrakt usługi i podstawowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="abf3d-136">The constructor takes two parameters, the type of the class that implements the service contract, and the base address of the service.</span></span>  
  
    3.  <span data-ttu-id="abf3d-137">Krok 3 — tworzy <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="abf3d-137">Step 3 – Creates a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="abf3d-138">Punkt końcowy usługi składa się z adresu, powiązanie i kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="abf3d-138">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="abf3d-139"><xref:System.ServiceModel.Description.ServiceEndpoint> Konstruktor przyjmuje w związku z tym typem interfejsu kontraktu usługi, powiązanie i adres.</span><span class="sxs-lookup"><span data-stu-id="abf3d-139">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor therefore takes the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="abf3d-140">Umowa serwisowa jest `ICalculator`, zdefiniowane przez użytkownika, która implementuje typu usługi.</span><span class="sxs-lookup"><span data-stu-id="abf3d-140">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="abf3d-141">Wiązanie używane w tym przykładzie jest <xref:System.ServiceModel.WSHttpBinding> czyli wbudowane powiązania, które służy do nawiązywania połączenia z punktami końcowymi, które odpowiadają WS-\* specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="abf3d-141">The binding used in this sample is <xref:System.ServiceModel.WSHttpBinding> which is a built-in binding that is used for connecting to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="abf3d-142">Aby uzyskać więcej informacji na temat wiązania WCF, zobacz [omówienie powiązań WCF](../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="abf3d-142">For more information about WCF bindings, see [WCF Bindings Overview](../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="abf3d-143">Adres jest dołączany do podstawowego adresu do identyfikowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="abf3d-143">The address is appended to the base address to identify the endpoint.</span></span> <span data-ttu-id="abf3d-144">Adres podany w tym kodzie jest "CalculatorService", dlatego jest w pełni kwalifikowany adres punktu końcowego `"http://localhost:8000/GettingStarted/CalculatorService"`.</span><span class="sxs-lookup"><span data-stu-id="abf3d-144">The address specified in this code is "CalculatorService" so the fully qualified address for the endpoint is `"http://localhost:8000/GettingStarted/CalculatorService"`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="abf3d-145">Dodawanie punktu końcowego usługi jest opcjonalny podczas korzystania z programu .NET Framework 4 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="abf3d-145">Adding a service endpoint is optional when using .NET Framework 4 or later.</span></span> <span data-ttu-id="abf3d-146">W tych wersjach Jeśli punkty końcowe nie są dodawane w kodzie lub konfiguracji usługi WCF dodaje jeden domyślny punkt końcowy dla każdej kombinacji adresu podstawowego i kontrakt implementowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="abf3d-146">In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="abf3d-147">Aby uzyskać więcej informacji na temat domyślne punkty końcowe zobacz [Określanie adresu punktu końcowego](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="abf3d-147">For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="abf3d-148">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [uproszczona konfiguracja](../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="abf3d-148">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
    4.  <span data-ttu-id="abf3d-149">Krok 4 — Włączanie wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="abf3d-149">Step 4 – Enable metadata exchange.</span></span> <span data-ttu-id="abf3d-150">Klienci będą używać wymiany metadanych do Generowanie serwerów proxy, które będą używane do wywoływania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="abf3d-150">Clients will use metadata exchange to generate proxies that will be used to call the service operations.</span></span> <span data-ttu-id="abf3d-151">Umożliwia tworzenie wymiany metadanych <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienia, należy ustawić go w <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwości `true`i dodać zachowanie, aby <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` zbiór <xref:System.ServiceModel.ServiceHost> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="abf3d-151">To enable metadata exchange create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set it’s <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, and add the behavior to the <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>  
  
    5.  <span data-ttu-id="abf3d-152">Krok 5 — Open <xref:System.ServiceModel.ServiceHost> do nasłuchiwania pod kątem przychodzących wiadomości.</span><span class="sxs-lookup"><span data-stu-id="abf3d-152">Step 5 – Open the <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="abf3d-153">Zauważ, że kod oczekuje na użytkownika trafić wprowadzić.</span><span class="sxs-lookup"><span data-stu-id="abf3d-153">Notice the code waits for the user to hit enter.</span></span> <span data-ttu-id="abf3d-154">Jeśli nie tego zrobić, aplikacja zostanie natychmiast zamknięta i usługa zostanie zamknięta. Zwróć również uwagę bloku try/catch używane.</span><span class="sxs-lookup"><span data-stu-id="abf3d-154">If you do not do this, the app will close immediately and the service will shut down.Also notice a  try/catch block used.</span></span> <span data-ttu-id="abf3d-155">Po <xref:System.ServiceModel.ServiceHost> został uruchomiony, inny kod znajduje się w bloku try/catch.</span><span class="sxs-lookup"><span data-stu-id="abf3d-155">After the <xref:System.ServiceModel.ServiceHost> has been instantiated, all other code is placed in a try/catch block.</span></span> <span data-ttu-id="abf3d-156">Aby uzyskać więcej informacji na temat bezpiecznego przechwytywanie wyjątków zgłaszanych przez <xref:System.ServiceModel.ServiceHost>, zobacz [unikanie problemów z instrukcją Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="abf3d-156">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="abf3d-157">Edytowanie pliku App.config w GettingStartedLib w celu odzwierciedlenia zmian w kodzie:</span><span class="sxs-lookup"><span data-stu-id="abf3d-157">Edit App.config in GettingStartedLib to reflect the changes made in code:</span></span> 
> 1. <span data-ttu-id="abf3d-158">Zmień wiersz 14 `<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="abf3d-158">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
> 2. <span data-ttu-id="abf3d-159">Zmień wiersz 17 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="abf3d-159">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
> 3. <span data-ttu-id="abf3d-160">Zmień wiersz 22 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="abf3d-160">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>
        
### <a name="to-verify-the-service-is-working"></a><span data-ttu-id="abf3d-161">Aby sprawdzić, czy usługa działa</span><span class="sxs-lookup"><span data-stu-id="abf3d-161">To verify the service is working</span></span>  
  
1.  <span data-ttu-id="abf3d-162">Uruchom aplikację konsolową GettingStartedHost z wewnątrz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="abf3d-162">Run the GettingStartedHost console application from inside [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span> <span data-ttu-id="abf3d-163">Podczas uruchamiania na [!INCLUDE[wv](../../../includes/wv-md.md)] i nowszych systemów operacyjnych, usługa musi być uruchomiony z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="abf3d-163">When running on [!INCLUDE[wv](../../../includes/wv-md.md)] and later operating systems, the service must be run with administrator privileges.</span></span> <span data-ttu-id="abf3d-164">Ponieważ program Visual Studio zostało uruchomione z uprawnieniami administratora, GettingStartedHost również jest uruchamiane z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="abf3d-164">Because Visual Studio was run with Administrator privileges, GettingStartedHost is also run with Administrator privileges.</span></span> <span data-ttu-id="abf3d-165">Można również rozpocząć nowy wiersz polecenia, w których jest on uruchomiony z uprawnieniami administratora i uruchom service.exe znajdujący się w nim.</span><span class="sxs-lookup"><span data-stu-id="abf3d-165">You can also start a new command prompt running it with Administrator privileges and run service.exe within it.</span></span>  
  
2.  <span data-ttu-id="abf3d-166">Otwórz program Internet Explorer i przejdź do usługi debugowania strony na `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="abf3d-166">Open Internet Explorer and browse to the service's debug page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abf3d-167">Przykład</span><span class="sxs-lookup"><span data-stu-id="abf3d-167">Example</span></span>  
 <span data-ttu-id="abf3d-168">Poniższy przykład zawiera kontrakt usługi i implementację z poprzednich kroków samouczka i hostuje usługę w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="abf3d-168">The following example includes the service contract and implementation from previous steps in the tutorial and hosts the service in a console application.</span></span>  
  
 <span data-ttu-id="abf3d-169">Aby skompilować to za pomocą kompilatora wiersza polecenia, skompilować IService1.cs i Service1.cs do biblioteki klas odwołuje się do `System.ServiceModel.dll`.</span><span class="sxs-lookup"><span data-stu-id="abf3d-169">To compile this with a command-line compiler, compile IService1.cs and Service1.cs into a class library referencing `System.ServiceModel.dll`.</span></span> <span data-ttu-id="abf3d-170">I skompiluj plik Program.cs aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="abf3d-170">And compile Program.cs to a console application.</span></span>  
  
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
>  <span data-ttu-id="abf3d-171">Usługi, takie jak tego wymaga uprawnienia do rejestrowania adresy HTTP na komputerze w celu nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="abf3d-171">Services such as this one require permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="abf3d-172">Administrator konta mają to uprawnienie, ale konta bez uprawnień administratora musi mieć uprawnienie dla przestrzeni nazw protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="abf3d-172">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="abf3d-173">Aby uzyskać więcej informacji o sposobie konfigurowania rezerwacji przestrzeni nazw, zobacz [Konfigurowanie protokołów HTTP i HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="abf3d-173">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="abf3d-174">Podczas uruchamiania w programie Visual Studio, service.exe muszą być uruchomione z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="abf3d-174">When running under Visual Studio, the service.exe must be run with administrator privileges.</span></span>  
  
 <span data-ttu-id="abf3d-175">Teraz usługa jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="abf3d-175">Now the service is running.</span></span> <span data-ttu-id="abf3d-176">Przejdź do [porady: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="abf3d-176">Proceed to [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="abf3d-177">Aby uzyskać informacje dotyczące rozwiązywania problemów, zobacz [Rozwiązywanie problemów z samouczka Wprowadzenie](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="abf3d-177">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abf3d-178">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abf3d-178">See Also</span></span>  
 [<span data-ttu-id="abf3d-179">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="abf3d-179">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="abf3d-180">Host samodzielny</span><span class="sxs-lookup"><span data-stu-id="abf3d-180">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
