---
title: Tworzenie długo działającej usługi przepływu pracy
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: dae33cfcd5a2ef7b5269ebb040cf53b4c0e0b039
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945595"
---
# <a name="creating-a-long-running-workflow-service"></a>Tworzenie długo działającej usługi przepływu pracy
W tym temacie opisano sposób tworzenia długotrwałej usługi przepływu pracy. Długotrwałe usługi przepływu pracy mogą działać przez długi czas. W pewnym momencie przepływ pracy może przejść w stan bezczynności, aby uzyskać dodatkowe informacje. W takim przypadku przepływ pracy został utrwalony w bazie danych SQL i zostanie usunięty z pamięci. Po udostępnieniu dodatkowych informacji wystąpienie przepływu pracy jest ładowane z powrotem do pamięci i kontynuuje wykonywanie.  W tym scenariuszu wdrażasz bardzo uproszczony system określania kolejności.  Klient wysyła początkowy komunikat do usługi przepływu pracy w celu uruchomienia zamówienia. Zwraca identyfikator zamówienia do klienta. W tym momencie usługa przepływu pracy oczekuje na inną wiadomość od klienta i przejdzie w stan bezczynności i zostanie utrwalona w SQL Server bazie danych.  Gdy klient wyśle następny komunikat w celu uporządkowania elementu, usługa przepływu pracy zostanie ponownie załadowana do pamięci i zakończy przetwarzanie zamówienia. W przykładzie kodu zwraca ciąg informujący o tym, że element został dodany do zamówienia. Przykład kodu nie jest to rzeczywista światowa aplikacja technologii, ale raczej prosty przykład, który ilustruje długotrwałe uruchamianie usług przepływu pracy. W tym temacie założono, że wiesz już, jak tworzyć projekty i rozwiązania w programie Visual Studio 2012.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby móc korzystać z tego przewodnika, musisz mieć zainstalowane następujące oprogramowanie:

1. Microsoft SQL Server 2008

2. Visual Studio 2012

3. Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]

4. Znasz już programy WCF i Visual Studio 2012 i wiesz, jak tworzyć projekty/rozwiązania.

### <a name="to-setup-the-sql-database"></a>Aby skonfigurować SQL Database

1. Aby wystąpienia usługi przepływu pracy były utrwalane, musisz mieć zainstalowaną Microsoft SQL Server i należy skonfigurować bazę danych do przechowywania utrwalonych wystąpień przepływu pracy. Uruchom program Microsoft SQL Management Studio, klikając przycisk **Start** , wybierając pozycję **wszystkie programy**, **Microsoft SQL Server 2008**i **Microsoft SQL Management Studio**.

2. Kliknij przycisk **Połącz** , aby zalogować się do wystąpienia SQL Server

3. Kliknij prawym przyciskiem myszy **bazę danych** w widoku drzewa, a następnie wybierz pozycję **Nowa baza danych.** Aby utworzyć nową bazę danych o `SQLPersistenceStore`nazwie.

4. Uruchom plik skryptu SqlWorkflowInstanceStoreSchema. SQL znajdujący się w katalogu C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en w bazie danych SQLPersistenceStore, aby skonfigurować wymaganą schemat bazy danych.

5. Uruchom plik skryptu SqlWorkflowInstanceStoreLogic. SQL znajdujący się w katalogu C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en w bazie danych SQLPersistenceStore, aby skonfigurować wymaganą logikę bazy danych.

### <a name="to-create-the-web-hosted-workflow-service"></a>Aby utworzyć usługę hostowanego przepływu pracy w sieci Web

1. Utwórz puste rozwiązanie programu Visual Studio 2012 i nadaj mu `OrderProcessing`nazwę.

2. Dodaj nowy projekt aplikacji usługi przepływu pracy WCF o `OrderService` nazwie do rozwiązania.

