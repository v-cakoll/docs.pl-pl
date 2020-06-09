---
title: Działania dotyczące komunikatów
ms.date: 03/30/2017
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
ms.openlocfilehash: 69a0e9a415b10d9c58d04eac27e48b1ed6a78064
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576398"
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

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]Definiuje następujące działania dotyczące komunikatów:

- <xref:System.ServiceModel.Activities.Send>— Użyj <xref:System.ServiceModel.Activities.Send> działania, aby wysłać wiadomość.

- <xref:System.ServiceModel.Activities.SendReply>— Użyj <xref:System.ServiceModel.Activities.SendReply> działania, aby wysłać odpowiedź do odebranej wiadomości. To działanie jest używane przez usługi przepływu pracy podczas implementowania żądania/odpowiedzi unikatowy MEP.

- <xref:System.ServiceModel.Activities.Receive>— Użyj <xref:System.ServiceModel.Activities.Receive> działania, aby odebrać komunikat.

- <xref:System.ServiceModel.Activities.ReceiveReply>— Użyj <xref:System.ServiceModel.Activities.ReceiveReply> działania, aby otrzymać komunikat odpowiedzi. To działanie jest używane przez klientów usługi przepływu pracy podczas implementowania żądania/odpowiedzi unikatowy MEP.

## <a name="messaging-activities-and-message-exchange-patterns"></a>Działania obsługi komunikatów i wzorce wymiany komunikatów

UNIKATOWY MEP datagramu obejmuje klienta wysyłającego wiadomość i usługi otrzymującej komunikat. Jeśli klient jest przepływem pracy, użyj <xref:System.ServiceModel.Activities.Send> działania do wysłania wiadomości. Aby odebrać ten komunikat w przepływie pracy, użyj <xref:System.ServiceModel.Activities.Receive> działania. <xref:System.ServiceModel.Activities.Send>Każdy z <xref:System.ServiceModel.Activities.Receive> nich ma właściwość o nazwie `Content` . Ta właściwość zawiera dane, które są wysyłane lub odbierane. Podczas wdrażania żądania-Response unikatowy MEP zarówno klienta, jak i usługi używają par działań. Klient używa <xref:System.ServiceModel.Activities.Send> działania do wysłania wiadomości i <xref:System.ServiceModel.Activities.ReceiveReply> działania w celu odebrania odpowiedzi z usługi. Te dwa działania są skojarzone ze sobą przez <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> Właściwość. Ta właściwość jest ustawiona na <xref:System.ServiceModel.Activities.Send> działanie, które wysłało oryginalną wiadomość. Usługa używa również pary skojarzonych działań: <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply> . Te dwa działania są skojarzone z <xref:System.ServiceModel.Activities.SendReply.Request%2A> właściwością. Ta właściwość jest ustawiona na <xref:System.ServiceModel.Activities.Receive> działanie, które odebrało oryginalną wiadomość. <xref:System.ServiceModel.Activities.ReceiveReply>Działania i <xref:System.ServiceModel.Activities.SendReply> , takie jak <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> umożliwiają wysyłanie <xref:System.ServiceModel.Channels.Message> wystąpienia lub typu kontraktu komunikatu.

Ze względu na długotrwały charakter przepływów pracy ważne jest, aby wzorzec komunikacji dwukierunkowej obsługiwał również długotrwałe konwersacje. Aby można było obsługiwać długotrwałe konwersacje, klienci inicjujący konwersacje muszą zapewnić usługę z możliwością wywołania jej ponownie w późniejszym czasie, gdy dane staną się dostępne. Na przykład żądanie zamówienia zakupu jest przesyłane do zatwierdzenia przez Menedżera, ale może nie być przetwarzane przez dzień, tydzień lub nawet rok; po podaniu zatwierdzenia należy wznowić przepływ pracy, który zarządza zatwierdzeniem zamówienia zakupu. Ten wzorzec komunikacji dwukierunkowej jest obsługiwany w przepływach pracy przy użyciu korelacji. Do implementacji wzorca dupleksowego, używania <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> działań. W <xref:System.ServiceModel.Activities.Receive> działaniu zainicjuj korelację przy użyciu <xref:System.ServiceModel.Activities.CorrelationHandle> . W <xref:System.ServiceModel.Activities.Send> ustawieniu działanie, które obsługuje dojście korelacji jako <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> wartość właściwości. Aby uzyskać więcej informacji, zobacz [trwały dupleks](durable-duplex-correlation.md).

> [!NOTE]
> Implementacja przepływności przepływu pracy przy użyciu korelacji wywołania zwrotnego ("trwały dupleks") jest przeznaczona dla długotrwałych konwersacji. Nie jest to takie samo, jak w przypadku programu WCF z kontraktami wywołania zwrotnego, w których konwersacja jest krótkoterminowa (okres istnienia kanału).

