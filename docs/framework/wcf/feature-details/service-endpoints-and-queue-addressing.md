---
title: Punkty końcowe usługi i adresowanie kolejki
ms.date: 03/30/2017
ms.assetid: 7d2d59d7-f08b-44ed-bd31-913908b83d97
ms.openlocfilehash: a17e680732cd257fbdfd95eb09df8c53f5894400
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600390"
---
# <a name="service-endpoints-and-queue-addressing"></a>Punkty końcowe usługi i adresowanie kolejki
W tym temacie omówiono sposób, w jaki klienci adresów odczytywać z kolejek i jak punkty końcowe usługi mapują na kolejki. Na poniższej ilustracji przedstawiono wdrożenie klasycznej aplikacji Windows Communication Foundation (WCF) w kolejce.  
  
 ![Diagram aplikacji znajdujących się w kolejce](media/distributed-queue-figure.jpg "Rozproszona-Queueed-Figure")  
  
 Klient, który wysyła komunikat do usługi, kieruje komunikat do kolejki docelowej. Aby usługa mogła odczytywać wiadomości z kolejki, ustawia adres nasłuchu do kolejki docelowej. Adresowanie w programie WCF odbywa się na podstawie Uniform Resource Identifier (URI), gdy nazwy kolejek usługi kolejkowania komunikatów (MSMQ) nie są oparte na identyfikatorze URI. W związku z tym ważne jest, aby zrozumieć, jak rozadresować kolejki utworzone w usłudze MSMQ przy użyciu programu WCF.  
  
## <a name="msmq-addressing"></a>Adresowanie MSMQ  
 Usługa MSMQ używa ścieżek i nazw formatów do identyfikowania kolejki. Ścieżki określają nazwę hosta i `QueueName` . Opcjonalnie może istnieć `Private$` między nazwą hosta a a, `QueueName` Aby wskazać kolejkę prywatną, która nie została opublikowana w usłudze katalogowej Active Directory.  
  
 Nazwy ścieżek są mapowane na "FormatNames" w celu określenia dodatkowych aspektów adresu, w tym routingu i protokołu transferu Menedżera kolejki. Menedżer kolejki obsługuje dwa protokoły transferu: natywny protokół MSMQ i protokół komunikacyjny protokołu SOAP (SRMP).  
  
 Aby uzyskać więcej informacji na temat nazwy ścieżki i formatu usługi MSMQ, zobacz [Informacje o kolejkach komunikatów](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms706032(v=vs.85)).  
  
## <a name="netmsmqbinding-and-service-addressing"></a>Usługi Msmqbinding i adresowanie usługi  
 Podczas adresowania wiadomości do usługi, schemat w identyfikatorze URI jest wybierany w oparciu o transport używany do komunikacji. Każdy transport w usłudze WCF ma unikatowy schemat. Schemat musi odzwierciedlać charakter transportu używany do komunikacji. Na przykład net. TCP, net. pipe, HTTP i tak dalej.  
  
 Kolejkowanie w kolejce usługi MSMQ w programie WCF uwidacznia schemat net. MSMQ. Każdy komunikat rozkierowany przy użyciu schematu net. MSMQ jest wysyłany za pośrednictwem `NetMsmqBinding` kanału transportu w kolejce usługi MSMQ.  
  
 Adresowanie kolejki w programie WCF opiera się na następującym wzorcu:  
  
 NET. MSMQ:// \<*host-name*> /[Private/]\<*queue-name*>  
  
 gdzie:  
  
- \<*host-name*>to nazwa komputera, który hostuje kolejkę docelową.  
  
- [Private] jest opcjonalny. Jest używany podczas adresowania kolejki docelowej, która jest kolejką prywatną. Aby zająć się kolejką publiczną, nie należy określać elementu Private. Należy pamiętać, że w przeciwieństwie do ścieżek MSMQ nie ma "$" w formularzu identyfikatora URI WCF.  
  
- \<*queue-name*>jest nazwą kolejki. Nazwa kolejki może również odwoływać się do podkolejki. W tym celu \<*queue-name*>  =  \<*name-of-queue*> [;* Nazwa kolejki podrzędnej*].  
  
 Example1: Aby rozwiązać kolejkę prywatną PurchaseOrders hostowaną na komputerze ABC atadatum.com, identyfikator URI będzie net. MSMQ://abc.adatum.com/private/PurchaseOrders.  
  
 Example2: aby obsłużyć kolejkę publiczną AccountsPayable hostowaną na komputerze z interfejsem def atadatum.com, identyfikator URI będzie net. MSMQ://def.adatum.com/AccountsPayable.  
  
 Adres kolejki jest używany jako identyfikator URI nasłuchiwania przez odbiornik do odczytywania komunikatów. Inaczej mówiąc, adres kolejki jest równoważny portowi nasłuchiwania gniazda TCP.  
  
 Punkt końcowy, który odczytuje z kolejki, musi określać adres kolejki przy użyciu tego samego schematu określonego wcześniej podczas otwierania ServiceHost. Aby zapoznać się z przykładami, zobacz [net MSMQ Binding](../samples/net-msmq-binding.md).  
  
