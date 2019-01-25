---
title: Uzyskiwanie dostępu do usług za pomocą klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
ms.openlocfilehash: 03b37dae72be0ffa589159b2aedc2ac16e35139e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583210"
---
# <a name="accessing-services-using-a-client"></a>Uzyskiwanie dostępu do usług za pomocą klienta
Aplikacje klienckie należy utworzyć, konfigurowanie i komunikować się z usługami za pomocą obiektów klienta lub kanału WCF. [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md) temat zawiera omówienie obiektów i kroki związane z tworzeniem podstawowych obiektów klienta i kanału i korzystanie z nich.  
  
 Ten temat zawiera szczegółowe informacje na temat niektórych problemów z klientem, aplikacje i obiekty klienta i kanału, które mogą być użyteczne, w zależności od danego scenariusza.  
  
## <a name="overview"></a>Omówienie  
 W tym temacie opisano zachowanie oraz zagadnienia odnoszące się do:  
  
-   Okresy istnienia kanału i sesji.  
  
-   Obsługa wyjątków.  
  
-   Problemy z blokowaniem opis.  
  
-   Inicjowanie kanałów interaktywnie.  
  
### <a name="channel-and-session-lifetimes"></a>Kanał i okresy istnienia sesji  
 Aplikacje Windows Communication Foundation (WCF) zawiera dwie kategorie kanałów, datagram i sessionful.  
  
 A *datagram* kanał jest kanału, w którym nieskorelowane są wszystkie komunikaty. Kanał datagram w przypadku niepowodzenia operacji wejściowych lub wyjściowych, następnej operacji jest zwykle nie mają wpływu i mogą być używane ponownie ten sam kanał. W związku z tym kanały datagram zwykle nie błędów.  
  
 *Sessionful* kanałów, są jednak kanałów za pomocą połączenia z punktem końcowym. Wiadomości w sesji na jednej stronie są zawsze powiązane z tej samej sesji z drugiej strony. Ponadto zarówno uczestników sesji musi wyrazić zgodę, w ramach danej sesji zostały uznane za pomyślne zostały spełnione wymagania swojej rozmowy. Jeśli nie zgadzasz się, może być błędów kanału sesji.  
  
 Otwórz klientów jawnie lub niejawnie, wywołując pierwszą operacją.  
  
