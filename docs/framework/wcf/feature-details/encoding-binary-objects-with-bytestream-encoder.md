---
title: "Kodowanie obiektów binarnych za pomocą kodera elementu ByteStream"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: acf9d2ace66702c5f0bc522d97ae92869891a38b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>Kodowanie obiektów binarnych za pomocą kodera elementu ByteStream
Wysyłanie i odbieranie nieprzetworzone dane binarne z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] jest konfigurowana przy użyciu <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.  
  
## <a name="byte-stream-message-encoder-architecture"></a>Architektura kodera wiadomości strumień bajtów  
 Używane przez koder komunikatów binarnych [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ma nie funkcje przetwarzania, sprawdzanie poprawności lub identyfikowanie danych binarnych w komunikacie. Pakiet danych jest zakodowany w formacie XML, wysyłane odebranych i zdekodowane. Koder przetwarza dane po przekazywany do transportu i przed wysłaniem wiadomości do kolejki wiadomości. Funkcjonalnie kodera binarnego koduje dane wiadomości w `<binary>` elementy do wysyłania i usuwa elementy po odebraniu komunikatu.  
  
## <a name="using-the-byte-stream-message-encoder"></a>Za pomocą kodera wiadomości strumień bajtów  
 W poniższym przykładzie przedstawiono kontraktu usługi, który implementuje kodera wiadomości strumienia bajtów.  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 Poniższy przykład przedstawia wywoływanie usługi.  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 W przypadku przy użyciu usługa, która implementuje infrastrukturze wiadomości (na przykład router), komunikat jest przetwarzany bez sprawdzania, sprawdzanie poprawności lub inny sposób interakcji z komunikatu, jak pokazano w poniższym przykładzie.  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a>Scenariusze  
 Koder strumień bajtów jest przydatne w następujących scenariuszach.  
  
-   Przesyłanie obrazu JPEG między komputerami za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. W tym scenariuszu obraz pojawią się za pomocą transportu ze źródła zewnętrznego, a dane przesyłane będzie raw bajtów, które tworzą obrazu. Usługi będzie odbierać dane binarne i wyświetlić obraz.  
  
-   Odczytywanie informacji poza kolejki komunikatów i jego przetwarzanie. Komunikat będzie odczytywać menedżera kolejki komunikatów i przekazywane kanał kolejki wiadomości mają być obsługiwane. Kanał wiadomości w kolejce będzie pełnił rolę menedżera kolejki w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] stosu kanału.  
  
 W przypadku wysyłania wiadomości kanałem kolejki komunikatów, nadawca nie ma kontroli nad bajtów odebranych z menedżera kolejek. Odbierania proces nie ma funkcji do odczytywania bajtów raw, wiadomość zostanie odebrana nieprawidłowo sformatowane i nie będą przetwarzane; zakłada się, że proces odbierania możliwości tłumaczenia odebrane bajty do można używać formatu.
