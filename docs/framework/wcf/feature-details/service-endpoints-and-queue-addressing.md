---
title: "Punkty końcowe usługi i adresowanie kolejki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d2d59d7-f08b-44ed-bd31-913908b83d97
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ebfd4b977083206dc0210441fff2c0c08079e34a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="service-endpoints-and-queue-addressing"></a>Punkty końcowe usługi i adresowanie kolejki
W tym temacie omówiono sposób klienci adresu usługi, które zapoznały się z kolejek oraz sposobu mapowania punktów końcowych usługi kolejki. Dla przypomnienia, na poniższej ilustracji przedstawiono klasycznego [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] wdrożenia aplikacji w kolejce.  
  
 ![Diagram aplikacji w kolejce](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "rozproszonych kolejki — rysunek")  
  
 Dla klienta, który można wysłać wiadomości do usługi Klient adresów wiadomości do kolejki docelowej. Dla usługi do czytania wiadomości z kolejki ustawia jego adres nasłuchiwania do kolejki docelowej. Adresowanie w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest oparta na protokole Uniform Resource Identifier URI podczas nazwy kolejki usługi kolejkowania komunikatów (MSMQ) nie są oparte na identyfikator URI. Bardzo w związku z tym ważne jest zrozumienie, jak adres kolejki utworzone za pomocą usługi MSMQ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="msmq-addressing"></a>Adresowanie usługi MSMQ  
 Usługa MSMQ używana ścieżki i nazwy formatu kolejki. Ścieżki Określ nazwę hosta i `QueueName`. Opcjonalnie można `Private$` między nazwą hosta i `QueueName` wskazująca kolejki prywatnej, która nie jest publikowany w usłudze katalogowej Active Directory.  
  
 Nazwy ścieżek są mapowane na "FormatNames", aby określić dodatkowe aspekty adres, w tym protokół transferu menedżera kolejek i routing. Menedżer kolejek obsługuje dwa protokoły transferu: natywnego protokołu MSMQ i SOAP Reliable Messaging Protocol (SRMP).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Ścieżka i format nazwy usługi MSMQ, zobacz [o usługi kolejkowania komunikatów](http://go.microsoft.com/fwlink/?LinkId=94837).  
  
## <a name="netmsmqbinding-and-service-addressing"></a>NetMsmqBinding i adresowania usługi  
 Podczas adresowania wiadomości do usługi, schemat w identyfikatorze URI zostanie wybrany na podstawie transportu używany do komunikacji. Każdy transport w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ma unikatowy schemat. Schemat musi odzwierciedlać rodzaj transportu używany do komunikacji. Na przykład net.tcp, net.pipe, HTTP i tak dalej.  
  
 Transport kolejki usługi MSMQ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przedstawia schemat net.msmq. Dowolny komunikat reagować, wykonując Schemat net.msmq są wysyłane przy użyciu `NetMsmqBinding` kanałem transport z kolejką usługi MSMQ.  
  
 Adresowanie kolejki w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] opiera się na następujący wzór:  
  
 NET.MSMQ: / / \< *nazwy hosta*> / [prywatnej /] \< *Nazwa kolejki*>  
  
 gdzie:  
  
-   \<*Nazwa hosta*> jest nazwą komputera obsługującego kolejki docelowej.  
  
-   [prywatnej] jest opcjonalna. Jest używany podczas adresowanie kolejki docelowej, która jest kolejki prywatnej. Aby zaadresować kolejkę publiczną, nie można określać prywatnych. Należy zauważyć, że w przeciwieństwie do ścieżek usługi MSMQ nie jest "$" w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] formularza identyfikatora URI.  
  
