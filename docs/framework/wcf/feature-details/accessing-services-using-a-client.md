---
title: Uzyskiwanie dostępu do usług za pomocą klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
ms.openlocfilehash: 001f30d7a0dde952a7d18bfbc50f2c3622287406
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576554"
---
# <a name="accessing-services-using-a-client"></a>Uzyskiwanie dostępu do usług za pomocą klienta
Aplikacje klienckie muszą tworzyć, konfigurować i używać obiektów klienta lub kanału WCF w celu komunikowania się z usługami. Temat [Omówienie klienta WCF](../wcf-client-overview.md) zawiera omówienie obiektów i kroków związanych z tworzeniem podstawowych obiektów klienta i kanałów oraz ich używania.  
  
 Ten temat zawiera szczegółowe informacje dotyczące niektórych problemów dotyczących aplikacji klienckich oraz obiektów klienta i kanałów, które mogą być przydatne w zależności od danego scenariusza.  
  
## <a name="overview"></a>Omówienie  
 W tym temacie opisano zachowanie i problemy związane z:  
  
- Okresy istnienia kanału i sesji.  
  
- Obsługa wyjątków.  
  
- Omówienie problemów z blokowaniem.  
  
- Interaktywna Inicjalizacja kanałów.  
  
### <a name="channel-and-session-lifetimes"></a>Okresy istnienia kanału i sesji  
 Aplikacje Windows Communication Foundation (WCF) zawierają dwie kategorie kanałów, datagram i sesję.  
  
 Kanał *datagramu* to kanał, w którym wszystkie komunikaty są nieskorelowane. Jeśli operacja wejścia lub wyjścia kończy się niepowodzeniem w kanale datagramu, następna operacja jest zwykle niezależna i można ponownie użyć tego samego kanału. Z tego powodu kanały datagramów zazwyczaj nie są błędne.  
  
 Kanały *sesji* są jednak kanały z połączeniem z innym punktem końcowym. Komunikaty w sesji po jednej stronie są zawsze skorelowane z tą samą sesją po drugiej stronie. Ponadto obydwie Uczestnicy sesji muszą wyrazić zgodę na spełnienie wymagań związanych z konwersacją dla danej sesji. Jeśli użytkownicy nie będą mogli wyrazić zgody, może wystąpić błąd w kanale sesji.  
  
 Otwórz klientów jawnie lub niejawnie, wywołując pierwszą operację.  
  
> [!NOTE]
> Próba jawnego wykrywania nieprawidłowych kanałów sesji nie jest zazwyczaj użyteczna, ponieważ powiadomienie jest zależne od implementacji sesji. Na przykład, ponieważ <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> (za pomocą niezawodnej sesji wyłączone) wyświetla sesję połączenia TCP, w przypadku nasłuchiwania <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=nameWithType> zdarzenia w usłudze lub klienta, który prawdopodobnie zostanie natychmiast powiadomiony w przypadku awarii sieci. Jednak niezawodne sesje (ustanowione przez powiązania, w których <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> włączono) są przeznaczone do izolowania usług z małych awarii sieci. Jeśli sesja może zostać ponownie ustanowiona w rozsądnym czasie, to to samo powiązanie — skonfigurowane dla sesji niezawodnych — może nie powodować błędów do momentu kontynuowania przez dłuższy okres czasu.  
  
 Większość powiązań dostarczonych przez system (które uwidaczniają kanały do warstwy aplikacji) domyślnie używa sesji, ale nie jest <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> . Aby uzyskać więcej informacji, zobacz [Korzystanie z sesji](../using-sessions.md).  
  
