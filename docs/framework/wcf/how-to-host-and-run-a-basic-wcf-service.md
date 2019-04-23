---
title: 'Samouczek: Hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: ad9536b1f27ba3945bf76d0474de4825033a1e8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197909"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="36756-102">Samouczek: Hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="36756-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="36756-103">W tym samouczku opisano trzeci pięć zadania wymagane do utworzenia podstawowej aplikacji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="36756-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="36756-104">Aby zapoznać się z omówieniem samouczków, zobacz [samouczka: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="36756-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="36756-105">Następne zadanie do tworzenia aplikacji WCF jest hostowanie usługi WCF w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="36756-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="36756-106">Usługa WCF ujawnia co najmniej jeden *punktów końcowych*, z których każdy ujawnia co najmniej jednej operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="36756-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="36756-107">Punkt końcowy usługi określa następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="36756-107">A service endpoint specifies the following information:</span></span> 
- <span data-ttu-id="36756-108">Adres, gdzie można znaleźć usługi.</span><span class="sxs-lookup"><span data-stu-id="36756-108">An address where you can find the service.</span></span>
- <span data-ttu-id="36756-109">Wiązanie, który zawiera informacje opisujące, jak klientowi komunikowanie się z usługą.</span><span class="sxs-lookup"><span data-stu-id="36756-109">A binding that contains the information that describes how a client must communicate with the service.</span></span> 
- <span data-ttu-id="36756-110">Kontrakt definiujący funkcje, które usługa zapewnia swoim klientom.</span><span class="sxs-lookup"><span data-stu-id="36756-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="36756-111">Ten samouczek zawiera informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="36756-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="36756-112">Utwórz i skonfiguruj projekt aplikacji konsoli do hostowania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="36756-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="36756-113">Dodaj kod do obsługi usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="36756-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="36756-114">Należy zaktualizować plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="36756-114">Update the configuration file.</span></span>
> - <span data-ttu-id="36756-115">Uruchom usługę WCF i weryfikować ją jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="36756-115">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="36756-116">Tworzenie i konfigurowanie projektu aplikacji konsoli w do hostowania usługi</span><span class="sxs-lookup"><span data-stu-id="36756-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="36756-117">Utwórz projekt aplikacji konsoli w programie Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="36756-117">Create a console app project in Visual Studio:</span></span> 
 
    1. <span data-ttu-id="36756-118">Z **pliku** menu, wybierz opcję **Otwórz** > **projekt/rozwiązanie** i przejdź do **GettingStarted** rozwiązania możesz wcześniej utworzony (*GettingStarted.sln*).</span><span class="sxs-lookup"><span data-stu-id="36756-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="36756-119">Wybierz pozycję **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="36756-119">Select **Open**.</span></span>

    2. <span data-ttu-id="36756-120">Z **widoku** menu, wybierz opcję **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="36756-120">From the **View** menu, select **Solution Explorer**.</span></span>
    
    3. <span data-ttu-id="36756-121">W **Eksploratora rozwiązań** wybierz **GettingStarted** rozwiązania (najwyższy węzeł), a następnie wybierz **Dodaj** > **nowy projekt** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="36756-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 

    4. <span data-ttu-id="36756-122">W **Dodaj nowy projekt** oknie po lewej stronie wybierz **pulpitu Windows** kategorię w obszarze **Visual C#**  lub **języka Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="36756-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="36756-123">Wybierz **Aplikacja konsoli (.NET Framework)** szablonu, a następnie wprowadź *GettingStartedHost* dla **nazwa**.</span><span class="sxs-lookup"><span data-stu-id="36756-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="36756-124">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="36756-124">Select **OK**.</span></span>