3. W oknie dialogowym właściwości projektu wybierz kartę **Sieć Web** .

    1. W obszarze **Akcja początkowa** wybierz **określoną stronę** i `Service1.xamlx`Określ.

         ![Właściwości sieci Web projektu usługi przepływu pracy](./media/creating-a-long-running-workflow-service/start-action-specific-page-option.png "Tworzenie opcji strony dotyczącej usługi przepływu pracy hostowanej w sieci Web")

    2. W obszarze **serwery** wybierz opcję **Użyj lokalnego serwera sieci Web IIS**.

         ![Ustawienia lokalnego serwera sieci Web](./media/creating-a-long-running-workflow-service/use-local-web-server.png "Tworzenie usługi hostowanego przepływu pracy w sieci Web — opcja Użyj lokalnego serwera sieci Web usług IIS")

        > [!WARNING]
        >  Aby to ustawienie było możliwe, należy uruchomić program Visual Studio 2012 w trybie administratora.

         Te dwa kroki umożliwiają skonfigurowanie projektu usługi przepływu pracy do hostowania przez usługi IIS.

4. Otwórz `Service1.xamlx` , jeśli nie jest jeszcze otwarty i Usuń istniejące działania **ReceiveRequest** i **SendResponse** .

5. Wybierz działanie **usługi sekwencyjnej** i kliknij link **zmienne** , a następnie Dodaj zmienne pokazane na poniższej ilustracji. Spowoduje to dodanie niektórych zmiennych, które będą używane później w usłudze przepływu pracy.

    > [!NOTE]
    > Jeśli obiekt CorrelationHandle nie znajduje się na liście rozwijanej Typ zmiennej, wybierz pozycję **Przeglądaj w poszukiwaniu typów** z listy rozwijanej. Wpisz obiekt CorrelationHandle w polu **Nazwa typu** wybierz pozycję obiekt CorrelationHandle z listy kontrolnej, a następnie kliknij przycisk **OK**.

     ![Dodaj zmienne](./media/creating-a-long-running-workflow-service/add-variables-sequential-service-activity.gif "Dodaj zmienne do działania usługi sekwencyjnej.")

6. Przeciągnij i upuść szablon działania **ReceiveAndSendReply** do działania **sekwencyjnego usługi** . Ten zestaw działań otrzyma komunikat od klienta i wyśle odpowiedź z powrotem.

    1. Wybierz działanie **Odbierz** i ustaw właściwości wyróżnione na poniższej ilustracji.

         ![Ustawianie właściwości działania Odbierz](./media/creating-a-long-running-workflow-service/set-receive-activity-properties.png "Ustaw właściwości działania Odbierz.")

         Właściwość DisplayName ustawia nazwę wyświetlaną dla działania Receive w projektancie. Właściwości ServiceContractName i OperationName określają nazwę kontraktu usługi i operacji, które są implementowane przez działanie Receive. Aby uzyskać więcej informacji na temat sposobu używania kontraktów w usługach przepływu pracy, zobacz [Używanie kontraktów w przepływie pracy](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).

    2. Kliknij link **Definiuj...** w działaniu **ReceiveStartOrder** i ustaw właściwości wyświetlane na poniższej ilustracji.  Zauważ, że przycisk radiowy **Parametry** jest zaznaczony, parametr o `p_customerName` nazwie `customerName` jest powiązany ze zmienną. Spowoduje to skonfigurowanie działania **odbioru** w celu odbierania pewnych danych i powiązania tych danych ze zmiennymi lokalnymi.

         ![Ustawianie danych odbieranych przez działanie Odbierz](./media/creating-a-long-running-workflow-service/set-properties-for-receive-content.png "Ustaw właściwości danych odbieranych przez działanie Receive.")

    3. Wybierz działanie **SendReplyToReceive** i ustaw wyróżnioną Właściwość widoczną na poniższej ilustracji.

         ![Ustawianie właściwości działania SendReply](./media/creating-a-long-running-workflow-service/set-properties-for-reply-activities.png "SetReplyProperties")

    4. Kliknij link **Definiuj...** w działaniu **SendReplyToStartOrder** i ustaw właściwości wyświetlane na poniższej ilustracji. Zauważ, że wybrano przycisk radiowy **Parametry** ; parametr o nazwie `p_orderId` jest powiązany `orderId` ze zmienną. To ustawienie określa, że działanie SendReplyToStartOrder zwróci wartość typu String do obiektu wywołującego.

         ![Konfigurowanie danych zawartości działania SendReply](./media/creating-a-long-running-workflow-service/setreplycontent-for-sendreplytostartorder-activity.png "Skonfiguruj ustawienie dla działania SetReplyToStartOrder.")

    5. Przeciągnij i upuść działanie przypisywania między działaniami **Receive** i **SendReply** i ustaw właściwości, jak pokazano na poniższej ilustracji:

         ![Dodawanie działania Assign](./media/creating-a-long-running-workflow-service/add-an-assign-activity.png "Dodaj działanie Assign.")

         Spowoduje to utworzenie nowego identyfikatora zamówienia i umieszczenie wartości w zmiennej IDZamówienia.

    6. Wybierz działanie **ReplyToStartOrder** . W oknie właściwości kliknij przycisk wielokropka dla **CorrelationInitializers**. Wybierz łącze **Dodaj inicjator** , wpisz `orderIdHandle` w polu tekstowym inicjatora wybierz inicjator korelacji zapytania dla typu korelacji, a następnie wybierz pozycję p_orderId w polu listy rozwijanej zapytania XPath. Te ustawienia są pokazane na poniższej ilustracji. Kliknij przycisk **OK**.  Powoduje to zainicjowanie korelacji między klientem a tym wystąpieniem usługi przepływu pracy. Po odebraniu komunikatu zawierającego ten identyfikator zamówienia jest on kierowany do tego wystąpienia usługi przepływu pracy.

         ![Dodawanie inicjatora korelacji](./media/creating-a-long-running-workflow-service/add-correlationinitializers.png "Dodaj inicjator korelacji.")

