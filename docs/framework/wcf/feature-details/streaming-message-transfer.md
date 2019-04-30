---
title: Strumieniowy transfer komunikatów
ms.date: 03/30/2017
ms.assetid: 72a47a51-e5e7-4b76-b24a-299d51e0ae5a
ms.openlocfilehash: e58b0ce698df310a5e18bcd24201fb2e27a9c1aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747579"
---
# <a name="streaming-message-transfer"></a>Strumieniowy transfer komunikatów
Transportów Windows Communication Foundation (WCF) obsługuje dwa tryby do przesyłania komunikatów:  
  
- Transfery buforowanego przytrzymaj cały komunikat w buforze pamięci, do czasu ukończenia transferu. Buforowane wiadomości musi być całkowicie dostarczana, zanim odbiorca może go odczytać.  
  
- Transfery przesyłane strumieniowo uwidocznić komunikatu jako strumień. Odbiornik uruchamia przetwarzania komunikatu, aby całkowicie został dostarczony.  
  
- Transfery przesyłane strumieniowo można poprawić skalowalność usługi, eliminując potrzebę dużej ilości pamięci, buforów. Czy zmiana trybu transferu zwiększa skalowalność, zależy od rozmiaru wiadomości przesyłane. Rozmiary dużych bloków komunikatów Preferuj przy użyciu transferu przesyłane strumieniowo.  
  
 Domyślnie HTTP, protokół TCP/IP i transportu nazwanego potoku używać buforowanego transferu. W tym dokumencie opisano, jak przełączyć te transportu z buforowanego tryb transferu przesyłane strumieniowo i konsekwencje tej czynności.  
  
## <a name="enabling-streamed-transfers"></a>Włączanie transfery przesyłane strumieniowo  
 Wybieranie między trybami buforowanego i przesyłane strumieniowo transfer odbywa się na element powiązania transportu. Element powiązania ma <xref:System.ServiceModel.TransferMode> właściwość, która może być równa `Buffered`, `Streamed`, `StreamedRequest`, lub `StreamedResponse`. Ustawienie trybu transferu `Streamed` umożliwia przesyłanie strumieniowe komunikacji w obu kierunkach. Ustawienie trybu transferu `StreamedRequest` lub `StreamedResponse` umożliwia przesyłanie strumieniowe komunikacji wskazany tylko w kierunku.  
  
 <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.NetTcpBinding>, I <xref:System.ServiceModel.NetNamedPipeBinding> udostępniają powiązania <xref:System.ServiceModel.TransferMode> właściwości. Dla innych transportu należy utworzyć niestandardowego powiązania, aby ustawić tryb transferu.  
  
 Decyzja dotycząca użycia buforowanego lub przesyłane strumieniowo transferu jest decyzja lokalnego punktu końcowego. Dla transportu HTTP tryb transferu nie propagować przez połączenie lub na serwerach i innych pośredników. Ustawianie trybu transferu nie zostaną uwzględnione w opisie interfejsu usługi. Po wygenerowaniu klasy klienta dla usługi, możesz edytować plik konfiguracji usługi przeznaczone do użycia w przypadku transferów przesyłane strumieniowo można ustawić trybu. Dla protokołu TCP i rodzajów transportu nazwanego potoku tryb transferu jest propagowany jako potwierdzenie zasad.  
  
 Aby uzyskać przykłady kodu, zobacz [jak: Włączanie przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md).  
  
## <a name="enabling-asynchronous-streaming"></a>Włączanie asynchronicznego przesyłania strumieniowego  
 Aby włączyć, asynchronicznego przesyłania strumieniowego, Dodaj <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> zachowanie punktu końcowego usługi hosta i ustaw jego <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> właściwość `true`.  
  
 Ta wersja programu WCF również adde możliwości true asynchronicznego przesyłania strumieniowego po stronie wysyłania. Poprawia skalowalność usługi w scenariuszach, gdzie jest strumienia komunikatów do wielu klientów, z których niektóre są powolne podczas odczytu; prawdopodobnie z powodu przeciążenia sieci lub są nie do czytania w ogóle. W tych scenariuszach WCF już nie blokuje określonych wątków w usłudze na klienta. Zapewnia to, że usługa jest w stanie do przetworzenia wiele większej liczby klientów, zwiększając w ten sposób skalowalność usługi.  
  
## <a name="restrictions-on-streamed-transfers"></a>Ograniczenia dotyczące transferu przesyłane strumieniowo  
 Przy użyciu trybu transferu przesyłane strumieniowo powoduje, że czas uruchomienia wymusić dodatkowe ograniczenia.  
  
 Operacje, które występują w strumieniu transportu może mieć kontrakt co najwyżej jeden wejściowych lub wyjściowych parametr. Ten parametr odnosi się do całej treści komunikatu i musi być <xref:System.ServiceModel.Channels.Message>, pochodne typu <xref:System.IO.Stream>, lub <xref:System.Xml.Serialization.IXmlSerializable> implementacji. Wartość zwracana dla operacji jest odpowiednikiem parametru wyjściowego.  
  
 Niektóre funkcje usługi WCF, takie jak niezawodną obsługę komunikatów, transakcje i zabezpieczenia na poziomie komunikatu protokołu SOAP, zależy od tego, buforowanie wiadomości dla transmisji. Za pomocą tych funkcji może być ograniczenie lub wyeliminowanie zalet wydajności przy użyciu przesyłania strumieniowego. Aby zabezpieczyć przesyłane strumieniowo transportu, tylko zabezpieczenia na poziomie transportu lub zabezpieczenia na poziomie transportu, a także zabezpieczeń wiadomości tylko do uwierzytelniania.  
  
 Nagłówków protokołu SOAP zawsze są buforowane, nawet wtedy, gdy tryb transferu jest ustawiony na przesyłane strumieniowo. Nagłówki komunikatu nie może przekraczać rozmiaru `MaxBufferSize` przydziału transportu. Aby uzyskać więcej informacji na temat tego ustawienia, zobacz [przydziały dla transportu](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
## <a name="differences-between-buffered-and-streamed-transfers"></a>Różnice między buforowanego i przesyłane strumieniowo transferu  
 Tryb transferu z buforowanego do strumieniowego również zmiana kształtu natywnych kanału TCP i transportu nazwanego potoku. Buforowanego transferu jest kształtu kanału natywnych <xref:System.ServiceModel.Channels.IDuplexSessionChannel>. W przypadku transferów przesyłane strumieniowo są natywne kanały <xref:System.ServiceModel.Channels.IRequestChannel> i <xref:System.ServiceModel.Channels.IReplyChannel>. Zmienianie trybu transferu w istniejącej aplikacji, która wykorzystuje te służy do transportu bezpośrednio (oznacza to, nie za pośrednictwem umowy serwisowej) wymaga zmiany kształtu kanału oczekiwany dla fabryki kanałów i odbiorników.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Włączanie przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
