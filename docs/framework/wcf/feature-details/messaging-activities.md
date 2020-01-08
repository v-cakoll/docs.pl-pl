---
title: Działania dotyczące komunikatów
ms.date: 03/30/2017
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
ms.openlocfilehash: 1e65a3ead9df4103fb270911e3bbb2cc03fcfcba
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347578"
---
# <a name="messaging-activities"></a>Działania dotyczące komunikatów

Działania obsługi komunikatów umożliwiają przepływom pracy wysyłanie i odbieranie komunikatów WCF. Dodając działania obsługi komunikatów do przepływu pracy, można modelować wszelkie arbitralnie złożone wzorce wymiany komunikatów (unikatowy MEP).

## <a name="message-exchange-patterns"></a>Wzorce wymiany komunikatów

Istnieją trzy podstawowe wzorce wymiany komunikatów:

- **Datagram** — w przypadku korzystania z datagramu unikatowy MEP klient wysyła komunikat do usługi, ale usługa nie odpowiada. Jest to czasami nazywane "pożar i zapomnij". Usługa Fire i zapomnij wymiany jest taka, która wymaga potwierdzenia pomyślnego dostarczenia poza pasmem. Komunikat może zostać utracony podczas przesyłania i nigdy nie docierał do usługi. Jeśli klient pomyślnie wyśle komunikat, nie gwarantuje to, że usługa odebrała komunikat. Datagram jest podstawowym blokiem konstrukcyjnym do obsługi komunikatów, ponieważ można stworzyć własny MEPs na jego podstawie.

- **Żądanie-odpowiedź** — w przypadku korzystania z odpowiedzi żądania unikatowy MEP klient wysyła komunikat do usługi, usługa wykonuje wymagane przetwarzanie, a następnie wysyła odpowiedź z powrotem do klienta. Wzorzec składa się z par żądanie-odpowiedź. Przykłady wywołań żądania-odpowiedź to zdalne wywołania procedury (RPC) i żądania GET przeglądarki. Ten wzorzec jest również znany jako półdupleks.

- **Dupleks** — w przypadku używania dupleksu unikatowy MEP klient i usługa może wysyłać komunikaty do siebie w dowolnej kolejności. UNIKATOWY MEP dupleks jest taka sama jak rozmowa telefoniczna, gdzie każdy wypowiadany wyraz jest komunikatem.

Działania związane z obsługą komunikatów umożliwiają wdrożenie dowolnych z tych podstawowych MEPs oraz wszelkich arbitralnie złożonych unikatowy MEP.

## <a name="messaging-activities"></a>Działania dotyczące komunikatów

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] definiuje następujące działania dotyczące komunikatów:

- <xref:System.ServiceModel.Activities.Send>— Użyj działania <xref:System.ServiceModel.Activities.Send> do wysłania wiadomości.

- <xref:System.ServiceModel.Activities.SendReply> — Użyj działania <xref:System.ServiceModel.Activities.SendReply>, aby wysłać odpowiedź do odebranej wiadomości. To działanie jest używane przez usługi przepływu pracy podczas implementowania żądania/odpowiedzi unikatowy MEP.

- <xref:System.ServiceModel.Activities.Receive>— Użyj działania <xref:System.ServiceModel.Activities.Receive> do odebrania komunikatu.

- <xref:System.ServiceModel.Activities.ReceiveReply> — Użyj działania <xref:System.ServiceModel.Activities.ReceiveReply>, aby odebrać komunikat odpowiedzi. To działanie jest używane przez klientów usługi przepływu pracy podczas implementowania żądania/odpowiedzi unikatowy MEP.

## <a name="messaging-activities-and-message-exchange-patterns"></a>Działania obsługi komunikatów i wzorce wymiany komunikatów