### <a name="multiple-contracts-in-a-queue"></a>Wiele kontraktów w kolejce  
 Komunikaty w kolejce mogą implementować różne kontrakty. W takim przypadku ważne jest, aby jedna z następujących wartości była prawdziwa, aby pomyślnie odczytywać i przetwarzać wszystkie komunikaty:  
  
- Określ punkt końcowy usługi implementującej wszystkie umowy. Jest to zalecane podejście.  
  
- Określ wiele punktów końcowych z różnymi kontraktami, ale upewnij się, że wszystkie punkty końcowe używają tego samego `NetMsmqBinding` obiektu. Logika wysyłania w elemencie ServiceModel używa pompy komunikatów, która odczytuje komunikaty z kanału transportowego do wysłania, które ostatecznie demultipleksuje komunikaty na podstawie kontraktu do różnych punktów końcowych. Dla pary URI/powiązania nasłuchiwania jest tworzona pompa komunikatów. Adres kolejki jest używany jako identyfikator URI nasłuchiwania przez odbiornik umieszczony w kolejce. Jeśli wszystkie punkty końcowe używają tego samego obiektu wiążącego, gwarantuje to, że jedna pompa komunikatów jest używana do odczytu komunikatu i demultipleksowania do odpowiednich punktów końcowych na podstawie kontraktu.  
  
### <a name="srmp-messaging"></a>Wiadomości SRMP  
 Jak wspomniano wcześniej, można użyć protokołu SRMP do transferów kolejek do kolejki. Jest to często używane, gdy transport HTTP przesyła komunikaty między kolejką transmisji a kolejką docelową.  
  
 Aby korzystać z protokołu transferu SRMP, adresowanie komunikatów przy użyciu schematu identyfikatora URI net. MSMQ, jak wspomniano wcześniej, i określić wybór protokołu SRMP lub zabezpieczonej metody SRMP we `QueueTransferProtocol` właściwości `NetMsmqBinding` .  
  
 Określanie `QueueTransferProtocol` właściwości jest funkcją tylko do wysyłania. Jest to wskazanie przez klienta, którego rodzaju protokół transferu kolejki ma być używany.  
  
### <a name="using-active-directory"></a>Azure Active Directory  
 Usługa MSMQ obsługuje integrację Active Directory. Gdy usługa MSMQ jest zainstalowana z integracją Active Directory, maszyna musi być częścią domeny systemu Windows. Active Directory służy do publikowania kolejek do odnajdywania; kolejki te są nazywane *kolejkami publicznymi*. Podczas rozwiązywania kolejki można rozpoznać kolejkę za pomocą Active Directory. Jest to podobne do sposobu, w jaki system nazw domen (DNS) jest używany do rozpoznawania adresu IP nazwy sieciowej. `UseActiveDirectory`Właściwość w `NetMsmqBinding` jest wartością logiczną, która wskazuje, czy kanał umieszczony w kolejce musi używać Active Directory do rozpoznawania identyfikatora URI kolejki. Domyślnie jest ono ustawione na wartość `false` . Jeśli `UseActiveDirectory` Właściwość jest ustawiona na `true` , kanał umieszczony w kolejce używa Active Directory do przekonwertowania nazwy net. MSMQ://URI na nazwę formatu.  
  
 `UseActiveDirectory`Właściwość ma znaczenie tylko dla klienta wysyłającego wiadomość, ponieważ jest używana do rozpoznawania adresu kolejki podczas wysyłania komunikatów.  
  
### <a name="mapping-netmsmq-uri-to-message-queuing-format-names"></a>Mapowanie identyfikatora URI net. MSMQ na nazwy formatu usługi kolejkowania komunikatów  
 Kanał umieszczony w kolejce obsługuje mapowanie nazwy URI net. MSMQ do kanału na nazwy formatu MSMQ. Poniższa tabela zawiera podsumowanie reguł używanych do mapowania między nimi.  
  
|Adres kolejki oparty na identyfikatorze URI WCF|Użyj właściwości Active Directory|Właściwość protokołu transferu kolejki|Wypływające nazwy formatu usługi MSMQ|  
|----------------------------------|-----------------------------------|--------------------------------------|---------------------------------|  
|`Net.msmq://<machine-name>/private/abc`|False (domyślnie)|Natywny (domyślny)|`DIRECT=OS:machine-name\private$\abc`|  
|`Net.msmq://<machine-name>/private/abc`|Fałsz|SRMP|`DIRECT=http://machine/msmq/private$/abc`|  
|`Net.msmq://<machine-name>/private/abc`|True|Natywne|`PUBLIC=some-guid`(identyfikator GUID kolejki)|  
  
