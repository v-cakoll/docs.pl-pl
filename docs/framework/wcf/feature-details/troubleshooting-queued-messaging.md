---
title: Rozwiązywanie problemów obsługi komunikatów kolejek
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: 7990d4b9847ee2f35b9fe6269bb211763c4c80b6
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095011"
---
# <a name="troubleshooting-queued-messaging"></a>Rozwiązywanie problemów obsługi komunikatów kolejek

Ta sekcja zawiera typowe pytania i pomoc dotycząca rozwiązywania problemów dotyczących korzystania z kolejek w programie Windows Communication Foundation (WCF).

## <a name="common-questions"></a>Często zadawane pytania

**P:** Używam programu WCF Beta 1 i zainstalowano poprawkę usługi MSMQ. Czy muszę usunąć poprawkę?

**Odpowiedź:** tak. Ta poprawka nie jest już obsługiwana. Funkcja WCF działa teraz w usłudze MSMQ bez wymaganej poprawki.

**P:** Istnieją dwa powiązania usługi MSMQ: <xref:System.ServiceModel.NetMsmqBinding> i <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Czego mam używać i kiedy?

Odp **.:** Użyj <xref:System.ServiceModel.NetMsmqBinding>, jeśli chcesz użyć usługi MSMQ jako transportu do kolejkowanej komunikacji między dwiema aplikacjami WCF. Użyj <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>, jeśli chcesz używać istniejących aplikacji usługi MSMQ do komunikowania się z nowymi aplikacjami WCF.

**P:** Czy muszę uaktualnić usługę MSMQ, aby używać powiązań <xref:System.ServiceModel.NetMsmqBinding> i `MsmqIntegration`?

**Odpowiedź:** Nie. Oba powiązania działają z usługą MSMQ 3,0 w systemach Windows XP i Windows Server 2003. Niektóre funkcje powiązań stają się dostępne po uaktualnieniu do usługi MSMQ 4,0 w systemie Windows Vista.

**P:** Jakie funkcje powiązań <xref:System.ServiceModel.NetMsmqBinding> i <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> są dostępne w usłudze MSMQ 4,0, ale nie w usłudze MSMQ 3,0?

Odp **.:** W przypadku usługi MSMQ 4,0 dostępne są następujące funkcje, ale nie w usłudze MSMQ 3,0:

- Niestandardowa Kolejka utraconych wiadomości jest obsługiwana tylko w przypadku usługi MSMQ 4,0.

- Usługi MSMQ 3,0 i 4,0 obsługują skażone komunikaty inaczej.

- Tylko usługa MSMQ 4,0 obsługuje zdalne odczyty transakcyjne.

Aby uzyskać więcej informacji, zobacz [różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).

**P:** Czy mogę używać usługi MSMQ 3,0 po jednej stronie komunikacji w kolejce i usługi MSMQ 4,0 po drugiej stronie?

**Odpowiedź:** tak.

**P:** Chcę zintegrować istniejące aplikacje usługi MSMQ z nowymi klientami lub serwerami WCF. Czy muszę uaktualnić obie strony mojej infrastruktury usługi MSMQ?

**Odpowiedź:** Nie. Po obu stronach nie ma potrzeby uaktualniania do usługi MSMQ 4,0.

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Ta sekcja zawiera odpowiedzi na najczęstsze problemy z rozwiązywaniem problemów. Niektóre problemy, które są znane ograniczenia są również opisane w informacjach o wersji.

**P:** Próbuję użyć kolejki prywatnej i otrzymuję następujący wyjątek: `System.InvalidOperationException`: adres URL jest nieprawidłowy. Adres URL kolejki nie może zawierać znaku "$". Użyj składni w usłudze net. MSMQ://machine/private/queueName, aby rozwiązać kolejkę prywatną.

Odp **.:** Sprawdź Uniform Resource Identifier kolejki (URI) w konfiguracji i kodzie. Nie używaj znaku "$" w identyfikatorze URI. Na przykład, aby rozwiązać kolejkę prywatną o nazwie OrdersQueue, określ identyfikator URI jako `net.msmq://localhost/private/ordersQueue`.