UNIKATOWY MEP datagramu obejmuje klienta wysyłającego wiadomość i usługi otrzymującej komunikat. Jeśli klient jest przepływem pracy, Użyj działania <xref:System.ServiceModel.Activities.Send> do wysłania wiadomości. Aby odebrać ten komunikat w przepływie pracy, Użyj działania <xref:System.ServiceModel.Activities.Receive>. Działania <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> mają właściwość o nazwie `Content`. Ta właściwość zawiera dane, które są wysyłane lub odbierane. Podczas wdrażania żądania-Response unikatowy MEP zarówno klienta, jak i usługi używają par działań. Klient używa działania <xref:System.ServiceModel.Activities.Send>, aby wysłać komunikat i <xref:System.ServiceModel.Activities.ReceiveReply> działanie w celu otrzymania odpowiedzi z usługi. Te dwa działania są skojarzone ze sobą przez właściwość <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>. Ta właściwość jest ustawiona na działanie <xref:System.ServiceModel.Activities.Send>, które wysłało oryginalną wiadomość. Usługa używa również pary skojarzonych działań: <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>. Te dwa działania są skojarzone z właściwością <xref:System.ServiceModel.Activities.SendReply.Request%2A>. Ta właściwość jest ustawiona na działanie <xref:System.ServiceModel.Activities.Receive>, które odebrało oryginalny komunikat. Działania <xref:System.ServiceModel.Activities.ReceiveReply> i <xref:System.ServiceModel.Activities.SendReply>, takie jak <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive>, umożliwiają wysyłanie wystąpienia <xref:System.ServiceModel.Channels.Message> lub typu kontraktu komunikatu.

Ze względu na długotrwały charakter przepływów pracy ważne jest, aby wzorzec komunikacji dwukierunkowej obsługiwał również długotrwałe konwersacje. Aby można było obsługiwać długotrwałe konwersacje, klienci inicjujący konwersacje muszą zapewnić usługę z możliwością wywołania jej ponownie w późniejszym czasie, gdy dane staną się dostępne. Na przykład żądanie zamówienia zakupu jest przesyłane do zatwierdzenia przez Menedżera, ale może nie być przetwarzane przez dzień, tydzień lub nawet rok; po podaniu zatwierdzenia należy wznowić przepływ pracy, który zarządza zatwierdzeniem zamówienia zakupu. Ten wzorzec komunikacji dwukierunkowej jest obsługiwany w przepływach pracy przy użyciu korelacji. Aby zaimplementować Wzorzec dupleksu, użyj działań <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive>. Na <xref:System.ServiceModel.Activities.Receive> działanie zainicjuj korelację przy użyciu <xref:System.ServiceModel.Activities.CorrelationHandle>. W ustawieniu działania <xref:System.ServiceModel.Activities.Send>, które obsługują korelację jako wartość właściwości <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A>. Aby uzyskać więcej informacji, zobacz [trwały dupleks](durable-duplex-correlation.md).

> [!NOTE]
> Implementacja przepływności przepływu pracy przy użyciu korelacji wywołania zwrotnego ("trwały dupleks") jest przeznaczona dla długotrwałych konwersacji. Nie jest to takie samo, jak w przypadku programu WCF z kontraktami wywołania zwrotnego, w których konwersacja jest krótkoterminowa (okres istnienia kanału).

## <a name="message-formatting-and-messaging-activities"></a>Formatowanie komunikatów i działania dotyczące komunikatów

Działania <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.ReceiveReply> mają właściwość o nazwie `Content`. Ta właściwość jest typu <xref:System.ServiceModel.Activities.ReceiveContent> i reprezentuje dane, które odbiera <xref:System.ServiceModel.Activities.Receive> lub <xref:System.ServiceModel.Activities.ReceiveReply>. .NET Framework definiuje dwie powiązane klasy o nazwie <xref:System.ServiceModel.Activities.ReceiveMessageContent> i <xref:System.ServiceModel.Activities.ReceiveParametersContent> z których oba pochodzą z <xref:System.ServiceModel.Activities.ReceiveContent>. Ustaw właściwość `Content` działania <xref:System.ServiceModel.Activities.Receive> lub <xref:System.ServiceModel.Activities.ReceiveReply> na wystąpienie jednego z tych typów w taki sposób, aby dane były odbierane w usłudze przepływu pracy. Typ, który ma być używany, zależy od typu danych odbieranych przez działanie. Jeśli działanie odbierze obiekt `Message` lub typ kontraktu komunikatu, użyj <xref:System.ServiceModel.Activities.ReceiveMessageContent>. Jeśli działanie odbiera zestaw kontraktów danych lub typów XML, które mogą być serializowane, użyj <xref:System.ServiceModel.Activities.ReceiveParametersContent>. <xref:System.ServiceModel.Activities.ReceiveParametersContent> umożliwia wysłanie wielu parametrów, podczas gdy <xref:System.ServiceModel.Activities.ReceiveMessageContent> pozwala tylko na wysłanie jednego obiektu, wiadomości (lub typu kontraktu wiadomości).

