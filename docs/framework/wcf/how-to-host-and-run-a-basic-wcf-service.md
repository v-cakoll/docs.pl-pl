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
ms.openlocfilehash: 984c5e73a8efc4e9c2d487485267868ffa2f60f3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928725"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>Samouczek: Hostowanie i uruchamianie podstawowej usługi Windows Communication Foundation

W tym samouczku opisano trzecią z pięciu zadań wymaganych do utworzenia aplikacji podstawowej Windows Communication Foundation (WCF). Aby zapoznać się z omówieniem samouczków, [zobacz Samouczek: Rozpocznij pracę z aplikacjami](getting-started-tutorial.md)Windows Communication Foundation.

Następnym zadaniem do tworzenia aplikacji WCF jest Hostowanie usługi WCF w aplikacji konsolowej. Usługa WCF udostępnia jeden lub więcej *punktów końcowych*, z których każdy udostępnia jedną lub więcej operacji usługi. Punkt końcowy usługi określa następujące informacje:

- Adres, na którym można znaleźć usługę.
- Powiązanie zawierające informacje opisujące, jak klient musi komunikować się z usługą. 
- Kontrakt definiujący funkcje udostępniane klientom przez usługę.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Utwórz i skonfiguruj projekt aplikacji konsoli na potrzeby hostowania usługi WCF.
> - Dodaj kod do hostowania usługi WCF.
> - Zaktualizuj plik konfiguracji.
> - Uruchom usługę WCF i sprawdź, czy jest uruchomiona.

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>Tworzenie i Konfigurowanie projektu aplikacji konsolowej na potrzeby hostowania usługi

1. Utwórz projekt aplikacji konsolowej w programie Visual Studio: 
 
    1. Z menu **plik** wybierz pozycję **Otwórz** > **projekt/rozwiązanie** i przejdź do utworzonego wcześniej rozwiązania **GettingStarted** (*GettingStarted. sln*). Wybierz pozycję **Otwórz**.

    2. Z menu **Widok** wybierz pozycję **Eksplorator rozwiązań**.
    
    3. W oknie **Eksplorator rozwiązań** wybierz rozwiązanie **GettingStarted** (górny węzeł), a następnie wybierz pozycję **Dodaj** > **Nowy projekt** z menu skrótów. 

    4. W oknie **Dodaj nowy projekt** po lewej stronie wybierz kategorię **pulpit systemu Windows** w obszarze **Wizualizacja C#**  lub **Visual Basic**. 

    5. Wybierz szablon **aplikacja konsoli (.NET Framework)** , a następnie wprowadź *GettingStartedHost* jako **nazwę**. Kliknij przycisk **OK**.

2. Dodaj odwołanie w projekcie **GettingStartedHost** do projektu **GettingStartedLib** : 

    1. W oknie **Eksplorator rozwiązań** wybierz folder **odwołania** w projekcie **GettingStartedHost** , a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów. 

    2. W oknie dialogowym **Dodawanie odwołania** w obszarze **projekty** po lewej stronie okna wybierz pozycję **rozwiązanie**. 
 
    3. Wybierz pozycję **GettingStartedLib** w środkowej sekcji okna, a następnie wybierz przycisk **OK**. 

       Ta akcja powoduje, że typy zdefiniowane w projekcie **GettingStartedLib** są dostępne dla projektu **GettingStartedHost** .

3. Dodaj odwołanie do <xref:System.ServiceModel> zestawu w projekcie **GettingStartedHost** : 

    1. W oknie **Eksplorator rozwiązań** wybierz folder **odwołania** w projekcie **GettingStartedHost** , a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów.
    
    2. W oknie **Dodaj odwołanie** w obszarze **zestawy** po lewej stronie okna wybierz pozycję **Struktura**. 

    3. Wybierz **System. ServiceModel**, a następnie wybierz **przycisk OK**. 
    
    4. Zapisz rozwiązanie, wybierając kolejno pozycje **plik** > **Zapisz wszystko**.

