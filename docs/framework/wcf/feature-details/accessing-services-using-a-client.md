---
title: Uzyskiwanie dostępu do usług za pomocą klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
ms.openlocfilehash: 1369403b493683f58640047fe042708afc5d5b46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495999"
---
# <a name="accessing-services-using-a-client"></a>Uzyskiwanie dostępu do usług za pomocą klienta
Aplikacje klienckie należy utworzyć, konfigurowanie i łączyć się z usługami za pomocą obiektów klienta lub kanału WCF. [Przegląd klienta programu WCF](../../../../docs/framework/wcf/wcf-client-overview.md) temat zawiera omówienie obiektów i kroki związane z tworzeniem podstawowych obiektów klienta i kanału i za ich pomocą.  
  
 Ten temat zawiera szczegółowe informacje na temat niektórych problemów z klientem, aplikacji i klienta i kanał obiektów, które mogą być użyteczne, w zależności od danego scenariusza.  
  
## <a name="overview"></a>Omówienie  
 W tym temacie opisano zachowanie i zagadnień dotyczących:  
  
-   Okresy istnienia kanału i sesji.  
  
-   Obsługa wyjątków.  
  
-   Opis problemy z blokowaniem.  
  
-   Inicjowanie kanałów interaktywnie.  
  
### <a name="channel-and-session-lifetimes"></a>Kanał i okresy istnienia sesji  
 Aplikacje systemu Windows Communication Foundation (WCF) obejmuje dwie kategorie kanały, datagram i sessionful.  
  
 A *datagram* kanał jest kanału, w którym są nieskorelowane wszystkie komunikaty. W przypadku niepowodzenia operacji wejściowych lub wyjściowych z kanału datagramowego następnej operacji jest zwykle nie dotyczy, a można ponownie użyć tego samego kanału. W związku z tym kanały datagram zwykle nie fault.  
  
 *Sessionful* kanały, są jednak kanałów z połączeniem z innych punktów końcowych. Wiadomości w sesji na jednej stronie są zawsze powiązane z tej samej sesji z drugiej strony. Ponadto zarówno uczestników sesji musi zaakceptować, czy dla tej sesji wziąć pod uwagę pomyślnie zostały spełnione wymagania ich konwersacji. Jeśli użytkownik nie wyrazi zgodę, zamykania kanału może fault.  
  
 Otwórz klientów jawnie lub niejawnie, wywołując pierwszej operacji.  
  
