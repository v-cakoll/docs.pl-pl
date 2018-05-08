---
title: Tworzenie długo działającej usługi przepływu pracy
ms.date: 03/30/2017
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
ms.openlocfilehash: 1ddb995b849a15451c36d5d11c95a4904a3e0496
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="creating-a-long-running-workflow-service"></a>Tworzenie długo działającej usługi przepływu pracy
W tym temacie opisano sposób tworzenia usługi przepływu pracy długotrwałe. Długotrwałe usług przepływu pracy mogą działać przez dłuższy czas. W pewnym momencie przepływ pracy może być bezczynności oczekiwanie na dodatkowe informacje. W takim przypadku przepływ pracy zostanie na stałe zapisana bazy danych SQL i zostanie usunięty z pamięci. Po udostępnieniu dodatkowe informacje wystąpienia przepływu pracy jest ładowany do pamięci i kontynuuje wykonywanie.  W tym scenariuszu w przypadku implementowania bardzo uproszczonego systemu porządkowania.  Klient wysyła początkowy komunikat do usługi przepływu pracy, aby uruchomić kolejność. Zwraca identyfikator zamówienia do klienta. W tym momencie usługi przepływu pracy jest oczekiwanie na kolejny komunikat z klienta i przechodzi w stan bezczynności i zostanie na stałe zapisana bazy danych programu SQL Server.  Gdy klient wysyła następny komunikat do kolejność elementów, usługi przepływu pracy jest ładowany do pamięci i zakończeniu przetwarzania zamówienia. W przykładowym kodzie zwraca ciąg informujący, że element został dodany do zlecenia. Przykładowy kod ma nie być rzeczywistych stosowania technologii, ale zamiast prosty przykład, który przedstawiono długotrwała usług przepływu pracy. W tym temacie założono, wiesz, jak utworzyć [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projekty i rozwiązania.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Musi mieć zainstalowane, aby korzystać z tego przewodnika następujące oprogramowanie:  
  
1.  Microsoft SQL Server 2008  
  
2.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
3.  Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]  
  
4.  Znasz WCF i [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] i wiedzieć, jak tworzyć projekty/rozwiązania.  
  
### <a name="to-setup-the-sql-database"></a>Konfiguracja bazy danych SQL  
  
1.  Aby wystąpienia usługi przepływu pracy utrwalenia musi mieć zainstalowany program Microsoft SQL Server i skonfiguruj bazę danych do przechowywania wystąpień utrwalonych przepływów pracy. Uruchom program Microsoft SQL Management Studio, klikając **Start** przycisku, wybierając **wszystkie programy**, **Microsoft SQL Server 2008**, i **programu Microsoft SQL Management Studio**.  
  
2.  Kliknij przycisk **Connect** przycisk, aby zalogować się do wystąpienia programu SQL Server  
  
3.  Kliknij prawym przyciskiem myszy **baz danych** w widoku drzewa, a następnie wybierz **nowej bazy danych...** Aby utworzyć nową bazę danych o nazwie `SQLPersistenceStore`.  
  
4.  Uruchom plik skryptu SqlWorkflowInstanceStoreSchema.sql znajduje się w katalogu C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en w bazie danych SQLPersistenceStore, aby skonfigurować schematów potrzebne bazy danych.  
  
5.  Uruchom plik skryptu SqlWorkflowInstanceStoreLogic.sql znajduje się w katalogu C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en w bazie danych SQLPersistenceStore, aby skonfigurować logiki potrzebne bazy danych.  
  
### <a name="to-create-the-web-hosted-workflow-service"></a>Aby utworzyć sieci Web hostowanej usługi przepływu pracy  
  
1.  Utwórz pustą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] rozwiązania, nadaj mu nazwę `OrderProcessing`.  
  
2.  Dodaj nowy projekt aplikacji usługi przepływu pracy WCF o nazwie `OrderService` do rozwiązania.  
  