**P:** Wywołanie `ServiceHost.Open()` w Kolejkowanej aplikacji zgłasza następujący wyjątek: `System.ArgumentException`: adres podstawowy nie może zawierać ciągu zapytania identyfikatora URI. Dlaczego?

Odp **.:** Sprawdź identyfikator URI kolejki w pliku konfiguracji i w kodzie. Podczas gdy kolejki MSMQ obsługują znak "?", identyfikatory URI interpretują ten znak jako początek zapytania ciągu. Aby uniknąć tego problemu, użyj nazw kolejek, które nie zawierają znaków "?".

**P:** Moje wysłanie zakończyło się pomyślnie, ale na odbiorniku nie została wywołana żadna operacja usługi. Dlaczego?

Odp **.:** Aby określić odpowiedź, należy wykonać następującą listę kontrolną:

- Sprawdź, czy wymagania dotyczące kolejki transakcyjnej są zgodne z określonymi gwarancjami. Należy pamiętać o następujących zasadach:

  - Można wysyłać trwałe wiadomości (datagramy i sesje) z gwarancjami "dokładnie raz" (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) tylko do kolejki transakcyjnej.

  - Sesje można wysyłać tylko za pomocą gwarancji "dokładnie raz".

  - Transakcja jest wymagana do odbierania komunikatów w sesji z kolejki transakcyjnej.

  - Można wysyłać i odbierać nietrwałe lub trwałe komunikaty (tylko datagramy) bez gwarancji (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) tylko do kolejki nietransakcyjnej.

- Sprawdź kolejkę utraconych wiadomości. Jeśli znajdziesz tam komunikaty, określ, dlaczego nie zostały one dostarczone.

- Sprawdź kolejki wychodzące pod kątem problemów z łącznością lub rozruchem.

**P:** Określono niestandardową kolejkę utraconych wiadomości, ale po uruchomieniu aplikacji nadawcy otrzymuję wyjątek, że nie można odnaleźć kolejki utraconych wiadomości lub aplikacja wysyłająca nie ma uprawnień do kolejki utraconych wiadomości. Dlaczego tak się dzieje?

Odp **.:** Niestandardowy identyfikator URI kolejki utraconych wiadomości musi zawierać "localhost" lub nazwę komputera w pierwszym segmencie, na przykład net. MSMQ://localhost/private/myAppdead-letter Queue.

**P:** Czy zawsze konieczne jest zdefiniowanie niestandardowej kolejki utraconych wiadomości lub czy istnieje domyślna kolejka utraconych wiadomości?

