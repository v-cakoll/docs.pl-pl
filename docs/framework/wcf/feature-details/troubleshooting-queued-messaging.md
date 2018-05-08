---
title: Rozwiązywanie problemów obsługi komunikatów kolejek
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: 45a3bf82662fcc01b732428d1ca351e4ae8ddca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="troubleshooting-queued-messaging"></a>Rozwiązywanie problemów obsługi komunikatów kolejek
Ta sekcja zawiera typowe pytania i rozwiązywanie problemów z pomocy dotyczącej korzystania z kolejek w systemie Windows Communication Foundation (WCF).  
  
## <a name="common-questions"></a>Często zadawane pytania  
 **Pytanie:** użyta WCF Beta 1 i zainstalowaniu poprawki usługi MSMQ. Należy usunąć poprawkę?  
  
 **Odpowiedź:** tak. Ta poprawka jest już obsługiwany. Usługi WCF działa teraz na usługę MSMQ bez poprawki wymagane.  
  
 **Pytanie:** istnieją dwa powiązania dla usługi MSMQ: <xref:System.ServiceModel.NetMsmqBinding> i <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Co należy użyć, gdy?  
  
 **Odpowiedź:** użyć <xref:System.ServiceModel.NetMsmqBinding> gdy chcesz użyć usługi MSMQ jako transportu do komunikacji między dwiema aplikacjami WCF z obsługą kolejek. Użyj <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> Jeśli chcesz użyć istniejącej aplikacji usługi MSMQ do komunikowania się z nowych aplikacji WCF.  
  
 **Pytanie:** należy uaktualnić usługi MSMQ, aby użyć <xref:System.ServiceModel.NetMsmqBinding> i `MsmqIntegration` powiązania?  
  
 **Odp.:** Nie. Zarówno powiązania pracować z usługi MSMQ w wersji 3.0 na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. Niektóre funkcje powiązania stają się dostępne po uaktualnieniu MSMQ 4.0 w [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 **Pytanie:** jakie funkcje <xref:System.ServiceModel.NetMsmqBinding> i <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> powiązania są dostępne w MSMQ 4.0, ale usługa MSMQ nie 3.0?  
  
 **Odpowiedź:** są dostępne w MSMQ 4.0, ale usługa MSMQ nie 3.0 następujące funkcje:  
  
-   Niestandardowej kolejki utraconych wiadomości jest obsługiwana tylko na MSMQ 4.0.  
  
-   Usługa MSMQ 3.0 i 4.0 inaczej obsługi wiadomości.  
  
-   Tylko usługi MSMQ 4.0 obsługuje zdalne odczytu transakcyjnego.  
  
 Aby uzyskać więcej informacji, zobacz [różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
 **Pytanie:** można używać usługi MSMQ 3.0 na jednej stronie komunikatu w kolejce i MSMQ 4.0 po drugiej stronie?  
  
 **Odpowiedź:** tak.  
  
 **Pytanie:** chcę integracji istniejących aplikacji usługi MSMQ z nowej usługi WCF klientów lub serwerów. Należy uaktualnić obie strony Moje infrastruktury MSMQ?  
  
 **Odp.:** Nie. Nie masz dokonać uaktualnienia do usługi MSMQ 4.0 po obu stronach.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 W tej sekcji zamieszczono odpowiedzi na najczęstsze Rozwiązywanie problemów. Niektóre problemy, które są znane ograniczenia są także opisane w informacjach o wersji.  
  
 **Pytanie:** próbuję użyć kolejki prywatnej i pojawia się następujący wyjątek: `System.InvalidOperationException`: adres URL jest nieprawidłowy. Adres URL kolejki nie może zawierać znaku "$". Aby zaadresować kolejkę prywatną, należy użyć składni net.msmq://machine/private/queueName.  
  
 **Odpowiedź:** Sprawdź, czy kolejka identyfikator URI (Uniform Resource) w konfiguracji i kod. Nie należy używać znaku "$" w identyfikatorze URI. Na przykład aby zaadresować kolejkę prywatną o nazwie OrdersQueue, określ identyfikator URI jako net.msmq://localhost/private/ordersQueue.  
  
 **Pytanie:** wywoływania `ServiceHost.Open()` na aplikację w kolejce zwraca następujący wyjątek: `System.ArgumentException`: adres podstawowy nie może zawierać ciągu zapytania identyfikatora URI. Dlaczego?  
  
 **Odpowiedź:** Sprawdź kolejki identyfikatora URI w pliku konfiguracji i w kodzie. Podczas obsługują kolejki usługi MSMQ '?' znaków, identyfikatory URI zinterpretować ten znak jako początku ciągu zapytania. Aby uniknąć tego problemu, należy użyć nazwy kolejki, które nie zawierają '?' znaków.  
  
 **Pytanie:** Moje wysyłania zakończyła się pomyślnie, ale żadna operacja usługi został wywołany odbiornika. Dlaczego?  
  
 **Odpowiedź:** ustalenie odpowiedź skorzystać z poniższej liście kontrolnej:  
  
-   Sprawdź, czy wymagania transakcyjnej kolejki są zgodne z gwarancji określony. Należy uwzględnić następujące zasady:  
  
    -   Wiadomości można wysyłać trwałe (datagramy i sesji) z "dokładnie jednokrotne" gwarancji (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) tylko do kolejką transakcyjną.  
  
    -   Możesz wysłać sesji tylko z "dokładnie jednokrotne" gwarancji.  
  
    -   Transakcja jest wymagana do odbierania wiadomości w sesji z kolejką transakcyjną.  
  
    -   Można wysyłać ani odbierać nietrwałe lub trwałe wiadomości (tylko datagramy) nie gwarancji (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) tylko do kolejki nietransakcyjnej.  
  
-   Sprawdź kolejki utraconych wiadomości. Jeśli znajdziesz komunikaty nie ustalić, dlaczego ich nie zostały dostarczone.  
  
-   Sprawdzanie kolejek wychodzących dla łączności lub rozwiązaniu problemów.  
  
 **Pytanie:** określony niestandardowej kolejki utraconych wiadomości, ale po uruchomieniu aplikacji nadawcy pojawia się wyjątek, który nie znajduje się kolejka utraconych wiadomości, lub aplikacja wysyłająca nie ma uprawnień do kolejki utraconych wiadomości. Dlaczego jest sytuacja?  
  
 **Odpowiedź:** niestandardowej kolejki utraconych wiadomości identyfikator URI musi zawierać wartość "localhost" lub nazwa komputera pierwszy segment, na przykład net.msmq://localhost/private/myAppdead-letter kolejki.  
  
 **Pytanie:** jest zawsze za zdefiniowanie niestandardowej kolejki utraconych wiadomości, lub jest domyślnej kolejki utraconych wiadomości?  
  
 **A:** w przypadku zapewnienia "dokładnie jednokrotne" (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`), a jeśli nie określisz niestandardowej kolejki utraconych wiadomości, wartością domyślną jest kolejki utraconych wiadomości transakcyjnych całego systemu.  
  
 W przypadku zapewnienia none (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), a następnie domyślnie nie ma żadnych funkcji kolejki utraconych wiadomości.  
  
 **Pytanie:** Moje zgłasza usługi na SvcHost.Open z komunikatem "wymagania EndpointListener nie może spełnić ListenerFactory". Dlaczego?  
  
 A. Sprawdź umowy serwisowej. Być może została put "IsOneWay =`true`" dla wszystkich operacji usługi. Kolejki obsługują tylko operacje jednokierunkowe usługi.  
  
 **Pytanie:** są wiadomości w kolejce, ale jest wywoływana żadna operacja usługi. Co to jest problem?  
  
 **Odpowiedź:** ustalić, czy host usług jest uszkodzona. Możesz sprawdzić patrzeć śledzenia lub wykonania `IErrorHandler`. Błędy hosta usługi domyślnie, jeśli Trująca wiadomość została wykryta.  
  
 **Pytanie:** są wiadomości w kolejce, ale nie pobierania aktywowaniu usługi umieszczonych w kolejce Moje hostowanych w sieci Web. Dlaczego?  
  
 **Odpowiedź:** Najczęstszą przyczyną jest uprawnienia.  
  
1.  Upewnij się, że `NetMsmqActivator` proces jest uruchomiony i tożsamość `NetMsmqActivator` proces podano Odczyt i wyszukiwanie uprawnienia kolejki.  
  
2.  Jeśli `NetMsmqActivator` jest monitorowanie kolejek na komputerze zdalnym, upewnij się, że `NetMsmqActivator` nie jest uruchamiany w ograniczonym tokenu. Aby uruchomić `NetMsmqActivator` z tokenem bez ograniczeń:  
  
    ```  
    sc sidtype NetMsmqActivator unrestricted  
    ```  
  
 -Security problemy związane z hosta sieci Web można znaleźć w publikacji: [sieć Web hostująca aplikację w kolejce](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).  
  
 **Pytanie:** co to jest najprostszym sposobem sesji dostępu?  
  
 **A:** ustawić autouzupełniania =`true` na operację, która odnosi się do ostatniej wiadomości w sesji i ustaw autouzupełniania =`false` dla wszystkich pozostałych operacji usługi.  
  
 **Pytanie:** gdzie mogę znaleźć odpowiedzi na często zadawane pytania na MSMQ?  
  
 **Odpowiedź:** uzyskać więcej informacji na temat usługi MSMQ, zobacz [usługi kolejkowania wiadomości firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=87810).  
  
 **Pytanie:** Dlaczego moja usługa throw `ProtocolException` podczas czytania z kolejki, który zawiera zarówno sesji wiadomości w kolejce i datagram wiadomości w kolejce?  
  
 **Odpowiedź:** jest główną różnicą w sposób Kolejkowana sesja komunikaty i wiadomości w kolejce datagram składają się. W związku z tym usługa, która oczekuje Przeczytaj wiadomość w kolejce sesji nie można odebrać wiadomości w kolejce datagram i usługi oczekującej elementu odczytać wiadomość datagramu umieszczonych w kolejce nie może zostać wyświetlony komunikat sesji. Próba odczytania obu typów wiadomości z jedną kolejką zgłasza następujący wyjątek:  
  
```  
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.   
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.  
```  
  
 Kolejki utraconych wiadomości systemu, a także wszelkie niestandardowej kolejki utraconych wiadomości, jest szczególnie podatne na ten problem, jeśli aplikacja wyśle zarówno sesji wiadomości w kolejce i ustawił w kolejce wiadomości datagramów na tym samym komputerze. Jeśli nie można pomyślnie wysłać wiadomości, zostanie przeniesiona do kolejki utraconych wiadomości. W tej sytuacji jest możliwe zarówno sesji i datagram wiadomości w kolejce wiadomości utraconych. Nie można oddzielić oba typy wiadomości w czasie wykonywania podczas czytania z kolejki, w związku z tym aplikacje najlepiej nie przesyłać zarówno sesji wiadomości w kolejce i ustawił w kolejce wiadomości datagramów na tym samym komputerze.  
  
### <a name="msmq-integration-specific-troubleshooting"></a>Integracja usługi MSMQ: Określonych Rozwiązywanie problemów  
 **Pytanie:** przy wysyłaniu wiadomości lub otworzyć hosta usługi, pojawia się błąd, który wskazuje schemat jest nieprawidłowy. Dlaczego?  
  
 **Odpowiedź:** użycie powiązania integracji usługi MSMQ, należy użyć schematu postać msmq.formatname. Na przykład msmq.formatname:DIRECT=OS:.\private$\OrdersQueue. Jednak po określeniu niestandardowej kolejki utraconych wiadomości, należy użyć Schemat net.msmq.  
  
 **Pytanie:** po Użyj nazwy formatu publicznych lub prywatnych i otworzyć hosta usługi na [!INCLUDE[wv](../../../../includes/wv-md.md)], występuje błąd. Dlaczego?  
  
 **Odpowiedź:** kanał integracji WCF na [!INCLUDE[wv](../../../../includes/wv-md.md)] sprawdza, jeśli będzie można otworzyć kolejki podrzędne dla kolejki głównej aplikacji do obsługi wiadomości. Nazwa podrzędnej kolejki jest pochodną msmq.formatname identyfikatora URI przekazane do odbiornika. Nazwa podrzędnej kolejki w usłudze MSMQ może zawierać tylko z bezpośrednią nazwą formatu. Dlatego zostanie wyświetlony błąd. Zmień identyfikator URI kolejki z bezpośrednią nazwą formatu.  
  
 **Pytanie:** podczas odbierania wiadomości z aplikacji usługi MSMQ, wiadomość znajduje się w kolejce i nie został odczytany przez aplikację odbierającą WCF. Dlaczego?  
  
 **Odpowiedź:** Sprawdź, czy wiadomość została treści. Jeśli wiadomość ma nie treści, kanał integracji usługi MSMQ ignoruje komunikat. Implementowanie `IErrorHandler` powiadamianych wyjątków i sprawdź dane śledzenia.  
  
### <a name="security-related-troubleshooting"></a>Rozwiązywanie problemów związanych z zabezpieczeniami z  
 **Pytanie:** uruchamianych próbki, który używa domyślnego powiązania w trybie grupy roboczej, prawdopodobnie jest wysyłana wiadomości, ale nigdy nie są odbierane przez odbiornik.  
  
 **Odpowiedź:** domyślnie komunikaty są podpisane przy użyciu certyfikatu wewnętrznego usługi MSMQ, która wymaga usługi katalogowej Active Directory. W trybie grupy roboczej ponieważ usługi Active Directory nie jest dostępna, podpisywania wiadomości nie powiedzie się. Dlatego trafia wiadomości do kolejki utraconych wiadomości i wskazuje przyczynę błędu, takie jak "Zły podpis".  
  
 Obejście jest wyłączyć zabezpieczeń. Odbywa się przez ustawienie <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A>  =  <xref:System.ServiceModel.NetMsmqSecurityMode.None> Aby pracować w trybie grupy roboczej.  
  
 Inne obejście jest uzyskanie <xref:System.ServiceModel.MsmqTransportSecurity> z <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> właściwości i wartości <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>i ustaw certyfikatu klienta.  
  
 Jeszcze inne obejście polega na zainstalowaniu usługi MSMQ z integracją usługi Active Directory.  
  
 **Pytanie:** po wysłać wiadomość z powiązaniem domyślne (transportu zabezpieczeń włączone) w usłudze Active Directory do kolejki, wyświetlany jest komunikat "nie można odnaleźć certyfikatu wewnętrznego". Jak rozwiązać ten problem?  
  
 **Odpowiedź:** oznacza to, że należy odnawiać certyfikat nadawcy w usłudze Active Directory. Aby to zrobić, otwórz **Panelu sterowania**, **narzędzia administracyjne**, **Zarządzanie komputerem**, kliknij prawym przyciskiem myszy **MSMQ**i wybierz **Właściwości**. Wybierz **certyfikatu użytkownika** i kliknij polecenie **odnawiania** przycisku.  
  
 **Pytanie:** po wysłać komunikat przy użyciu <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> i Określ certyfikat do użycia, wyświetlany jest komunikat "Nieprawidłowy certyfikat". Jak rozwiązać ten problem?  
  
 **Odpowiedź:** tryb certyfikatu nie można używać magazynu certyfikatów komputera lokalnego. Należy skopiować certyfikat z magazynu certyfikatów komputera w magazynie bieżącego użytkownika za pomocą przystawki certyfikatów. Aby uzyskać certyfikat przystawki:  
  
1.  Kliknij przycisk **Start**, wybierz pozycję **Uruchom**, typ `mmc`i kliknij przycisk **OK**.  
  
2.  W **programu Microsoft Management Console**, otwórz **pliku** menu i wybierz **Dodaj/Usuń przystawkę**.  
  
3.  W **Dodaj/Usuń przystawkę** okno dialogowe, kliknij przycisk **Dodaj** przycisku.  
  
4.  W **Dodawanie przystawki autonomicznej** okno dialogowe, wybierz opcję certyfikaty i kliknij przycisk **Dodaj**.  
  
5.  W **certyfikaty** przystawki wybierz pozycję **Moje konto użytkownika** i kliknij przycisk **Zakończ**.  
  
6.  Następnie dodać drugi certyfikatów przystawki przy użyciu poprzednich kroków, ale tym razem wybierz **konto komputera** i kliknij przycisk **dalej**.  
  
7.  Wybierz **komputera lokalnego** i kliknij przycisk **Zakończ**. Można teraz przeciągnij i upuść certyfikaty z magazynu certyfikatów komputera w magazynie bieżącego użytkownika.  
  
 **Pytanie:** gdy mój usługi odczytuje z kolejki na inny komputer w trybie grupy roboczej, uzyskać Wystąpił wyjątek "odmowa dostępu".  
  
 **Odpowiedź:** w trybie grupy roboczej dla aplikacji zdalnej do uzyskiwania dostępu do kolejki, aplikacja musi mieć uprawnienia dostępu do kolejki. Dodaj "Anonimowego logowania" do listy kontroli dostępu dla kolejek (ACL) i nadaj uprawnienia do odczytu.  
  
 **Pytanie:** klient usługi sieciowej (lub klienta, który nie ma konta domeny) wysyła wiadomość w kolejce, wysyłania nie powiedzie się z nieprawidłowym certyfikatem. Jak rozwiązać ten problem?  
  
 **Odpowiedź:** Sprawdź konfigurację powiązania. Powiązanie domyślna ma MSMQ zabezpieczeń transportu włączone do podpisania wiadomości. Wyłącz ją.  
  
### <a name="remote-transacted-receives"></a>Odbiera zdalnego nietransakcyjnego  
 **Pytanie:** po mam kolejki na komputerze A, a usługi WCF odczytującego komunikaty z kolejki na komputerze B (zdalnego nietransakcyjnego odbierać scenariusz), wiadomości nie są odczytywane z kolejki. Śledzenie informacji wskazuje receive nie powiodło się komunikat "nie można zaimportować transakcji." Co można zrobić, aby rozwiązać ten problem?  
  
 **Odpowiedź:** istnieją trzy możliwe przyczyny to:  
  
-   Jeśli jesteś w trybie domeny odbiór zdalny nietransakcyjnego wymaga dostępu do sieci koordynatora transakcji rozproszonych (MSDTC). Możesz je włączyć za pomocą **Dodaj/Usuń składniki**.  
  
     ![Włączanie usługi network DTC access](../../../../docs/framework/wcf/feature-details/media/applicationserveraddcomps.jpg "ApplicationServerAddComps")  
  
-   Sprawdź trybu uwierzytelniania do komunikowania się z menedżerem transakcji. Jeśli jesteś w trybie grupy roboczej, należy wybrać "Bez uwierzytelniania wymagany". Jeśli jesteś w trybie domeny, należy wybrać "Wymagane uwierzytelnianie wzajemne".  
  
     ![Włączanie transakcje XA](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")  
  
-   Upewnij się, że usługa MSDTC jest na liście wyjątków w **Zapora połączenia internetowego** ustawienia.  
  
-   Upewnij się, że używasz [!INCLUDE[wv](../../../../includes/wv-md.md)]. Usługa MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje zdalne odczytu transakcyjnego. MSMQ we wcześniejszych wersjach systemu Windows nie obsługuje zdalnego odczytu transakcyjnego.  
  
 **Pytanie:** podczas czytania z kolejki usługa jest usługą sieciową, na przykład w sieci Web hosta, dlaczego jest zgłaszany wyjątek odmowy dostępu jest wywoływane podczas czytania z kolejki?  
  
 **Odpowiedź:** dostęp do odczytu usług sieciowych muszą zostać dodane do kolejki, listy ACL, aby upewnić się, że Usługa sieciowa może odczytać z kolejki.  
  
 **Pytanie:** czy za pomocą usługi MSMQ activation service można aktywować aplikacje oparte na wiadomości z kolejki na komputerze zdalnym?  
  
 **Odpowiedź:** tak. Aby to zrobić, należy skonfigurować usługę MSMQ aktywacji do uruchamiania jako usługa sieciowa i dodać dostępu do sieci usługi do kolejki na komputerze zdalnym.  
  
## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>Przy użyciu powiązań niestandardowych MSMQ z włączoną funkcję ReceiveContext  
 Podczas korzystania z niestandardowego powiązania usługi MSMQ z <xref:System.ServiceModel.Channels.ReceiveContext> włączona, przetwarzanie wiadomości przychodzących będą używać wątku puli wątków, ponieważ MSMQ macierzystym nie obsługuje zakończenia We/Wy dla asynchronicznego <xref:System.ServiceModel.Channels.ReceiveContext> odbiera. Wynika to z faktu przetworzenia takiego komunikatu używa wewnętrznej transakcji dla <xref:System.ServiceModel.Channels.ReceiveContext> i usługi MSMQ nie obsługuje przetwarzania asynchronicznego. Aby obejść ten problem, można dodać <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> do punktu końcowego, aby wymusić synchronicznego przetwarzania lub ustaw <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> do 1.