3.  W oknie dialogowym właściwości projektu, zaznacz **Web** kartę.  
  
    1.  W obszarze **Akcja uruchamiania** wybierz **określonej strony** i określ `Service1.xamlx`.  
  
         ![Właściwości sieci Web projektu usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")  
  
    2.  W obszarze **serwerów** wybierz **Użyj lokalnym serwerem sieci Web IIS**.  
  
         ![Ustawienia serwera sieci Web w lokalnej](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")  
  
        > [!WARNING]
        >  Należy uruchomić [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] w trybie administratora, aby to ustawienie.  
  
         Następujące dwa kroki konfigurowania projektu usługi przepływu pracy, który ma być obsługiwana przez usługi IIS.  
  
4.  Otwórz `Service1.xamlx` przypadku nie otwarto już i usuń istniejącą **ReceiveRequest** i **SendResponse** działań.  
  
5.  Wybierz **usługa Sekwencyjna** działania i kliknij przycisk **zmienne** link i dodać zmienne pokazano na poniższej ilustracji. W ten sposób dodaje niektóre zmienne, które będą używane później w usłudze przepływu pracy.  
  
    > [!NOTE]
    >  Jeśli obiekt CorrelationHandle nie ma listy rozwijanej Typ zmiennej, wybierz **Przeglądaj w poszukiwaniu typy** z listy rozwijanej. Typ obiektu CorrelationHandle w **nazwy typu** polu, wybierz obiekt CorrelationHandle w polu listy i kliknij przycisk **OK**.  
  
     ![Dodawanie zmiennych](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")  
  
6.  Przeciągnij i upuść **ReceiveAndSendReply** szablon działania do **usługa Sekwencyjna** działania. Ten zbiór działań zostanie wyświetlony komunikat z klienta i wysyłać odpowiedzi ponownie.  
  
    1.  Wybierz **Receive** działania i ustaw właściwości wyróżnione na poniższej ilustracji.  
  
         ![Właściwości działania odbierania zestawu](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")  
  
         Właściwość DisplayName ustawia nazwę wyświetlaną dla działania Receive w projektancie. Właściwości ServiceContractName i OperationName Określ nazwę kontraktu usługi i operacji, które są implementowane przez działanie Receive. Aby uzyskać więcej informacji na temat używania kontraktów w przepływie pracy usług zobacz [za pomocą kontraktów w przepływie pracy](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).  
  
    2.  Kliknij przycisk **zdefiniuj...**  łącze w **ReceiveStartOrder** działania i ustaw właściwości wyświetlane na poniższej ilustracji.  Zwróć uwagę, że **parametry** przycisk radiowy zostanie wybrany, parametr o nazwie `p_customerName` jest powiązany z `customerName` zmiennej. Spowoduje to skonfigurowanie **Receive** działanie, aby odbierać niektóre dane i powiązać te dane do zmiennych lokalnych.  
  
         ![Ustawienia danych odebranych przez działanie Receive](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")  
  
    3.  Wybierz **SendReplyToReceive** działania i ustaw dla właściwości wyróżnione pokazano na poniższej ilustracji.  
  
         ![Ustawianie właściwości działania SendReply](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")  
  
    4.  Kliknij przycisk **zdefiniuj...**  łącze w **SendReplyToStartOrder** działania i ustaw właściwości wyświetlane na poniższej ilustracji. Zwróć uwagę, że **parametry** przycisk radiowy zostanie wybrany; parametr o nazwie `p_orderId` jest powiązany z `orderId` zmiennej. To ustawienie określa, że działanie SendReplyToStartOrder zwróci wartość typu ciąg do obiektu wywołującego.  
  
         ![Konfigurowanie danych zawartości działania SendReply](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")  
  
    5.  Przeciągnij i upuść działanie Przypisz między **Receive** i **SendReply** działań i ustaw właściwości, jak pokazano na poniższej ilustracji:  
  
         ![Dodawanie działaniu assign](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")  
  
         Tworzy nowy identyfikator zamówienia i umieszcza wartość w zmiennej orderId.  
  
    6.  Wybierz **ReplyToStartOrder** działania. W oknie dialogowym właściwości kliknij przycisk wielokropka **CorrelationInitializers**. Wybierz **dodać inicjatora** połączyć, wprowadź `orderIdHandle` w polu tekstowym inicjatora wybierz inicjatora korelacji zapytań dla typu korelacji, a następnie wybierz p_orderId w polu listy rozwijanej kwerendy XPATH. Te ustawienia są wyświetlane na poniższej ilustracji. Kliknij przycisk **OK**.  To inicjuje korelację między klientem a to wystąpienie usługi przepływu pracy. Jeśli wiadomość zawierającą porządek ten identyfikator jest odebrana jest kierowany do tego wystąpienia usługi przepływu pracy.  
  
         ![Dodawanie inicjatora korelacji](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")  
  
7.  Przeciągnij i upuść innego **ReceiveAndSendReply** działania na końcu przepływu pracy (poza **sekwencji** zawierający pierwszy **Receive** i  **SendReply** działań). Zostanie wyświetlony to drugi komunikat wysyłany przez klienta i odpowiedzieć na.  
  
    1.  Wybierz **sekwencji** zawierający nowo dodanego **Receive** i **SendReply** działania i kliknij przycisk **zmienne** przycisku. Dodaj zmienną wyróżnione na poniższej ilustracji:  
  
         ![Dodawanie nowych zmiennych](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")  
  
    2.  Wybierz **Receive** działania i ustaw właściwości wyświetlane na poniższej ilustracji:  
  
         ![Ustaw właściwości acitivity Receive](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")  
  
    3.  Kliknij przycisk **zdefiniuj...**  łącze w **ReceiveAddItem** działania i Dodaj parametry pokazano na poniższej ilustracji: spowoduje to skonfigurowanie działanie receive, aby zaakceptować dwa parametry: identyfikator zamówienia i identyfikator elementu porządkowana.  
  
         ![Określanie parametrów dla drugiego odbierania](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")  
  
    4.  Kliknij przycisk **CorrelateOn** wielokropka przycisk, a następnie wprowadź `orderIdHandle`. W obszarze **kwerendy XPath**, kliknij strzałkę listy rozwijanej i wybierz `p_orderId`. Spowoduje to skonfigurowanie korelację na drugiej stronie działanie odbierania. Aby uzyskać więcej informacji na temat korelacji zobacz [korelacji](../../../../docs/framework/wcf/feature-details/correlation.md).  
  
         ![Ustawienie właściwości CorrelatesOn](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")  
  
    5.  Przeciągnij i upuść **Jeśli** działanie natychmiast po **ReceiveAddItem** działania. To działanie działa tak samo jak w przypadku instrukcji.  
  
        1.  Ustaw **warunku** właściwości `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`  
  
        2.  Przeciągnij i upuść **przypisać** do działania w **następnie** sekcji, a drugi do **Else** sekcję ustawić właściwości **przypisać** działania, jak pokazano na poniższej ilustracji.  
  
             ![Przypisywanie wynik wywołania usługi](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")  
  
             Jeśli warunek nie jest `true` **następnie** sekcji zostaną wykonane. Jeśli warunek nie jest `false` **Else** sekcji jest wykonywana.  
  
        3.  Wybierz **SendReplyToReceive** działania i zestaw **DisplayName** właściwości pokazano na poniższej ilustracji.  
  
             ![Ustawianie właściwości działania SendReply](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")  
  
        4.  Kliknij przycisk **zdefiniuj...**  łącze w **SetReplyToAddItem** działania i skonfiguruj go tak, jak pokazano na poniższej ilustracji. Spowoduje to skonfigurowanie **SendReplyToAddItem** działaniu zwracać wartość `orderResult` zmiennej.  
  
             ![Ustawienia powiązania danych dla działanie SendReply programu](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")  
  
8.  Otwórz plik web.config i dodaj następujące elementy w \<zachowanie > sekcji, aby umożliwić utrwalania przepływu pracy.  
  
    ```xml  
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />  
              <workflowIdle timeToUnload="0"/>  
    ```  
  
    > [!WARNING]
    >  Upewnij się, że zmieniło hosta i nazwa wystąpienia serwera SQL w poprzednim fragmentu kodu.  
  
9. Skompiluj rozwiązanie.  
  
### <a name="to-create-a-client-application-to-call-the-workflow-service"></a>Aby utworzyć aplikację klienta do wywołania tej usługi przepływu pracy  
  
1.  Dodaj nowy projekt aplikacji konsoli o nazwie `OrderClient` do rozwiązania.  
  
2.  Dodaj odwołania do następujących zestawów do `OrderClient` projektu  
  
    1.  System.ServiceModel.dll  
  
    2.  System.ServiceModel.Activities.dll  
  
3.  Dodaj odwołania do usługi do usługi przepływu pracy i określ `OrderService` jako obszar nazw.  
  
4.  W `Main()` metody projektu klienta, Dodaj następujący kod:  
  
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
  
5.  Skompiluj rozwiązanie, a następnie uruchom `OrderClient` aplikacji. Klient zostanie wyświetlony następujący tekst:  
  
    ```Output  
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...  
    ```  
  
6.  Aby sprawdzić, czy utrwaleniu usługi przepływu pracy, uruchom program SQL Server Management Studio, przechodząc do **Start** menu, wybranie opcji **wszystkie programy**, **Microsoft SQL Server 2008**, **Programu SQL Server Management Studio**.  
  
    1.  W okienku po lewej stronie rozwiń węzeł, **baz danych**, **SQLPersistenceStore**, **widoków** i kliknij prawym przyciskiem myszy **System.Activities.DurableInstancing.Instances**  i wybierz **zaznacz 1000 pierwszych wierszy**. W **wyniki** Sprawdź okienko zobacz co najmniej jedno wystąpienie na liście. Mogą istnieć inne wystąpienia z poprzednie uruchomienia, jeśli wystąpił wyjątek podczas uruchamiania. Możesz usunąć istniejące wiersze, klikając prawym przyciskiem myszy **System.Activities.DurableInstancing.Instances** i wybierając **Edytuj pierwszych 200 wierszy**, naciskając klawisz **Execute** przycisku wybranie wszystkich wierszy w okienku wyników, a użycie **usunąć**.  Aby sprawdzić wystąpienia wyświetlana w bazie danych jest wystąpienie aplikacji utworzone, sprawdź, widok wystąpienia jest pusta, przed uruchomieniem klienta. Gdy klient jest uruchomiony ponownie uruchom zapytanie (zaznacz 1000 pierwszych wierszy) i sprawdź dodano nowe wystąpienie.  
  
7.  Naciśnij klawisz enter, aby wysłać wiadomość elementu Dodaj do usługi przepływu pracy. Klient zostanie wyświetlony następujący tekst:  
  
    ```Output  
    Sending add item messageService returned: Item added to orderPress any key to continue . . .  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)
