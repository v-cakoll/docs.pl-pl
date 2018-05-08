---
title: Działania dotyczące komunikatów
ms.date: 03/30/2017
ms.assetid: 8498f215-1823-4aba-a6e1-391407f8c273
ms.openlocfilehash: 1ae03b1671aa5c938bb3897edb919643f795f8a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="messaging-activities"></a>Działania dotyczące komunikatów
Zezwalaj na działania obsługi komunikatów przepływy pracy w celu wysyłania i odbierania wiadomości WCF. Przez dodanie obsługi komunikatów działań w przepływie pracy można modelu żadnych wiadomości arbitralnie złożonych wzorców programu exchange (MEP).  
  
## <a name="message-exchange-patterns"></a>Wzorce wymiany komunikatów  
 Istnieją trzy wzorce exchange podstawowe wiadomości:  
  
-   **Datagram** — przy użyciu datagram MEP klient wysyła komunikat do usługi, ale usługa nie odpowiada. Jest to czasem nazywane "wyzwalać i zapomnij". Uruchomienie a zapomnieć exchange to taki, który wymaga potwierdzenia poza pasmem pomyślnie dostawy. Komunikat mogą zostać utracone podczas przesyłania i nigdy nie dotarcia do usługi. Jeśli klient prześle wiadomość, nie gwarantuje to, że usługa odebrała komunikat. Datagram jest podstawowym bloku konstrukcyjnego do obsługi wiadomości, można tworzyć własne MEPs na nim.  
  
-   **Żądanie-odpowiedź** — przy użyciu MEP żądań i odpowiedzi klienta wysyła komunikat do usługi, usługa nie wymagane przetwarzanie, a następnie wysyła odpowiedź z powrotem do klienta. Wzorzec składa się z pary żądanie / odpowiedź. Przykłady wywołań żądań i odpowiedzi są zdalnych wywołań procedur (RPC) i GET przeglądarką żądania. Ten wzorzec jest nazywany również półdupleks.  
  
-   **Dupleks** — przy użyciu dupleksu MEP klienta i usługi będą mogły wysyłać wiadomości ze sobą w dowolnej kolejności. Dupleks MEP przypomina rozmowy telefonicznej każdego wyrazu jest używany w przypadku komunikatu.  
  
 Działania obsługi komunikatów pozwalają na wdrożenie żadnego z tych podstawowych MEPs oraz wszelkie MEP arbitralnie złożonych.  
  
## <a name="messaging-activities"></a>Działania dotyczące komunikatów  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] Definiuje następujące działania obsługi komunikatów:  
  
-   <xref:System.ServiceModel.Activities.Send>-Użyj <xref:System.ServiceModel.Activities.Send> działania, aby wysłać wiadomość.  
  
-   <xref:System.ServiceModel.Activities.SendReply> -Użyj <xref:System.ServiceModel.Activities.SendReply> działanie, aby wysłać odpowiedź do odebranego komunikatu. To działanie jest używany przez usługi przepływu pracy podczas wykonywania żądania/odpowiedzi MEP.  
  
-   <xref:System.ServiceModel.Activities.Receive>-Użyj <xref:System.ServiceModel.Activities.Receive> działania można odebrać wiadomości.  
  
-   <xref:System.ServiceModel.Activities.ReceiveReply> -Użyj <xref:System.ServiceModel.Activities.ReceiveReply> działania komunikat odpowiedzi. To działanie jest używane przez klientów usługi przepływu pracy podczas wykonywania żądania/odpowiedzi MEP.  
  
