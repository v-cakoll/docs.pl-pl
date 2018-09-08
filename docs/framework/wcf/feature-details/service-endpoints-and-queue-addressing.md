---
title: Punkty końcowe usługi i adresowanie kolejki
ms.date: 03/30/2017
ms.assetid: 7d2d59d7-f08b-44ed-bd31-913908b83d97
ms.openlocfilehash: 71ebf29e51118a7f555f3e79598e49ffd65e0c63
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180829"
---
# <a name="service-endpoints-and-queue-addressing"></a>Punkty końcowe usługi i adresowanie kolejki
W tym temacie omówiono, jak klienci adresów usług, które są odczytywane z kolejki i sposobu mapowania punktów końcowych usługi do kolejek. Przypominamy Poniższa ilustracja przedstawia klasycznego wdrożenia aplikacji w kolejce usług Windows Communication Foundation (WCF).  
  
 ![Diagram aplikacji w kolejce](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "rozproszonych kolejka rysunek")  
  
 Dla klienta wysłać wiadomość do usługi Klient adresów komunikat do kolejki docelowej. Usługi do odczytywania komunikatów z kolejki ustawia jego adresu nasłuchiwania kolejki docelowej. Adresowanie w programie WCF jest jednolite zasobów identyfikator URI na podstawie nazwy kolejki usługi kolejkowania komunikatów (MSMQ) nie są na podstawie identyfikatora URI. Dlatego ważne jest zrozumienie, jak rozwiązywać problemy z kolejki utworzone w usłudze MSMQ przy użyciu usługi WCF.  
  