### <a name="the-proper-use-of-sessions"></a>Odpowiednie użycie sesji  
 Sesje zapewniają sposób, aby wiedzieć, czy cała wymiana komunikatów została ukończona, oraz czy obie strony uznały się pomyślnie. Zaleca się, aby aplikacja wywołująca otworzyła kanał, używać jej i zamknąć kanał wewnątrz jednego bloku try. Jeśli kanał sesji jest otwarty, a <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> Metoda jest wywoływana jednokrotnie, a wywołanie zwrotne powiodło się, sesja zakończyła się pomyślnie. Pomyślne w tym przypadku oznacza, że wszystkie dostawy gwarantują spełnienie określonego powiązania, a druga strona nie wywołuje <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=nameWithType> kanału przed wywołaniem <xref:System.ServiceModel.ICommunicationObject.Close%2A> .  
  
 W poniższej sekcji przedstawiono przykład tego podejścia klienta.  
  
### <a name="handling-exceptions"></a>Obsługa wyjątków  
 Obsługa wyjątków w aplikacjach klienckich jest prosta. Jeśli kanał jest otwarty, używany i zamknięty wewnątrz bloku try, Konwersacja zakończyła się powodzeniem, chyba że zostanie zgłoszony wyjątek. Zazwyczaj Jeśli wystąpi wyjątek, konwersacja jest przerywana.  
  
> [!NOTE]
> `using` `Using` Nie zaleca się używania instrukcji (w Visual Basic). Wynika to z faktu, `using` że koniec instrukcji może spowodować wyjątki, które mogą być maskowanymi innymi wyjątkami, które mogą być potrzebne. Aby uzyskać więcej informacji, zobacz [Korzystanie z funkcji Close i Abort w celu zwolnienia zasobów klienta WCF](../samples/use-close-abort-release-wcf-client-resources.md).  
  
 Poniższy przykład kodu przedstawia zalecany wzorzec klienta przy użyciu bloku try/catch, a nie `using` instrukcji.  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
> Sprawdzanie wartości <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=nameWithType> właściwości jest warunkiem wyścigu i nie jest zalecane, aby określić, czy należy ponownie użyć lub zamknąć kanał.  
  
 Kanały datagramów nigdy nie wystąpią nawet wtedy, gdy wyjątki występują po zamknięciu. Ponadto klienci niebędący w trybie dupleksu, którzy nie mogą uwierzytelnić się przy użyciu bezpiecznej konwersacji zwykle generują <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType> . Jeśli jednak uwierzytelnianie dupleksowe za pomocą bezpiecznej konwersacji nie powiedzie się, klient otrzyma <xref:System.TimeoutException?displayProperty=nameWithType> zamiast.  
  
 Aby uzyskać więcej informacji na temat pracy z informacjami o błędach na poziomie aplikacji, zobacz [określanie i obsługa błędów w kontraktach i usługach](../specifying-and-handling-faults-in-contracts-and-services.md). [Oczekiwane wyjątki](../samples/expected-exceptions.md) opisują oczekiwane wyjątki i pokazują, jak je obsłużyć. Aby uzyskać więcej informacji o sposobie obsługi błędów podczas tworzenia kanałów, zobacz [Obsługa wyjątków i błędów](../extending/handling-exceptions-and-faults.md).  
  