7. Przeciągnij i upuść inne **działanie ReceiveAndSendReply** na końcu przepływu pracy (poza **sekwencją** zawierającą pierwsze działania **Receive** i **SendReply** ). Spowoduje to odebranie drugiej wiadomości wysyłanej przez klienta i odreagowanie na nie.

    1. Wybierz **sekwencję** zawierającą nowo dodane działania **Receive** i **SendReply** , a następnie kliknij przycisk **zmienne** . Dodaj zmienną wyróżnioną na poniższej ilustracji:

         ![Dodawanie nowych zmiennych](./media/creating-a-long-running-workflow-service/add-the-itemid-variable.png "Dodaj zmienną ItemId.")
         
         Należy również `orderResult` dodać jako `Sequence` ciąg w zakresie.

    2. Wybierz działanie **Odbierz** i ustaw właściwości wyświetlane na poniższej ilustracji:

         ![Ustawianie właściwości działania Odbierz](./media/creating-a-long-running-workflow-service/set-receive-activities-properties.png "Ustaw właściwości Odbierz działania.")
         
         > [!NOTE]
         >  Nie zapomnij zmienić pola ServiceContractName z `../IAddItem`.

    3. Kliknij link **Definiuj...** w działaniu **ReceiveAddItem** i Dodaj parametry pokazane na poniższej ilustracji: spowoduje to skonfigurowanie działania odbioru w celu zaakceptowania dwóch parametrów, identyfikatora zamówienia i identyfikatora uporządkowanego elementu.

         ![Określanie parametrów dla drugiego odbioru](./media/creating-a-long-running-workflow-service/add-receive-two-parameters.png "Skonfiguruj działanie Odbierz, aby otrzymywać dwa parametry.")

    4. Kliknij przycisk wielokropka **CorrelateOn** , `orderIdHandle`a następnie wprowadź. W obszarze **zapytania XPath**kliknij strzałkę listy rozwijanej i wybierz `p_orderId`pozycję. Powoduje to skonfigurowanie korelacji w drugim działaniu Receive. Aby uzyskać więcej informacji na temat [](../../../../docs/framework/wcf/feature-details/correlation.md)korelacji, zobacz Korelacja.

         ![Ustawianie właściwości CorrelatesOn](./media/creating-a-long-running-workflow-service/correlateson-setting.png "Ustaw Właściwość CorrelatesOn.")

    5. Przeciągnij i upuść działanie **if** bezpośrednio po działaniu **ReceiveAddItem** . To działanie działa podobnie jak w przypadku instrukcji if.

        1. Ustaw właściwość **Condition** na`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`

        2. Przeciągnij i upuść działanie przypisywania do w sekcji **then** i inne w sekcji **else** ustaw właściwości działania **przypisane** , jak pokazano na poniższej ilustracji.

             ![Przypisywanie wyniku wywołania usługi](./media/creating-a-long-running-workflow-service/assign-result-of-service-call.png "Przypisz wynik wywołania usługi.")

             Jeśli warunek jest `true` wykonany, sekcja zostanie wykonana. Jeśli warunek jest `false` wykonywany w sekcji **else** .

        3. Wybierz działanie **SendReplyToReceive** i ustaw właściwość **DisplayName** pokazane na poniższej ilustracji.

             ![Ustawianie właściwości działania SendReply](./media/creating-a-long-running-workflow-service/send-reply-activity-property.png "Ustaw właściwość działania SendReply.")

        4. Kliknij link **Definiuj...** w działaniu **SetReplyToAddItem** i skonfiguruj go tak, jak pokazano na poniższej ilustracji. Spowoduje to skonfigurowanie działania **SendReplyToAddItem** w celu zwrócenia wartości w `orderResult` zmiennej.

             ![Ustawianie powiązania danych dla działania SendReply](./media/creating-a-long-running-workflow-service/set-property-for-sendreplytoadditem.gif "Ustaw właściwość dla działania SendReplyToAddItem.")

