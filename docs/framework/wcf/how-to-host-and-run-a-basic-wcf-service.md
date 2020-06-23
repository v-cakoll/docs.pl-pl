---
title: 'Samouczek: Hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation'
description: Dowiedz się, jak hostować usługę WCF w aplikacji konsolowej w ramach serii artykułów, które ułatwiają rozpoczęcie tworzenia aplikacji WCF.
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 5318991087e71430523681d601d3b38c4513027b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246133"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="5402f-103">Samouczek: Hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="5402f-103">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="5402f-104">W tym samouczku opisano trzecią z pięciu zadań wymaganych do utworzenia aplikacji podstawowej Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5402f-104">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="5402f-105">Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="5402f-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="5402f-106">Następnym zadaniem do tworzenia aplikacji WCF jest Hostowanie usługi WCF w aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="5402f-106">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="5402f-107">Usługa WCF udostępnia jeden lub więcej *punktów końcowych*, z których każdy udostępnia jedną lub więcej operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="5402f-107">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="5402f-108">Punkt końcowy usługi określa następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="5402f-108">A service endpoint specifies the following information:</span></span>

- <span data-ttu-id="5402f-109">Adres, na którym można znaleźć usługę.</span><span class="sxs-lookup"><span data-stu-id="5402f-109">An address where you can find the service.</span></span>
- <span data-ttu-id="5402f-110">Powiązanie zawierające informacje opisujące, jak klient musi komunikować się z usługą.</span><span class="sxs-lookup"><span data-stu-id="5402f-110">A binding that contains the information that describes how a client must communicate with the service.</span></span>
- <span data-ttu-id="5402f-111">Kontrakt definiujący funkcje udostępniane klientom przez usługę.</span><span class="sxs-lookup"><span data-stu-id="5402f-111">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="5402f-112">Z tego samouczka dowiesz się, jak wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5402f-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5402f-113">Utwórz i skonfiguruj projekt aplikacji konsoli na potrzeby hostowania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="5402f-113">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="5402f-114">Dodaj kod do hostowania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="5402f-114">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="5402f-115">Zaktualizuj plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5402f-115">Update the configuration file.</span></span>
> - <span data-ttu-id="5402f-116">Uruchom usługę WCF i sprawdź, czy jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="5402f-116">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="5402f-117">Tworzenie i Konfigurowanie projektu aplikacji konsolowej na potrzeby hostowania usługi</span><span class="sxs-lookup"><span data-stu-id="5402f-117">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="5402f-118">Utwórz projekt aplikacji konsolowej w programie Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="5402f-118">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="5402f-119">Z menu **plik** wybierz pozycję **Otwórz**  >  **projekt/rozwiązanie** i przejdź do utworzonego wcześniej rozwiązania **GettingStarted** (*GettingStarted. sln*).</span><span class="sxs-lookup"><span data-stu-id="5402f-119">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="5402f-120">Wybierz pozycję **Open** (Otwórz).</span><span class="sxs-lookup"><span data-stu-id="5402f-120">Select **Open**.</span></span>

    2. <span data-ttu-id="5402f-121">Z menu **Widok** wybierz pozycję **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="5402f-121">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="5402f-122">W oknie **Eksplorator rozwiązań** wybierz rozwiązanie **GettingStarted** (górny węzeł), a następnie wybierz pozycję **Dodaj**  >  **Nowy projekt** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="5402f-122">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="5402f-123">W oknie **Dodaj nowy projekt** po lewej stronie wybierz kategorię **pulpit systemu Windows** w obszarze **Visual C#** lub **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="5402f-123">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="5402f-124">Wybierz szablon **aplikacja konsoli (.NET Framework)** , a następnie wprowadź *GettingStartedHost* jako **nazwę**.</span><span class="sxs-lookup"><span data-stu-id="5402f-124">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="5402f-125">Wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="5402f-125">Select **OK**.</span></span>