## <a name="messaging-activities-and-message-exchange-patterns"></a>Działania obsługi wiadomości i wzorce wymiany komunikatów  
 Datagram MEP obejmuje wysyłania wiadomości oraz odbieranie wiadomości usługi klienta. Jeśli klient jest użycie przepływu pracy <xref:System.ServiceModel.Activities.Send> działania do wysłania tej wiadomości. Aby odbierać wiadomości w przepływie pracy, użyj <xref:System.ServiceModel.Activities.Receive> działania. <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> działania każdego mają właściwość o nazwie `Content`. Ta właściwość zawiera dane są wysyłane lub odbierane. Podczas implementowania MEP żądań i odpowiedzi zarówno klient, jak i usługi używają par działań. Klient używa <xref:System.ServiceModel.Activities.Send> działania do wysłania tej wiadomości i <xref:System.ServiceModel.Activities.ReceiveReply> działania do odbierania odpowiedzi z usługi. Te dwa działania są powiązane ze sobą przez <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> właściwości. Ta właściwość jest ustawiona na <xref:System.ServiceModel.Activities.Send> działanie, które oryginalnej wiadomości. Usługa również używa parę działań skojarzone: <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.SendReply>. Te dwa działania są skojarzone przez <xref:System.ServiceModel.Activities.SendReply.Request%2A> właściwości. Ta właściwość jest ustawiona na <xref:System.ServiceModel.Activities.Receive> działanie, które odebrano oryginalnej wiadomości. <xref:System.ServiceModel.Activities.ReceiveReply> i <xref:System.ServiceModel.Activities.SendReply> działania, takie jak <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> umożliwiają wysyłanie <xref:System.ServiceModel.Channels.Message> wystąpienia lub typ kontraktu komunikatu.  
  
 Z powodu długotrwałej rodzaj przepływów pracy jest ważna w przypadku dupleksu wzorzec komunikacji również obsługiwać długotrwałe konwersacji. Aby obsługiwać konwersacje długotrwałe, klientów, którzy zainicjować konwersacji musi świadczyć usługi możliwość wywołać ją z powrotem w późniejszym czasie, gdy dane będą dostępne. Na przykład do zatwierdzenia przez Menedżera zostało przesłane żądanie zamówienia zakupu, ale nie może on przetworzony dnia, tygodnia lub nawet roku; przepływ pracy, który zarządza zatwierdzenia zamówienia zakupu muszą znać wznowić po zatwierdzeniu. Ten wzorzec komunikację dupleksową jest obsługiwana w przepływach pracy przy użyciu korelacji. Aby zaimplementować wzorzec dupleksowy, użyj <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> działań. Na <xref:System.ServiceModel.Activities.Receive> działania, zainicjować a korelacji przy użyciu specjalnego wartości klucza <!--zz <xref:System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName%2A>--> `System.ServiceModel.Activities.CorrelationHandle.CallbackHandleName`. Na <xref:System.ServiceModel.Activities.Send> dojścia korelacji jako zestaw działań <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> wartości właściwości. Aby uzyskać więcej informacji, zobacz [trwałe dupleksu](../../../../docs/framework/wcf/feature-details/durable-duplex-correlation.md).  
  
> [!NOTE]
>  Wykonania przepływu pracy dupleks przy użyciu korelacji wywołania zwrotnego ("trwałe dupleks") jest przeznaczony dla konwersacji długotrwałe. To nie jest taka sama jak WCF z wywołania zwrotnego kontraktów dupleksowych gdzie konwersacji jest krótki pracy (okres istnienia kanału).  
  