Odp **.:** Jeśli program Assurances ma wartość "dokładnie raz" (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`), a jeśli nie określisz niestandardowej kolejki utraconych wiadomości, wartością domyślną będzie Kolejka utraconych wiadomości transakcyjnych w całej systemie.

Jeśli program Assurances nie ma (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), wartość domyślna nie jest funkcją kolejki utraconych wiadomości.

**P:** Moja usługa zgłasza na SvcHost. Otwórz z komunikatem "EndpointListener wymagania nie mogą być spełnione przez ListenerFactory". Dlaczego?

A. Sprawdź kontrakt usługi. Być może zapomniano umieścić "IsOneWay =`true`" we wszystkich operacjach usługi. Kolejki obsługują tylko jednokierunkowe operacje usługi.

**P:** W kolejce znajdują się komunikaty, ale nie jest wywoływana żadna operacja usługi. Na czym polega problem?

Odp **.:** Ustal, czy wystąpił błąd hosta usługi. Możesz sprawdzić, patrząc na ślad lub implementując `IErrorHandler`. Błędy hosta usługi domyślnie, jeśli zostanie wykryty Trująca wiadomość.

**P:** W kolejce znajdują się komunikaty, ale Usługa My hostowana w sieci Web nie jest aktywowana. Dlaczego?

Odp **.:** Najbardziej typową przyczyną są uprawnienia.

1. Upewnij się, że proces `NetMsmqActivator` jest uruchomiony, a tożsamość procesu `NetMsmqActivator` ma przyznane uprawnienie Odczyt i wyszukiwanie w kolejce.

2. Jeśli `NetMsmqActivator` jest monitorowane kolejki na komputerze zdalnym, należy się upewnić, że `NetMsmqActivator` nie działa w ramach ograniczonego tokenu. Aby uruchomić `NetMsmqActivator` przy użyciu nieograniczonego tokenu:

    ```console
    sc sidtype NetMsmqActivator unrestricted
    ```

W przypadku problemów z hostem sieci Web niezwiązanych z zabezpieczeniami odnoszą się do: [hostowanie aplikacji w kolejce](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).

**P:** Co to jest najprostszy sposób uzyskiwania dostępu do sesji?

Odp **.:** Ustaw Autouzupełnianie =`true` operacji, która odnosi się do ostatniej wiadomości w sesji, i ustaw Autouzupełnianie =`false` dla wszystkich pozostałych operacji usługi.

**P:** Dlaczego moja usługa zgłasza `ProtocolException` podczas odczytywania z kolejki zawierającej zarówno komunikaty sesji w kolejce, jak i komunikaty datagramu w kolejce?

Odp **.:** Istnieje fundamentalna różnica w sposobie, w jaki kolejkowane komunikaty sesji i kolejkowane komunikaty datagramu. Z tego względu usługa, która oczekuje na odczytanie komunikatu sesji z kolejką, nie może odebrać komunikatu dataqueue w kolejce, a usługa oczekuje na odczytanie komunikatu dataqueue w kolejce nie może odebrać komunikatu sesji. Próba odczytania obu rodzajów komunikatów z tej samej kolejki zgłasza następujący wyjątek:

```console
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.
```

Kolejka utraconych wiadomości systemowych, a także jakakolwiek niestandardowa Kolejka utraconych wiadomości, jest szczególnie podatna na ten problem, jeśli aplikacja wyśle w kolejce komunikaty sesji i dataqueue z tego samego komputera. Jeśli wiadomość nie może zostać wysłana pomyślnie, zostanie ona przeniesiona do kolejki utraconych wiadomości. W takich okolicznościach istnieje możliwość, że zarówno sesja, jak i datagram komunikatów w kolejce utraconych wiadomości. Nie ma możliwości oddzielenia obydwu typów komunikatów w czasie wykonywania podczas odczytywania z kolejki, w związku z tym aplikacje nie powinny wysyłać komunikatów sesji w kolejce i komunikatów dataqueue umieszczonych w kolejce z tego samego komputera.

### <a name="msmq-integration-specific-troubleshooting"></a>Integracja z usługą MSMQ: konkretne Rozwiązywanie problemów

**P:** Po wysłaniu wiadomości lub po otwarciu hosta usługi otrzymuję komunikat o błędzie informujący, że schemat jest nieprawidłowy. Dlaczego?

Odp **.:** W przypadku korzystania z powiązania integracji usługi MSMQ należy użyć schematu MSMQ. formatname. Na przykład MSMQ. formatname: DIRECT = OS: .\private $ \OrdersQueue. Ale w przypadku określenia niestandardowej kolejki utraconych wiadomości należy użyć schematu net. MSMQ.

**P:** Gdy używam nazwy formatu publicznego lub prywatnego i otworzysz hosta usługi w systemie Windows Vista, pojawia się błąd. Dlaczego?

Odp **.:** Kanał integracji WCF w systemie Windows Vista umożliwia sprawdzenie, czy podkolejka może być otwarta dla kolejki aplikacji głównej w celu obsługi skażonych komunikatów. Nazwa kolejki podrzędnej pochodzi od identyfikatora URI MSMQ. formatname przesłanego do odbiornika. Nazwa kolejki podrzędnej w usłudze MSMQ może być tylko nazwą formatu bezpośredniego. Zostanie wyświetlony komunikat o błędzie. Zmień identyfikator URI kolejki na nazwę formatu bezpośredniego.

**P:** W przypadku odebrania komunikatu z aplikacji MSMQ komunikat znajduje się w kolejce i nie jest odczytywany przez odebraną aplikację WCF. Dlaczego?

Odp **.:** Sprawdź, czy komunikat ma treść. Jeśli komunikat nie ma treści, kanał integracji usługi MSMQ zignoruje komunikat. Zaimplementuj `IErrorHandler`, aby otrzymywać powiadomienia o wyjątkach i sprawdź dane śledzenia.

### <a name="security-related-troubleshooting"></a>Rozwiązywanie problemów związanych z zabezpieczeniami

**P:** Gdy uruchamiam przykład, który używa domyślnego powiązania w trybie grupy roboczej, komunikaty pozornie są wysyłane, ale nigdy nie odbierane przez odbiornik.

Odp **.:** Domyślnie komunikaty są podpisane przy użyciu wewnętrznego certyfikatu usługi MSMQ, który wymaga usługi katalogowej Active Directory. W trybie grupy roboczej, ponieważ Active Directory nie jest dostępny, podpisywanie komunikatu kończy się niepowodzeniem. W związku z tym komunikat znajduje się w kolejce utraconych wiadomości i Przyczyna niepowodzenia, na przykład "zła sygnatura".

Obejście polega na wyłączeniu zabezpieczeń. W tym celu należy ustawić <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A> = <xref:System.ServiceModel.NetMsmqSecurityMode.None>, aby działał on w trybie grupy roboczej.

Innym obejściem jest uzyskanie <xref:System.ServiceModel.MsmqTransportSecurity> ze właściwości <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> i ustawienie go na <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>i ustawienie certyfikatu klienta.

Jeszcze inne obejście polega na zainstalowaniu usługi MSMQ z integracją Active Directory.

**P:** Gdy wysyłam komunikat z domyślnym powiązaniem (włączone zabezpieczenia transportu) w Active Directory do kolejki, otrzymuję komunikat "nie znaleziono certyfikatu wewnętrznego". Jak mogę rozwiązać ten problem?

Odp **.:** Oznacza to, że należy odnowić certyfikat w Active Directory dla nadawcy. W tym celu Otwórz **Panel sterowania**, **Narzędzia administracyjne**, **Zarządzanie komputerem**, kliknij prawym przyciskiem myszy pozycję **MSMQ**i wybierz pozycję **Właściwości**. Wybierz kartę **certyfikat użytkownika** , a następnie kliknij przycisk **Odnów** .

**P:** Gdy wyślę komunikat przy użyciu <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> i określisz certyfikat do użycia, otrzymuję komunikat o nieprawidłowym certyfikacie. Jak mogę rozwiązać ten problem?

Odp **.:** Nie można użyć magazynu certyfikatów komputera lokalnego z trybem certyfikatu. Należy skopiować certyfikat z magazynu certyfikatów komputera do bieżącego magazynu użytkowników przy użyciu przystawki certyfikat. Aby uzyskać przystawkę certyfikatu:

1. Kliknij przycisk **Start**, wybierz polecenie **uruchom**, wpisz `mmc`i kliknij przycisk **OK**.

2. W programie **Microsoft Management Console**Otwórz menu **plik** i wybierz polecenie **Dodaj/Usuń przystawkę**.

3. W oknie dialogowym **Dodaj/Usuń przystawkę** kliknij przycisk **Dodaj** .

4. W oknie dialogowym **Dodaj autonomiczną przystawkę** wybierz pozycję Certyfikaty, a następnie kliknij przycisk **Dodaj**.

5. W oknie dialogowym Przystawka **certyfikatów** wybierz pozycję **Moje konto użytkownika,** a następnie kliknij przycisk **Zakończ**.

6. Następnie Dodaj drugą przystawkę Certyfikaty przy użyciu poprzednich kroków, ale tym razem wybierz pozycję **konto komputera** i kliknij przycisk **dalej**.

7. Wybierz pozycję **komputer lokalny** i kliknij przycisk **Zakończ**. Teraz możesz przeciągać i upuszczać certyfikaty z magazynu certyfikatów komputera do bieżącego magazynu użytkownika.

**P:** Gdy Usługa My odczytuje z kolejki na innym komputerze w trybie grupy roboczej, otrzymuję wyjątek "odmowa dostępu".

Odp **.:** W trybie grupy roboczej dla aplikacji zdalnej, aby uzyskać dostęp do kolejki, aplikacja musi mieć uprawnienia dostępu do kolejki. Dodaj "Logowanie anonimowe" do listy kontroli dostępu (ACL) kolejki i nadaj im uprawnienie do odczytu.

**P:** Gdy klient usługi sieciowej (lub dowolny klient, który nie ma konta domeny) wysyła komunikat w kolejce, wysyłanie kończy się niepowodzeniem z nieprawidłowym certyfikatem. Jak mogę rozwiązać ten problem?

Odp **.:** Sprawdź konfigurację powiązania. Domyślne powiązanie ma włączone zabezpieczenia transportu usługi MSMQ w celu podpisania wiadomości. Go wyłączyć.

### <a name="remote-transacted-receives"></a>Zdalne odbierane odbiory

**P:** Jeśli mam kolejkę na maszynie A, a usługa WCF, która odczytuje komunikaty z kolejki na komputerze B (zdalnie zrealizowany scenariusz odbierania), wiadomości nie są odczytywane z kolejki. Śledzenie informacji wskazuje, że odbieranie nie powiodło się z komunikatem "nie można zaimportować transakcji". Co mogę zrobić, aby rozwiązać ten problem?

Odp **.:** Istnieją trzy możliwe przyczyny tego:

- W trybie domeny zdalne odbieranie transakcyjne wymaga dostępu do sieci firmy Microsoft Distributed Transaction Coordinator (MSDTC). Możesz włączyć tę funkcję przy użyciu opcji **Dodaj/Usuń składniki**.

  ![Zrzut ekranu pokazujący Włączanie dostępu do usługi DTC przez sieć.](./media/troubleshooting-queued-messaging/enable-distributed-transaction-coordinator-access.jpg)

- Sprawdź tryb uwierzytelniania, aby komunikować się z menedżerem transakcji. Jeśli jesteś w trybie grupy roboczej, należy wybrać opcję "nie jest wymagane uwierzytelnienie". Jeśli jesteś w trybie domeny, należy wybrać opcję "wymagane uwierzytelnianie wzajemne.

  ![Włączanie transakcji XA](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")

- Upewnij się, że usługa MSDTC znajduje się na liście wyjątków w ustawieniach **zapory połączenia internetowego** .

- Upewnij się, że korzystasz z systemu Windows Vista. Usługa MSMQ w systemie Windows Vista obsługuje zdalnie odczytywanie transakcyjne. Usługa MSMQ w starszych wersjach systemu Windows nie obsługuje zdalnej operacji odczytu.

**P:** Gdy usługa jest odczytywana z kolejki usługi sieciowej, na przykład w hoście sieci Web, Dlaczego otrzymuję wyjątek odmowy dostępu w przypadku odczytu z kolejki?

Odp **.:** Dostęp do odczytu usługi sieciowej należy dodać do listy ACL kolejki, aby upewnić się, że usługa sieciowa może odczytywać dane z kolejki.

**P:** Czy mogę użyć usługi aktywacji usługi MSMQ w celu aktywowania aplikacji na podstawie komunikatów w kolejce na maszynie zdalnej?

**Odpowiedź:** tak. W tym celu należy skonfigurować usługę aktywacji usługi MSMQ do uruchamiania jako usługa sieciowa i dodać do kolejki dostęp do usługi sieciowej na maszynie zdalnej.

## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>Używanie niestandardowych powiązań usługi MSMQ z włączonym użyciem funkcji ReceiveContext

W przypadku korzystania z niestandardowego powiązania usługi MSMQ z włączonym <xref:System.ServiceModel.Channels.ReceiveContext> przetwarzanie komunikatu przychodzącego korzysta z wątku puli wątków, ponieważ natywna usługa MSMQ nie obsługuje kończenia operacji we/wy dla odbieranych <xref:System.ServiceModel.Channels.ReceiveContext> asynchronicznych. Wynika to z faktu, że przetwarzanie takich komunikatów używa transakcji wewnętrznych dla <xref:System.ServiceModel.Channels.ReceiveContext>, a usługa MSMQ nie obsługuje przetwarzania asynchronicznego. Aby obejść ten problem, można dodać <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> do punktu końcowego w celu wymuszenia przetwarzania synchronicznego lub ustawienia <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> na 1.