## <a name="add-code-to-host-the-service"></a>Dodawanie kodu do obsługi usługi

Aby hostować usługę, należy dodać kod w celu wykonania następujących czynności: 

1. Utwórz identyfikator URI dla adresu podstawowego.
2. Utwórz wystąpienie klasy do hostowania usługi.
3. Utwórz punkt końcowy usługi.
4. Włącz wymianę metadanych.
5. Otwórz hosta usługi, aby nasłuchiwać komunikatów przychodzących.
  
Wprowadź następujące zmiany w kodzie:

1. Otwórz plik **program.cs** lub **Module1. vb** w projekcie **GettingStartedHost** i Zastąp jego kod następującym kodem:

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
    
    Aby uzyskać informacje o tym, jak działa ten kod, zobacz [kroki programu hostingu usług](#service-hosting-program-steps).

2. Aktualizowanie właściwości projektu:

   1. W oknie **Eksplorator rozwiązań** wybierz folder **GettingStartedHost** , a następnie wybierz polecenie **Właściwości** z menu skrótów.

   2. Na stronie właściwości **GettingStartedHost** wybierz kartę **aplikacja** :

      - W C# obszarze projekty wybierz pozycję **GettingStartedHost. program** z listy **obiekt startowy** .

      - W przypadku projektów Visual Basic wybierz pozycję **Service. program** z listy **obiektów początkowych** .

   3. Z menu **plik** wybierz pozycję **Zapisz wszystko**.

## <a name="verify-the-service-is-working"></a>Sprawdź, czy usługa działa

1. Skompiluj rozwiązanie, a następnie uruchom aplikację konsolową **GettingStartedHost** z wewnątrz programu Visual Studio. 

    Usługa musi być uruchomiona z uprawnieniami administratora. Ponieważ program Visual Studio został otwarty z uprawnieniami administratora, po uruchomieniu programu **GettingStartedHost** w programie Visual Studio aplikacja jest również uruchamiana z uprawnieniami administratora. Alternatywnie możesz otworzyć nowy wiersz polecenia jako administrator (wybierz opcję **więcej** > **Uruchom jako administrator** z menu skrótów) i uruchomić **GettingStartedHost. exe** w tym obszarze.

2. Otwórz przeglądarkę internetową i przejdź do strony usługi pod adresem `http://localhost:8000/GettingStarted/CalculatorService`.
   
   > [!NOTE]
   > Takie usługi, jak to jest wymagane, muszą mieć odpowiednie uprawnienia do rejestrowania adresów HTTP na maszynie do nasłuchiwania. Konta administratorów mają to uprawnienie, ale konta niebędące administratorami muszą mieć uprawnienia do przestrzeni nazw protokołu HTTP. Więcej informacji o sposobie konfigurowania rezerwacji przestrzeni nazw znajduje się w temacie [Konfigurowanie protokołów HTTP i https](feature-details/configuring-http-and-https.md). 

## <a name="service-hosting-program-steps"></a>Kroki programu hostingu usług

Kroki w kodzie dodanym do hostowania usługi są opisane w następujący sposób:

- **Krok 1**: Utwórz wystąpienie `Uri` klasy w celu przechowywania adresu podstawowego usługi. Adres URL, który zawiera adres podstawowy, ma opcjonalny identyfikator URI, który identyfikuje usługę. Adres podstawowy jest sformatowany w następujący sposób: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`. Adres podstawowy usługi kalkulatora używa transportu HTTP, localhost, portu 8000 i segmentu URI GettingStarted.

- **Krok 2**: Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> klasy, która będzie używana do hostowania usługi. Konstruktor przyjmuje dwa parametry: typ klasy implementującej kontrakt usługi i adres podstawowy usługi.

- **Krok 3**. <xref:System.ServiceModel.Description.ServiceEndpoint> Utwórz wystąpienie. Punkt końcowy usługi składa się z adresu, powiązania i kontraktu usługi. <xref:System.ServiceModel.Description.ServiceEndpoint> Konstruktor składa się z typu interfejsu kontraktu usługi, powiązania i adresu. Kontrakt usługi jest `ICalculator`zdefiniowany i zaimplementowany w typie usługi. Powiązanie dla tego przykładu jest <xref:System.ServiceModel.WSHttpBinding>, które jest wbudowanym powiązaniem i łączy się z punktami końcowymi, które są zgodne ze specyfikacjami WS-*. Aby uzyskać więcej informacji na temat powiązań WCF, zobacz temat [powiązania WCF — Omówienie](bindings-overview.md). Adres jest dołączany do adresu podstawowego, aby zidentyfikować punkt końcowy. Kod określa adres jako CalculatorService oraz w pełni kwalifikowany adres punktu końcowego jako `http://localhost:8000/GettingStarted/CalculatorService`.

    > [!IMPORTANT]
    > W przypadku .NET Framework w wersji 4 i nowszych dodanie punktu końcowego usługi jest opcjonalne. W przypadku tych wersji, jeśli nie dodasz kodu lub konfiguracji, program WCF dodaje jeden domyślny punkt końcowy dla każdej kombinacji adresu podstawowego i kontraktu zaimplementowanego przez usługę. Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, zobacz [Określanie adresu punktu końcowego](specifying-an-endpoint-address.md). Aby uzyskać więcej informacji na temat domyślnych punktów końcowych, powiązań i zachowań, zobacz [Uproszczona konfiguracja](simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](samples/simplified-configuration-for-wcf-services.md).

- **Krok 4**. Włącz wymianę metadanych. Klienci używają wymiany metadanych do generowania serwerów proxy na potrzeby wywoływania operacji usługi. Aby włączyć wymianę metadanych, Utwórz <xref:System.ServiceModel.Description.ServiceMetadataBehavior> wystąpienie, ustaw jego <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> Właściwość `ServiceMetadataBehavior` na `true`, a następnie <xref:System.ServiceModel.ServiceHost> Dodaj obiekt do <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> kolekcji wystąpień.

- **Krok 5**. Otwórz <xref:System.ServiceModel.ServiceHost> , aby nasłuchiwać wiadomości przychodzących. Aplikacja czeka na naciśnięcie klawisza **Enter**. Po utworzeniu wystąpienia <xref:System.ServiceModel.ServiceHost>aplikacji wykonuje blok try/catch. Aby uzyskać więcej informacji na temat bezpiecznego przechwytywania wyjątków zgłoszonych przez <xref:System.ServiceModel.ServiceHost>program, zobacz [Używanie funkcji Close i Abort w celu zwolnienia zasobów klienta WCF](samples/use-close-abort-release-wcf-client-resources.md).

> [!IMPORTANT]
> Po dodaniu biblioteki usług WCF program Visual Studio hostuje ją w przypadku debugowania przez uruchomienie hosta usługi. Aby uniknąć konfliktów, można uniemożliwić programowi Visual Studio hostowanie biblioteki usług WCF. 
>
> 1. Wybierz projekt **GettingStartedLib** w **Eksplorator rozwiązań** a następnie wybierz **Właściwości** z menu skrótów.
> 2. Wybierz **Opcje WCF** i usuń zaznaczenie pozycji **Uruchom hosta usługi WCF podczas debugowania innego projektu w tym samym rozwiązaniu**.

## <a name="next-steps"></a>Następne kroki

W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Utwórz i skonfiguruj projekt aplikacji konsoli na potrzeby hostowania usługi WCF.
> - Dodaj kod do hostowania usługi WCF.
> - Zaktualizuj plik konfiguracji.
> - Uruchom usługę WCF i sprawdź, czy jest uruchomiona.

Przejdź do następnego samouczka, aby dowiedzieć się, jak utworzyć klienta WCF.

> [!div class="nextstepaction"]
> [Samouczek: Tworzenie klienta WCF](how-to-create-a-wcf-client.md)