2. <span data-ttu-id="36756-125">Dodaj odwołanie w **GettingStartedHost** projekt **GettingStartedLib** projektu:</span><span class="sxs-lookup"><span data-stu-id="36756-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span> 

    1. <span data-ttu-id="36756-126">W **Eksploratora rozwiązań** wybierz **odwołania** folderze **GettingStartedHost** projektu, a następnie wybierz **Dodaj odwołanie** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="36756-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="36756-127">W **Dodaj odwołanie** okna dialogowego, w obszarze **projektów** w lewej części okna wybierz **rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="36756-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span> 
 
    3. <span data-ttu-id="36756-128">Wybierz **GettingStartedLib** w Centrum części okna, a następnie wybierz pozycję **OK**.</span><span class="sxs-lookup"><span data-stu-id="36756-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span> 

       <span data-ttu-id="36756-129">Ta akcja powoduje, że typy zdefiniowane w **GettingStartedLib** dostępnych do projektu **GettingStartedHost** projektu.</span><span class="sxs-lookup"><span data-stu-id="36756-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="36756-130">Dodaj odwołanie w **GettingStartedHost** projekt <xref:System.ServiceModel> zestawu:</span><span class="sxs-lookup"><span data-stu-id="36756-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="36756-131">W **Eksploratora rozwiązań** wybierz **odwołania** folderze **GettingStartedHost** projektu, a następnie wybierz **Dodaj odwołanie** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="36756-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>
    
    2. <span data-ttu-id="36756-132">W **Dodaj odwołanie** okna, w obszarze **zestawy** w lewej części okna wybierz **Framework**.</span><span class="sxs-lookup"><span data-stu-id="36756-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span> 

    3. <span data-ttu-id="36756-133">Wybierz **System.ServiceModel**, a następnie wybierz pozycję **OK**.</span><span class="sxs-lookup"><span data-stu-id="36756-133">Select **System.ServiceModel**, and then select **OK**.</span></span> 
    
    4. <span data-ttu-id="36756-134">Zapisz rozwiązanie, wybierając **pliku** > **Zapisz wszystko**.</span><span class="sxs-lookup"><span data-stu-id="36756-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="36756-135">Dodaj kod do obsługi usługi</span><span class="sxs-lookup"><span data-stu-id="36756-135">Add code to host the service</span></span>