### <a name="client-blocking-and-performance"></a>Blokowanie i wydajność klienta  
 Gdy aplikacja synchronicznie wywołuje operację żądanie-odpowiedź, zostaje zablokowana przez klienta do momentu otrzymania wartości zwracanej lub wyjątek (na przykład <xref:System.TimeoutException?displayProperty=nameWithType> ). Takie zachowanie jest podobne do zachowania lokalnego. Gdy aplikacja synchronicznie wywołuje operację na obiekcie klienta lub kanale programu WCF, klient nie zwraca do momentu, gdy warstwa kanału nie będzie mogła zapisywać danych w sieci ani nie zostanie zgłoszony wyjątek. Natomiast wzorzec wymiany komunikatów jednokierunkowych (określony przez oznaczenie operacji z <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> ustawioną na `true` ) może spowodować, że niektórzy klienci jeszcze więcej odpowiadają, w zależności od powiązania i komunikatów, które zostały już wysłane. Operacje jednokierunkowe dotyczą tylko wymiany komunikatów, nie są jeszcze mniejsze. Aby uzyskać więcej informacji, zobacz jednokierunkowe [usługi](one-way-services.md).  
  
 Duże fragmenty danych mogą spowalniać przetwarzanie klienta niezależnie od tego, jaki jest wzorzec wymiany komunikatów. Aby zrozumieć, jak obsłużyć te problemy, zobacz artykuł [duże ilości danych i przesyłanie strumieniowe](large-data-and-streaming.md).  
  
 Jeśli aplikacja musi wykonywać większą pracę podczas kończenia operacji, należy utworzyć parę metod asynchronicznych w interfejsie kontraktu usługi, który implementuje klient WCF. Najprostszym sposobem jest użycie `/async` przełącznika w [narzędziu narzędzia metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Aby zapoznać się z przykładem, zobacz [How to: calling Service Operations asynchronicznie](how-to-call-wcf-service-operations-asynchronously.md).  
  
 Aby uzyskać więcej informacji o zwiększaniu wydajności klienta, zobacz [aplikacje klienckie warstwy środkowej](middle-tier-client-applications.md).  
  
### <a name="enabling-the-user-to-select-credentials-dynamically"></a>Umożliwienie użytkownikowi dynamicznego wybierania poświadczeń  
 <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer>Interfejs umożliwia aplikacjom wyświetlanie interfejsu użytkownika, który umożliwia użytkownikowi wybranie poświadczeń, za pomocą których kanał jest tworzony przed rozpoczęciem czasomierzy limitu czasu.  
  
 Deweloperzy aplikacji mogą korzystać z wstawionego <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> na dwa sposoby. Aplikacja kliencka może wywołać jedną <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (lub wersję asynchroniczną) przed otwarciem kanału ( *jawne* podejście) lub wywołać pierwszą operację ( *niejawne* podejście).  
  
 W przypadku użycia podejścia niejawnego aplikacja musi wywołać pierwszą operację na <xref:System.ServiceModel.ClientBase%601> <xref:System.ServiceModel.IClientChannel> rozszerzeniu lub. Jeśli wywołuje coś innego niż pierwsza operacja, zgłaszany jest wyjątek.  
  
 W przypadku użycia jawnego podejścia aplikacja musi wykonać następujące kroki w kolejności:  
  
1. Wywołaj jedną <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (lub wersję asynchroniczną).  
  
2. Gdy inicjatory zostały zwrócone, należy wywołać <xref:System.ServiceModel.ICommunicationObject.Open%2A> metodę dla <xref:System.ServiceModel.IClientChannel> obiektu lub <xref:System.ServiceModel.IClientChannel> obiektu zwróconego z <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=nameWithType> właściwości.  
  
3. Wywołania operacji.  
  
 Zaleca się, aby aplikacje z jakością produkcyjną kontrolować proces interfejsu użytkownika, przyjmując jawne podejście.  
  
 Aplikacje korzystające z niejawnej metody wywołują inicjatory interfejsu użytkownika, ale jeśli użytkownik aplikacji nie odpowie w okresie limitu czasu wysyłania powiązania, zostanie wygenerowany wyjątek, gdy interfejs użytkownika zwróci wartość.  
  
## <a name="see-also"></a>Zobacz też

- [Usługi dwukierunkowe](duplex-services.md)
- [Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktów jednokierunkowych i kontraktów „żądanie-odpowiedź”](how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego](how-to-access-services-with-a-duplex-contract.md)
- [Instrukcje: dostęp do usługi WSE 3.0](how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Instrukcje: używanie elementu ChannelFactory](how-to-use-the-channelfactory.md)
- [Instrukcje: Asynchroniczne wywoływanie operacji usługi](how-to-call-wcf-service-operations-asynchronously.md)
- [Aplikacje klienckie warstwy środkowej](middle-tier-client-applications.md)
