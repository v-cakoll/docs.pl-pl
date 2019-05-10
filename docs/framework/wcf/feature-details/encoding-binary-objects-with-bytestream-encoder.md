---
title: Kodowanie obiektów binarnych za pomocą kodera elementu ByteStream
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 09a919e11971f81bc76dca0e45a7eb0e70ef749e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626925"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>Kodowanie obiektów binarnych za pomocą kodera elementu ByteStream
Wysyłanie i odbieranie nieprzetworzone dane binarne za pomocą programu Windows Communication Foundation (WCF) została skonfigurowana przy użyciu <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.  
  
## <a name="byte-stream-message-encoder-architecture"></a>Architektura kodera komunikatów Stream bajtów  
 Koder komunikatu binarnego używany przez usługę WCF nie ma żadnych funkcji do przetwarzania, sprawdzanie poprawności lub Identyfikowanie podstawowych danych binarnych w komunikacie. Pakiet danych jest zakodowany w formacie XML, wysyłane, odebrano i zdekodowane. Koder przetwarza dane po przekazywany do transportu i przed wysłaniem wiadomości do kolejki komunikatów. Funkcjonalnie kodera binarnego jest zawijany dane wiadomości w `<binary>` elementy do wysyłania i usuwa elementy po otrzymaniu komunikatu.  
  
## <a name="using-the-byte-stream-message-encoder"></a>Przy użyciu kodera komunikatów Stream bajtów  
 Poniższy przykład zawiera kontrakt usługi, która implementuje koder komunikatów strumienia bajtów.  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 Poniższy przykład pokazuje usługi wywoływana.  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 W przypadku usługi, który implementuje infrastrukturze komunikatu (na przykład router), komunikat jest przetwarzany bez sprawdzania, sprawdzanie poprawności lub inny sposób interakcji z wiadomością, jak pokazano w poniższym przykładzie.  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a>Scenariusze  
 Koder Stream bajt jest przydatne w następujących scenariuszach.  
  
- Przenoszenie obrazu JPEG między komputerami przy użyciu usługi WCF. W tym scenariuszu obrazu zostaną dostarczone za pomocą transportu ze źródła zewnętrznego, a dane wysłane będzie pierwotne bajtów, które składają się na obrazie. Usługa będzie odbierać dane binarne i wyświetlić obraz.  
  
- Odczytywanie informacji poza kolejki komunikatów i przetwarza go. Komunikat będzie odczytywać menedżera kolejki komunikatów i przekazywane kanał kolejki wiadomości do obsłużenia. Kanał wiadomości w kolejce będzie pełnił rolę menedżera kolejki w stosie kanału WCF.  
  
 W przypadku wysyłania komunikatu za pośrednictwem kanału kolejki komunikatów, nadawca nie ma kontroli nad bajtów odebranych przez menedżera kolejki. Odbieranie proces ma możliwość odczytywania bajtów raw, wiadomości będą odbierane nieprawidłowo sformatowane, a nie będą przetwarzane; zakłada się, że proces odbierania możliwości tłumaczenia odebranych bajtów do miał format.
