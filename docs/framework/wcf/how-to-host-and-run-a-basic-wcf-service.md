---
title: 'Samouczek: Hostuj i uruchamiaj podstawową usługę Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 30eb86987b83427b94c6fff22755cde3d73dd9f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184083"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>Samouczek: Hostuj i uruchamiaj podstawową usługę Windows Communication Foundation

W tym samouczku opisano trzecie z pięciu zadań wymaganych do utworzenia podstawowej aplikacji Programu Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, zobacz [Samouczek: Wprowadzenie do aplikacji Programu Windows Communication Foundation](getting-started-tutorial.md).

Następnym zadaniem tworzenia aplikacji WCF jest hostowanie usługi WCF w aplikacji konsoli. Usługa WCF udostępnia jeden lub więcej *punktów końcowych,* z których każdy udostępnia jedną lub więcej operacji usługi. Punkt końcowy usługi określa następujące informacje:

- Adres, pod którym można znaleźć usługę.
- Powiązanie, które zawiera informacje, które opisuje, jak klient musi komunikować się z usługą.
- Kontrakt, który definiuje funkcje, które usługa zapewnia swoim klientom.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Tworzenie i konfigurowanie projektu aplikacji konsoli do obsługi usługi WCF.
> - Dodaj kod do hostowania usługi WCF.
> - Zaktualizuj plik konfiguracyjny.
> - Uruchom usługę WCF i sprawdź, czy jest uruchomiona.

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>Tworzenie i konfigurowanie projektu aplikacji konsoli do obsługi usługi

1. Tworzenie projektu aplikacji konsoli w programie Visual Studio:

    1. Z menu **Plik** wybierz polecenie **Otwórz** > **projekt/rozwiązanie** i przejdź do utworzonego wcześniej rozwiązania **GettingStarted** (*GettingStarted.sln*). Wybierz pozycję **Otwórz**.

    2. Z menu **Widok** wybierz pozycję **Eksplorator rozwiązań**.

    3. W oknie **Eksplorator rozwiązań** wybierz rozwiązanie GettingStarted (węzeł **górny),** a następnie z menu skrótów wybierz polecenie **Dodaj** > **nowy projekt.**

    4. W oknie **Dodaj nowy projekt** po lewej stronie wybierz kategorię Pulpit systemu **Windows** w obszarze **Visual C#** lub **Visual Basic**.

    5. Wybierz szablon **Aplikacji konsoli (.NET Framework)** i wprowadź *gettingstartedhost* dla **nazwy**. Kliknij przycisk **OK**.

2. Dodaj odwołanie w projekcie **GettingStartedHost** do projektu **GettingStartedLib:**

    1. W oknie **Eksplorator rozwiązań** wybierz folder **Odwołania** w ramach projektu **GettingStartedHost,** a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów.

    2. W oknie dialogowym **Dodawanie odwołania** w obszarze **Projekty** po lewej stronie okna wybierz pozycję **Rozwiązanie**.

    3. Wybierz **pozycję GettingStartedLib** w środkowej części okna, a następnie wybierz przycisk **OK**.

       Ta akcja sprawia, że typy zdefiniowane w projekcie **GettingStartedLib** dostępne dla **projektu GettingStartedHost.**

3. Dodaj odwołanie w projekcie **GettingStartedHost** do <xref:System.ServiceModel> zestawu:

    1. W oknie **Eksplorator rozwiązań** wybierz folder **Odwołania** w ramach projektu **GettingStartedHost,** a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów.

    2. W oknie **Dodaj odwołanie** w obszarze **Zestawy** po lewej stronie okna wybierz pozycję **Framework**.

    3. Wybierz **opcję System.ServiceModel**, a następnie wybierz **przycisk OK**.

    4. Zapisz rozwiązanie, wybierając **pozycję Zapisz** > **wszystkie**pliki .

## <a name="add-code-to-host-the-service"></a>Dodaj kod do hostowania usługi

Aby hostować usługę, należy dodać kod, aby wykonać następujące czynności:

1. Utwórz identyfikator URI dla adresu podstawowego.
2. Utwórz wystąpienie klasy do obsługi usługi.
3. Tworzenie punktu końcowego usługi.
4. Włącz wymianę metadanych.
5. Otwórz hosta usługi, aby nasłuchiwać wiadomości przychodzących.
  
Wprowadzać następujące zmiany w kodzie:

1. Otwórz plik **Program.cs** lub **Module1.vb** w projekcie **GettingStartedHost** i zastąp jego kod następującym kodem:

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

    Aby uzyskać informacje o tym, jak działa ten kod, zobacz [Kroki programu hostingu usługi](#service-hosting-program-steps).

2. Zaktualizuj właściwości projektu:

   1. W oknie **Eksplorator rozwiązań** wybierz folder **GettingStartedHost,** a następnie z menu **skrótów** wybierz polecenie Właściwości.

   2. Na stronie **Właściwości GettingStartedHost** wybierz kartę **Aplikacja:**

      - W przypadku projektów w języku C# wybierz pozycję **GettingStartedHost.Program** z listy **obiektów uruchamiania.**

      - W przypadku projektów języka Visual Basic wybierz pozycję **Service.Program** z listy **obiektów Uruchamianie.**

   3. Z menu **Plik** wybierz polecenie **Zapisz wszystko**.

## <a name="verify-the-service-is-working"></a>Sprawdź, czy usługa działa

1. Skompiluj rozwiązanie, a następnie uruchom aplikację konsoli **GettingStartedHost** z wewnątrz programu Visual Studio.

    Usługa musi być uruchamiana z uprawnieniami administratora. Ponieważ program Visual Studio został otwarty z uprawnieniami administratora, po uruchomieniu **GettingStartedHost** w programie Visual Studio, aplikacja jest również uruchamiana z uprawnieniami administratora. Alternatywnie można otworzyć nowy wiersz polecenia jako administrator (wybierz **pozycję Więcej** > **Uruchom jako administrator** z menu skrótów) i uruchomić w nim plik **GettingStartedHost.exe.**

2. Otwórz przeglądarkę internetową i przejdź do strony `http://localhost:8000/GettingStarted/CalculatorService`usługi pod adresem .

   > [!NOTE]
   > Usługi takie jak ten wymagają odpowiedniego uprawnienia do rejestrowania adresów HTTP na komputerze do nasłuchiwania. Konta administratorów mają to uprawnienie, ale konta niebędące administratorami muszą mieć uprawnienia do obszarów nazw HTTP. Aby uzyskać więcej informacji na temat konfigurowania rezerwacji obszaru nazw, zobacz [Konfigurowanie protokołu HTTP i HTTPS](feature-details/configuring-http-and-https.md).

## <a name="service-hosting-program-steps"></a>Kroki programu hostingu usług

Kroki w kodzie dodany do hosta usługi są opisane w następujący sposób:

- **Krok 1:** Utwórz `Uri` wystąpienie klasy, aby pomieścić adres podstawowy usługi. Adres URL zawierający adres podstawowy ma opcjonalny identyfikator URI identyfikujący usługę. Adres podstawowy jest sformatowany w następujący sposób: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`. Adres podstawowy usługi kalkulatora używa transportu HTTP, localhost, port 8000 i segmentu URI, GettingStarted.

- **Krok 2:** Utwórz <xref:System.ServiceModel.ServiceHost> wystąpienie klasy, której używasz do hostowania usługi. Konstruktor przyjmuje dwa parametry: typ klasy, która implementuje kontrakt serwisowy i adres podstawowy usługi.

- **Krok 3:** <xref:System.ServiceModel.Description.ServiceEndpoint> Utwórz wystąpienie. Punkt końcowy usługi składa się z adresu, powiązania i umowy serwisowej. Konstruktor <xref:System.ServiceModel.Description.ServiceEndpoint> składa się z typu interfejsu umowy serwisowej, powiązania i adresu. Umowa serwisowa `ICalculator`jest , które zostały zdefiniowane i implementowane w typie usługi. Powiązanie dla tego <xref:System.ServiceModel.WSHttpBinding>przykładu jest , który jest wbudowanym powiązaniem i łączy się z punktami końcowymi, które są zgodne ze specyfikacjami WS-*. Aby uzyskać więcej informacji na temat powiązań WCF, zobacz [omówienie powiązań WCF](bindings-overview.md). Należy dołączyć adres do adresu podstawowego, aby zidentyfikować punkt końcowy. Kod określa adres jako CalculatorService i w pełni kwalifikowany `http://localhost:8000/GettingStarted/CalculatorService`adres dla punktu końcowego jako .

    > [!IMPORTANT]
    > W przypadku platformy .NET Framework w wersji 4 i nowszej dodawanie punktu końcowego usługi jest opcjonalne. W przypadku tych wersji, jeśli nie dodasz kodu lub konfiguracji, WCF dodaje jeden domyślny punkt końcowy dla każdej kombinacji adresu podstawowego i umowy zaimplementowane przez usługę. Aby uzyskać więcej informacji o domyślnych punktach końcowych, zobacz [Określanie adresu punktu końcowego](specifying-an-endpoint-address.md). Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [uproszczona konfiguracja usług WCF](samples/simplified-configuration-for-wcf-services.md).

- **Krok 4:** Włącz wymianę metadanych. Klienci używają wymiany metadanych do generowania serwerów proxy do wywoływania operacji usługi. Aby włączyć wymianę metadanych, utwórz wystąpienie, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ustaw jego <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> właściwość `true`na , i dodaj `ServiceMetadataBehavior` obiekt do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekcji <xref:System.ServiceModel.ServiceHost> wystąpienia.

- **Krok 5:** Otwórz, <xref:System.ServiceModel.ServiceHost> aby nasłuchiwać przychodzących wiadomości. Aplikacja czeka na naciśnięcie klawisza **Enter**. Po wystąpieniu <xref:System.ServiceModel.ServiceHost>aplikacji wykonuje blok try/catch. Aby uzyskać więcej informacji na <xref:System.ServiceModel.ServiceHost>temat bezpiecznego przechwytywania wyjątków zgłaszanych przez program , zobacz [Użyj zamknij i Przerwij, aby zwolnić zasoby klienta WCF.](samples/use-close-abort-release-wcf-client-resources.md)

> [!IMPORTANT]
> Po dodaniu biblioteki usługi WCF, Visual Studio hostuje go dla Ciebie, jeśli debugować go przez uruchomienie hosta usługi. Aby uniknąć konfliktów, można uniemożliwić visual studio z hostingu biblioteki usługi WCF.
>
> 1. Wybierz projekt **GettingStartedLib** w **Eksploratorze rozwiązań** i wybierz polecenie Właściwości z menu **skrótów.**
> 2. Wybierz **opcję Opcje WCF** i odznacz **opcję Uruchom hosta usługi WCF podczas debugowania innego projektu w tym samym rozwiązaniu**.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Tworzenie i konfigurowanie projektu aplikacji konsoli do obsługi usługi WCF.
> - Dodaj kod do hostowania usługi WCF.
> - Zaktualizuj plik konfiguracyjny.
> - Uruchom usługę WCF i sprawdź, czy jest uruchomiona.

Przejdź do następnego samouczka, aby dowiedzieć się, jak utworzyć klienta WCF.

> [!div class="nextstepaction"]
> [Samouczek: Tworzenie klienta WCF](how-to-create-a-wcf-client.md)
