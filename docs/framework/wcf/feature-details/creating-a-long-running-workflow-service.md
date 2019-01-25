---
title: Tworzenie długo działającej usługi przepływu pracy
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: b3c5cd8a64f32a199932a40ed2d94b0a545b0dc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585409"
---
# <a name="creating-a-long-running-workflow-service"></a>Tworzenie długo działającej usługi przepływu pracy
W tym temacie opisano tworzenie długo działającej usługi przepływu pracy. Długotrwałe usług przepływu pracy może działać przez dłuższy czas. W pewnym momencie przepływu pracy może być bezczynny, oczekiwanie na kilku dodatkowych informacji. W takim przypadku przepływ pracy jest trwały do usługi SQL database i zostanie usunięty z pamięci. Po udostępnieniu dodatkowych informacji wystąpienia przepływu pracy jest ładowany do pamięci i kontynuuje wykonywanie.  W tym scenariuszu w przypadku wdrażania bardzo uproszczony system zamawiania.  Klient wysyła pierwszy komunikat do usługi przepływu pracy, aby rozpocząć kolejności. Zwraca identyfikator zamówienia dla klienta. W tym momencie Usługa przepływu pracy oczekuje na inny komunikat z klienta i przechodzi w stan bezczynności i jest umieszczone w bazie danych programu SQL Server.  Gdy klient wysyła następnej wiadomości w celu uporządkowania elementów, usługi przepływu pracy jest ładowany do pamięci i zakończeniu przetwarzania zamówienia. W przykładowym kodzie zwraca ciąg z informacją, że element został dodany do zamówienia. Przykładowy kod nie jest przeznaczona do rzeczywistej aplikacji w technologii, ale raczej prosty przykład ilustrujący długo działającej usługi przepływu pracy. W tym temacie założono, że wiesz, jak tworzyć projekty programu Visual Studio 2012 i rozwiązań.

## <a name="prerequisites"></a>Wymagania wstępne
 Musi mieć następujące oprogramowanie, które są zainstalowane, aby użyć tego przewodnika:

1.  Microsoft SQL Server 2008

2.  Visual Studio 2012

3.  Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]

4.  Znają WCF i programu Visual Studio 2012 i wiedzieć, jak tworzyć projekty i rozwiązania.

### <a name="to-setup-the-sql-database"></a>Aby skonfigurować bazy danych SQL

1.  Aby wystąpień usługi przepływu pracy w celu jego utrwalenia muszą mieć zainstalowany program Microsoft SQL Server i skonfiguruj bazę danych do przechowywania wystąpień utrwalonych przepływu pracy. Uruchom program Microsoft SQL Management Studio, klikając pozycję **Start** przycisku, wybierając **wszystkie programy**, **Microsoft SQL Server 2008**, i **programu Microsoft SQL Management Studio**.

2.  Kliknij przycisk **Connect** przycisk, aby zalogować się do wystąpienia programu SQL Server

3.  Kliknij prawym przyciskiem myszy **baz danych** w widoku drzewa i wybierz pozycję **nową bazę danych...** Aby utworzyć nową bazę danych o nazwie `SQLPersistenceStore`.

4.  Uruchom plik skryptu SqlWorkflowInstanceStoreSchema.sql znajduje się w katalogu C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en SQLPersistenceStore bazy danych do skonfigurowania schematy potrzebne bazy danych.

5.  Uruchom plik skryptu SqlWorkflowInstanceStoreLogic.sql znajduje się w katalogu C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en SQLPersistenceStore bazy danych do skonfigurowania logiki potrzebne bazy danych.

### <a name="to-create-the-web-hosted-workflow-service"></a>Aby utworzyć w sieci Web hostowanej usługi przepływu pracy

1.  Utwórz puste rozwiązanie programu Visual Studio 2012, nadaj jej nazwę `OrderProcessing`.

2.  Dodaj nowy projekt aplikacji usługi przepływu pracy WCF o nazwie `OrderService` do rozwiązania.