## <a name="message-formatting-and-messaging-activities"></a>Formatowanie komunikatów i działania dotyczące komunikatów

<xref:System.ServiceModel.Activities.Receive>Działania i <xref:System.ServiceModel.Activities.ReceiveReply> mają właściwość o nazwie `Content` . Ta właściwość jest typu <xref:System.ServiceModel.Activities.ReceiveContent> i reprezentuje dane, które <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.ReceiveReply> odbiera. .NET Framework definiuje dwie powiązane klasy o nazwie <xref:System.ServiceModel.Activities.ReceiveMessageContent> i <xref:System.ServiceModel.Activities.ReceiveParametersContent> obie pochodne od <xref:System.ServiceModel.Activities.ReceiveContent> . Ustaw <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.ReceiveReply> Właściwość działania lub `Content` na wystąpienie jednego z tych typów, aby odbierać dane do usługi przepływu pracy. Typ, który ma być używany, zależy od typu danych odbieranych przez działanie. Jeśli działanie odbierze `Message` obiekt lub typ kontraktu komunikatu, użyj <xref:System.ServiceModel.Activities.ReceiveMessageContent> . Jeśli działanie odbiera zestaw kontraktów danych lub typów XML, które mogą być serializowane, użyj <xref:System.ServiceModel.Activities.ReceiveParametersContent> . <xref:System.ServiceModel.Activities.ReceiveParametersContent>umożliwia wysyłanie wielu parametrów, a <xref:System.ServiceModel.Activities.ReceiveMessageContent> jedynie umożliwia wysyłanie tylko jednego obiektu, wiadomości (lub typu kontraktu wiadomości).

> [!NOTE]
> <xref:System.ServiceModel.Activities.ReceiveMessageContent>może być również używany z pojedynczym kontraktem danych lub typem XML, który może być serializowany. Różnica między użyciem <xref:System.ServiceModel.Activities.ReceiveParametersContent> z pojedynczym parametrem a obiektem przekazanym bezpośrednio do <xref:System.ServiceModel.Activities.ReceiveMessageContent> formatu sieci. Zawartość parametru jest opakowana w element XML, który odnosi się do nazwy operacji, a serializowany obiekt jest opakowany w element XML przy użyciu nazwy parametru (na przykład `<Echo><msg>Hello, World</msg></Echo>` ). Zawartość komunikatu nie jest opakowana przez nazwę operacji. Zamiast tego serializowany obiekt jest umieszczany w elemencie XML przy użyciu kwalifikowanej nazwy typu XML (na przykład `<string>Hello, World</string>` ).

<xref:System.ServiceModel.Activities.Send>Działania i <xref:System.ServiceModel.Activities.SendReply> mają również właściwość o nazwie `Content` . Ta właściwość jest typu <xref:System.ServiceModel.Activities.SendContent> i reprezentuje dane wysyłane przez <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> operacje lub. .NET Framework definiuje dwa typy powiązane <xref:System.ServiceModel.Activities.SendMessageContent> i <xref:System.ServiceModel.Activities.SendParametersContent> obie pochodne od <xref:System.ServiceModel.Activities.SendContent> . Ustaw <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> Właściwość działania lub `Content` na wystąpienie jednego z tych typów w celu wysłania danych z usługi przepływu pracy. Typ, który ma być używany, zależy od typu danych wysyłanych przez działanie. Jeśli działanie wysyła `Message` obiekt lub typ kontraktu komunikatu, użyj <xref:System.ServiceModel.Activities.SendMessageContent> . Jeśli działanie wysyła typ kontraktu danych, użyj <xref:System.ServiceModel.Activities.SendParametersContent> . <xref:System.ServiceModel.Activities.SendParametersContent>umożliwia wysyłanie wielu parametrów, a <xref:System.ServiceModel.Activities.SendMessageContent> jedynie umożliwia wysyłanie tylko jednego obiektu, wiadomości (lub typu kontraktu wiadomości).

Przy bezwzględnym programowaniu w działaniach związanych z przesyłaniem komunikatów należy używać generycznego <xref:System.Activities.InArgument%601> i <xref:System.Activities.OutArgument%601> do otaczania obiektów przypisanych do właściwości komunikatów lub <xref:System.ServiceModel.Activities.Send> parametrów <xref:System.ServiceModel.Activities.SendReply> działań,, <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.ReceiveReply> . Służy <xref:System.Activities.InArgument%601> do działania i działania oraz <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> <xref:System.Activities.OutArgument%601> dla <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.ReceiveReply> działań i. `In`argumenty są używane z działaniami wysyłania, ponieważ dane są przesyłane do działań. `Out`argumenty są używane z działaniami odbierania, ponieważ dane są przesyłane z działań, jak pokazano w poniższym przykładzie.

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

