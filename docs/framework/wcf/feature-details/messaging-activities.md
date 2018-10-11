---
title: Działania dotyczące komunikatów
ms.date: 03/30/2017
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
ms.openlocfilehash: 3391f7442ef4922a847a58b6316eb177cbcfbd5e
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086345"
---
# <a name="messaging-activities"></a>Działania dotyczące komunikatów
Działań dotyczących komunikatów umożliwiają przepływy pracy służące do wysyłania i odbierania komunikatów WCF. Dodając działań dotyczących komunikatów do przepływu pracy można modelować wszystkie wzorce exchange dowolnie złożone komunikat (MEP).

## <a name="message-exchange-patterns"></a>Wzorce wymiany komunikatów
 Istnieją trzy wzorce exchange podstawowe wiadomości:

-   **Datagram** — korzystając z datagram MEP klient wysyła komunikat do usługi, ale usługa nie odpowiada. Jest to czasami nazywane "fire and forget". Element zostanie wyzwolony i zapomnij programu exchange to taki, który wymaga potwierdzenia out-of-band skutecznej. Komunikat może zostać utracone podczas przesyłania i nigdy nie dotrzeć do usługi. Jeśli klient jest pomyślnie wysyłana wiadomość, nie gwarantuje to, że usługa odebrała wiadomość. Datagram jest elementem konstrukcyjnym podstawowych do obsługi komunikatów, jak tworzyć własne MEPs na ich podstawie.

-   **Odpowiedź na żądanie** — przy użyciu MEP odpowiedź na żądanie klienta wysyła komunikat do usługi, usługa nie wymagane przetwarzanie, a następnie wysyła odpowiedź z powrotem do klienta. Wzorzec składa się z pary odpowiedź na żądanie. Odpowiedź na żądanie wywołania przykłady zdalnych wywołań procedur (RPC) i przeglądarka GET żądań. Ten wzorzec jest nazywany również półdupleks.

-   **Dwukierunkowe** — w przypadku usługi dwukierunkowego MEP klient i usługa wiadomości można wysyłać do siebie nawzajem w dowolnej kolejności. Dwukierunkowego MEP przypomina rozmowy telefonicznej, gdzie każdy wyraz mowy jest komunikat.

 Działań dotyczących komunikatów umożliwiają implementowanie dowolnego z tych podstawowych MEPs, a także wszelkie MEP dowolnie złożone.

## <a name="messaging-activities"></a>Działania dotyczące komunikatów
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Definiuje następujących działań dotyczących komunikatów:

-   <xref:System.ServiceModel.Activities.Send>-Użyj <xref:System.ServiceModel.Activities.Send> działanie, aby wysłać wiadomość.

-   <xref:System.ServiceModel.Activities.SendReply> -Użyj <xref:System.ServiceModel.Activities.SendReply> działanie, aby wysłać odpowiedź do odebranego komunikatu. To działanie jest używane przez usługi przepływu pracy podczas implementowania żądanie/nietypizowana odpowiedź MEP.

-   <xref:System.ServiceModel.Activities.Receive>-Użyj <xref:System.ServiceModel.Activities.Receive> działanie komunikat o błędzie.

-   <xref:System.ServiceModel.Activities.ReceiveReply> -Użyj <xref:System.ServiceModel.Activities.ReceiveReply> działanie, aby odbierać komunikat odpowiedzi. To działanie jest używany przez klientów usługi przepływu pracy, podczas implementowania żądanie/nietypizowana odpowiedź MEP.