-   \<*Nazwa kolejki*> jest nazwą kolejki. Nazwa kolejki może również dotyczyć podkolejki. W związku z tym \< *Nazwa kolejki*> = \< *nazwy z kolejki*> [; *podrzędne queue nazwa*].  
  
 Example1: Aby zaadresować kolejkę prywatną PurchaseOrders hostowanych na komputerze atadatum.com abc, identyfikator URI będzie mieć net.msmq://abc.adatum.com/private/PurchaseOrders.  
  
 Przykład2: Aby zaadresować kolejkę publiczną AccountsPayable hostowanych na komputerze atadatum.com def, identyfikator URI będzie mieć net.msmq://def.adatum.com/AccountsPayable.  
  
 Adres kolejki jest używany jako identyfikatora URI nasłuchiwania przez odbiornik do odczytu wiadomości. Innymi słowy adres kolejki jest odpowiednikiem gniazda portu TCP nasłuchiwania.  
  
 Odczyty z kolejki punktu końcowego, należy określić adres kolejki przy użyciu tego samego schematu określony wcześniej podczas otwierania elementu ServiceHost. Przykłady można znaleźć [Net powiązanie MSMQ](../../../../docs/framework/wcf/samples/net-msmq-binding.md) i [próbek do powiązania integracji usługi kolejkowania komunikatów](http://msdn.microsoft.com/en-us/997d11cb-f2c5-4ba0-9209-92843d4d0e1a).  
  
### <a name="multiple-contracts-in-a-queue"></a>Wiele kontraktów w kolejce  
 Wiadomości w kolejce można zaimplementować różnymi umowami. W tym przypadku jest istotne, jedną z następujących jest wartość PRAWDA, aby pomyślnie odczytywać i przetwarzać komunikaty:  
  
-   Określ punkt końcowy usługi, który implementuje wszystkich umów. Jest to zalecane podejście.  
  
-   Określ wiele punktów końcowych z różnymi umowami, ale należy upewnić się, że wszystkie punkty końcowe używać tego samego `NetMsmqBinding` obiektu. Wysyłania logikę ServiceModel używa pompę komunikat o treści wiadomości poza kanał transportu do wysyłki ostatecznie demultipleksowanie wiadomości opartych na kontraktu do różnych punktów końcowych. Przekazywanie komunikatów jest tworzony dla pary powiązania/identyfikatora URI nasłuchiwania. Adres kolejki jest używany jako identyfikatora URI nasłuchiwania przez odbiornik umieszczonych w kolejce. O użycie wszystkich punktów końcowych tego samego obiektu powiązania gwarantuje, że pompa pojedynczym komunikacie jest używany do odczytywania wiadomości i demultipleksowania do odpowiednich punktów końcowych na podstawie umowy.  
  
### <a name="srmp-messaging"></a>SRMP obsługi wiadomości  
 Jak opisano wcześniej można użyć protokołu SRMP transferów kolejki do kolejki. Jest ona powszechnie stosowana, gdy transport HTTP przesyła wiadomości między kolejki transmisji i kolejki docelowej.  
  
 Do korzystania z protokołu transferu SRMP, adres wiadomości przy użyciu net.msmq schemat identyfikatora URI, jak wspomniano wcześniej i określ wybór SRMP lub zabezpieczone SRMP w `QueueTransferProtocol` właściwość `NetMsmqBinding`.  
  
 Określanie `QueueTransferProtocol` właściwość jest tylko do wysyłania funkcji. Jest to wskazanie przez klienta, jakiego rodzaju kolejki transfer protokół do użycia.  
  
### <a name="using-active-directory"></a>Przy użyciu usługi Active Directory  
 Usługa MSMQ jest dostarczany z obsługą integracji usługi Active Directory. Jeśli usługa MSMQ jest zainstalowana w integracji usługi Active Directory, komputer musi być częścią domeny systemu Windows. Usługi Active Directory jest używana do publikowania kolejek na potrzeby odnajdowania; kolejki takie są nazywane *kolejek publicznych*. Gdy adresowanie kolejki, kolejki można rozwiązać przy użyciu usługi Active Directory. Jest to podobne do używania systemu nazw domen (DNS) do rozpoznawania adresów IP, nazwy sieci. `UseActiveDirectory` Właściwości w `NetMsmqBinding` jest wartością logiczną, która wskazuje, czy kanał umieszczonych w kolejce muszą używać usługi Active Directory można rozpoznać identyfikatora URI kolejki. Domyślnie jest ustawiona wartość `false`. Jeśli `UseActiveDirectory` właściwość jest ustawiona na `true`, a następnie zwrócony używa usługi Active Directory, aby przekonwertować net.msmq:// identyfikatora URI nazwy formatu.  
  
 `UseActiveDirectory` Właściwość ma znaczenie tylko dla klienta, który wysyła wiadomości, ponieważ jest używany do rozpoznawania adresów kolejki przy wysyłaniu wiadomości.  
  
### <a name="mapping-netmsmq-uri-to-message-queuing-format-names"></a>Mapowanie identyfikatora URI net.msmq do nazwy formatu usługi kolejkowania komunikatów  
 Zwrócony obsługuje mapowania nazwy identyfikatora URI net.msmq dostarczony do kanału do nazwy formatu MSMQ. W poniższej tabeli przedstawiono reguły używane do mapowania między nimi.  
  
|Adres URI usługi WCF na podstawie kolejki|Użyj właściwości usługi Active Directory|Właściwość Transfer Protocol kolejki|Wynikowa nazwy formatu MSMQ|  
|----------------------------------|-----------------------------------|--------------------------------------|---------------------------------|  
|NET.MSMQ://\<nazwa komputera >/prywatnej/abc|Wartość FAŁSZ (ustawienie domyślne)|Native (domyślnie)|DIRECT = OS:machine-name\private$ \abc|  
|NET.MSMQ://\<nazwa komputera >/prywatnej/abc|False|SRMP|DIRECT = http://machine/msmq/private$ / abc|  
|NET.MSMQ://\<nazwa komputera >/prywatnej/abc|Wartość true|Natywny|PUBLICZNY = niektóre guid (identyfikator GUID kolejki)|  
  
### <a name="reading-messages-from-the-dead-letter-queue-or-the-poison-message-queue"></a>Odczytywanie wiadomości z kolejki utraconych wiadomości i kolejki wiadomości Poison  
 Aby odczytać wiadomości z kolejki wiadomości poison, która jest podkolejki kolejki docelowej, otwórz `ServiceHost` adres podkolejki.  
  
 Przykład: Usługa, która odczytuje z kolejki wiadomości poison kolejki prywatnej PurchaseOrders z komputera lokalnego czy adresów net.msmq://localhost/private/PurchaseOrders;poison.  
  
 Aby odczytać wiadomości z kolejki utraconych wiadomości transakcyjnych systemu, identyfikator URI musi mieć postać: net.msmq://localhost/system$; DeadXact.  
  
 Aby odczytać wiadomości z kolejki utraconych wiadomości nietransakcyjne systemu, identyfikator URI musi być w formie: net.msmq://localhost/system$; utraconych wiadomości.  
  
 Podczas korzystania z niestandardowej kolejki utraconych wiadomości, należy pamiętać, że kolejka utraconych wiadomości musi znajdować się na komputerze lokalnym. Tak identyfikator URI kolejki utraconych wiadomości jest ograniczony do formularza:  
  
 NET.MSMQ: //localhost/ [prywatnej /] \< *niestandardowe wiadomości list kolejki nazwa-*>.  
  
 A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi sprawdza, czy wszystkie komunikaty o otrzymaniu zostały skierowane do określonej kolejki jest nasłuchiwanie. Kolejki docelowej wiadomości niezgodna kolejki, który znajduje się w usługa nie przetwarza wiadomości. Jest to problem, który musi adresów usług nasłuchujących do kolejki utraconych wiadomości, ponieważ wszystkie wiadomości w kolejce wiadomości utraconych miały mają być dostarczone w innym miejscu. Aby odczytać wiadomości z kolejki utraconych wiadomości lub skażone kolejki, `ServiceBehavior` z <xref:System.ServiceModel.AddressFilterMode.Any> parametr musi być używany. Na przykład zobacz [kolejki utraconych wiadomości](../../../../docs/framework/wcf/samples/dead-letter-queues.md).  
  
## <a name="msmqintegrationbinding-and-service-addressing"></a>MsmqIntegrationBinding i adresowania usługi  
 `MsmqIntegrationBinding` Jest używany do komunikacji z tradycyjne aplikacje usługi MSMQ. Aby ułatwić współdziałanie z istniejącej aplikacji usługi MSMQ, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje tylko format nazw adresowania. W związku z tym komunikatów wysyłanych za pomocą tego powiązania musi odpowiadać schemat identyfikatora URI:  
  
 MSMQ.formatname:\<*MSMQ format nazwy*>>  
  
 Nazwa formatu MSMQ ma postać określony przez usługę MSMQ w [o usługi kolejkowania komunikatów](http://go.microsoft.com/fwlink/?LinkId=94837).  
  
 Należy pamiętać, że można używać tylko bezpośrednich nazw formatu i nazwy formatu publiczne i prywatne (wymaga integracji usługi Active Directory) podczas odbierania wiadomości z kolejki przy użyciu `MsmqIntegrationBinding`. Jednak zaleca się, że używasz bezpośrednich nazw formatu. Na przykład na [!INCLUDE[wv](../../../../includes/wv-md.md)], inne nazwą formatu powoduje błąd, ponieważ system próbuje otworzyć kolejkę, które mogą być otwierane tylko w przypadku bezpośrednich nazw formatu.  
  
 Podczas adresowania za pomocą SRMP `MsmqIntegrationBinding`, nie jest wymagane do dodania /msmq/ w bezpośredniej nazwy formatu ułatwiające wysyłki Internet Information Services (IIS). Na przykład: gdy adresowanie kolejki przy użyciu SRMP abc protokołu, zamiast bezpośredniego = http://adatum.com/msmq/private$ / abc, należy używać bezpośrednio = http://adatum.com/private$ / abc.  
  
 Należy pamiętać, że nie można użyć net.msmq:// adresowania z `MsmqIntegrationBinding`. Ponieważ `MsmqIntegrationBinding` obsługuje dowolnych MSMQ format nazwy addressing, można użyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, która używa tego powiązania do funkcji multiemisji i dystrybucji listy w usłudze MSMQ. Jedynym wyjątkiem jest określenie `CustomDeadLetterQueue` przy użyciu `MsmqIntegrationBinding`. Musi to być net.msmq:// formularza, podobnie jak jest określona za pomocą `NetMsmqBinding`.  
  
## <a name="see-also"></a>Zobacz też  
 [Sieć Web hostująca aplikację Zakolejkowaną](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
