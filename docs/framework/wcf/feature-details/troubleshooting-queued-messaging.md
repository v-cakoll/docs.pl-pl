---
title: Rozwiązywanie problemów obsługi komunikatów kolejek
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: 760ef4801c0881829dbc57b4022dcea4ed8c64bb
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645215"
---
# <a name="troubleshooting-queued-messaging"></a>Rozwiązywanie problemów obsługi komunikatów kolejek
Ta sekcja zawiera typowe pytania i rozwiązywanie problemów z pomocy dotyczącej korzystania z kolejek w Windows Communication Foundation (WCF).  
  
## <a name="common-questions"></a>Często zadawane pytania  
 **PYT.:** Czy mogę używać WCF Beta 1 i mam już zainstalowaną poprawkę usługi MSMQ. Należy usunąć poprawkę?  
  
 **ODP.:** Tak. Ta poprawka nie jest już obsługiwana. Usługi WCF działa teraz w usłudze MSMQ bez wymogu poprawki.  
  
 **PYT.:** Istnieją dwa powiązania dla usługi MSMQ: <xref:System.ServiceModel.NetMsmqBinding> i <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Do czego mogę używać i kiedy?  
  
 **ODP.:** Użyj <xref:System.ServiceModel.NetMsmqBinding> kiedy chcesz używać usługi MSMQ jako transportu dla komunikacji między dwiema aplikacjami usługi WCF z obsługą kolejek. Użyj <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> kiedy chcesz korzystać z istniejących aplikacji usługi MSMQ do komunikowania się z nowych aplikacji WCF.  
  
 **PYT.:** Czy muszę uaktualnić usługi MSMQ, aby użyć <xref:System.ServiceModel.NetMsmqBinding> i `MsmqIntegration` powiązania?  
  
 **ODP.:** Nie. Zarówno powiązania pracować MSMQ 3.0 na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. Niektóre funkcje powiązania stają się dostępne po uaktualnieniu do usługi MSMQ 4.0 w [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
 **PYT.:** Jakie funkcje <xref:System.ServiceModel.NetMsmqBinding> i <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> powiązania są dostępne w usłudze MSMQ 4.0, ale nie w usłudze MSMQ 3.0?  
  
 **ODP.:** Następujące funkcje są dostępne w usłudze MSMQ 4.0, ale nie w usłudze MSMQ 3.0:  
  
- Niestandardowe kolejki utraconych wiadomości jest obsługiwana tylko w usłudze MSMQ 4.0.  
  
- Usługa MSMQ 3.0 i 4.0 obsłużyć inaczej skażone komunikaty.  
  
- Tylko usługi MSMQ 4.0 obsługuje odczyt transakcyjne zdalny.  
  
 Aby uzyskać więcej informacji, zobacz [różnice w funkcjach kolejkowania w Windows Vista, Windows Server 2003 i Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
 **PYT.:** Czy można użyć usługa MSMQ 3.0, po jednej stronie komunikatu w kolejce i MSMQ 4.0 po drugiej stronie?  
  
 **ODP.:** Tak.  
  
 **PYT.:** Chcę integrowanie istniejących aplikacji usługi MSMQ z nowej usługi WCF klientów lub serwerów. Należy uaktualnić obie strony mojej infrastruktury usługi MSMQ?  
  
 **ODP.:** Nie. Jest konieczne uaktualnienie do usługi MSMQ 4.0 po obu stronach.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Ta sekcja zawiera odpowiedzi na typowe problemy dotyczące rozwiązywania problemów. Niektóre problemy, które są znane ograniczenia są także opisane w informacjach o wersji.  
  
 **PYT.:** Próbuję użyć kolejki prywatnej i pojawia się następujący wyjątek: `System.InvalidOperationException`: Adres URL jest nieprawidłowy. Adres URL kolejki nie może zawierać znaku "$". Aby rozwiązać kolejki prywatnej, należy użyć składni net.msmq://machine/private/queueName.  
  
 **ODP.:** Sprawdź, czy kolejka identyfikator (URI) w swojej konfiguracji i kodu. Nie używaj znaku "$" w identyfikatorze URI. Na przykład aby spełnić kolejki prywatnej o nazwie OrdersQueue, należy określić identyfikator URI jako net.msmq://localhost/private/ordersQueue.  
  
 **PYT.:** Wywoływanie `ServiceHost.Open()` w mojej aplikacji umieszczonych w kolejce zgłasza następujący wyjątek: `System.ArgumentException`: Adres podstawowy nie może zawierać ciągu zapytania identyfikatora URI. Dlaczego?  
  
 **ODP.:** Sprawdź kolejki identyfikator URI w pliku konfiguracji i w kodzie. Kolejki usługi MSMQ obsługują korzystanie z '?' znak, identyfikatorów URI interpretuje ten znak jako początek ciągu zapytania. Aby uniknąć tego problemu, należy użyć nazwy kolejek, które nie zawierają "?" znaków.  
  
 **PYT.:** Wyślij moje zakończyło się pomyślnie, ale żadna operacja usługi jest wywoływane na odbiorcy. Dlaczego?  
  
 **ODP.:** Aby ustalić, odpowiedź na pytanie, pracować przy użyciu poniższej liście kontrolnej:  
  
- Upewnij się, że wymagania kolejkę transakcyjną są zgodne z gwarancji określony. Należy zwrócić uwagę następujących zasad:  
  
    - Komunikaty można wysyłać trwałe (datagramy i sesji) za pomocą "dokładnie jednokrotne" gwarancji (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) tylko dla kolejek transakcyjnych.  
  
    - Możesz wysłać sesji tylko w przypadku zapewnienia "dokładnie jednokrotne".  
  
    - Transakcja jest wymagany do odbierania komunikatów w sesji z kolejką transakcyjną.  
  
    - Możesz wysyłać lub odbierać lotnych lub trwałe wiadomości (tylko datagramy) z żadnych zapewnień (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) tylko do kolejki nietransakcyjnej.  
  
- Sprawdź kolejki utraconych wiadomości. Jeśli znajdziesz tam wiadomości, należy ustalić, dlaczego one nie zostały dostarczone.  
  
- Sprawdzanie kolejek wychodzących dla łączności lub odnoszący się problemy.  
  
 **PYT.:** Określony niestandardowy kolejki utraconych wiadomości, ale po uruchomieniu aplikacji nadawcy, pojawia się wyjątek, który nie znajduje się kolejka utraconych lub aplikacji wysyłającej nie ma uprawnienia do kolejki utraconych wiadomości. Dlaczego tak się dzieje?  
  
 **ODP.:** Niestandardowe kolejki utraconych wiadomości URI musi zawierać wartość "localhost" lub nazwa komputera pierwszy segment, na przykład net.msmq://localhost/private/myAppdead-letter kolejki.  
  
 **PYT.:** Go zawsze jest konieczne do definiowania niestandardowej kolejki utraconych wiadomości, lub czy istnieje kolejka utraconych wiadomości domyślnej?  
  
 **ODP.:** W przypadku zapewnienia "dokładnie jednokrotne" (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`), a jeśli nie określisz niestandardowe kolejki utraconych wiadomości, wartością domyślną jest kolejki utraconych wiadomości transakcyjnych całego systemu.  
  
 W przypadku zapewnienia none (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), a następnie wartość domyślna to żadnych funkcji kolejki utraconych wiadomości.  
  
 **PYT.:** Moja usługa zgłoszenie SvcHost.Open za pomocą komunikatu "EndpointListener nie może spełnić wymagań przez ListenerFactory". Dlaczego?  
  
 A. Sprawdź swoje kontraktu usługi. Użytkownik zapomniał do umieszczenia "ustawienie właściwości IsOneWay =`true`" dla wszystkich operacji usługi. Kolejki obsługują tylko operacje jednokierunkowe usługi.  
  
 **PYT.:** Występują komunikaty w kolejce, ale jest wywoływana żadna operacja usługi. Na czym polega problem?  
  
 **ODP.:** Określ, jeśli uległa awarii hosta usługi. Możesz sprawdzić, patrząc śledzenia lub implementacji `IErrorHandler`. Błędy hosta usługi domyślnie w przypadku wykrycia Zarządzanie skażonymi komunikatami.  
  
 **PYT.:** Występują komunikaty w kolejce, ale nie włączono wprowadzenie umieszczonych w kolejce usługi hostowanej w sieci Web. Dlaczego?  
  
 **ODP.:** Najbardziej typową przyczyną jest uprawnień.  
  
1. Upewnij się, że `NetMsmqActivator` proces jest uruchomiony i tożsamość `NetMsmqActivator` proces otrzymuje odczytu i wyszukiwanie uprawnień w kolejce.  
  
2. Jeśli `NetMsmqActivator` jest monitorowanie kolejek na komputerze zdalnym, upewnij się, że `NetMsmqActivator` nie jest uruchomiony tokenu ograniczone. Aby uruchomić `NetMsmqActivator` nieograniczony tokenem:  
  
    ```  
    sc sidtype NetMsmqActivator unrestricted  
    ```  
  
 Powiązane zagadnienia hosta sieci Web niezwiązanych z zabezpieczeniami można znaleźć: [Web hostująca aplikację Zakolejkowaną](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).  
  
 **PYT.:** Co to jest najłatwiejszym sposobem sesje dostępu?  
  
 **ODP.:** Ustaw autouzupełniania =`true` na operację, która odnosi się do ostatniego komunikatu w sesji, a następnie ustaw autouzupełniania =`false` dla wszystkich pozostałych operacji usługi.  
  
 **PYT.:** Gdzie znaleźć odpowiedzi na często zadawane pytania w usłudze MSMQ  
  
 **ODP.:** Aby uzyskać więcej informacji na temat usługi MSMQ, zobacz [usługi kolejkowania komunikatów Microsoft](https://go.microsoft.com/fwlink/?LinkId=87810).  
  
 **PYT.:** Dlaczego zgłosi Moja usługa `ProtocolException` podczas czytania z kolejki, który zawiera zarówno sesji wiadomości w kolejce i datagram wiadomości w kolejce?  
  
 **ODP.:** Jest główną różnicą w komunikatach umieszczonych w kolejce sposób sesji i składają się datagram umieszczonych w kolejce komunikatów. W związku z tym usługa, która oczekuje na odczytywanie wiadomości w kolejce sesji nie może odbierać wiadomości w kolejce datagram i usługi oczekującej elementu do odczytu komunikatu w kolejce datagram nie może zostać wyświetlony komunikat sesji. Podjęto próbę odczytu oba rodzaje komunikatów z tej samej kolejki zgłasza następujący wyjątek:  
  
```  
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.   
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.  
```  
  
 Kolejka utraconych wiadomości systemu, jak również wszelkie niestandardowe kolejka utraconych wiadomości jest szczególnie podatne na ten problem, jeśli aplikacja wysyła zarówno sesji wiadomości w kolejce i umieszczonych w kolejce komunikatów datagramów na tym samym komputerze. Nie można pomyślnie wysłać komunikatu, jest przenoszony do kolejki utraconych wiadomości. W poniższych sytuacjach jest możliwość zarówno sesji i datagram wiadomości w kolejce wiadomości utraconych. Nie istnieje sposób, aby oddzielić oba rodzaje komunikatów w czasie wykonywania, podczas czytania z kolejki, dlatego aplikacje publiczni nie mogą wysyłać zarówno sesji wiadomości w kolejce i umieszczonych w kolejce komunikatów datagramów na tym samym komputerze.  
  
### <a name="msmq-integration-specific-troubleshooting"></a>Integracja usługi MSMQ: Rozwiązywanie określonych problemów  
 **PYT.:** Przy wysyłaniu wiadomości lub podczas otwierania hosta usługi, pojawia się błąd, który wskazuje, że schemat jest nieprawidłowy. Dlaczego?  
  
 **ODP.:** Gdy używasz powiązanie integracji usługi MSMQ, musi używać schematu msmq.formatname. Na przykład msmq.formatname:DIRECT=OS:.\private$\OrdersQueue. Jednak podczas określania niestandardowych kolejki utraconych wiadomości musi używać schematu net.msmq.  
  
 **PYT.:** Kiedy użyć nazwy formatu publicznych lub prywatnych i otworzyć hosta usługi na [!INCLUDE[wv](../../../../includes/wv-md.md)], występuje błąd. Dlaczego?  
  
 **ODP.:** Kanał integracja WCF na [!INCLUDE[wv](../../../../includes/wv-md.md)] kontroli w celu sprawdzenia, jeśli kolejki podrzędnej będzie można otworzyć kolejki głównej aplikacji do obsługi wiadomości. Nazwa kolejki podrzędnej jest pochodną msmq.formatname przekazanych przez identyfikator URI do odbiornika. Nazwa kolejki podrzędnej, w usłudze MSMQ może zawierać tylko z bezpośrednią nazwą formatu. Dlatego zostanie wyświetlony błąd. Zmień URI kolejki z bezpośrednią nazwą formatu.  
  
 **PYT.:** Podczas odbierania komunikatu z aplikacji usługi MSMQ, wiadomość znajduje się w kolejce i nie został odczytany przez aplikację odbierającą WCF. Dlaczego?  
  
 **ODP.:** Sprawdź, czy wiadomość zawiera treść. Jeśli wiadomość ma bez treści, kanał integracji usługi MSMQ ignoruje komunikat. Implementowanie `IErrorHandler` otrzymywania wyjątków i sprawdź śladów.  
  
### <a name="security-related-troubleshooting"></a>Rozwiązywanie związanych z zabezpieczeniami  
 **PYT.:** Po uruchomieniu przykładu, który używa domyślnego powiązania w trybie grupy roboczej, wydaje się, że są wysyłane wiadomości, ale nigdy nie są odbierane przez odbiornik.  
  
 **ODP.:** Domyślnie komunikaty są podpisywane przy użyciu certyfikatu wewnętrznego MSMQ, która wymaga usługi katalogowej Active Directory. W trybie grupy roboczej ponieważ usługi Active Directory nie jest dostępna, podpisywania wiadomości kończy się niepowodzeniem. Dlatego komunikat trafia do kolejki utraconych wiadomości i wskazuje przyczynę błędu, takie jak "Nieodpowiedni podpis".  
  
 Obejście polega na wyłączyć funkcję zabezpieczeń. Jest to realizowane przez ustawienie <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A>  =  <xref:System.ServiceModel.NetMsmqSecurityMode.None> aby umożliwić jej pracę w trybie grupy roboczej.  
  
 Inne obejście jest uzyskanie <xref:System.ServiceModel.MsmqTransportSecurity> z <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> właściwości i ustaw ją na <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>i ustaw certyfikat klienta.  
  
 Jeszcze inne obejście jest zainstalowanie usługi MSMQ z integracją usługi Active Directory.  
  
 **PYT.:** Gdy wysyłanie wiadomości przy użyciu domyślnego powiązania (transportu włączone zabezpieczeń) w usłudze Active Directory do kolejki, wyświetlany jest komunikat "nie można odnaleźć certyfikatu wewnętrznego". Jak rozwiązać ten problem?  
  
 **ODP.:** Oznacza to, czy należy odnawiać certyfikat w usłudze Active Directory dla nadawcy. Aby to zrobić, otwórz **Panelu sterowania**, **narzędzia administracyjne**, **Zarządzanie komputerem**, kliknij prawym przyciskiem myszy **MSMQ**i wybierz **Właściwości**. Wybierz **certyfikatu użytkownika** kartę, a następnie kliknij przycisk **Odnów** przycisku.  
  
 **PYT.:** Kiedy mogę wysłać komunikat przy użyciu <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> i Określ certyfikat do użycia, wyświetlany jest komunikat "Nieprawidłowy certyfikat". Jak rozwiązać ten problem?  
  
 **ODP.:** Tryb certyfikatu nie można używać magazynu certyfikatów komputera lokalnego. Musisz skopiować certyfikat z magazynu certyfikatów komputera w magazynie bieżącego użytkownika za pomocą przystawki certyfikatów. Aby uzyskać certyfikat w przystawce:  
  
1. Kliknij przycisk **Start**, wybierz opcję **Uruchom**, typ `mmc`i kliknij przycisk **OK**.  
  
2. W **programu Microsoft Management Console**, otwórz **pliku** menu, a następnie wybierz **Dodaj/Usuń przystawkę**.  
  
3. W **Dodaj/Usuń przystawkę** okno dialogowe, kliknij przycisk **Dodaj** przycisku.  
  
4. W **Dodawanie przystawki autonomicznej** okno dialogowe, wybierz opcję certyfikaty i kliknij przycisk **Dodaj**.  
  
5. W **certyfikaty** przystawki okno dialogowe, zaznacz **Moje konto użytkownika** i kliknij przycisk **Zakończ**.  
  
6. Następnie dodaj sekundy certyfikatów w przystawce przy użyciu poprzednich kroków, ale tym razem wybierz pozycję **konto komputera** i kliknij przycisk **dalej**.  
  
7. Wybierz **komputera lokalnego** i kliknij przycisk **Zakończ**. Możesz teraz przeciągać i upuszczać certyfikaty z magazynu certyfikatów komputera w magazynie bieżącego użytkownika.  
  
 **PYT.:** Kiedy Moja Usługa odczytuje z kolejki na inny komputer w trybie grupy roboczej, wyświetlany wyjątek "odmowa dostępu".  
  
 **ODP.:** W trybie grupy roboczej, dla aplikacji zdalnej uzyskać dostęp do kolejki aplikacja musi mieć uprawnienia dostępu do kolejki. Dodaj "Logowanie anonimowe" do listy kontroli dostępu kolejki (ACL) i nadaj mu uprawnienia do odczytu.  
  
 **PYT.:** Klient usługi sieciowej (lub dowolnego klienta, który nie ma konta domeny) wysyła wiadomość w kolejce, Wyślij nie powiedzie się z nieprawidłowym certyfikatem. Jak rozwiązać ten problem?  
  
 **ODP.:** Sprawdź konfigurację powiązania. Powiązanie domyślnej ma usługi MSMQ z zabezpieczeń transportu włączone do podpisywanie komunikatów. Wyłącz ją.  
  
### <a name="remote-transacted-receives"></a>Odbiera zdalnego dokonana transakcja  
 **PYT.:** Jeśli mam kolejki dla komputera i usługi WCF, która odczytuje komunikaty z kolejki na komputerze B (zdalne transacted odbieranie scenariusz), wiadomości nie odczytany z kolejki. Informacje śledzenia wskazuje odbieranie nie powiodło się komunikat "transakcji nie można zaimportować." Co mogę zrobić, aby rozwiązać ten problem?  
  
 **ODP.:** Istnieją trzy możliwe przyczyny to:  
  
- Jeśli jesteś w trybie domeny zdalne transacted otrzymywać wymaga dostępu do sieci transakcji Koordynator MSDTC (Microsoft Distributed). Możesz je włączyć za pomocą **Dodaj/Usuń składniki**.  
  
     ![Zrzut ekranu przedstawiający Włączanie sieci usługi DTC dostępu.](./media/troubleshooting-queued-messaging/enable-distributed-transaction-coordinator-access.jpg)  
  
- Sprawdź tryb uwierzytelniania podczas komunikowania się z menedżerem transakcji. Jeśli jesteś w trybie grupy roboczej, należy wybrać "Uwierzytelnienie niewymagane". Jeśli jesteś w trybie domeny, należy wybrać "Wymagane uwierzytelnianie wzajemne".  
  
     ![Enabling XA transactions](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")  
  
- Upewnij się, że usługa MSDTC jest na liście wyjątków w **Zapora połączenia internetowego** ustawienia.  
  
- Upewnij się, że używasz [!INCLUDE[wv](../../../../includes/wv-md.md)]. Usługa MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje odczyt transakcyjne zdalny. Usługi MSMQ w starszych wersjach Windows nie obsługuje zdalnego odczytu transakcyjnego.  
  
 **PYT.:** Gdy usługa czytania z kolejki jest usługą sieciową, na przykład w sieci Web hosta, dlaczego jest zgłaszany wyjątek odmowy dostępu jest wywoływane podczas czytania z kolejki?  
  
 **ODP.:** Dostęp do odczytu usługi sieciowej należy dodać do kolejki, listy ACL, aby upewnić się, że Usługa sieciowa może odczytać z kolejki.  
  
 **PYT.:** Jednak aktywować aplikacje w oparciu o wiadomości w kolejce na komputerze zdalnym można używać usługi MSMQ aktywacji?  
  
 **ODP.:** Tak. Aby to zrobić, należy skonfigurować usługę Aktywacja usługi MSMQ, aby uruchomić jako usługę sieci i dodać dostęp do usługi sieciowej do kolejki na komputerze zdalnym.  
  
## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>Przy użyciu usługi MSMQ niestandardowego powiązania za pomocą elementu ReceiveContext włączone  
 Korzystając z niestandardowego powiązania usługi MSMQ z <xref:System.ServiceModel.Channels.ReceiveContext> włączona, przetwarzanie wiadomości przychodzących będą używać wątku z puli wątków, ponieważ natywnej usługi MSMQ nie obsługuje zakończenia operacji We/Wy dla asynchronicznego <xref:System.ServiceModel.Channels.ReceiveContext> odbiera. Jest to spowodowane przetworzenia takiego komunikatu używa wewnętrzne transakcje w <xref:System.ServiceModel.Channels.ReceiveContext> i usługi MSMQ nie obsługuje przetwarzania asynchronicznego. Aby obejść ten problem, można dodać <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> do punktu końcowego, aby wymusić synchronicznego przetwarzania lub ustaw <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> na 1.