> [!NOTE]
> <xref:System.ServiceModel.Activities.ReceiveMessageContent> można również użyć z pojedynczym kontraktem danych lub typem XML, który może być serializowany. Różnica między używaniem <xref:System.ServiceModel.Activities.ReceiveParametersContent> z pojedynczym parametrem a obiektem przesłanym bezpośrednio do <xref:System.ServiceModel.Activities.ReceiveMessageContent> jest formatem sieci. Zawartość parametru jest opakowana w element XML, który odnosi się do nazwy operacji, a serializowany obiekt jest opakowany w element XML przy użyciu nazwy parametru (na przykład `<Echo><msg>Hello, World</msg></Echo>`). Zawartość komunikatu nie jest opakowana przez nazwę operacji. Zamiast tego serializowany obiekt jest umieszczany w elemencie XML przy użyciu kwalifikowanej nazwy typu XML (na przykład `<string>Hello, World</string>`).

Działania <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.SendReply> mają również właściwość o nazwie `Content`. Ta właściwość jest typu <xref:System.ServiceModel.Activities.SendContent> i reprezentuje dane wysyłane przez <xref:System.ServiceModel.Activities.Send> lub <xref:System.ServiceModel.Activities.SendReply> działania. .NET Framework definiuje dwa typy powiązane o nazwie <xref:System.ServiceModel.Activities.SendMessageContent> i <xref:System.ServiceModel.Activities.SendParametersContent> obu, które pochodzą z <xref:System.ServiceModel.Activities.SendContent>. Ustaw właściwość `Content` działania <xref:System.ServiceModel.Activities.Send> lub <xref:System.ServiceModel.Activities.SendReply> na wystąpienie jednego z tych typów w celu wysłania danych z usługi przepływu pracy. Typ, który ma być używany, zależy od typu danych wysyłanych przez działanie. Jeśli działanie wysyła obiekt `Message` lub typ kontraktu komunikatu, należy użyć <xref:System.ServiceModel.Activities.SendMessageContent>. Jeśli działanie wysyła typ kontraktu danych, użyj <xref:System.ServiceModel.Activities.SendParametersContent>. <xref:System.ServiceModel.Activities.SendParametersContent> umożliwia wysyłanie wielu parametrów, podczas gdy <xref:System.ServiceModel.Activities.SendMessageContent> pozwala tylko na wysłanie jednego obiektu, wiadomości (lub typu kontraktu wiadomości).

Przy bezwzględnym programowaniu w działaniach związanych z przesyłaniem komunikatów należy użyć ogólnych <xref:System.Activities.InArgument%601> i <xref:System.Activities.OutArgument%601> do zawijania obiektów przypisanych do właściwości komunikatów lub parametrów <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Receive>i <xref:System.ServiceModel.Activities.ReceiveReply>. <xref:System.Activities.InArgument%601> działań <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.SendReply> oraz <xref:System.Activities.OutArgument%601> dla działań <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.ReceiveReply>. argumenty `In` są używane z działaniami wysyłania, ponieważ dane są przesyłane do działań. argumenty `Out` są używane z działaniami odbierania, ponieważ dane są przesyłane z działań, jak pokazano w poniższym przykładzie.

```csharp
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

Podczas implementowania usługi przepływu pracy, która definiuje operację żądania/odpowiedzi zwracającą wartość void, należy utworzyć wystąpienie <xref:System.ServiceModel.Activities.SendReply> działania i ustawić właściwość <xref:System.ServiceModel.Activities.SendReply.Content%2A> na puste wystąpienie jednego z typów zawartości (<xref:System.ServiceModel.Activities.SendMessageContent> lub <xref:System.ServiceModel.Activities.SendParametersContent>), jak pokazano w poniższym przykładzie.

```csharp
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