<span data-ttu-id="36756-136">Do obsługi usługi, możesz dodać kod, aby wykonać poniższe kroki:</span><span class="sxs-lookup"><span data-stu-id="36756-136">To host the service, you add code to do the following steps:</span></span> 
   1. <span data-ttu-id="36756-137">Utwórz identyfikator URI dla adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="36756-137">Create a URI for the base address.</span></span>
   2. <span data-ttu-id="36756-138">Utwórz wystąpienie klasy do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="36756-138">Create a class instance for hosting the service.</span></span>
   3. <span data-ttu-id="36756-139">Tworzenie punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="36756-139">Create a service endpoint.</span></span>
   4. <span data-ttu-id="36756-140">Włącz wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="36756-140">Enable metadata exchange.</span></span>
   5. <span data-ttu-id="36756-141">Otwórz hosta usługi do nasłuchiwania pod kątem przychodzących wiadomości.</span><span class="sxs-lookup"><span data-stu-id="36756-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="36756-142">Wprowadź następujące zmiany w kodzie:</span><span class="sxs-lookup"><span data-stu-id="36756-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="36756-143">Otwórz **Program.cs** lub **Module1.vb** w pliku **GettingStartedHost** projektu i zastąp jego kod poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="36756-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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
                // Step 1: Create a URI to serve as the base address.
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

                // Step 2: Create a ServiceHost instance.
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

                try
                {
                    // Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                    // Step 4: Enable metadata exchange.
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                    smb.HttpGetEnabled = true;
                    selfHost.Description.Behaviors.Add(smb)    ;

                    // Step 5: Start the service.
                    selfHost.Open();
                    Console.WriteLine("The service is ready.");

                    // Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.");
                    Console.WriteLine();
                    Console.ReadLine();
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
    Imports GettingStartedLib.GettingStartedLib

    Module Service

        Class Program
            Shared Sub Main()
                ' Step 1: Create a URI to serve as the base address.
                Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

                ' Step 2: Create a ServiceHost instance.
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
               Try

                    ' Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint( _
                        GetType(ICalculator), _
                        New WSHttpBinding(), _
                        "CalculatorService")

                    ' Step 4: Enable metadata exchange.
                    Dim smb As New ServiceMetadataBehavior()
                    smb.HttpGetEnabled = True
                    selfHost.Description.Behaviors.Add(smb)

                    ' Step 5: Start the service.
                    selfHost.Open()
                    Console.WriteLine("The service is ready.")

                    ' Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.")
                    Console.WriteLine()
                    Console.ReadLine()
                    selfHost.Close()

                Catch ce As CommunicationException
                    Console.WriteLine("An exception occurred: {0}", ce.Message)
                    selfHost.Abort()
                End Try
            End Sub
        End Class

    End Module
    ```
    
    <span data-ttu-id="36756-144">Aby uzyskać informacje o tym, jak działa ten kod, zobacz [usług obsługującego program kroki](#service-hosting-program-steps).</span><span class="sxs-lookup"><span data-stu-id="36756-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="36756-145">Zaktualizuj właściwości projektu:</span><span class="sxs-lookup"><span data-stu-id="36756-145">Update the project properties:</span></span>

   1. <span data-ttu-id="36756-146">W **Eksploratora rozwiązań** wybierz **GettingStartedHost** folder, a następnie wybierz **właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="36756-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="36756-147">Na **GettingStartedHost** strony właściwości, zaznacz **aplikacji** karty:</span><span class="sxs-lookup"><span data-stu-id="36756-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="36756-148">Aby uzyskać C# projektów, wybierz opcję **GettingStartedHost.Program** z **obiekt początkowy** listy.</span><span class="sxs-lookup"><span data-stu-id="36756-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="36756-149">Dla projektów języka Visual Basic, wybierz **Service.Program** z **obiekt początkowy** listy.</span><span class="sxs-lookup"><span data-stu-id="36756-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="36756-150">Z **pliku** menu, wybierz opcję **Zapisz wszystko**.</span><span class="sxs-lookup"><span data-stu-id="36756-150">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="36756-151">Sprawdź, czy usługa działa</span><span class="sxs-lookup"><span data-stu-id="36756-151">Verify the service is working</span></span>

1. <span data-ttu-id="36756-152">Skompiluj rozwiązanie, a następnie uruchom **GettingStartedHost** konsoli aplikacji z poziomu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36756-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span> 

    <span data-ttu-id="36756-153">Usługa musi być uruchamiane z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="36756-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="36756-154">Ponieważ otwarty program Visual Studio z uprawnieniami administratora, po uruchomieniu **GettingStartedHost** w programie Visual Studio z uprawnieniami administratora oraz uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="36756-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="36756-155">Alternatywnie, można otworzyć wiersz polecenia jako administrator (wybierz **więcej** > **Uruchom jako administrator** z menu skrótów) i uruchom **GettingStartedHost.exe**  znajdujący się w nim.</span><span class="sxs-lookup"><span data-stu-id="36756-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="36756-156">Otwórz przeglądarkę internetową i przejdź do strony usługi na `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="36756-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>
   
   > [!NOTE]
   > <span data-ttu-id="36756-157">Usługi, takie jak tego wymaga odpowiednie uprawnienia, aby zarejestrować adresy HTTP na komputerze w celu nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="36756-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="36756-158">Administrator konta mają to uprawnienie, ale konta bez uprawnień administratora musi mieć uprawnienie dla przestrzeni nazw protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="36756-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="36756-159">Aby uzyskać więcej informacji o sposobie konfigurowania rezerwacji przestrzeni nazw, zobacz [Konfigurowanie protokołów HTTP i HTTPS](feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="36756-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span> 

## <a name="service-hosting-program-steps"></a><span data-ttu-id="36756-160">Usługa hostingu programu kroki</span><span class="sxs-lookup"><span data-stu-id="36756-160">Service hosting program steps</span></span>

<span data-ttu-id="36756-161">Kroki opisane w kod, który został dodany do hosta usługi są opisane na następujący:</span><span class="sxs-lookup"><span data-stu-id="36756-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="36756-162">**Krok 1**: Utwórz wystąpienie obiektu `Uri` klasy utrzymującej adres podstawowy usługi.</span><span class="sxs-lookup"><span data-stu-id="36756-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="36756-163">Adres URL, który zawiera adres podstawowy ma opcjonalny identyfikator URI, który identyfikuje usługę.</span><span class="sxs-lookup"><span data-stu-id="36756-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="36756-164">Adres podstawowy jest sformatowany w następujący sposób: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span><span class="sxs-lookup"><span data-stu-id="36756-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="36756-165">Adres podstawowy usługi Kalkulator korzysta z protokołu HTTP "," localhost "," port 8000 "i" segmentem identyfikatora URI, GettingStarted.</span><span class="sxs-lookup"><span data-stu-id="36756-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="36756-166">**Krok 2**: Utwórz wystąpienie obiektu <xref:System.ServiceModel.ServiceHost> klasy, których używasz do obsługi usługi.</span><span class="sxs-lookup"><span data-stu-id="36756-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="36756-167">Konstruktor przyjmuje dwa parametry: typ klasy, która implementuje kontrakt usługi i podstawowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="36756-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="36756-168">**Krok 3**: Utwórz <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="36756-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="36756-169">Punkt końcowy usługi składa się z adresu, powiązanie i kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="36756-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="36756-170"><xref:System.ServiceModel.Description.ServiceEndpoint> Konstruktor składa się z typu interfejsu kontraktu usługi, powiązanie i adres.</span><span class="sxs-lookup"><span data-stu-id="36756-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="36756-171">Umowa serwisowa jest `ICalculator`, zdefiniowane przez użytkownika, która implementuje typu usługi.</span><span class="sxs-lookup"><span data-stu-id="36756-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="36756-172">Powiązanie dla tego przykładu jest <xref:System.ServiceModel.WSHttpBinding>, która jest wbudowana powiązania i nawiązanie połączenia z punktami końcowymi, które odpowiadają WS-\* specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="36756-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="36756-173">Aby uzyskać więcej informacji na temat wiązania WCF, zobacz [omówienie powiązań WCF](bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="36756-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="36756-174">Można dołączyć adres na adres bazowy do identyfikowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="36756-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="36756-175">Kod określa adres CalculatorService oraz adres FQDN dla punktu końcowego jako `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="36756-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="36756-176">Dla programu .NET Framework w wersji 4 i nowszych dodanie punktu końcowego usługi jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="36756-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="36756-177">Dla tych wersji Jeśli nie dodasz kodu lub konfiguracji usługi WCF dodaje jeden domyślny punkt końcowy dla każdej kombinacji adresu podstawowego i kontrakt implementowane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="36756-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="36756-178">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [Określanie adresu punktu końcowego](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="36756-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="36756-179">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [konfiguracji uproszczony](simplified-configuration.md) i [uproszczony Konfiguracja usług WCF](samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="36756-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="36756-180">**Krok 4**: Włącz wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="36756-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="36756-181">Klienci używają wymiany metadanych do Generowanie serwerów proxy do wywoływania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="36756-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="36756-182">Aby włączyć wymiany metadanych, Utwórz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienia, ustaw jego <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> właściwości `true`i Dodaj `ServiceMetadataBehavior` obiekt <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> zbiór <xref:System.ServiceModel.ServiceHost> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="36756-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="36756-183">**Krok 5**: Otwórz <xref:System.ServiceModel.ServiceHost> do nasłuchiwania pod kątem przychodzących wiadomości.</span><span class="sxs-lookup"><span data-stu-id="36756-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="36756-184">Aplikacja oczekuje na naciśnij **Enter**.</span><span class="sxs-lookup"><span data-stu-id="36756-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="36756-185">Po tworzy wystąpienie aplikacji <xref:System.ServiceModel.ServiceHost>, wykonuje bloku try/catch.</span><span class="sxs-lookup"><span data-stu-id="36756-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="36756-186">Aby uzyskać więcej informacji na temat bezpiecznego przechwytywanie wyjątków zgłaszanych przez <xref:System.ServiceModel.ServiceHost>, zobacz [Użyj Zamknij i Abort, aby zwolnić zasoby klienta WCF](samples/use-close-abort-release-wcf-client-resources.md).</span><span class="sxs-lookup"><span data-stu-id="36756-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36756-187">Po dodaniu biblioteki usługi WCF, Visual Studio umieszcza dla Ciebie Jeśli debugujesz przez uruchomienie hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="36756-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="36756-188">Aby uniknąć konfliktów, można zapobiec programu Visual Studio hostowanie biblioteki usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="36756-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span> 
> 1. <span data-ttu-id="36756-189">Wybierz **GettingStartedLib** projektu w **Eksploratora rozwiązań** i wybierz polecenie **właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="36756-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="36756-190">Wybierz **opcje WCF** i usuń zaznaczenie pola wyboru **Start podczas debugowania innego projektu w tym samym rozwiązaniu Host usługi WCF**.</span><span class="sxs-lookup"><span data-stu-id="36756-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="36756-191">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="36756-191">Next steps</span></span>

<span data-ttu-id="36756-192">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="36756-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="36756-193">Utwórz i skonfiguruj projekt aplikacji konsoli do hostowania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="36756-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="36756-194">Dodaj kod do obsługi usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="36756-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="36756-195">Należy zaktualizować plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="36756-195">Update the configuration file.</span></span>
> - <span data-ttu-id="36756-196">Uruchom usługę WCF i weryfikować ją jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="36756-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="36756-197">Przejdź do następnego samouczka, aby dowiedzieć się, jak można utworzyć klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="36756-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="36756-198">Samouczek: Utworzenie klienta WCF</span><span class="sxs-lookup"><span data-stu-id="36756-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