## <a name="msmq-addressing"></a>Adresowanie usługi MSMQ  
 Usługa MSMQ używana ścieżki i nazwy formatu kolejki. Ścieżki Określ nazwę hosta i `QueueName`. Opcjonalnie może istnieć `Private$` między nazwą hosta i `QueueName` do wskazania kolejki prywatnej, który nie został opublikowany w usłudze katalogowej Active Directory.  
  
 Nazwy ścieżek są mapowane na "FormatNames", aby określić dodatkowe aspekty adres, w tym protokół transferu Menedżera routingu i kolejki. Menedżer kolejki obsługuje dwa protokoły transferu: natywny protokół usługi MSMQ i SOAP Reliable Messaging Protocol (SRMP).  
  
 Aby uzyskać więcej informacji na temat MSMQ ścieżkę i format nazw, zobacz [dotyczących usługi kolejkowania komunikatów](https://go.microsoft.com/fwlink/?LinkId=94837).  
  
## <a name="netmsmqbinding-and-service-addressing"></a>NetMsmqBinding i adresowania usługi  
 Podczas adresowania komunikatu do usługi, schemat w identyfikatorze URI jest wybierany zależnie od transportu, używany do komunikacji. Każdy transportu programu WCF ma unikatowy schemat. Schemat muszą odzwierciedlać rodzaj transportu używany do komunikacji. Na przykład net.tcp, net.pipe, HTTP i tak dalej.  
  
 Usługi MSMQ w kolejce transportu w ujawnia WCF Schemat net.msmq. Wszystkie komunikaty adresowane przy użyciu schematu net.msmq są wysyłane przy użyciu `NetMsmqBinding` za pośrednictwem kanału umieszczonych w kolejce transportu MSMQ.  
  
 Adresowanie kolejki programu WCF zależy od następującego wzorca:  
  
 NET.MSMQ: / / \< *nazwy hosta*> / [prywatne /] \< *Nazwa kolejki*>  
  
 gdzie:  
  
-   \<*Nazwa hosta*> jest nazwą komputera, który jest hostem kolejka docelowa.  
  
-   [prywatnej] jest opcjonalna. Jest używany podczas adresowania kolejki docelowej, która jest kolejki prywatnej. Aby rozwiązać kolejka publiczna, nie można określać prywatnych. Należy pamiętać, że, w przeciwieństwie do ścieżki MSMQ "$" w formie identyfikatora URI usługi WCF.  
  
-   \<*Nazwa kolejki*> jest nazwą kolejki. Nazwa kolejki może również dotyczyć kolejki podrzędnej. W efekcie \< *Nazwa kolejki*> = \< *nazwy z kolejki*> [; *podrzędne queue-name*].  
  
 Przykład1: Aby rozwiązać kolejki prywatnej PurchaseOrders hostowanych na komputerze abc atadatum.com, identyfikator URI będzie net.msmq://abc.adatum.com/private/PurchaseOrders.  
  
 Przykład2: Aby rozwiązać kolejki publicznej AccountsPayable hostowanych na komputerze def atadatum.com, identyfikator URI będzie net.msmq://def.adatum.com/AccountsPayable.  
  
 Adres kolejki jest używany jako identyfikator URI nasłuchiwania przez odbiornik do odczytywania komunikatów z. Innymi słowy adres kolejki jest odpowiednikiem nasłuchiwania gniazda portu TCP.  
  
 Punkt końcowy, który odczytuje z kolejki, należy określić adres kolejki przy użyciu tego samego schematu określony wcześniej podczas otwierania elementu ServiceHost. Aby uzyskać przykłady, zobacz [netto powiązanie usługi MSMQ](../../../../docs/framework/wcf/samples/net-msmq-binding.md) i [przykłady do powiązania integracji usługi kolejkowania komunikatów](https://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a).  
  
### <a name="multiple-contracts-in-a-queue"></a>Wiele kontraktów w kolejce  
 Wiadomości w kolejce można zaimplementować różnymi umowami. W tym przypadku jest istotne, jedną z następujących jest wartość true, aby pomyślnie odczytywać i przetwarzać komunikaty:  
  
-   Określ punkt końcowy usługi, która implementuje wszystkich umów. Jest to zalecane podejście.  
  
-   Określ wiele punktów końcowych z różnymi umowami, ale upewnij się, że wszystkie punkty końcowe używać tego samego `NetMsmqBinding` obiektu. Dispatching logiki w modelu ServiceModel używa pompy komunikatów, która odczytuje komunikaty z kanał transportu do wysyłki ostatecznie demultipleksowanie komunikaty oparte na umowie do różnych punktów końcowych. "Pompy komunikatów" jest tworzony dla pary identyfikatora URI/wiązania nasłuchiwania. Adres kolejki jest używany jako identyfikator URI nasłuchiwania przez odbiornik umieszczonych w kolejce. Posiadanie wszystkich użycie punktów końcowych, tego samego obiektu powiązania gwarantuje, że pompa jednego komunikatu służy do odczytu komunikatu i cofnąć multipleksować do odpowiednich punktów końcowych na podstawie umowy.  
  
### <a name="srmp-messaging"></a>SRMP komunikatów  
 Jak już wspomniano można użyć protokołu SRMP transferów kolejki do kolejki. Jest to często używane, podczas transportu HTTP przesyła wiadomości między kolejki transmisji i kolejki docelowej.  
  
 Do korzystania z protokołu transferu SRMP, adres wiadomości przy użyciu net.msmq schemat identyfikatora URI, jak wspomniano wcześniej, a następnie określ wybór SRMP lub zabezpieczone SRMP w `QueueTransferProtocol` właściwość `NetMsmqBinding`.  
  
 Określanie `QueueTransferProtocol` właściwość jest tylko do wysyłania funkcji. Jest to wskazanie przez klienta, którego rodzaju kolejki transferu protokół do użycia.  
  
### <a name="using-active-directory"></a>Za pomocą usługi Active Directory  
 Usługa MSMQ jest dostarczany z obsługą integracji usługi Active Directory. Po zainstalowaniu usługi MSMQ z integracją usługi Active Directory maszyna musi być częścią domeny Windows. Usługi Active Directory jest używana do publikowania kolejek odnajdowania; kolejki takie są nazywane *kolejek publicznych*. Gdy adresowanie kolejki, kolejki można rozwiązać za pomocą usługi Active Directory. Jest to podobne do jak System nazw domen (DNS, Domain Name System) jest używany do rozpoznawania adresu IP, nazwy sieci. `UseActiveDirectory` Właściwość `NetMsmqBinding` jest wartością logiczną, wskazującą, czy kanał umieszczonych w kolejce należy użyć usługi Active Directory można rozpoznać kolejki identyfikatora URI. Domyślnie jest ustawiona `false`. Jeśli `UseActiveDirectory` właściwość jest ustawiona na `true`, następnie zwrócony używa usługi Active Directory można przekonwertować net.msmq:// identyfikatora URI do nazwy formatu.  
  
 `UseActiveDirectory` Właściwość ma znaczenie tylko w przypadku klienta, który wysyła wiadomość, ponieważ jest używany do rozpoznania adresu kolejki przy wysyłaniu wiadomości.  
  
### <a name="mapping-netmsmq-uri-to-message-queuing-format-names"></a>Mapowanie net.msmq identyfikator URI, do nazwy formatu usługi kolejkowania komunikatów  
 Zwrócony obsługuje mapowania nazwy identyfikatora URI net.msmq, które są dostarczane do kanału usługi MSMQ format nazw. Poniższa tabela zawiera podsumowanie reguł służy do mapowania między nimi.  
  
|Adres URI usługi WCF na podstawie kolejki|Użyj właściwości usługi Active Directory|Właściwość Transfer Protocol kolejki|Wynikowy nazwy formatu usługi MSMQ|  
|----------------------------------|-----------------------------------|--------------------------------------|---------------------------------|  
|Net.msmq://\<machine-name>/private/abc|FALSE (domyślnie)|Native (domyślnie)|DIRECT=OS:machine-name\private$\abc|  
|Net.msmq://\<machine-name>/private/abc|False|SRMP|DIRECT = OS:http://machine/msmq/private$/ abc|  
|Net.msmq://\<machine-name>/private/abc|True|Natywne|PUBLICZNY = niektóre guid (identyfikator GUID kolejki)|  
  
### <a name="reading-messages-from-the-dead-letter-queue-or-the-poison-message-queue"></a>Odczytywanie komunikatów z kolejki wiadomości utraconych lub kolejki komunikatów Poison  
 Aby odczytać wiadomości z kolejki komunikatów poison, która jest kolejki podrzędnej kolejki docelowej, należy otworzyć `ServiceHost` przy użyciu adresu kolejki podrzędnej.  
  
 Przykład: Usługa, która odczytuje z kolejki komunikatów poison kolejki prywatnej PurchaseOrders z komputera lokalnego czy adresów net.msmq://localhost/private/PurchaseOrders;poison.  
  
 Odczytywanie komunikatów z kolejki utraconych wiadomości transakcyjnych systemu, identyfikator URI musi mieć postać: net.msmq://localhost/system$; DeadXact.  
  
 Odczytywanie komunikatów z kolejki utraconych wiadomości nietransakcyjne systemu, identyfikatora URI musi mieć postać: net.msmq://localhost/system$; utraconych wiadomości.  
  
 Korzystając z niestandardowego kolejki utraconych wiadomości, należy pamiętać, że kolejki utraconych wiadomości musi znajdować się na komputerze lokalnym. W efekcie identyfikator URI dla kolejki utraconych wiadomości jest ograniczony do formularza:  
  
 NET.MSMQ: //localhost/ [prywatne /] \< *niestandardowe dead list kolejki nazwa-*>.  
  
 Usługa WCF sprawdza, czy wszystkie wiadomości otrzymywanych zostało zmodyfikowanych do określonej kolejki, którego nasłuchuje na. Kolejki docelowej komunikatu nie pasuje do kolejki, który znajduje się w, usługa nie przetwarza wiadomości. Jest to problem, który nasłuchuje do kolejki utraconych wiadomości usługi muszą spełnić, ponieważ wszystkie komunikaty w kolejce wiadomości utraconych miał trafić do dostarczenia gdzie indziej. Odczytywanie komunikatów z kolejki utraconych wiadomości lub kolejką skażone `ServiceBehavior` z <xref:System.ServiceModel.AddressFilterMode.Any> parametr musi być używany. Aby uzyskać przykład, zobacz [kolejki wiadomości utraconych](../../../../docs/framework/wcf/samples/dead-letter-queues.md).  
  
## <a name="msmqintegrationbinding-and-service-addressing"></a>MsmqIntegrationBinding i adresowania usługi  
 `MsmqIntegrationBinding` Jest używany do komunikacji z tradycyjnymi aplikacjami usługi MSMQ. Aby ułatwić współdziałanie z istniejącą aplikacją usługi MSMQ, WCF obsługuje tylko format nazw adresowania. W związku z tym komunikaty wysyłane za pomocą tego powiązania musi odpowiadać schemat identyfikatora URI:  
  
 msmq.formatname:\<*MSMQ-format-name*>>  
  
 Nazwa formatu MSMQ ma postać określony przez MSMQ w [dotyczących usługi kolejkowania komunikatów](https://go.microsoft.com/fwlink/?LinkId=94837).  
  
 Należy pamiętać, że można używać tylko bezpośrednich nazw formatu i nazwy formatu publicznych i prywatnych (wymaga integracji usługi Active Directory) podczas odbierania komunikatów z kolejki za pomocą `MsmqIntegrationBinding`. Jednak zaleca się, że używasz bezpośrednich nazw formatu. Na przykład na [!INCLUDE[wv](../../../../includes/wv-md.md)], przy użyciu innej nazwy formatu powoduje błąd, ponieważ system próbuje otworzyć kolejki podrzędnej, które mogą być otwierane tylko w przypadku bezpośrednich nazw formatu.  
  
 Podczas adresowania za pomocą SRMP `MsmqIntegrationBinding`, nie jest wymagane do dodania /msmq/ w bezpośrednią nazwą formatu ułatwiające Internet Information Services (IIS) z wysyłką. Na przykład: podczas adresowania kolejki abc przy użyciu SRMP protokół, zamiast bezpośrednio =http://adatum.com/msmq/private$/ abc, należy użyć DIRECT =http://adatum.com/private$/ abc.  
  
 Należy pamiętać, że nie można użyć net.msmq:// adresowanie z `MsmqIntegrationBinding`. Ponieważ `MsmqIntegrationBinding` obsługuje dowolnych MSMQ format nazw adresowania, możesz użyć usługi WCF, która używa tego powiązania, aby używać funkcji listy multiemisji i dystrybucji w usłudze MSMQ. Jedynym wyjątkiem jest określenie `CustomDeadLetterQueue` przy użyciu `MsmqIntegrationBinding`. Musi ono być net.msmq:// formularza, podobnie jak jest określony za pomocą `NetMsmqBinding`.  
  
## <a name="see-also"></a>Zobacz też  
 [Sieć Web hostująca aplikację zakolejkowaną](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