3.  W oknie dialogowym właściwości projektu zaznacz **Web** kartę.

    1.  W obszarze **Akcja uruchamiania** wybierz **konkretnej strony** i określ `Service1.xamlx`.

         ![Właściwości projektu usługi przepływu pracy w sieci Web](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")

    2.  W obszarze **serwerów** wybierz **Użyj lokalnym serwerem sieci Web IIS**.

         ![Local Web Server Settings](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")

        > [!WARNING]
        >  W trybie administratora, aby to ustawienie, należy uruchomić program Visual Studio 2012.

         Następujące dwa kroki konfigurowania projektu przepływu pracy usługi hostowane przez usługi IIS.

4.  Otwórz `Service1.xamlx` przypadku nie otwarto już i usuń istniejącą **ReceiveRequest** i **SendResponse** działań.

5.  Wybierz **usługa Sekwencyjna** działania i kliknij przycisk **zmienne** łącze i Dodaj zmienne pokazano na poniższej ilustracji. W ten sposób dodaje niektóre zmienne, które będą używane później w usłudze przepływu pracy.

    > [!NOTE]
    >  Jeśli CorrelationHandle nie znajduje się w rozwijanej Typ zmiennej, wybierz opcję **vyhledat typy** z listy rozwijanej. Wpisz CorrelationHandle w **nazwy typu** polu Wybierz CorrelationHandle w polu listy i kliknij **OK**.

     ![Dodaj zmienne](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")

6.  Przeciąganie i upuszczanie **ReceiveAndSendReply** szablon działania do **usługa Sekwencyjna** działania. Ten zbiór działań zostanie wyświetlony komunikat z klienta i wysyłać odpowiedzi ponownie.

    1.  Wybierz **Receive** działanie i ustaw właściwości wyróżnione na poniższej ilustracji.

         ![Zestaw otrzymywać właściwości działania](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")

         Właściwość DisplayName ustawia nazwę wyświetlaną dla działania odbierania w projektancie. Właściwości ServiceContractName i OperationName Określ nazwę kontraktu usługi i operacji, które są implementowane przez działanie Receive. Aby uzyskać więcej informacji o używaniu kontraktów w usługach przepływu pracy, zobacz [za pomocą kontraktów w przepływie pracy](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).

    2.  Kliknij przycisk **zdefiniować...**  łącze w **ReceiveStartOrder** działania i ustaw właściwości pokazane na poniższej ilustracji.  Należy zauważyć, że **parametry** przycisk radiowy zostanie wybrany, parametr o nazwie `p_customerName` jest powiązany z `customerName` zmiennej. Pozwoli to na skonfigurowanie **Receive** działanie, aby odbierać dane i powiązać te dane do zmiennych lokalnych.

         ![Ustawianie danych otrzymanych przez działanie Receive](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")

    3.  Wybierz **SendReplyToReceive** działanie i ustaw właściwość wyróżnione pokazano na poniższej ilustracji.

         ![Ustawianie właściwości działania SendReply](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")

    4.  Kliknij przycisk **zdefiniować...**  łącze w **SendReplyToStartOrder** działania i ustaw właściwości pokazane na poniższej ilustracji. Należy zauważyć, że **parametry** przycisk radiowy zostanie wybrany; parametr o nazwie `p_orderId` jest powiązany z `orderId` zmiennej. To ustawienie określa, że działanie SendReplyToStartOrder będzie zwracać wartość typu ciąg do obiektu wywołującego.

         ![Konfigurowanie danych zawartości działania SendReply](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")

    5.  Przeciągnij i upuść działanie Przypisz między **Receive** i **SendReply** działań i ustaw właściwości, jak pokazano na poniższej ilustracji:

         ![Dodawanie działania Przypisz](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")

         To może utworzy nowy identyfikator zamówienia, a następnie umieszcza wartość w zmiennej orderId.

    6.  Wybierz **ReplyToStartOrder** działania. W oknie dialogowym właściwości kliknij przycisk wielokropka dla **CorrelationInitializers**. Wybierz **Dodaj inicjator** połączyć, wprowadź `orderIdHandle` w polu tekstowym inicjatora wybierz inicjatora korelacji zapytania dla typu korelacji, a następnie wybierz p_orderId w polu listy rozwijanej kwerendy XPATH. Te ustawienia są wyświetlane na poniższej ilustracji. Kliknij przycisk **OK**.  Korelacja między klientem a to wystąpienie usługi przepływu pracy jest inicjowana. Gdy wiadomość zawierającą ta kolejność jest odebranych identyfikator odbywa się z tym wystąpieniem usługi przepływu pracy.

         ![Dodanie inicjatora korelacji](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")

7.  Przeciąganie i upuszczanie innego **ReceiveAndSendReply** działania na końcu przepływu pracy (poza **sekwencji** zawierający pierwszy **Receive** i  **SendReply** działań). Zostanie wyświetlony drugi komunikat wysyłany przez klienta i odpowiedzieć na.

    1.  Wybierz **sekwencji** zawiera nowo dodanych **Receive** i **SendReply** działania i kliknij przycisk **zmienne** przycisku. Dodaj zmienną wyróżnione na poniższej ilustracji:

         ![Dodawanie nowych zmiennych](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")

    2.  Wybierz **Receive** działania i ustaw właściwości pokazane na poniższej ilustracji:

         ![Ustaw właściwości działanie Receive](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")

    3.  Kliknij przycisk **zdefiniować...**  łącze w **ReceiveAddItem** działania i Dodaj parametry pokazano na poniższej ilustracji: umożliwia skonfigurowanie działania odbierania i akceptuje dwa parametry: identyfikator zamówienia i identyfikator elementu szeregowane.

         ![Określając parametry, z drugiej pobierają](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")

    4.  Kliknij przycisk **CorrelateOn** wielokropka przycisk, a następnie wprowadź `orderIdHandle`. W obszarze **kwerendy XPath**, kliknij strzałkę listy rozwijanej i wybierz `p_orderId`. Pozwoli to na skonfigurowanie korelacji w drugiej otrzymywać działania. Aby uzyskać więcej informacji na temat korelacji zobacz [korelacji](../../../../docs/framework/wcf/feature-details/correlation.md).

         ![Ustawienie właściwości CorrelatesOn](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")

    5.  Przeciąganie i upuszczanie **Jeśli** działanie natychmiast po **ReceiveAddItem** działania. To działanie będzie działać tak jak if instrukcji.

        1.  Ustaw **warunek** właściwości `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`

        2.  Przeciąganie i upuszczanie **przypisać** działania w celu **następnie** sekcji, a drugi do **Else** sekcji Ustaw właściwości **przypisać** działania, jak pokazano na poniższej ilustracji.

             ![Przypisywanie wynik wywołania usługi](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")

             Jeśli warunek nie jest `true` **następnie** sekcji zostaną wykonane. Jeśli warunek nie jest `false` **Else** sekcji jest wykonywany.

        3.  Wybierz **SendReplyToReceive** działania i ustaw **DisplayName** właściwość pokazano na poniższej ilustracji.

             ![Ustawianie właściwości działania SendReply](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")

        4.  Kliknij przycisk **zdefiniować...**  łącze w **SetReplyToAddItem** działania i skonfiguruj go tak, jak pokazano na poniższej ilustracji. Pozwoli to na skonfigurowanie **SendReplyToAddItem** działaniu zwracać wartość `orderResult` zmiennej.

             ![Ustawienie powiązania danych w celu działanie programu SendReply](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")

8.  Otwórz plik web.config i dodaj następujące elementy w \<zachowanie > sekcji, aby włączyć opcję trwałości przepływu pracy.

    ```xml
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />
              <workflowIdle timeToUnload="0"/>
    ```

    > [!WARNING]
    >  Upewnij się zastąpić hosta i nazwa wystąpienia serwera SQL w poprzednim fragmencie kodu.

9. Skompiluj rozwiązanie.

### <a name="to-create-a-client-application-to-call-the-workflow-service"></a>Aby utworzyć aplikację kliencką do wywoływania usługi przepływu pracy

1.  Dodaj nowy projekt aplikacji konsoli o nazwie `OrderClient` do rozwiązania.

2.  Dodaj odwołania do następujących zestawów, które mają `OrderClient` projektu

    1.  System.ServiceModel.dll

    2.  System.ServiceModel.Activities.dll

3.  Dodaj odwołanie do usługi przepływu pracy usługi i określ `OrderService` jak przestrzeń nazw.

4.  W `Main()` metoda projekt klienta, Dodaj następujący kod:

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

5.  Skompilować rozwiązanie i uruchomić `OrderClient` aplikacji. Klient spowoduje wyświetlenie następującego tekstu:

    ```Output
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...
    ```

6.  Aby sprawdzić, trwałość usługi przepływu pracy, uruchom program SQL Server Management Studio, przechodząc do **Start** menu wybranie **wszystkie programy**, **Microsoft SQL Server 2008**, **Programu SQL Server Management Studio**.

    1.  W okienku po lewej stronie ekranu należy rozwinąć, **baz danych**, **SQLPersistenceStore**, **widoków** i kliknij prawym przyciskiem myszy **System.Activities.DurableInstancing.Instances**  i wybierz **zaznacz 1000 pierwszych wierszy**. W **wyniki** okienko sprawdzić, zostanie wyświetlona co najmniej jedno wystąpienie na liście. Mogą istnieć inne wystąpienia z poprzednich przebiegów, jeśli wystąpił wyjątek podczas uruchamiania. Możesz usunąć istniejące wiersze, klikając prawym przyciskiem myszy **System.Activities.DurableInstancing.Instances** i wybierając polecenie **Edytuj pierwszych 200 wierszy**, naciskając klawisz **Execute** przycisku wybranie wszystkich wierszy w okienku wyników, a użycie **Usuń**.  Aby sprawdzić wystąpienia wyświetlana w bazie danych jest wystąpienie aplikacji, który został utworzony, sprawdź, widoku wystąpień jest pusta przed uruchomieniem klienta. Gdy klient jest uruchomiony ponownie uruchom zapytanie (zaznacz 1000 pierwszych wierszy) i sprawdź dodano nowe wystąpienie.

7.  Naciśnij klawisz enter, aby wysłać wiadomość elementu dodawanie do usługi przepływu pracy. Klient spowoduje wyświetlenie następującego tekstu:

    ```Output
    Sending add item messageService returned: Item added to orderPress any key to continue . . .
    ```

## <a name="see-also"></a>Zobacz także
- [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