2. <span data-ttu-id="5402f-126">Dodaj odwołanie w projekcie **GettingStartedHost** do projektu **GettingStartedLib** :</span><span class="sxs-lookup"><span data-stu-id="5402f-126">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span>

    1. <span data-ttu-id="5402f-127">W oknie **Eksplorator rozwiązań** wybierz folder **odwołania** w projekcie **GettingStartedHost** , a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="5402f-127">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="5402f-128">W oknie dialogowym **Dodawanie odwołania** w obszarze **projekty** po lewej stronie okna wybierz pozycję **rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="5402f-128">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span>

    3. <span data-ttu-id="5402f-129">Wybierz pozycję **GettingStartedLib** w środkowej sekcji okna, a następnie wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="5402f-129">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span>

       <span data-ttu-id="5402f-130">Ta akcja powoduje, że typy zdefiniowane w projekcie **GettingStartedLib** są dostępne dla projektu **GettingStartedHost** .</span><span class="sxs-lookup"><span data-stu-id="5402f-130">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="5402f-131">Dodaj odwołanie do zestawu w projekcie **GettingStartedHost** <xref:System.ServiceModel> :</span><span class="sxs-lookup"><span data-stu-id="5402f-131">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="5402f-132">W oknie **Eksplorator rozwiązań** wybierz folder **odwołania** w projekcie **GettingStartedHost** , a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="5402f-132">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="5402f-133">W oknie **Dodaj odwołanie** w obszarze **zestawy** po lewej stronie okna wybierz pozycję **Struktura**.</span><span class="sxs-lookup"><span data-stu-id="5402f-133">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="5402f-134">Wybierz **System. ServiceModel**, a następnie wybierz **przycisk OK**.</span><span class="sxs-lookup"><span data-stu-id="5402f-134">Select **System.ServiceModel**, and then select **OK**.</span></span>

    4. <span data-ttu-id="5402f-135">Zapisz rozwiązanie, wybierając kolejno pozycje **plik**  >  **Zapisz wszystko**.</span><span class="sxs-lookup"><span data-stu-id="5402f-135">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="5402f-136">Dodawanie kodu do obsługi usługi</span><span class="sxs-lookup"><span data-stu-id="5402f-136">Add code to host the service</span></span>

<span data-ttu-id="5402f-137">Aby hostować usługę, należy dodać kod w celu wykonania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5402f-137">To host the service, you add code to do the following steps:</span></span>

1. <span data-ttu-id="5402f-138">Utwórz identyfikator URI dla adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="5402f-138">Create a URI for the base address.</span></span>
2. <span data-ttu-id="5402f-139">Utwórz wystąpienie klasy do hostowania usługi.</span><span class="sxs-lookup"><span data-stu-id="5402f-139">Create a class instance for hosting the service.</span></span>
3. <span data-ttu-id="5402f-140">Utwórz punkt końcowy usługi.</span><span class="sxs-lookup"><span data-stu-id="5402f-140">Create a service endpoint.</span></span>
4. <span data-ttu-id="5402f-141">Włącz wymianę metadanych.</span><span class="sxs-lookup"><span data-stu-id="5402f-141">Enable metadata exchange.</span></span>
5. <span data-ttu-id="5402f-142">Otwórz hosta usługi, aby nasłuchiwać komunikatów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="5402f-142">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="5402f-143">Wprowadź następujące zmiany w kodzie:</span><span class="sxs-lookup"><span data-stu-id="5402f-143">Make the following changes to the code:</span></span>