## <a name="messaging-activities-and-message-exchange-patterns"></a>Działań dotyczących komunikatów i wzorców wymiany komunikatów
 Datagram MEP polega na klienta, wysyłanie wiadomości, a Usługa odbierania komunikatów. Jeśli klient jest użycie przepływu pracy <xref:System.ServiceModel.Activities.Send> działanie, aby wysłać wiadomość. Aby otrzymać tę wiadomość w przepływie pracy, użyj <xref:System.ServiceModel.Activities.Receive> działania. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> działania każdego mieć właściwość o nazwie `Content`. Ta właściwość zawiera danych wysyłanych lub odbieranych. Podczas implementowania MEP odpowiedź na żądanie klienta i usługi użyj pary działań. Klient używa <xref:System.ServiceModel.Activities.Send> działanie, aby wysłać wiadomość i <xref:System.ServiceModel.Activities.ReceiveReply> działanie do odbierania odpowiedzi z usługi. Te dwa działania są skojarzone ze sobą przez <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> właściwości. Ta właściwość jest ustawiona <xref:System.ServiceModel.Activities.Send> działania, który wysłał oryginalny wiadomość. Usługa również używa pary skojarzonych działań: <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>. Te dwa działania są skojarzone, <xref:System.ServiceModel.Activities.SendReply.Request%2A> właściwości. Ta właściwość jest ustawiona <xref:System.ServiceModel.Activities.Receive> działania, który otrzymał oryginalnej wiadomości. <xref:System.ServiceModel.Activities.ReceiveReply> i <xref:System.ServiceModel.Activities.SendReply> działania, takie jak <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> umożliwiają wysyłanie <xref:System.ServiceModel.Channels.Message> wystąpienie lub typ kontraktu komunikatu.

 Ze względu na charakter długotrwałe przepływy pracy jest ważne w przypadku dwukierunkowego wzorzec komunikacji w celu obsługi długotrwałych konwersacji. Do obsługi rozmów długotrwałych, klienci, którzy inicjowania rozmowy musi świadczyć usługi użytkownikom możliwość wywołać go z powrotem w późniejszym czasie, gdy dane będą dostępne. Na przykład żądanie zamówienia zakupu zostanie przesłana do zatwierdzenia przez menedżera, ale nie może być przetwarzana dla dnia, tygodnia lub nawet przez rok; przepływ pracy, który zarządza zatwierdzenia zamówienia zakupu musi wiedzieć, aby wznowić po zatwierdzeniu. Ten wzorzec komunikację dupleksową jest obsługiwana w przepływach pracy przy użyciu korelacji. Aby zaimplementować wzorzec dupleksowy, należy użyć <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> działań. Na <xref:System.ServiceModel.Activities.Receive> działania, zainicjuj korelacji przy użyciu specjalnych wartości klucza <!--zz <xref:System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName%2A>--> `System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName`. Na <xref:System.ServiceModel.Activities.Send> dojścia korelacji jako zestaw działań <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> wartości właściwości. Aby uzyskać więcej informacji, zobacz [trwałe dwukierunkowego](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md).

> [!NOTE]
>  Wykonania przepływu pracy dupleks przy użyciu wywołania zwrotnego korelacja ("trwałość dupleks") jest przeznaczona dla długotrwałych konwersacji. To nie jest taka sama jak WCF dwukierunkowego za pomocą wywołania zwrotnege kontraktów typu gdzie konwersacji jest krótko działających (okres istnienia kanału).

## <a name="message-formatting-and-messaging-activities"></a>Formatowanie wiadomości i działań dotyczących komunikatów
 <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.ReceiveReply> działania mają właściwość o nazwie `Content`. Ta właściwość jest typu <xref:System.ServiceModel.Activities.ReceiveContent> i reprezentuje dane <xref:System.ServiceModel.Activities.Receive> lub <xref:System.ServiceModel.Activities.ReceiveReply> odbiera działania. .NET Framework definiuje dwie klasy pokrewne o nazwie <xref:System.ServiceModel.Activities.ReceiveMessageContent> i <xref:System.ServiceModel.Activities.ReceiveParametersContent> oba są uzyskiwane z <xref:System.ServiceModel.Activities.ReceiveContent>. Ustaw <xref:System.ServiceModel.Activities.Receive> lub <xref:System.ServiceModel.Activities.ReceiveReply> działania `Content` właściwości wystąpienia jednego z tych typów w celu odbierania danych w usłudze przepływu pracy. Typ do użycia zależy od typu danych, który otrzyma działania. Jeśli działanie otrzyma `Message` obiektu lub komunikat typu kontraktu, należy użyć <xref:System.ServiceModel.Activities.ReceiveMessageContent>. Jeśli działanie odbiera zestaw kontraktu danych lub typy XML, które może być Zserializowany, użyj <xref:System.ServiceModel.Activities.ReceiveParametersContent>. <xref:System.ServiceModel.Activities.ReceiveParametersContent> umożliwi to wysyłanie wielu parametrów, dlatego <xref:System.ServiceModel.Activities.ReceiveMessageContent> pozwala tylko jeden obiekt send, wiadomość (lub typ kontraktu komunikatu).

