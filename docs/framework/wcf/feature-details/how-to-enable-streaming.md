---
title: 'Instrukcje: Włączanie przesyłania strumieniowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 2521b6ac237a76cac64cebca91bbaa792bba2c67
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627658"
---
# <a name="how-to-enable-streaming"></a>Instrukcje: Włączanie przesyłania strumieniowego
Windows Communication Foundation (WCF) można wysyłać wiadomości przy użyciu transferu buforowane lub przesyłane strumieniowo. W domyślny tryb zbuforowany transferu wiadomości musi być całkowicie dostarczana przed odbiorca może go odczytać. W transmisji strumieniowej tryb transferu, można rozpocząć przetworzyć komunikatu przed przekazaniem całkowicie odbiornika. Tryb przesyłania strumieniowego jest przydatne, gdy informacje jest przekazywany jest długi i mogą być przetwarzane pojedynczo. Tryb przesyłania strumieniowego jest również przydatne, gdy komunikat jest zbyt duży, aby całkowicie buforowany.  
  
 Włączanie przesyłania strumieniowego, należy zdefiniować `OperationContract` odpowiednio i włączanie przesyłania strumieniowego na poziomie transportu.  
  
### <a name="to-stream-data"></a>Przesyłanie strumieniowe danych  
  
1.  Przesyłanie strumieniowe danych `OperationContract` dla usługi musi spełnić dwa wymagania:  
  
    1.  Parametr, który przechowuje dane, które mają być przesyłane strumieniowo musi być jedynym parametrem w metodzie. Na przykład jeśli komunikat wejściowy jest repliką strumieniowe przesyłanie, operacja musi mieć dokładnie jeden parametr wejściowy. Podobnie jeśli komunikat wyjściowy jest przesyłane strumieniowo, operacja musi mieć dokładnie jeden wyjściowy parametru lub wartości zwracanej.  
  
    2.  Co najmniej jeden z typów wartości parametrów i zwrotu musi być albo <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, lub <xref:System.Xml.Serialization.IXmlSerializable>.  
  
     Oto przykład umowę na strumieniu danych.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     `GetStream` Operacja odbiera niektórych buforowanych danych wejściowych jako `string`, które są buforowane, a następnie zwraca `Stream`, który jest przesyłany strumieniowo. Z drugiej strony `UploadStream` przyjmuje `Stream` (przesyłane strumieniowo) i zwraca `bool` (buforowanej). `EchoStream` przyjmuje i zwraca `Stream` jest przykładem operacji, których dane wejściowe i wyjściowe komunikaty są zarówno przesyłane strumieniowo. Na koniec `GetReversedStream` nie dane wejściowe przyjmuje i zwraca `Stream` (przesyłane strumieniowo).  
  
2.  Przesyłania strumieniowego musi być włączona w powiązaniu. Możesz ustawić `TransferMode` właściwość, która może mieć jedną z następujących wartości:  
  
    1.  `Buffered`,  
  
    2.  `Streamed`, która umożliwia komunikację przesyłania strumieniowego w obu kierunkach.  
  
    3.  `StreamedRequest`, która umożliwia przesyłanie strumieniowe żądania tylko.  
  
    4.  `StreamedResponse`, który umożliwia przesyłanie strumieniowe tylko odpowiedź.  
  
     `BasicHttpBinding` Udostępnia `TransferMode` właściwości powiązania, tak jak `NetTcpBinding` i `NetNamedPipeBinding`. `TransferMode` Właściwości można również ustawić dla elementu powiązania transportu i używać w niestandardowym powiązaniu.  
  
     Poniższe przykłady pokazują, jak ustawić `TransferMode` według kodu oraz zmian w pliku konfiguracji. Przykłady również ustawiają `maxReceivedMessageSize` otrzymywać właściwość 64 MB, co powoduje dzienny limit maksymalny dozwolony rozmiar wiadomości. Wartość domyślna `maxReceivedMessageSize` wynosi 64 KB, który zwykle jest zbyt mała dla przesyłania strumieniowego scenariuszy. Ustaw ustawienie limitu przydziału, zgodnie z potrzebami, w zależności od tego, maksymalny rozmiar wiadomości, które Twoja aplikacja oczekuje otrzymać. Należy również zauważyć, że `maxBufferSize` określa maksymalny rozmiar, który jest buforowana i odpowiednio ją ustawić.  
  
    1.  Poniższy fragment konfiguracji z przykładu przedstawia ustawienia `TransferMode` właściwości do przesyłania strumieniowego na `basicHttpBinding` i niestandardowego powiązania protokołu HTTP.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]   
  
    2.  Poniższy fragment kodu przedstawia ustawienia `TransferMode` właściwości do przesyłania strumieniowego na `basicHttpBinding` i niestandardowego powiązania protokołu HTTP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3.  Poniższy fragment kodu przedstawia ustawienia `TransferMode` właściwości do przesyłania strumieniowego na niestandardowego powiązania protokołu TCP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3.  Operacje `GetStream`, `UploadStream`, i `EchoStream` wszystko zaradzenia wysyłanie danych bezpośrednio z pliku lub zapisywania odebranych danych bezpośrednio do pliku. Poniższy kod jest `GetStream`.  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Zapisywanie niestandardowych strumienia  
  
1.  Specjalnego przetwarzania każdego fragmentu strumienia danych podczas ich przesyłania lub odebraniu wyprowadzić klasę niestandardowe strumienia z <xref:System.IO.Stream>. Na przykład niestandardowe strumienia poniższy kod zawiera `GetReversedStream` metody i `ReverseStream` klasy —.  
  
     `GetReversedStream` Tworzy i zwraca nowe wystąpienie klasy `ReverseStream`. Rzeczywiste przetwarzanie odbywa się zgodnie z system odczytuje z `ReverseStream` obiektu. `ReverseStream.Read` Metoda odczytuje fragmentów bajtów z pliku podstawowego, cofa ich, a następnie zwraca bajtów odwróconej. Ta metoda nie odwrotnego zawartości całego pliku; Odwraca ono jednym fragmencie bajtów w danym momencie. W tym przykładzie przedstawiono sposób wykonywania przetwarzania strumienia, ponieważ zawartość jest do odczytu lub zapisu ze strumienia.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Zobacz także
- [Duże ilości danych i przesyłanie strumieniowe](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
- [Strumień](../../../../docs/framework/wcf/samples/stream.md)