8. Otwórz plik Web. config i Dodaj następujące elementy w \<sekcji zachowanie >, aby włączyć trwałość przepływu pracy.

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    >  Upewnij się, że w poprzednim fragmencie kodu zastąpisz nazwę hosta i wystąpienie programu SQL Server.

9. Skompiluj rozwiązanie.

### <a name="to-create-a-client-application-to-call-the-workflow-service"></a>Aby utworzyć aplikację kliencką do wywoływania usługi przepływu pracy

1. Dodaj nowy projekt aplikacji konsoli o nazwie `OrderClient` do rozwiązania.

2. Dodaj odwołania do następujących zestawów do `OrderClient` projektu

    1. System.ServiceModel.dll

    2. System.ServiceModel.Activities.dll

3. Dodaj odwołanie do usługi przepływu pracy i określ `OrderService` jako przestrzeń nazw.

4. `Main()` W metodzie projektu klienta Dodaj następujący kod:

    ```
    static void Main(string[] args)
    {
       // Send initial message to start the workflow service
       Console.WriteLine("Sending start message");
       StartOrderClient startProxy = new StartOrderClient();
       string orderId = startProxy.StartOrder("Kim Abercrombie");

       // The workflow service is now waiting for the second message to be sent
       Console.WriteLine("Workflow service is idle...");
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");
       Console.ReadLine();

       // Send the second message
       Console.WriteLine("Sending add item message");
       AddItemClient addProxy = new AddItemClient();
       AddItem item = new AddItem();
       item.p_itemId = "Zune HD";
       item.p_orderId = orderId;

       string orderResult = addProxy.AddItem(item);
       Console.WriteLine("Service returned: " + orderResult);
    }
    ```

5. Skompiluj rozwiązanie i uruchom `OrderClient` aplikację. Klient wyświetli następujący tekst:

    ```Output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6. Aby sprawdzić, czy usługa przepływu pracy została utrwalona, uruchom SQL Server Management Studio, przechodząc do menu **Start** , wybierając kolejno pozycje **wszystkie programy**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.

    1. W okienku po lewej stronie rozwiń pozycję **bazy danych**, **SQLPersistenceStore**, **widoki** i kliknij prawym przyciskiem myszy pozycję **System. Activities. DurableInstancing. instances** , a następnie wybierz pozycję **Wybierz pierwsze 1000 wierszy**. W okienku **wyników** Sprawdź, czy na liście znajdują się co najmniej jedno wystąpienie. Mogą istnieć inne wystąpienia z wcześniejszych przebiegów, jeśli wystąpił wyjątek podczas uruchamiania. Istniejące wiersze można usunąć, klikając prawym przyciskiem myszy pozycję **System. Activities. DurableInstancing. instances** i wybierając pozycję **edytuj pierwsze wiersze 200**, naciskając przycisk **Execute** , wybierając pozycję wszystkie wiersze w okienku wyników i wybierając pozycję **Usuń**.  Aby sprawdzić, czy wystąpienie wyświetlane w bazie danych jest wystąpieniem utworzonym przez aplikację, sprawdź, czy widok wystąpień jest pusty przed uruchomieniem klienta. Gdy klient uruchomi ponownie zapytanie (wybierz pierwsze 1000 wierszy) i sprawdź, czy zostało dodane nowe wystąpienie.

7. Naciśnij klawisz ENTER, aby wysłać komunikat Dodawanie elementu do usługi przepływu pracy. Klient wyświetli następujący tekst:

    ```Output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a>Zobacz także

- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