> [!NOTE]
>  <xref:System.ServiceModel.Activities.ReceiveMessageContent> można również za pomocą kontraktu danych jednego lub typu XML, który może być serializowany. Różnica między <xref:System.ServiceModel.Activities.ReceiveParametersContent> z pojedynczy parametr oraz obiekt przekazany bezpośrednio do <xref:System.ServiceModel.Activities.ReceiveMessageContent> to format o komunikacji sieciowej. Zawartość parametru jest opakowane w elemencie XML, który odpowiada nazwie operacji i Zserializowany obiekt jest opakowany element XML przy użyciu nazwy parametrów (na przykład `<Echo><msg>Hello, World</msg></Echo>`). Zawartość komunikatu nie jest otoczony przez nazwy operacji. Zamiast tego Zserializowany obiekt znajduje się w obrębie elementu XML przy użyciu nazwy kwalifikowanej XML typu (na przykład `<string>Hello, World</string>`).

 <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.SendReply> działania mają również właściwość o nazwie `Content`. Ta właściwość jest typu <xref:System.ServiceModel.Activities.SendContent> i reprezentuje dane <xref:System.ServiceModel.Activities.Send> lub <xref:System.ServiceModel.Activities.SendReply> wysyła działania. .NET Framework definiuje dwa typy powiązanej o nazwie <xref:System.ServiceModel.Activities.SendMessageContent> i <xref:System.ServiceModel.Activities.SendParametersContent> oba są uzyskiwane z <xref:System.ServiceModel.Activities.SendContent>. Ustaw <xref:System.ServiceModel.Activities.Send> lub <xref:System.ServiceModel.Activities.SendReply> działania `Content` właściwości wystąpienia jednego z tych typów w celu wysyłania danych z usługi przepływu pracy. Typ do użycia zależy od typu danych, które wysyła działania. Jeśli działanie wysyła `Message` obiektu lub komunikat typu kontraktu, należy użyć <xref:System.ServiceModel.Activities.SendMessageContent>. Jeśli działanie wysyła użycie typu kontraktu danych <xref:System.ServiceModel.Activities.SendParametersContent>. <xref:System.ServiceModel.Activities.SendParametersContent> umożliwi to wysyłanie wielu parametrów, dlatego <xref:System.ServiceModel.Activities.SendMessageContent> umożliwia tylko wysyłanie obiektów (komunikatu lub typ kontraktu komunikatu).

 Programowanie obowiązkowo, przy użyciu działań dotyczących komunikatów, za pomocą ogólnego <xref:System.Activities.InArgument%601> i <xref:System.Activities.OutArgument%601> opakowywać obiektów, możesz przypisać do właściwości wiadomości lub parametry <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Receive>i <xref:System.ServiceModel.Activities.ReceiveReply>działań. Użyj <xref:System.Activities.InArgument%601> dla <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.SendReply> działań i <xref:System.Activities.OutArgument%601> dla <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.ReceiveReply> działań. `In` argumenty są używane z działań wysyłania, ponieważ dane jest przekazywana do działania. `Out` argumenty są używane z działaniami receive, ponieważ data jest przekazywana poza działań, jak pokazano w poniższym przykładzie.

