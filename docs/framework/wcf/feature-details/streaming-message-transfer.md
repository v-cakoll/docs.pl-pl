---
title: Strumieniowy transfer komunikatów
ms.date: 03/30/2017
ms.assetid: 72a47a51-e5e7-4b76-b24a-299d51e0ae5a
ms.openlocfilehash: 462144856750a1b8726b574fdc82746da2d72ff7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594793"
---
# <a name="streaming-message-transfer"></a>Strumieniowy transfer komunikatów
Transporty programu Windows Communication Foundation (WCF) obsługują dwa tryby przesyłania komunikatów:  
  
- Transfery buforowane przechowują całą wiadomość w buforze pamięci do momentu zakończenia transferu. Komunikat buforowany musi być całkowicie dostarczony przed odczytaniem przez odbiorcę.  
  
- Transfery przesyłane strumieniowo uwidaczniają komunikat jako strumień. Odbiorca zacznie przetwarzać komunikat, zanim zostanie on całkowicie dostarczony.  
  
- Transfery przesyłane strumieniowo mogą zwiększyć skalowalność usługi, eliminując konieczność stosowania dużych buforów pamięci. Bez względu na to, czy zmiana trybu transferu zwiększa skalowalność, zależy od rozmiaru transferowanych komunikatów. Duże rozmiary komunikatów preferują korzystanie z transferów przesyłanych strumieniowo.  
  
 Domyślnie transporty HTTP, TCP/IP i nazwanego potoku używają buforowanych transferów. W tym dokumencie opisano sposób przełączania tych transportów z buforowanego do trybu transferu strumieniowego i konsekwencji tego działania.  
  
## <a name="enabling-streamed-transfers"></a>Włączanie transferu strumieniowego  
 Wybór między trybami transferu buforowanego i przesyłanym strumieniowo odbywa się na elemencie powiązania transportu. Element Binding ma właściwość, <xref:System.ServiceModel.TransferMode> która może być ustawiona na `Buffered` , `Streamed` , `StreamedRequest` , lub `StreamedResponse` . Ustawienie trybu transferu w taki sposób, aby `Streamed` włączyć komunikację przesyłania strumieniowego w obu kierunkach. Ustawienie trybu transferu na `StreamedRequest` lub `StreamedResponse` umożliwia komunikację przesyłania strumieniowego tylko w określonym kierunku.  
  
 <xref:System.ServiceModel.BasicHttpBinding>Powiązania, <xref:System.ServiceModel.NetTcpBinding> , i <xref:System.ServiceModel.NetNamedPipeBinding> uwidaczniają <xref:System.ServiceModel.TransferMode> Właściwość. W przypadku innych transportów należy utworzyć niestandardowe powiązanie, aby ustawić tryb transferu.  
  
 Decyzja o użyciu buforowanych lub przesyłanych strumieniowo jest lokalną decyzją punktu końcowego. W przypadku transportów HTTP tryb transferu nie jest propagowany przez połączenie lub do serwerów i innych pośredników. Ustawienie trybu transferu nie jest odzwierciedlone w opisie interfejsu usługi. Po wygenerowaniu klasy klienta dla usługi należy edytować plik konfiguracji usług przeznaczonych do użycia z transferem strumieniowym w celu ustawienia trybu. W przypadku transportów TCP i nazwanych potoków tryb transferu jest propagowany jako potwierdzenie zasad.  
  
 Aby zapoznać się z przykładami kodu, zobacz [How to: Enable Streaming](how-to-enable-streaming.md).  
  
## <a name="enabling-asynchronous-streaming"></a>Włączanie przesyłania strumieniowego asynchronicznego  
 Aby włączyć asynchroniczne przesyłanie strumieniowe, Dodaj <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> zachowanie punktu końcowego do hosta usługi i ustaw jego <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> Właściwość na `true` .  
  
 Ta wersja programu WCF ADDE również możliwość wysyłania strumieniowych asynchronicznie na stronie wysyłającej. Poprawia to skalowalność usługi w scenariuszach, w których przesyła strumieniowo komunikaty do wielu klientów, z których niektóre są wolne do odczytu; prawdopodobnie z powodu przeciążenia sieci lub nie są w ogóle odczytywane. W tych scenariuszach usługa WCF nie blokuje już pojedynczych wątków w usłudze na klienta. Dzięki temu usługa może przetwarzać wielu kolejnych klientów w taki sposób, aby zwiększyć skalowalność usługi.  
  
## <a name="restrictions-on-streamed-transfers"></a>Ograniczenia dotyczące transferów przesyłanych strumieniowo  
 Użycie trybu transferu strumieniowego powoduje wymuszenie dodatkowych ograniczeń przez czas wykonywania.  
  
 Operacje wykonywane w ramach transportowego przesyłania strumieniowego mogą mieć kontrakt z co najwyżej jednym parametrem wejściowym lub wyjściowym. Ten parametr odnosi się do całej treści wiadomości i musi być <xref:System.ServiceModel.Channels.Message> typem pochodnym <xref:System.IO.Stream> lub <xref:System.Xml.Serialization.IXmlSerializable> implementacją. Posiadanie wartości zwracanej dla operacji jest równoważne z parametrem wyjściowym.  
  
 Niektóre funkcje WCF, takie jak niezawodne komunikaty, transakcje i zabezpieczenia na poziomie komunikatów protokołu SOAP, polegają na buforowaniu komunikatów przesyłanych. Korzystanie z tych funkcji może zmniejszyć lub wyeliminować korzyści wynikające z wydajności uzyskane przy użyciu przesyłania strumieniowego. Aby zabezpieczyć strumień przesyłanych strumieniowo, należy używać tylko zabezpieczeń na poziomie transportu lub zabezpieczeń na poziomie transportu oraz zabezpieczeń komunikatów opartych na uwierzytelnianiu.  
  
 Nagłówki protokołu SOAP są zawsze buforowane, nawet gdy tryb transferu jest ustawiony na przesyłanie strumieniowe. Nagłówki wiadomości nie mogą przekraczać rozmiaru `MaxBufferSize` przydziału transportowego. Aby uzyskać więcej informacji na temat tego ustawienia, zobacz [transport Transports](transport-quotas.md).  
  
## <a name="differences-between-buffered-and-streamed-transfers"></a>Różnice między buforowanym i przesyłanym strumieniowo transferem  
 Zmiana trybu transferu z buforowanego na strumień powoduje także zmianę kształtu kanału natywnego transportów TCP i nazwanego potoku. W przypadku transferów buforowanych kształt kanału natywnego to <xref:System.ServiceModel.Channels.IDuplexSessionChannel> . W przypadku transferów przesyłanych strumieniowo kanały natywne to <xref:System.ServiceModel.Channels.IRequestChannel> i <xref:System.ServiceModel.Channels.IReplyChannel> . Zmiana trybu transferu w istniejącej aplikacji, która używa tych transportów bezpośrednio (czyli nie przez kontrakt usługi) wymaga zmiany oczekiwanego kształtu kanału dla fabryk i odbiorników kanałów.  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: włączanie przesyłania strumieniowego](how-to-enable-streaming.md)