## <a name="message-formatting-and-messaging-activities"></a>Elementy i działania dotyczące komunikatów  
 <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.ReceiveReply> działania mają właściwości o nazwie `Content`. Ta właściwość jest typu <xref:System.ServiceModel.Activities.ReceiveContent> i reprezentuje dane <xref:System.ServiceModel.Activities.Receive> lub <xref:System.ServiceModel.Activities.ReceiveReply> odbiera działania. .NET Framework definiuje dwie klasy pokrewne o nazwie <xref:System.ServiceModel.Activities.ReceiveMessageContent> i <xref:System.ServiceModel.Activities.ReceiveParametersContent> które są pochodnymi <xref:System.ServiceModel.Activities.ReceiveContent>. Ustaw <xref:System.ServiceModel.Activities.Receive> lub <xref:System.ServiceModel.Activities.ReceiveReply> działania `Content` dla właściwości wystąpienia jednego z następujących typów na odbieranie danych do usługi przepływu pracy. Typ do użycia zależy od typu danych, którą otrzymuje działania. Jeśli działanie odbiera `Message` obiektu lub komunikat typu kontraktu, użyj <xref:System.ServiceModel.Activities.ReceiveMessageContent>. Jeśli działanie otrzymuje zestaw kontraktu danych lub typów XML, które można serializować, użyj <xref:System.ServiceModel.Activities.ReceiveParametersContent>. <xref:System.ServiceModel.Activities.ReceiveParametersContent> Umożliwia wysłanie wiele parametrów, podczas gdy <xref:System.ServiceModel.Activities.ReceiveMessageContent> zezwala tylko jeden obiekt wysyłania, komunikatu (lub typ kontraktu komunikatu).  
  
> [!NOTE]
>  <xref:System.ServiceModel.Activities.ReceiveMessageContent> można również kontraktu danych jednego lub typu XML, który można serializować. Różnica między używaniem <xref:System.ServiceModel.Activities.ReceiveParametersContent> jeden parametr i przekazanego bezpośrednio do obiektu <xref:System.ServiceModel.Activities.ReceiveMessageContent> to format danych przesyłanych w sieci. Zawartość parametru jest ujęte w elemencie XML, który odpowiada nazwie operacji i Zserializowany obiekt jest opakowane w elemencie XML przy użyciu nazwy parametru (na przykład `<Echo><msg>Hello, World</msg></Echo>`). Zawartość komunikatu nie jest zawijany według nazwy operacji. Zamiast tego Zserializowany obiekt znajduje się w obrębie elementu XML przy użyciu nazwy kwalifikowanej XML typu (na przykład `<string>Hello, World</string>`).  
  
 <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.SendReply> działania również mieć właściwość o nazwie `Content`. Ta właściwość jest typu <xref:System.ServiceModel.Activities.SendContent> i reprezentuje dane <xref:System.ServiceModel.Activities.Send> lub <xref:System.ServiceModel.Activities.SendReply> wysyła działania. .NET Framework definiuje dwie powiązanych typów o nazwie <xref:System.ServiceModel.Activities.SendMessageContent> i <xref:System.ServiceModel.Activities.SendParametersContent> które są pochodnymi <xref:System.ServiceModel.Activities.SendContent>. Ustaw <xref:System.ServiceModel.Activities.Send> lub <xref:System.ServiceModel.Activities.SendReply> działania `Content` dla właściwości wystąpienia jednego z tych typów do wysyłania danych z usługi przepływu pracy. Typ do użycia zależy od typu danych, który wysyła działania. Jeśli działanie wysyła `Message` obiektu lub komunikat typu kontraktu, użyj <xref:System.ServiceModel.Activities.SendMessageContent>. Jeśli działanie wysyła use typu kontraktu danych <xref:System.ServiceModel.Activities.SendParametersContent>. <xref:System.ServiceModel.Activities.SendParametersContent> Umożliwia wysłanie wiele parametrów, podczas gdy <xref:System.ServiceModel.Activities.SendMessageContent> umożliwia tylko wysyłanie jeden obiekt (komunikatu lub typ kontraktu komunikatu).  
  
 Programowanie imperatively za pomocą działania obsługi komunikatów, za pomocą ogólnego <xref:System.Activities.InArgument%601> i <xref:System.Activities.OutArgument%601> opakowywać obiektów przypisać do właściwości komunikatu lub parametry <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Receive>i <xref:System.ServiceModel.Activities.ReceiveReply>działań. Użyj <xref:System.Activities.InArgument%601> dla <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.SendReply> działań i <xref:System.Activities.OutArgument%601> dla <xref:System.ServiceModel.Activities.Receive> i <xref:System.ServiceModel.Activities.ReceiveReply> działań. `In` argumenty są używane przez działań wysyłania, ponieważ dane jest przekazywany do działania. `Out` argumenty są używane przez działania receive, ponieważ data jest przekazywany z działania, jak pokazano w poniższym przykładzie.  
  
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
  
 Podczas wdrażania usługi przepływu pracy, który definiuje Operacja żądania/odpowiedzi, który zwraca typ void, musi utworzyć wystąpienia <xref:System.ServiceModel.Activities.SendReply> działania i zestaw <xref:System.ServiceModel.Activities.SendReply.Content%2A> właściwości puste wystąpienie jednego z typów zawartości (<xref:System.ServiceModel.Activities.SendMessageContent> lub <xref:System.ServiceModel.Activities.SendParametersContent>) jak pokazano w poniższym przykładzie.  
  
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
 Podczas wywoływania usługi przepływu pracy z poziomu aplikacji przepływu pracy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] generuje niestandardowych działań obsługi komunikatów, które hermetyzują zwykle <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.ReceiveReply> działań używanych w MEP żądania/odpowiedzi. Aby użyć tej funkcji kliknij prawym przyciskiem myszy projekt klienta w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] i wybierz **Dodaj odwołanie do usługi**. Wpisz adres podstawowy usługi w polu adres i kliknij Przejdź. Dostępne usługi są wyświetlane w **usług:** pole. Rozwiń węzeł usługi, aby wyświetlić Umowy obsługiwane. Wybierz umowę, który chcesz wybrać i zostanie wyświetlona lista dostępnych operacji, w **operacji** pole. Można określić przestrzeń nazw dla wygenerowanego działania i kliknij przycisk **OK**. Zostanie wyświetlony komunikat, operacja zakończona pomyślnie i po projekt w przyborniku są generowane działania niestandardowe okno dialogowe. Brak jednego działania dla każdej operacji zdefiniowane na kontrakt usługi. Po ponownie skompilować projekt można przeciągnąć i upuścić działań niestandardowych do przepływu pracy i wymaganych właściwości w oknie właściwości.  
  