```
Receive reserveSeat = new Receive
{
    ...
    Content = new ReceiveParametersContent
    {
        Parameters =
        {
            { "ReservationInfo", new OutArgument<ReservationRequest>(reservationInfo) }
        }
    }
};
SendReply reserveSeat = new SendReply
{
    ...
    Request = reserveSeat,
    Content = new SendParametersContent
    {
        Parameters =
        {
            { "ReservationId", new InArgument<string>(reservationId) }
        }
    },
};
```

 Podczas implementowania usługi przepływu pracy, który definiuje operację żądania/odpowiedzi, który zwraca wartość typu void, trzeba utworzyć <xref:System.ServiceModel.Activities.SendReply> działania i ustaw <xref:System.ServiceModel.Activities.SendReply.Content%2A> właściwość puste wystąpienie jednego z typów zawartości (<xref:System.ServiceModel.Activities.SendMessageContent> lub <xref:System.ServiceModel.Activities.SendParametersContent>) jak pokazano w poniższym przykładzie.

```
Receive rcv = new Receive()
{
ServiceContractName = "IService",
OperationName = "NullReturningContract",
Content = new ReceiveParametersContent( new Dictionary<string, OutArgument>() { { "message", new OutArgument<string>() } } )
};
SendReply sr = new SendReply()
{
Request = rcv
   Content = new SendParametersContent();
};
```

## <a name="add-service-reference"></a>Dodaj odwołanie do usługi
 Podczas wywoływania usługi przepływu pracy z poziomu aplikacji przepływu pracy, Visual Studio 2012 generuje niestandardowych działań dotyczących komunikatów, które hermetyzują zwykłego <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań używanych w żądanie/nietypizowana odpowiedź MEP. Aby użyć tej funkcji, kliknij prawym przyciskiem myszy projekt klienta w programie Visual Studio, a następnie wybierz **Dodaj** > **odwołanie do usługi**. W polu adresu wpisz adres podstawowy usługi, a następnie kliknij przycisk z rzeczywistym użyciem. Dostępne usługi są wyświetlane w **usług:** pole. Rozwiń węzeł usługi do wyświetlania zamówień obsługiwane. Zaznacz kontrakt, który chcesz wybrać i zostanie wyświetlona lista dostępnych operacji, w **operacji** pole. Następnie określ obszar nazw dla wygenerowanego działania i kliknij przycisk **OK**. Wtedy wyświetlone okno dialogowe komunikat, operacja została ukończona pomyślnie, a po mają odbudować projektu wygenerowane działania niestandardowe są w przyborniku. Występuje jedno działanie, dla każdej operacji zdefiniowany w kontrakcie usługi. Po ponownie skompilować projekt możesz przeciągnąć i upuścić niestandardowe działania przepływu pracy i ustawić wszelkie wymagane właściwości w oknie dialogowym właściwości.

<!--## Messaging Activity Templates
 To make setting up a request/response MEP on the client and service easier, Visual Studio 2012 provides two messaging activity templates. <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> is used on the service and <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> is used on the client. In both cases the templates add the appropriate messaging activities to your workflow. On the service, the <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> adds a <xref:System.ServiceModel.Activities.Receive> activity followed by a <xref:System.ServiceModel.Activities.SendReply> activity. The <xref:System.ServiceModel.Activities.SendReply.Request> property is automatically set to the <xref:System.ServiceModel.Activities.Receive> activity. On the client, the <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> adds a <xref:System.ServiceModel.Activities.Send> activity followed by a <xref:System.ServiceModel.Activities.ReceiveReply>. The <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> property is automatically set to the <xref:System.ServiceModel.Activities.Send> activity. To use these templates, just drag and drop the appropriate template onto your workflow.
-->
## <a name="messaging-activities-and-transactions"></a>Działań dotyczących komunikatów i transakcji
 Gdy połączenie jest nawiązywane w przypadku usługi przepływu pracy można przepływu transakcji do operacji usługi. Aby zrobić to miejsce <xref:System.ServiceModel.Activities.Receive> działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Zawiera działanie `Receive` działanie i treść. Transakcja przekazane do otoczenia podczas wykonywania treści pozostaje usługi <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Transakcja jest zakończona, gdy treść zakończy się wykonywanie. Aby uzyskać więcej informacji na temat przepływów pracy i transakcje zobacz [transakcje przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md).

## <a name="see-also"></a>Zobacz też
- [Jak wysyłanie i odbieranie błędów w usługach przepływu pracy](https://go.microsoft.com/fwlink/?LinkId=189151)
- [Tworzenie długo działającej usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