> [!NOTE]
>  W trakcie jawnie wykryć błędnej zamykania kanałów nie jest zazwyczaj przydatne, ponieważ po wyświetleniu powiadomienia zależy od implementacji sesji. Na przykład ponieważ <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> (z niezawodnej sesji wyłączona) udostępnia sesji połączenia TCP, jeśli nasłuchiwanie na <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=nameWithType> zdarzenia usługi lub klienta, prawdopodobnie szybko zgłaszane w przypadku awarii sieci. Ale niezawodnej sesji (ustala powiązań, w którym <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> jest włączona) są przeznaczone do ochronić usług z błędami małej sieci. Jeśli w rozsądnym czasie, to samo powiązanie można ustanowić sesji — skonfigurowana dla sesji niezawodnej — nie może być fault dopóki przerwanie kontynuowany przez dłuższy okres.  
  
 Większość powiązania dostarczane przez system (które ujawnia kanały do warstwy aplikacji) używają sesji domyślnie, ale <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> nie. Aby uzyskać więcej informacji, zobacz [sesji przy użyciu](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="the-proper-use-of-sessions"></a>Użycie odpowiednich sesji  
 Sesje umożliwiają exchange cały komunikat została zakończona, a obie strony uznawany za pomyślny. Zaleca się, że aplikacja wywołująca otworzyć kanału, go używać i zamknąć kanał wewnątrz bloku try jeden. Jeśli kanał sesji jest otwarty i <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> metoda jest wywoływana raz i tego wywołania zwraca pomyślnie, a następnie sesji zakończyła się pomyślnie. Pomyślne w takim przypadku oznacza, że wszystkie dostarczania gwarantuje określone powiązanie zostały spełnione, a druga strona nie wywołał <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=nameWithType> w kanale przed wywołaniem <xref:System.ServiceModel.ICommunicationObject.Close%2A>.  
  
 Poniższa sekcja zawiera przykład tej metody klienta.  
  
### <a name="handling-exceptions"></a>Obsługa wyjątków  
 Obsługa wyjątków w aplikacjach klienckich jest prosta. Jeśli kanał jest otwarty, używane i zamknięte wewnątrz bloku try, następnie konwersacji zakończyła się pomyślnie, chyba że jest zgłaszany wyjątek. Zwykle jeśli wyjątek konwersacji została przerwana.  
  
> [!NOTE]
>  Użycie `using` instrukcji (`Using` w języku Visual Basic) nie jest zalecane. Jest to spowodowane koniec `using` instrukcji może spowodować wyjątki, które można zamaskować pozostałe wyjątki trzeba wiedzieć o. Aby uzyskać więcej informacji, zobacz [unikanie problemów z instrukcją Using](../../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 Poniższy przykład kodu pokazuje wzorzec zalecane klienta za pomocą bloku try/catch, a nie `using` instrukcji.  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
>  Wartości <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=nameWithType> jest sytuacja wyścigu i nie jest zalecane w celu ustalenia, czy można użyć ponownie lub zamknąć kanał.  
  
 Kanały datagram fault nigdy nie nawet wtedy, gdy wyjątki występują po zamknięciu. Ponadto throw-duplex klientów, którzy nie mogą się uwierzytelnić, zwykle za pomocą bezpiecznej konwersacji <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>. Jednak jeśli dupleksu klienta przy użyciu bezpiecznej konwersacji uwierzytelnianie zakończy się niepowodzeniem, klient odbierze <xref:System.TimeoutException?displayProperty=nameWithType> zamiast tego.  
  
 Aby uzyskać więcej informacji o pracy z informacje o błędzie na poziomie aplikacji, zobacz [określanie i obsługa błędów w kontraktach i usługach](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). [Oczekiwano wyjątki](../../../../docs/framework/wcf/samples/expected-exceptions.md) opisuje oczekiwane wyjątki oraz sposób ich obsługę. Aby uzyskać więcej informacji o sposobie obsługi błędów podczas tworzenia kanałów, zobacz [obsługi wyjątków i błędów](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
### <a name="client-blocking-and-performance"></a>Blokowanie klienta i wydajności  
 Gdy aplikacji synchronicznie odwołuje się operacja żądanie odpowiedź, bloki klienta do momentu otrzymania wartości zwracanej lub wyjątek (takie jak <xref:System.TimeoutException?displayProperty=nameWithType>) zostanie zgłoszony. To zachowanie jest podobne do zachowania lokalnego. Aplikację synchronicznie wywołuje operację na obiekcie klienta WCF lub kanału, klient nie powrócić do momentu warstwie kanału można zapisać danych w sieci lub dopóki nie jest zgłaszany wyjątek. I podczas wymiany komunikatów jednokierunkowe (określonego przez oznaczenie operacji o <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> ustawioną `true`) ułatwia niektórzy klienci również zablokować poprawę reakcji, jednokierunkowe operacje, w zależności od powiązania i jakie komunikaty są już wysyłane. Operacje jednokierunkowe są tylko o wymianie wiadomości, ma więcej i nie mniejsza. Aby uzyskać więcej informacji, zobacz [usług One-Way](../../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
 Fragmenty dużej ilości danych może opóźnić klienta przetwarzania niezależnie od tego, jakie z środków wymiany komunikatów. Aby poznać sposób obsługi tych problemów, zobacz [duże ilości danych i przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Jeśli aplikacja może kontynuować pracę podczas operacji, należy utworzyć pary metod asynchronicznych na interfejsu kontraktu usługi, który implementuje klienta WCF. Najprostszym sposobem, w tym celu jest użycie `/async` Włącz [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Na przykład zobacz [porady: wywołania operacji usługi asynchronicznie](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Aby uzyskać więcej informacji na temat zwiększa wydajność klienta, zobacz [aplikacje klienckie warstwy środkowej](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).  
  
### <a name="enabling-the-user-to-select-credentials-dynamically"></a>Włączanie użytkownikowi na wybranie dynamicznie poświadczeń  
 <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> Interfejs umożliwia aplikacjom wyświetlania interfejsu użytkownika, który umożliwia użytkownikowi wybranie poświadczeń, z którymi jest tworzony kanał przed rozpoczęciem czasomierze limitu czasu.  
  
 Deweloperzy aplikacji ułatwia użycie wstawionego <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> na dwa sposoby. Aplikacja kliencka można wywołać albo <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (lub asynchroniczną wersję) przed otwarciem kanał ( *jawne* podejście) lub zadzwoń pierwszej operacji ( *niejawne*podejście).  
  
 Jeśli w sposób niejawny, aplikacja musi wywołać pierwszą operacją na <xref:System.ServiceModel.ClientBase%601> lub <xref:System.ServiceModel.IClientChannel> rozszerzenia. Jeśli wywołuje inny niż pierwsza operacja, jest zwracany wyjątek.  
  
 Jeśli używa jawnego podejście, aplikacji, należy wykonać następujące kroki w kolejności:  
  
1.  Wywołaj albo <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (lub asynchroniczną wersję).  
  
2.  Zwracanie inicjatory ma wywoływać albo <xref:System.ServiceModel.ICommunicationObject.Open%2A> metoda <xref:System.ServiceModel.IClientChannel> obiektu lub na <xref:System.ServiceModel.IClientChannel> obiektu zwróconego z <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=nameWithType> właściwości.  
  
3.  Wywoływanie operacji.  
  
 Zaleca się, że wysokiej jakości aplikacji kontroli procesu interfejsu użytkownika przez przyjęcie podejścia jawnego.  
  
 Aplikacje używające niejawnego metody invoke inicjatory interfejsu użytkownika, ale jeśli użytkownik aplikacji nie odpowiada przed upływem limitu czasu wysyłania w powiązania, jest zwracany wyjątek, po powrocie z interfejsu użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi dwukierunkowe](../../../../docs/framework/wcf/feature-details/duplex-services.md)  
 [Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktów jednokierunkowych i kontraktów „żądanie-odpowiedź”](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)  
 [Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [Instrukcje: dostęp do usługi WSE 3.0](../../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)  
 [Instrukcje: używanie elementu ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)  
 [Instrukcje: asynchroniczne wywoływanie operacji usługi](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)  
 [Aplikacje klienckie warstwy środkowej](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)