> [!NOTE]
>  Próby wykrycia jawnie uszkodzoną kanały sesji nie jest zazwyczaj przydatne, ponieważ po wyświetleniu powiadomienia są zależne od implementacji sesji. Na przykład ponieważ <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> (z niezawodnej sesji wyłączone) wydobywa informacje dotyczące sesji połączenia protokołu TCP, jeśli słuchania <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=nameWithType> zdarzenia usługi lub klienta, prawdopodobnie szybko otrzymywać powiadomienia w przypadku awarii sieci. Ale niezawodnej sesji (ustanowione przez powiązań, w którym <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> jest włączona) są przeznaczone do usług sieciowych o małym rozmiarze błędy związane. Jeśli sesja można ustanowić w rozsądnym czasie, tego samego powiązania — skonfigurowane dotyczące sesji niezawodnych — nie może być błędów do momentu przerwania kontynuowane przez dłuższy czas.  
  
 Domyślnie, większość powiązania dostarczane przez system, (które udostępnianie kanałów w warstwie aplikacji) używają sesji, ale <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> nie. Aby uzyskać więcej informacji, zobacz [przy użyciu sesji](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="the-proper-use-of-sessions"></a>Prawidłowego użycia sesji  
 Sesje umożliwiają exchange cały komunikat zostało ukończone, a obie strony uznawany za pomyślny. Zalecane jest, że aplikacja wywołująca Otwórz kanał, jej używać i zamknij kanał wewnątrz bloku try jeden. Jeśli kanał sesji jest otwarty, a <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> metoda jest wywoływana jeden raz, to wywołanie zwraca pomyślnie, a następnie sesja zakończyła się pomyślnie. Pomyślne w tym przypadku oznacza, że wszystkie dostarczania gwarantuje określone powiązanie zostały spełnione, a druga strona nie wywołał <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=nameWithType> na kanale przed wywołaniem <xref:System.ServiceModel.ICommunicationObject.Close%2A>.  
  
 W poniższej sekcji przedstawiono przykład tej metody klienta.  
  
### <a name="handling-exceptions"></a>Obsługa wyjątków  
 Obsługa wyjątków w aplikacjach klienckich jest bardzo proste. Jeśli kanał jest otwarty, używane i zamknięte wewnątrz bloku try, następnie konwersacji zakończyła się pomyślnie, chyba że zgłaszany jest wyjątek. Zwykle jeśli wyjątek jest zgłaszany konwersacji został przerwany.  
  
> [!NOTE]
>  Korzystanie z `using` — instrukcja (`Using` w języku Visual Basic) nie jest zalecane. Jest to spowodowane koniec `using` instrukcji może spowodować, że wyjątki, które może maskować innych wyjątków, musisz wiedzieć o. Aby uzyskać więcej informacji, zobacz [Użyj Zamknij i Abort, aby zwolnić zasoby klienta WCF](../../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 Poniższy przykład kodu pokazuje wzorzec opartej na zalecanym kliencie za pomocą bloku try/catch i nie `using` instrukcji.  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
>  Wartości <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=nameWithType> właściwość sytuacja wyścigu i nie jest zalecane w celu ustalenia, czy do ponownego użycia lub zamknięcia kanału.  
  
 Kanały datagram nigdy nie błędów, nawet jeśli wyjątek występuje po zamknięciu. Ponadto klientów-duplex, którzy nie próbę uwierzytelnienia przy użyciu bezpiecznej konwersacji zazwyczaj generują <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>. Jednak jeśli dwukierunkowego klienta przy użyciu bezpiecznej konwersacji nie powiedzie się uwierzytelnianie, klient odbierze <xref:System.TimeoutException?displayProperty=nameWithType> zamiast tego.  
  
 Aby uzyskać bardziej szczegółowe informacje na temat pracy przy użyciu informacji o błędzie na poziomie aplikacji, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). [Oczekiwane wyjątki](../../../../docs/framework/wcf/samples/expected-exceptions.md) opisuje oczekiwane wyjątki i pokazuje, jak je obsłużyć. Aby uzyskać więcej informacji na temat obsługi błędów podczas tworzenia kanałów, zobacz [obsługi wyjątków i błędów](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
### <a name="client-blocking-and-performance"></a>Blokowanie klienta i wydajności  
 Kiedy aplikacja synchronicznie wywołuje operacja żądanie odpowiedź, bloków klienta, dopóki nie zostanie odebrana wartość zwracaną lub wyjątek (takie jak <xref:System.TimeoutException?displayProperty=nameWithType>) jest zgłaszany. To zachowanie jest podobne do zachowania lokalnego. Gdy aplikacja wywołuje synchronicznie operacji na obiekt klienta WCF lub kanał, klient nie zwraca do momentu warstwy kanału można zapisywać dane z siecią lub dopóki nie zostanie zgłoszony wyjątek. I podczas wymiany komunikatów jednokierunkowe (określone przez oznaczenie operację, używając <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> równa `true`) ułatwia niektórzy klienci zwiększyć szybkość reakcji, jednokierunkowe operacje można również zablokować, zależnie od powiązania i jakie komunikaty zostały już wysyłane. Operacje jednokierunkowe są tylko o wymianie wiadomości, nie ma więcej i nie mniejszy. Aby uzyskać więcej informacji, zobacz [usług One-Way](../../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
 Dużej ilości danych na fragmenty może spowalniać klienta przetwarzania niezależnie od tego, jakie wymiany komunikatów. Aby zrozumieć sposób obsługi tych problemów, zobacz [duże ilości danych i przesyłanie strumieniowe](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Jeśli aplikacja musi kontynuować pracę podczas kończenia operacji, należy utworzyć pary metod asynchronicznych na interfejsie kontraktu usługi, który implementuje klienta WCF. W tym celu najłatwiej używać `/async` Włącz [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Aby uzyskać przykład, zobacz [jak: Asynchroniczne wywoływanie operacji usługi](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Aby uzyskać więcej informacji na temat zwiększa wydajność klienta, zobacz [aplikacje klienckie warstwy środkowej](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).  
  
### <a name="enabling-the-user-to-select-credentials-dynamically"></a>Włączanie użytkownikowi na wybranie dynamicznie poświadczeń  
 <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> Interfejs umożliwia aplikacji wyświetlanie interfejsu użytkownika, który umożliwia użytkownikowi wybranie poświadczeń za pomocą których kanał jest tworzony, przed rozpoczęciem czasomierzy limitu czasu.  
  
 Deweloperzy aplikacji mogą udostępnić użytkowania wstawiono <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> na dwa sposoby. Aplikacja kliencka może wywołać albo <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (lub wersja asynchroniczna) przed otwierania kanału ( *jawne* podejście) lub wywołać pierwszą operacją ( *niejawne*podejście).  
  
 Jeśli w sposób niejawny, aplikacja musi wywołać pierwszą operacją na <xref:System.ServiceModel.ClientBase%601> lub <xref:System.ServiceModel.IClientChannel> rozszerzenia. Jeśli wywoływanych przez nią coś innego niż pierwszą operacją, zwracany jest wyjątek.  
  
 Jeśli przy użyciu podejścia jawne, aplikacja musi wykonać następujące kroki w kolejności:  
  
1.  Wywołaj opcję <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (lub asynchronicznej wersji).  
  
2.  Po zwróceniu mieć inicjatory, wywołaj albo <xref:System.ServiceModel.ICommunicationObject.Open%2A> metody <xref:System.ServiceModel.IClientChannel> obiektu lub na <xref:System.ServiceModel.IClientChannel> obiekt zwracany z <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=nameWithType> właściwości.  
  
3.  Wywoływanie operacji.  
  
 Zaleca się, że aplikacje wysokiej jakości kontrolowania procesu interfejsu użytkownika przez przyjęcie podejścia jawnego.  
  
 Aplikacje, które używają podejście niejawne wywołania inicjatory interfejsu użytkownika, ale jeśli użytkownik aplikacji nie odpowiedział w określonym przedziale czasu wysyłania powiązania, wyjątek jest generowany, gdy zwraca interfejs użytkownika.  
  
## <a name="see-also"></a>Zobacz także
- [Usługi dwukierunkowe](../../../../docs/framework/wcf/feature-details/duplex-services.md)
- [Instrukcje: Uzyskiwanie dostępu do usług za pomocą jednokierunkowego i kontraktów "żądanie odpowiedź"](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Instrukcje: Dostęp do usług za pomocą kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Instrukcje: Dostęp do programu WSE 3.0 usługi](../../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Instrukcje: Używanie elementu ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
- [Instrukcje: Asynchroniczne wywoływanie operacji usługi](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [Aplikacje klienckie warstwy środkowej](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)