1. <span data-ttu-id="5402f-144">Otwórz plik **program.cs** lub **Module1. vb** w projekcie **GettingStartedHost** i Zastąp jego kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="5402f-144">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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
                    selfHost.Description.Behaviors.Add(smb);

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

    <span data-ttu-id="5402f-145">Aby uzyskać informacje o tym, jak działa ten kod, zobacz [kroki programu hostingu usług](#service-hosting-program-steps).</span><span class="sxs-lookup"><span data-stu-id="5402f-145">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="5402f-146">Aktualizowanie właściwości projektu:</span><span class="sxs-lookup"><span data-stu-id="5402f-146">Update the project properties:</span></span>

   1. <span data-ttu-id="5402f-147">W oknie **Eksplorator rozwiązań** wybierz folder **GettingStartedHost** , a następnie wybierz polecenie **Właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="5402f-147">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="5402f-148">Na stronie właściwości **GettingStartedHost** wybierz kartę **aplikacja** :</span><span class="sxs-lookup"><span data-stu-id="5402f-148">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="5402f-149">W przypadku projektów C# wybierz pozycję **GettingStartedHost. program** z listy **obiekt startowy** .</span><span class="sxs-lookup"><span data-stu-id="5402f-149">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="5402f-150">W przypadku projektów Visual Basic wybierz pozycję **Service. program** z listy **obiektów początkowych** .</span><span class="sxs-lookup"><span data-stu-id="5402f-150">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="5402f-151">Z menu **plik** wybierz pozycję **Zapisz wszystko**.</span><span class="sxs-lookup"><span data-stu-id="5402f-151">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="5402f-152">Sprawdź, czy usługa działa</span><span class="sxs-lookup"><span data-stu-id="5402f-152">Verify the service is working</span></span>

1. <span data-ttu-id="5402f-153">Skompiluj rozwiązanie, a następnie uruchom aplikację konsolową **GettingStartedHost** z wewnątrz programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5402f-153">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span>

    <span data-ttu-id="5402f-154">Usługa musi być uruchomiona z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="5402f-154">The service must be run with administrator privileges.</span></span> <span data-ttu-id="5402f-155">Ponieważ program Visual Studio został otwarty z uprawnieniami administratora, po uruchomieniu programu **GettingStartedHost** w programie Visual Studio aplikacja jest również uruchamiana z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="5402f-155">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="5402f-156">Alternatywnie, możesz otworzyć nowy wiersz polecenia jako administrator (wybierz opcję **więcej**  >  **Uruchom jako administrator** z menu skrótów) i uruchomić **GettingStartedHost.exe** w nim.</span><span class="sxs-lookup"><span data-stu-id="5402f-156">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="5402f-157">Otwórz przeglądarkę internetową i przejdź do strony usługi pod adresem `http://localhost:8000/GettingStarted/CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="5402f-157">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="5402f-158">Takie usługi, jak to jest wymagane, muszą mieć odpowiednie uprawnienia do rejestrowania adresów HTTP na maszynie do nasłuchiwania.</span><span class="sxs-lookup"><span data-stu-id="5402f-158">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="5402f-159">Konta administratorów mają to uprawnienie, ale konta niebędące administratorami muszą mieć uprawnienia do przestrzeni nazw protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5402f-159">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="5402f-160">Więcej informacji o sposobie konfigurowania rezerwacji przestrzeni nazw znajduje się w temacie [Konfigurowanie protokołów HTTP i https](feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="5402f-160">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span>

## <a name="service-hosting-program-steps"></a><span data-ttu-id="5402f-161">Kroki programu hostingu usług</span><span class="sxs-lookup"><span data-stu-id="5402f-161">Service hosting program steps</span></span>

<span data-ttu-id="5402f-162">Kroki w kodzie dodanym do hostowania usługi są opisane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5402f-162">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="5402f-163">**Krok 1**. utworzenie wystąpienia `Uri` klasy w celu przechowywania adresu podstawowego usługi.</span><span class="sxs-lookup"><span data-stu-id="5402f-163">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="5402f-164">Adres URL, który zawiera adres podstawowy, ma opcjonalny identyfikator URI, który identyfikuje usługę.</span><span class="sxs-lookup"><span data-stu-id="5402f-164">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="5402f-165">Adres podstawowy jest sformatowany w następujący sposób: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>` .</span><span class="sxs-lookup"><span data-stu-id="5402f-165">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="5402f-166">Adres podstawowy usługi kalkulatora używa transportu HTTP, localhost, portu 8000 i segmentu URI GettingStarted.</span><span class="sxs-lookup"><span data-stu-id="5402f-166">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="5402f-167">**Krok 2**. Tworzenie wystąpienia <xref:System.ServiceModel.ServiceHost> klasy, która jest używana do hostowania usługi.</span><span class="sxs-lookup"><span data-stu-id="5402f-167">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="5402f-168">Konstruktor przyjmuje dwa parametry: typ klasy implementującej kontrakt usługi i adres podstawowy usługi.</span><span class="sxs-lookup"><span data-stu-id="5402f-168">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="5402f-169">**Krok 3** <xref:System.ServiceModel.Description.ServiceEndpoint> . Tworzenie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5402f-169">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="5402f-170">Punkt końcowy usługi składa się z adresu, powiązania i kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="5402f-170">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="5402f-171"><xref:System.ServiceModel.Description.ServiceEndpoint>Konstruktor składa się z typu interfejsu kontraktu usługi, powiązania i adresu.</span><span class="sxs-lookup"><span data-stu-id="5402f-171">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="5402f-172">Kontrakt usługi jest `ICalculator` zdefiniowany i zaimplementowany w typie usługi.</span><span class="sxs-lookup"><span data-stu-id="5402f-172">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="5402f-173">Powiązanie dla tego przykładu jest <xref:System.ServiceModel.WSHttpBinding> , które jest wbudowanym powiązaniem i łączy się z punktami końcowymi, które są zgodne ze specyfikacjami WS-\*.</span><span class="sxs-lookup"><span data-stu-id="5402f-173">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="5402f-174">Aby uzyskać więcej informacji na temat powiązań WCF, zobacz temat [powiązania WCF — Omówienie](bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5402f-174">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="5402f-175">Adres jest dołączany do adresu podstawowego, aby zidentyfikować punkt końcowy.</span><span class="sxs-lookup"><span data-stu-id="5402f-175">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="5402f-176">Kod określa adres jako CalculatorService oraz w pełni kwalifikowany adres punktu końcowego jako `http://localhost:8000/GettingStarted/CalculatorService` .</span><span class="sxs-lookup"><span data-stu-id="5402f-176">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="5402f-177">W przypadku .NET Framework w wersji 4 i nowszych dodanie punktu końcowego usługi jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="5402f-177">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="5402f-178">W przypadku tych wersji, jeśli nie dodasz kodu lub konfiguracji, program WCF dodaje jeden domyślny punkt końcowy dla każdej kombinacji adresu podstawowego i kontraktu zaimplementowanego przez usługę.</span><span class="sxs-lookup"><span data-stu-id="5402f-178">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="5402f-179">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [Określanie adresu punktu końcowego](specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="5402f-179">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="5402f-180">Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5402f-180">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="5402f-181">**Krok 4**. włączenie wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="5402f-181">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="5402f-182">Klienci używają wymiany metadanych do generowania serwerów proxy na potrzeby wywoływania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="5402f-182">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="5402f-183">Aby włączyć wymianę metadanych, Utwórz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie, ustaw jego <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> Właściwość na `true` , a następnie Dodaj `ServiceMetadataBehavior` obiekt do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekcji <xref:System.ServiceModel.ServiceHost> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="5402f-183">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="5402f-184">**Krok 5**. Otwieranie <xref:System.ServiceModel.ServiceHost> w celu nasłuchiwania komunikatów przychodzących.</span><span class="sxs-lookup"><span data-stu-id="5402f-184">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="5402f-185">Aplikacja czeka na naciśnięcie klawisza **Enter**.</span><span class="sxs-lookup"><span data-stu-id="5402f-185">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="5402f-186">Po utworzeniu wystąpienia aplikacji <xref:System.ServiceModel.ServiceHost> wykonuje blok try/catch.</span><span class="sxs-lookup"><span data-stu-id="5402f-186">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="5402f-187">Aby uzyskać więcej informacji na temat bezpiecznego przechwytywania wyjątków zgłoszonych przez <xref:System.ServiceModel.ServiceHost> program, zobacz [Używanie funkcji Close i Abort w celu zwolnienia zasobów klienta WCF](samples/use-close-abort-release-wcf-client-resources.md).</span><span class="sxs-lookup"><span data-stu-id="5402f-187">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5402f-188">Po dodaniu biblioteki usług WCF program Visual Studio hostuje ją w przypadku debugowania przez uruchomienie hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="5402f-188">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="5402f-189">Aby uniknąć konfliktów, można uniemożliwić programowi Visual Studio hostowanie biblioteki usług WCF.</span><span class="sxs-lookup"><span data-stu-id="5402f-189">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span>
>
> 1. <span data-ttu-id="5402f-190">Wybierz projekt **GettingStartedLib** w **Eksplorator rozwiązań** a następnie wybierz **Właściwości** z menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="5402f-190">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="5402f-191">Wybierz **Opcje WCF** i usuń zaznaczenie pozycji **Uruchom hosta usługi WCF podczas debugowania innego projektu w tym samym rozwiązaniu**.</span><span class="sxs-lookup"><span data-stu-id="5402f-191">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5402f-192">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5402f-192">Next steps</span></span>

<span data-ttu-id="5402f-193">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5402f-193">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="5402f-194">Utwórz i skonfiguruj projekt aplikacji konsoli na potrzeby hostowania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="5402f-194">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="5402f-195">Dodaj kod do hostowania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="5402f-195">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="5402f-196">Zaktualizuj plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="5402f-196">Update the configuration file.</span></span>
> - <span data-ttu-id="5402f-197">Uruchom usługę WCF i sprawdź, czy jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="5402f-197">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="5402f-198">Przejdź do następnego samouczka, aby dowiedzieć się, jak utworzyć klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="5402f-198">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5402f-199">Samouczek: tworzenie klienta WCF</span><span class="sxs-lookup"><span data-stu-id="5402f-199">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