<!--## Messaging Activity Templates  
 To make setting up a request/response MEP on the client and service easier, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] provides two messaging activity templates. <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> is used on the service and <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> is used on the client. In both cases the templates add the appropriate messaging activities to your workflow. On the service, the <xref:System.ServiceModel.Activities.Design.ReceiveAndSendReply> adds a <xref:System.ServiceModel.Activities.Receive> activity followed by a <xref:System.ServiceModel.Activities.SendReply> activity. The <xref:System.ServiceModel.Activities.SendReply.Request> property is automatically set to the <xref:System.ServiceModel.Activities.Receive> activity. On the client, the <xref:System.ServiceModel.Activities.Design.SendAndReceiveReply> adds a <xref:System.ServiceModel.Activities.Send> activity followed by a <xref:System.ServiceModel.Activities.ReceiveReply>. The <xref:System.ServiceModel.Activities.ReceiveReply.Request%2A> property is automatically set to the <xref:System.ServiceModel.Activities.Send> activity. To use these templates, just drag and drop the appropriate template onto your workflow.  
-->
## <a name="messaging-activities-and-transactions"></a>Działania obsługi wiadomości i transakcji  
 Wywołanie usługi przepływu pracy można przepływu transakcji do operacji usługi. Aby zrobić to miejsce <xref:System.ServiceModel.Activities.Receive> działania w ramach <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania. <xref:System.ServiceModel.Activities.TransactedReceiveScope> Zawiera działanie `Receive` działania i treść. Przepływ transakcji do otoczenia podczas wykonywania treści pozostaje usługi <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Transakcja jest zakończona po zakończeniu treści wykonywania. Aby uzyskać więcej informacji na temat przepływów pracy i transakcje zobacz [przepływu transakcji](../../../../docs/framework/windows-workflow-foundation/workflow-transactions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Jak wysyłanie i odbieranie błędów w usług przepływu pracy](http://go.microsoft.com/fwlink/?LinkId=189151)  
 [Tworzenie długo działającej usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)
