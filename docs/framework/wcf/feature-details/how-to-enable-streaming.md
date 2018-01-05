---
title: "Instrukcje: Włączanie przesyłania strumieniowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b75fe67d99fa611f248c8d5dbb779f47e2bc717d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-streaming"></a>Instrukcje: Włączanie przesyłania strumieniowego
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]można wysyłać wiadomości przy użyciu transferu buforowane lub przesyłany strumieniowo. W domyślnym trybie buforowane transferu wiadomości musi być całkowicie dostarczana przed odbiorca może go odczytać. W tryb przesyłania strumieniowego odbiornika można rozpocząć przetworzyć komunikatu przed przekazaniem całkowicie. Tryb strumieniowy jest przydatne, gdy informacje przekazywane jest obszerne i mogą być przetwarzane pojedynczo. Tryb strumieniowy jest również przydatne, gdy komunikat jest zbyt duży, aby całkowicie buforowany.  
  
 Do przesyłania strumieniowego, zdefiniuj `OperationContract` odpowiednio i przesyłania strumieniowego na poziomie transportu.  
  
### <a name="to-stream-data"></a>Do transmisji danych  
  
1.  Do transmisji danych `OperationContract` dla usługi muszą spełniać dwóch wymagań:  
  
    1.  Parametr, która przechowuje dane przesyłane strumieniowo musi być tylko parametru w metodzie. Na przykład jeśli komunikat wejściowy jest przesyłane strumieniowo, operacja musi mieć dokładnie jeden parametr wejściowy. Podobnie w przypadku komunikatu wyjściowego strumieniowe przesyłanie, operacja musi mieć dokładnie jeden wyjściowy parametru lub wartości zwracanej.  
  
    2.  Co najmniej jeden z typów parametru i zwracane wartości musi być równa albo <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, lub <xref:System.Xml.Serialization.IXmlSerializable>.  
  
     Oto przykład kontraktu danych przesyłany strumieniowo.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     `GetStream` Operacji odbiera niektórych buforowanych danych wejściowych jako `string`, które są buforowane oraz zwraca `Stream`, który przesyłane strumieniowo. Z drugiej strony `UploadStream` przyjmuje `Stream` (przesyłane strumieniowo) i zwraca `bool` (buforowanej). `EchoStream`pobiera i zwraca `Stream` jest przykładem operacji których dane wejściowe i komunikaty wyjściowe zarówno strumieniowo. Na koniec `GetReversedStream` przyjmuje nie dane wejściowe i zwraca `Stream` (przesyłane strumieniowo).  
  
2.  Przesyłania strumieniowego musi być włączony dla powiązania. Możesz ustawić `TransferMode` właściwości, które można wykonać jedną z następujących wartości:  
  
    1.  `Buffered`,  
  
    2.  `Streamed`, które umożliwia komunikację przesyłania strumieniowego w obu kierunkach.  
  
    3.  `StreamedRequest`, która umożliwia strumieniowe przesyłanie tylko żądania.  
  
    4.  `StreamedResponse`, która umożliwia strumieniowe przesyłanie tylko odpowiedź.  
  
     `BasicHttpBinding` Przedstawia `TransferMode` właściwość powiązanie, tak jak w przypadku `NetTcpBinding` i `NetNamedPipeBinding`. `TransferMode` Właściwości można także ustawić w elemencie powiązania transportu i używane do niestandardowego powiązania.  
  
     Poniższe przykłady pokazują, jak ustawić `TransferMode` przez kod i zmieniając pliku konfiguracji. Przykłady również ustawione `maxReceivedMessageSize` odbierania właściwości 64 MB, co powoduje zakończenie na maksymalny dozwolony rozmiar wiadomości w. Wartość domyślna `maxReceivedMessageSize` wynosi 64 KB, który zazwyczaj jest zbyt stara przesyłania strumieniowego scenariuszy. Określ odpowiednie w zależności od maksymalny rozmiar wiadomości, których aplikacja oczekuje na odbieranie to ustawienie limitu przydziału. Należy również zauważyć, że `maxBufferSize` określa maksymalny rozmiar, który jest buforowany i odpowiednio ją ustawić.  
  
    1.  Poniższy fragment konfiguracji z próbki pokazuje ustawienie `TransferMode` właściwości do przesyłania strumieniowego na `basicHttpBinding` i niestandardowego powiązania protokołu HTTP.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]   
  
    2.  Poniższy fragment kodu przedstawia ustawienie `TransferMode` właściwości do przesyłania strumieniowego na `basicHttpBinding` i niestandardowego powiązania protokołu HTTP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3.  Poniższy fragment kodu przedstawia ustawienie `TransferMode` właściwości do przesyłania strumieniowego na niestandardowego powiązania protokołu TCP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3.  Operacje `GetStream`, `UploadStream`, i `EchoStream` wszystkie postępowania w przypadku wysyłania danych bezpośrednio z pliku lub zapisywanie odebranych danych bezpośrednio w pliku. Poniższy kod jest przeznaczony dla `GetStream`.  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Pisanie niestandardowych strumieni  
  
1.  Aby wykonywać specjalnego przetwarzania dla każdego fragmentu strumień danych jest wysyłane lub odbierane, klasa wyprowadzona z niestandardowych strumieni <xref:System.IO.Stream>. Na przykład niestandardowych strumieni poniższy kod zawiera `GetReversedStream` — metoda i `ReverseStream` klasy —.  
  
     `GetReversedStream`Tworzy i zwraca nowe wystąpienie klasy `ReverseStream`. Aktualnie przetwarzanego się stanie, jak system odczytuje z `ReverseStream` obiektu. `ReverseStream.Read` Metoda odczytuje fragmentu bajtów z pliku źródłowego, odwraca je, a następnie zwraca odwróconej bajtów. Ta metoda nie wstecznego zawartości całego pliku; Odwraca ono jednym fragmencie bajtów w czasie. W tym przykładzie pokazano, jak wykonać przetwarzającym strumień zawartości jest do odczytu lub zapisu ze strumienia.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Duże ilości danych i przesyłanie strumieniowe](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 [Strumień](../../../../docs/framework/wcf/samples/stream.md)