### <a name="reading-messages-from-the-dead-letter-queue-or-the-poison-message-queue"></a>Odczytywanie wiadomości z kolejki utraconych wiadomości lub z kolejki trujących komunikatów  
 Aby odczytać wiadomości z kolejki komunikatów trujących, która jest podkolejką kolejki docelowej, Otwórz `ServiceHost` z adresem podkolejki.  
  
 Przykład: usługa, która odczytuje z kolejki "Trująca wiadomość" kolejki prywatnej PurchaseOrders z komputera lokalnego, będzie mieć adres net. MSMQ://localhost/private/PurchaseOrders; trujące.  
  
 Aby można było odczytać wiadomości z kolejki utraconych wiadomości transakcyjnych systemu, identyfikator URI musi mieć postać: net. MSMQ://localhost/system $;D eadXact.  
  
 Aby można było odczytywać komunikaty z kolejki utraconych wiadomości w systemie, identyfikator URI musi mieć postać: net. MSMQ://localhost/system $;D eadLetter.  
  
 W przypadku korzystania z niestandardowej kolejki utraconych wiadomości należy zauważyć, że kolejka utraconych wiadomości musi znajdować się na komputerze lokalnym. W związku z tym identyfikator URI dla kolejki utraconych wiadomości jest ograniczony do formularza:  
  
 NET. MSMQ://localhost/[Private/] \<*custom-dead-letter-queue-name*> .  
  
 Usługa WCF sprawdza, czy wszystkie odebrane komunikaty zostały rozkierowane do określonej kolejki, na której nasłuchuje. Jeśli kolejka docelowa komunikatu nie jest zgodna z kolejką, w której znajduje się w, usługa nie przetwarza komunikatu. Jest to problem polegający na tym, że usługi nasłuchujące w kolejce utraconych wiadomości muszą być adresami, ponieważ każdy komunikat w kolejce utraconych wiadomości został przewidziany w innym miejscu. Aby odczytać wiadomości z kolejki utraconych wiadomości lub z kolejki trującej, `ServiceBehavior` <xref:System.ServiceModel.AddressFilterMode.Any> należy użyć parametru z parametrem. Aby zapoznać się z przykładem, zobacz [kolejki utraconych wiadomości](../samples/dead-letter-queues.md).  
  
## <a name="msmqintegrationbinding-and-service-addressing"></a>MsmqIntegrationBinding i adresowanie usług  
 Służy `MsmqIntegrationBinding` do komunikacji z tradycyjnymi aplikacjami MSMQ. Aby ułatwić współdziałanie z istniejącą aplikacją MSMQ, WCF obsługuje tylko adresowanie nazw formatu. W ten sposób komunikaty wysyłane przy użyciu tego powiązania muszą być zgodne ze schematem identyfikatora URI:  
  
 MSMQ. formatname:\<*MSMQ-format-name*>>  
  
 Nazwa MSMQ-format-name ma postać określoną przez usługę MSMQ w [temacie Informacje o kolejkach komunikatów](https://docs.microsoft.com/previous-versions/windows/desktop/legacy/ms706032(v=vs.85)).  
  
 Należy pamiętać, że w przypadku otrzymywania wiadomości z kolejki przy użyciu programu można używać tylko bezpośrednich nazw formatu i nazw formatu publicznego i prywatnego (wymaga integracji Active Directory) `MsmqIntegrationBinding` . Zaleca się jednak używanie bezpośrednich nazw formatu. Na przykład w systemie Windows Vista użycie dowolnej innej nazwy formatu powoduje błąd, ponieważ system próbuje otworzyć podkolejkę, która może być otwierana tylko z bezpośrednimi nazwami formatu.  
  
 W przypadku adresowania SRMP przy użyciu `MsmqIntegrationBinding` nie istnieje wymóg dodania/MSMQ/w nazwie formatu bezpośredniego, aby pomóc Internet Information Services (IIS) z wysyłaniem. Na przykład: podczas adresowania kolejki ABC przy użyciu protokołu SRMP zamiast `DIRECT=http://adatum.com/msmq/private$/abc` , należy użyć `DIRECT=http://adatum.com/private$/abc` .  
  
 Należy pamiętać, że nie można użyć net. MSMQ://Addressing with `MsmqIntegrationBinding` . Ponieważ `MsmqIntegrationBinding` obsługuje adresowanie nazw formatu usługi MSMQ, można użyć usługi WCF korzystającej z tego powiązania do korzystania z funkcji listy multiemisji i dystrybucji w usłudze MSMQ. Jeden wyjątek jest określany `CustomDeadLetterQueue` podczas korzystania z `MsmqIntegrationBinding` . Musi mieć postać net. MSMQ://, podobnie jak w przypadku jej określenia przy użyciu `NetMsmqBinding` .  
  
## <a name="see-also"></a>Zobacz też

- [Sieć Web hostująca aplikację zakolejkowaną](web-hosting-a-queued-application.md)
