---
title: "Strumieniowy transfer komunikatów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72a47a51-e5e7-4b76-b24a-299d51e0ae5a
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ff9cedb589b9df79e17efcedc783938cc3c6647e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="streaming-message-transfer"></a>Strumieniowy transfer komunikatów
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]transport obsługuje dwa tryby przesyłania komunikatów:  
  
-   Transfery buforowanego przytrzymaj cały komunikat w buforze pamięci przed zakończeniem transferu. Buforowane wiadomości musi być całkowicie dostarczana przed odbiorca może go odczytać.  
  
-   Transfery przesyłanej strumieniowo ujawnia komunikatu jako strumień. Odbiornik rozpoczyna przetwarzanie komunikatu przed przekazaniem całkowicie.  
  
-   Transfery przesyłanej strumieniowo może zwiększyć skalowalność usługi, eliminując konieczność buforów dużej ilości pamięci. Czy zmienić tryb transferu zwiększa skalowalność, zależy od rozmiaru wiadomości przesyłane. Komunikat duże rozmiary Preferuj przy użyciu transferu przesyłany strumieniowo.  
  
 Domyślnie HTTP, TCP/IP i transportu nazwanego potoku używa buforowanego transferów. Ten dokument zawiera opis sposobu przełącznika te transportu z buforowanego tryb transmisji strumieniowej i skutków w ten sposób.  
  
## <a name="enabling-streamed-transfers"></a>Włączanie przesyłanej strumieniowo transferu  
 Wybieranie między trybami transmisji buforowanego i przesyłany strumieniowo odbywa się w elemencie powiązania transportu. Element powiązania ma <xref:System.ServiceModel.TransferMode> właściwość, która może być ustawiony na `Buffered`, `Streamed`, `StreamedRequest`, lub `StreamedResponse`. Ustawienie Tryb transferu `Streamed` umożliwia przesyłanie strumieniowe komunikacji w obu kierunkach. Ustawienie Tryb transferu `StreamedRequest` lub `StreamedResponse` umożliwia przesyłanie strumieniowe komunikacji w wybranym kierunku tylko.  
  
 <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.NetTcpBinding>, I <xref:System.ServiceModel.NetNamedPipeBinding> Uwidacznianie powiązania <xref:System.ServiceModel.TransferMode> właściwości. Dla innych transportu należy utworzyć niestandardowego powiązania, aby ustawić tryb transferu.  
  
 Decyzja o wykorzystaniu buforowane lub przesyłany strumieniowo transferu jest decyzji lokalnego punktu końcowego. Dla transportu HTTP tryb transferu nie propaguje przez połączenie lub na serwerach i innych pośredników. Ustawianie trybu transferu nie zostaną uwzględnione w opisie interfejsu usługi. Po wygenerowaniu klasy klienta dla usługi, musi edycję pliku konfiguracyjnego dla usług przeznaczony do użycia w przypadku transferów przesyłanej strumieniowo można ustawić trybu. Dla transportu nazwanego potoku i TCP tryb transferu jest propagowana jako potwierdzenia zasad.  
  
 Aby uzyskać przykłady kodu, zobacz [porady: Włączanie przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md).  
  
## <a name="enabling-asynchronous-streaming"></a>Włączanie asynchronicznego przesyłania strumieniowego  
 Aby włączyć, asynchronicznego przesyłania strumieniowego, Dodaj <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior> zachowania punktu końcowego usługi hosta i ustaw jej <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.AsynchronousSendEnabled%2A> właściwości `true`.  
  
 Ta wersja programu WCF również adde możliwości wartość true, asynchronicznego przesyłania strumieniowego po stronie wysyłającej. Zwiększa skalowalność usługi w scenariuszach, w którym jest strumienia komunikatów do wielu klientów, niektóre z nich są przetwarzane wolno podczas odczytywania; prawdopodobnie z powodu przeciążenia sieci lub czy nie odczytu w ogóle. W tych scenariuszach WCF nie blokuje poszczególnych wątków w usłudze na klienta. Dzięki temu, że usługa jest w stanie przetwarzać wiele większej liczby klientów w celu poprawy skalowalności usługi.  
  
## <a name="restrictions-on-streamed-transfers"></a>Ograniczenia dotyczące transferów przesyłanej strumieniowo  
 Przy użyciu tryb transmisji strumieniowej powoduje, że czas uruchomienia wymusić dodatkowe ograniczenia.  
  
 Operacje występujących między przesyłanej strumieniowo transportu może mieć kontrakt co najwyżej jeden wejściowych lub wyjściowych parametr. Ten parametr odpowiada całej treści wiadomości i musi być <xref:System.ServiceModel.Channels.Message>, typu pochodnego <xref:System.IO.Stream>, lub <xref:System.Xml.Serialization.IXmlSerializable> implementacji. Wartość zwracana operacji o jest odpowiednikiem o parametru wyjściowego.  
  
 Niektóre [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkcje, takie jak niezawodna obsługa komunikatów, transakcje i zabezpieczenia na poziomie komunikatu protokołu SOAP, zależą od tego, buforowanie wiadomości transmisji. Korzystanie z tych funkcji mogą ograniczenie lub wyeliminowanie zalet wydajności przy użyciu przesyłania strumieniowego. Aby zabezpieczyć przesyłanej strumieniowo transportu, użyj tylko zabezpieczenia na poziomie transportu lub zabezpieczenia na poziomie transportu plus zabezpieczeń wiadomości tylko do uwierzytelniania.  
  
 Nagłówki SOAP zawsze są buforowane, nawet wtedy, gdy tryb transferu jest ustawiony na przesyłanej strumieniowo. Nagłówki wiadomości nie może przekraczać wielkości `MaxBufferSize` przydziału transportu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]to ustawienie, zobacz [przydziały dla transportu](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
## <a name="differences-between-buffered-and-streamed-transfers"></a>Różnice między buforowanego i przesyłany strumieniowo transferu  
 Tryb transferu z buforowanego do strumieniowego również zmiana kształtu natywnego kanału TCP i transportu nazwanego potoku. Transferów buforowany, jest kształtu kanału natywnego <xref:System.ServiceModel.Channels.IDuplexSessionChannel>. Transferów przesyłany strumieniowo, są natywnego kanały <xref:System.ServiceModel.Channels.IRequestChannel> i <xref:System.ServiceModel.Channels.IReplyChannel>. Zmienianie trybu transferu w istniejących aplikacji, która wykorzystuje te transporty bezpośrednio (to znaczy nie za pomocą kontraktu usługi) konieczna jest zmiana kształtu kanału oczekiwanego fabryk kanałów i odbiorników.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Włączanie przesyłania strumieniowego](../../../../docs/framework/wcf/feature-details/how-to-enable-streaming.md)
