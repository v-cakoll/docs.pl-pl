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
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>Samouczek: Hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation

W tym samouczku opisano trzeci pięć zadania wymagane do utworzenia podstawowej aplikacji Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, zobacz [samouczka: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation](getting-started-tutorial.md).

Następne zadanie do tworzenia aplikacji WCF jest hostowanie usługi WCF w aplikacji konsoli. Usługa WCF ujawnia co najmniej jeden *punktów końcowych*, z których każdy ujawnia co najmniej jednej operacji usługi. Punkt końcowy usługi określa następujące informacje: 
- Adres, gdzie można znaleźć usługi.
- Wiązanie, który zawiera informacje opisujące, jak klientowi komunikowanie się z usługą. 
- Kontrakt definiujący funkcje, które usługa zapewnia swoim klientom.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> - Utwórz i skonfiguruj projekt aplikacji konsoli do hostowania usługi WCF.
> - Dodaj kod do obsługi usługi WCF.
> - Należy zaktualizować plik konfiguracji.
> - Uruchom usługę WCF i weryfikować ją jest uruchomiona.

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>Tworzenie i konfigurowanie projektu aplikacji konsoli w do hostowania usługi

1. Utwórz projekt aplikacji konsoli w programie Visual Studio: 
 
    1. Z **pliku** menu, wybierz opcję **Otwórz** > **projekt/rozwiązanie** i przejdź do **GettingStarted** rozwiązania możesz wcześniej utworzony (*GettingStarted.sln*). Wybierz pozycję **Otwórz**.

    2. Z **widoku** menu, wybierz opcję **Eksploratora rozwiązań**.
    
    3. W **Eksploratora rozwiązań** wybierz **GettingStarted** rozwiązania (najwyższy węzeł), a następnie wybierz **Dodaj** > **nowy projekt** z menu skrótów. 

    4. W **Dodaj nowy projekt** oknie po lewej stronie wybierz **pulpitu Windows** kategorię w obszarze **Visual C#**  lub **języka Visual Basic**. 

    5. Wybierz **Aplikacja konsoli (.NET Framework)** szablonu, a następnie wprowadź *GettingStartedHost* dla **nazwa**. Kliknij przycisk **OK**.

2. Dodaj odwołanie w **GettingStartedHost** projekt **GettingStartedLib** projektu: 

    1. W **Eksploratora rozwiązań** wybierz **odwołania** folderze **GettingStartedHost** projektu, a następnie wybierz **Dodaj odwołanie** z menu skrótów. 

    2. W **Dodaj odwołanie** okna dialogowego, w obszarze **projektów** w lewej części okna wybierz **rozwiązania**. 
 
    3. Wybierz **GettingStartedLib** w Centrum części okna, a następnie wybierz pozycję **OK**. 

       Ta akcja powoduje, że typy zdefiniowane w **GettingStartedLib** dostępnych do projektu **GettingStartedHost** projektu.

3. Dodaj odwołanie w **GettingStartedHost** projekt <xref:System.ServiceModel> zestawu: 

    1. W **Eksploratora rozwiązań** wybierz **odwołania** folderze **GettingStartedHost** projektu, a następnie wybierz **Dodaj odwołanie** z menu skrótów.
    
    2. W **Dodaj odwołanie** okna, w obszarze **zestawy** w lewej części okna wybierz **Framework**. 

    3. Wybierz **System.ServiceModel**, a następnie wybierz pozycję **OK**. 
    
    4. Zapisz rozwiązanie, wybierając **pliku** > **Zapisz wszystko**.

## <a name="add-code-to-host-the-service"></a>Dodaj kod do obsługi usługi

Do obsługi usługi, możesz dodać kod, aby wykonać poniższe kroki: 
   1. Utwórz identyfikator URI dla adresu podstawowego.
   2. Utwórz wystąpienie klasy do obsługi usługi.
   3. Tworzenie punktu końcowego usługi.
   4. Włącz wymiany metadanych.
   5. Otwórz hosta usługi do nasłuchiwania pod kątem przychodzących wiadomości.
  
Wprowadź następujące zmiany w kodzie:

1. Otwórz **Program.cs** lub **Module1.vb** w pliku **GettingStartedHost** projektu i zastąp jego kod poniższym kodem:

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
    
    Aby uzyskać informacje o tym, jak działa ten kod, zobacz [usług obsługującego program kroki](#service-hosting-program-steps).

2. Zaktualizuj właściwości projektu:

   1. W **Eksploratora rozwiązań** wybierz **GettingStartedHost** folder, a następnie wybierz **właściwości** z menu skrótów.

   2. Na **GettingStartedHost** strony właściwości, zaznacz **aplikacji** karty:

      - Aby uzyskać C# projektów, wybierz opcję **GettingStartedHost.Program** z **obiekt początkowy** listy.

      - Dla projektów języka Visual Basic, wybierz **Service.Program** z **obiekt początkowy** listy.

   3. Z **pliku** menu, wybierz opcję **Zapisz wszystko**.

## <a name="verify-the-service-is-working"></a>Sprawdź, czy usługa działa

1. Skompiluj rozwiązanie, a następnie uruchom **GettingStartedHost** konsoli aplikacji z poziomu programu Visual Studio. 

    Usługa musi być uruchamiane z uprawnieniami administratora. Ponieważ otwarty program Visual Studio z uprawnieniami administratora, po uruchomieniu **GettingStartedHost** w programie Visual Studio z uprawnieniami administratora oraz uruchomieniu aplikacji. Alternatywnie, można otworzyć wiersz polecenia jako administrator (wybierz **więcej** > **Uruchom jako administrator** z menu skrótów) i uruchom **GettingStartedHost.exe**  znajdujący się w nim.

2. Otwórz przeglądarkę internetową i przejdź do strony usługi na `http://localhost:8000/GettingStarted/CalculatorService`.
   
   > [!NOTE]
   > Usługi, takie jak tego wymaga odpowiednie uprawnienia, aby zarejestrować adresy HTTP na komputerze w celu nasłuchiwania. Administrator konta mają to uprawnienie, ale konta bez uprawnień administratora musi mieć uprawnienie dla przestrzeni nazw protokołu HTTP. Aby uzyskać więcej informacji o sposobie konfigurowania rezerwacji przestrzeni nazw, zobacz [Konfigurowanie protokołów HTTP i HTTPS](feature-details/configuring-http-and-https.md). 

## <a name="service-hosting-program-steps"></a>Usługa hostingu programu kroki

Kroki opisane w kod, który został dodany do hosta usługi są opisane na następujący:

- **Krok 1**: Utwórz wystąpienie obiektu `Uri` klasy utrzymującej adres podstawowy usługi. Adres URL, który zawiera adres podstawowy ma opcjonalny identyfikator URI, który identyfikuje usługę. Adres podstawowy jest sformatowany w następujący sposób: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`. Adres podstawowy usługi Kalkulator korzysta z protokołu HTTP "," localhost "," port 8000 "i" segmentem identyfikatora URI, GettingStarted.

- **Krok 2**: Utwórz wystąpienie obiektu <xref:System.ServiceModel.ServiceHost> klasy, których używasz do obsługi usługi. Konstruktor przyjmuje dwa parametry: typ klasy, która implementuje kontrakt usługi i podstawowego adresu usługi.

- **Krok 3**: Utwórz <xref:System.ServiceModel.Description.ServiceEndpoint> wystąpienia. Punkt końcowy usługi składa się z adresu, powiązanie i kontraktu usługi. <xref:System.ServiceModel.Description.ServiceEndpoint> Konstruktor składa się z typu interfejsu kontraktu usługi, powiązanie i adres. Umowa serwisowa jest `ICalculator`, zdefiniowane przez użytkownika, która implementuje typu usługi. Powiązanie dla tego przykładu jest <xref:System.ServiceModel.WSHttpBinding>, która jest wbudowana powiązania i nawiązanie połączenia z punktami końcowymi, które odpowiadają WS-* specyfikacji. Aby uzyskać więcej informacji na temat wiązania WCF, zobacz [omówienie powiązań WCF](bindings-overview.md). Można dołączyć adres na adres bazowy do identyfikowania punktu końcowego. Kod określa adres CalculatorService oraz adres FQDN dla punktu końcowego jako `http://localhost:8000/GettingStarted/CalculatorService`.

    > [!IMPORTANT]
    > Dla programu .NET Framework w wersji 4 i nowszych dodanie punktu końcowego usługi jest opcjonalne. Dla tych wersji Jeśli nie dodasz kodu lub konfiguracji usługi WCF dodaje jeden domyślny punkt końcowy dla każdej kombinacji adresu podstawowego i kontrakt implementowane przez usługę. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [Określanie adresu punktu końcowego](specifying-an-endpoint-address.md). Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązania i zachowań, zobacz [konfiguracji uproszczony](simplified-configuration.md) i [uproszczony Konfiguracja usług WCF](samples/simplified-configuration-for-wcf-services.md).

- **Krok 4**: Włącz wymiany metadanych. Klienci używają wymiany metadanych do Generowanie serwerów proxy do wywoływania operacji usługi. Aby włączyć wymiany metadanych, Utwórz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienia, ustaw jego <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> właściwości `true`i Dodaj `ServiceMetadataBehavior` obiekt <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> zbiór <xref:System.ServiceModel.ServiceHost> wystąpienia.

- **Krok 5**: Otwórz <xref:System.ServiceModel.ServiceHost> do nasłuchiwania pod kątem przychodzących wiadomości. Aplikacja oczekuje na naciśnij **Enter**. Po tworzy wystąpienie aplikacji <xref:System.ServiceModel.ServiceHost>, wykonuje bloku try/catch. Aby uzyskać więcej informacji na temat bezpiecznego przechwytywanie wyjątków zgłaszanych przez <xref:System.ServiceModel.ServiceHost>, zobacz [Użyj Zamknij i Abort, aby zwolnić zasoby klienta WCF](samples/use-close-abort-release-wcf-client-resources.md).

> [!IMPORTANT]
> Po dodaniu biblioteki usługi WCF, Visual Studio umieszcza dla Ciebie Jeśli debugujesz przez uruchomienie hosta usługi. Aby uniknąć konfliktów, można zapobiec programu Visual Studio hostowanie biblioteki usługi WCF. 
> 1. Wybierz **GettingStartedLib** projektu w **Eksploratora rozwiązań** i wybierz polecenie **właściwości** z menu skrótów.
> 2. Wybierz **opcje WCF** i usuń zaznaczenie pola wyboru **Start podczas debugowania innego projektu w tym samym rozwiązaniu Host usługi WCF**.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> - Utwórz i skonfiguruj projekt aplikacji konsoli do hostowania usługi WCF.
> - Dodaj kod do obsługi usługi WCF.
> - Należy zaktualizować plik konfiguracji.
> - Uruchom usługę WCF i weryfikować ją jest uruchomiona.

Przejdź do następnego samouczka, aby dowiedzieć się, jak można utworzyć klienta WCF.

> [!div class="nextstepaction"]
> [Samouczek: Utworzenie klienta WCF](how-to-create-a-wcf-client.md)