Podczas implementowania usługi przepływu pracy, która definiuje operację żądania/odpowiedzi zwracającą wartość void, należy utworzyć wystąpienie <xref:System.ServiceModel.Activities.SendReply> działania i ustawić <xref:System.ServiceModel.Activities.SendReply.Content%2A> Właściwość na puste wystąpienie jednego z typów zawartości ( <xref:System.ServiceModel.Activities.SendMessageContent> lub <xref:System.ServiceModel.Activities.SendParametersContent> ), jak pokazano w poniższym przykładzie.

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

Podczas wywoływania usługi przepływu pracy z poziomu aplikacji przepływu pracy program Visual Studio 2012 generuje niestandardowe działania związane z obsługą komunikatów, które hermetyzują zwykłe <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działania używane w żądaniu/odpowiedzi unikatowy MEP. Aby użyć tej funkcji, kliknij prawym przyciskiem myszy projekt klienta w programie Visual Studio i wybierz polecenie **Dodaj**  >  **odwołanie do usługi**. W polu Adres wpisz adres podstawowy usługi, a następnie kliknij pozycję Przejdź. Dostępne usługi są wyświetlane w polu **usługi:** . Rozwiń węzeł usługi, aby wyświetlić obsługiwane umowy. Wybierz kontrakt do wywołania, a lista dostępnych operacji zostanie wyświetlona w polu **operacje** . Następnie można określić obszar nazw dla wygenerowanego działania i kliknąć przycisk **OK**. Zobaczysz okno dialogowe z informacją, że operacja została ukończona pomyślnie, a wygenerowane działania niestandardowe znajdują się w przyborniku po ponownym skompilowaniu projektu. Istnieje jedno działanie dla każdej operacji zdefiniowanej w kontrakcie usługi. Po ponownym skompilowaniu projektu można przeciągnąć i upuścić niestandardowe działania w przepływie pracy i ustawić wymagane właściwości w oknie właściwości.

## <a name="messaging-activity-templates"></a>Szablony działań związanych z wiadomościami

Aby ułatwić skonfigurowanie żądania/odpowiedzi unikatowy MEP na kliencie i w usłudze, program Visual Studio 2012 udostępnia dwa szablony działań obsługi komunikatów. `System.ServiceModel.Activities.Design.ReceiveAndSendReply`jest używany w usłudze i `System.ServiceModel.Activities.Design.SendAndReceiveReply` jest używany na kliencie. W obu przypadkach szablony dodają odpowiednie działania dotyczące komunikatów do przepływu pracy. W usłudze program `System.ServiceModel.Activities.Design.ReceiveAndSendReply` dodaje <xref:System.ServiceModel.Activities.Receive> działanie, a po nim <xref:System.ServiceModel.Activities.SendReply> działanie. <xref:System.ServiceModel.Activities.SendReply.Request>Właściwość jest automatycznie ustawiana na <xref:System.ServiceModel.Activities.Receive> działanie. Na kliencie `System.ServiceModel.Activities.Design.SendAndReceiveReply` dodaje działanie, a <xref:System.ServiceModel.Activities.Send> po nim <xref:System.ServiceModel.Activities.ReceiveReply> . <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A>Właściwość jest automatycznie ustawiana na <xref:System.ServiceModel.Activities.Send> działanie. Aby użyć tych szablonów, przeciągnij i upuść odpowiedni szablon do przepływu pracy.

## <a name="messaging-activities-and-transactions"></a>Działania i transakcje komunikatów

Po wykonaniu wywołania do usługi przepływu pracy możesz chcieć przetworzyć transakcję do operacji usługi. W tym celu należy umieścić <xref:System.ServiceModel.Activities.Receive> działanie w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania. <xref:System.ServiceModel.Activities.TransactedReceiveScope>Działanie zawiera `Receive` działanie i treść. Transakcja przepływa do usługi pozostaje otaczająca przez cały czas wykonywania treści <xref:System.ServiceModel.Activities.TransactedReceiveScope> . Transakcja jest ukończona, gdy treść kończy się wykonywaniem. Aby uzyskać więcej informacji o przepływach pracy i transakcjach, zobacz [transakcje przepływu pracy](../../windows-workflow-foundation/workflow-transactions.md).

## <a name="see-also"></a>Zobacz też

- [Jak wysyłać i odbierać błędy w usługach przepływu pracy](https://go.microsoft.com/fwlink/?LinkId=189151)
- [Tworzenie długo działającej usługi przepływu pracy](creating-a-long-running-workflow-service.md)