Podczas wywoływania usługi przepływu pracy z poziomu aplikacji przepływu pracy program Visual Studio 2012 generuje niestandardowe działania obsługi komunikatów, które hermetyzują typowe <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działania używane w unikatowy MEP żądania/odpowiedzi. Aby użyć tej funkcji, kliknij prawym przyciskiem myszy projekt klienta w programie Visual Studio i wybierz polecenie **dodaj** > **odwołanie do usługi**. W polu Adres wpisz adres podstawowy usługi, a następnie kliknij pozycję Przejdź. Dostępne usługi są wyświetlane w polu **usługi:** . Rozwiń węzeł usługi, aby wyświetlić obsługiwane umowy. Wybierz kontrakt do wywołania, a lista dostępnych operacji zostanie wyświetlona w polu **operacje** . Następnie można określić obszar nazw dla wygenerowanego działania i kliknąć przycisk **OK**. Zobaczysz okno dialogowe z informacją, że operacja została ukończona pomyślnie, a wygenerowane działania niestandardowe znajdują się w przyborniku po ponownym skompilowaniu projektu. Istnieje jedno działanie dla każdej operacji zdefiniowanej w kontrakcie usługi. Po ponownym skompilowaniu projektu można przeciągnąć i upuścić niestandardowe działania w przepływie pracy i ustawić wymagane właściwości w oknie właściwości.

## <a name="messaging-activity-templates"></a>Szablony działań związanych z wiadomościami

Aby ułatwić skonfigurowanie żądania/odpowiedzi unikatowy MEP na kliencie i w usłudze, program Visual Studio 2012 udostępnia dwa szablony działań obsługi komunikatów. `System.ServiceModel.Activities.Design.ReceiveAndSendReply` jest używana w usłudze i `System.ServiceModel.Activities.Design.SendAndReceiveReply` jest używana na kliencie. W obu przypadkach szablony dodają odpowiednie działania dotyczące komunikatów do przepływu pracy. W usłudze `System.ServiceModel.Activities.Design.ReceiveAndSendReply` dodaje działanie <xref:System.ServiceModel.Activities.Receive>, a po nim działa <xref:System.ServiceModel.Activities.SendReply>. Właściwość <xref:System.ServiceModel.Activities.SendReply.Request> jest automatycznie ustawiana na działanie <xref:System.ServiceModel.Activities.Receive>. Na kliencie `System.ServiceModel.Activities.Design.SendAndReceiveReply` dodaje działanie <xref:System.ServiceModel.Activities.Send>, po którym następuje <xref:System.ServiceModel.Activities.ReceiveReply>. Właściwość <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> jest automatycznie ustawiana na działanie <xref:System.ServiceModel.Activities.Send>. Aby użyć tych szablonów, przeciągnij i upuść odpowiedni szablon do przepływu pracy.

## <a name="messaging-activities-and-transactions"></a>Działania i transakcje komunikatów

Po wykonaniu wywołania do usługi przepływu pracy możesz chcieć przetworzyć transakcję do operacji usługi. W tym celu należy umieścić <xref:System.ServiceModel.Activities.Receive> działania w ramach działania <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Działanie <xref:System.ServiceModel.Activities.TransactedReceiveScope> zawiera działanie `Receive` i treść. Transakcja przepływa do usługi pozostaje otaczająca przez cały czas wykonywania treści <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Transakcja jest ukończona, gdy treść kończy się wykonywaniem. Aby uzyskać więcej informacji o przepływach pracy i transakcjach, zobacz [transakcje przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md).

## <a name="see-also"></a>Zobacz także

- [Jak wysyłać i odbierać błędy w usługach przepływu pracy](https://go.microsoft.com/fwlink/?LinkId=189151)
- [Tworzenie długo działającej usługi przepływu pracy](creating-a-long-running-workflow-service.md)
