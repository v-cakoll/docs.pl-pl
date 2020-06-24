---
title: 'Instrukcje: Włączanie przesyłania strumieniowego'
description: Dowiedz się, jak włączyć przesyłanie strumieniowe komunikatów w programie WCF zamiast domyślnych transferów buforowanych, które muszą zostać całkowicie odebrane przed przetworzeniem.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 538fd8634094aa6fbf097ddb94469d7bca749a63
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247029"
---
# <a name="how-to-enable-streaming"></a>Instrukcje: Włączanie przesyłania strumieniowego
Windows Communication Foundation (WCF) może wysyłać komunikaty przy użyciu buforowanych lub przesyłanych strumieniowo transferów. W domyślnym trybie transferu buforowanego komunikat musi zostać całkowicie dostarczony przed odczytaniem przez odbiorcę. W trybie transferu strumieniowego odbiorca może zacząć przetwarzać komunikat, zanim zostanie on całkowicie dostarczony. Tryb przesyłania strumieniowego jest przydatny, gdy przesyłane informacje są długie i mogą być przetwarzane sekwencyjnie. Tryb przesyłania strumieniowego jest również przydatny, gdy komunikat jest zbyt duży, aby był całkowicie buforowany.  
  
 Aby włączyć przesyłanie strumieniowe, zdefiniuj odpowiednie `OperationContract` i Włącz przesyłanie strumieniowe na poziomie transportu.  
  
### <a name="to-stream-data"></a>Aby przesłać strumieniowo dane  
  
1. Aby przesłać strumieniowo dane, `OperationContract` dla usługi muszą być spełnione dwa wymagania:  
  
    1. Parametr, który przechowuje dane przeznaczone do przesyłania strumieniowego, musi być jedynym parametrem w metodzie. Na przykład jeśli komunikat wejściowy jest przesyłany strumieniowo, operacja musi mieć dokładnie jeden parametr wejściowy. Podobnie, jeśli wiadomość wyjściowa ma być przesyłana strumieniowo, operacja musi mieć dokładnie jeden parametr wyjściowy lub wartość zwracaną.  
  
    2. Co najmniej jeden z typów parametru i zwracanej wartości musi być albo <xref:System.IO.Stream> , <xref:System.ServiceModel.Channels.Message> lub <xref:System.Xml.Serialization.IXmlSerializable> .  
  
     Poniżej znajduje się przykład kontraktu dla danych przesyłanych strumieniowo.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     `GetStream`Operacja otrzymuje pewne buforowane dane wejściowe jako `string` , które są buforowane i zwraca obiekt `Stream` , który jest przesyłany strumieniowo. Odwrotnie `UploadStream` przyjmuje `Stream` (przesyłane strumieniowo) i zwraca `bool` (buforowana). `EchoStream`przyjmuje i zwraca `Stream` i jest przykładem operacji, której przesyłanie strumieniowe danych wejściowych i wyjściowych odbywa się jednocześnie. Na koniec `GetReversedStream` nie przyjmuje danych wejściowych i zwraca `Stream` (strumieniowo).  
  
2. W powiązaniu musi być włączone przesyłanie strumieniowe. Ustawiasz `TransferMode` Właściwość, która może przyjmować jedną z następujących wartości:  
  
    1. `Buffered`,  
  
    2. `Streamed`, co umożliwia komunikację przesyłania strumieniowego w obu kierunkach.  
  
    3. `StreamedRequest`, co umożliwia przesyłanie strumieniowe tylko żądania.  
  
    4. `StreamedResponse`, co umożliwia przesyłanie strumieniowe tylko odpowiedzi.  
  
     `BasicHttpBinding`Uwidacznia `TransferMode` Właściwość dla powiązania, tak jak `NetTcpBinding` i `NetNamedPipeBinding` . `TransferMode`Właściwość można również ustawić dla elementu powiązania transportu i użyć w niestandardowym powiązaniu.  
  
     W poniższych przykładach pokazano, jak ustawić `TransferMode` kod i zmienić plik konfiguracji. Te próbki również ustawiają `maxReceivedMessageSize` Właściwość na 64 MB, co powoduje umieszczenie limitu maksymalnego dozwolonego rozmiaru komunikatów podczas odbierania. Wartość domyślna `maxReceivedMessageSize` to 64 KB, która jest zwykle zbyt niska dla scenariuszy przesyłania strumieniowego. Ustaw odpowiednie ustawienie limitu przydziału w zależności od maksymalnego rozmiaru komunikatów, które oczekuje na otrzymywanie przez aplikację. Należy również zauważyć, że `maxBufferSize` steruje maksymalnym rozmiarem buforowanym i odpowiednio go ustawia.  
  
    1. Poniższy fragment konfiguracji z przykładu przedstawia Ustawianie `TransferMode` właściwości na potrzeby przesyłania strumieniowego `basicHttpBinding` i NIESTANDARDOWEGO powiązania HTTP.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]
  
    2. Poniższy fragment kodu przedstawia Ustawianie `TransferMode` właściwości na potrzeby przesyłania strumieniowego `basicHttpBinding` i NIESTANDARDOWEGO powiązania HTTP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. Poniższy fragment kodu przedstawia Ustawianie `TransferMode` właściwości na potrzeby przesyłania strumieniowego na niestandardowe powiązanie TCP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. Operacje `GetStream` , `UploadStream` i wszystkie związane `EchoStream` z wysyłaniem danych bezpośrednio z pliku lub zapisywanie danych odebranych bezpośrednio do pliku. Poniższy kod dotyczy `GetStream` .  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Pisanie strumienia niestandardowego  
  
1. Aby wykonać specjalne przetwarzanie każdego fragmentu strumienia danych w trakcie jego wysyłania lub odbierania, Utwórz niestandardową klasę strumienia <xref:System.IO.Stream> . Jako przykład niestandardowego strumienia, poniższy kod zawiera `GetReversedStream` metodę i `ReverseStream` klasę-.  
  
     `GetReversedStream`tworzy i zwraca nowe wystąpienie `ReverseStream` . Rzeczywiste przetwarzanie odbywa się, gdy system odczytuje z `ReverseStream` obiektu. `ReverseStream.Read`Metoda odczytuje fragmenty bajtów z pliku bazowego, odwraca je, a następnie zwraca odwrócone bajty. Ta metoda nie powoduje odwrócenia całej zawartości pliku; powoduje odwrócenie jednego fragmentu bajtów w danym momencie. Ten przykład pokazuje, jak można wykonać przetwarzanie strumienia, ponieważ zawartość jest odczytywana lub zapisywana ze strumienia.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Duże ilości danych i przesyłanie strumieniowe](large-data-and-streaming.md)
- [Strumień](../samples/stream.md)
