---
title: 'Instrukcje: Włączanie przesyłania strumieniowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 1d1eaa1ebf41ef86478dda795b3b199239cd37b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184935"
---
# <a name="how-to-enable-streaming"></a>Instrukcje: Włączanie przesyłania strumieniowego
Windows Communication Foundation (WCF) może wysyłać wiadomości przy użyciu buforowanych lub przesyłanych strumieniowo. W domyślnym trybie buforowanego transferu wiadomość musi zostać całkowicie dostarczona, zanim odbiorca będzie mógł ją odczytać. W trybie przesyłania strumieniowego odbiorca może rozpocząć przetwarzanie wiadomości, zanim zostanie całkowicie dostarczona. Tryb przesyłania strumieniowego jest przydatne, gdy informacje, które są przekazywane jest długa i mogą być przetwarzane szeregowo. Tryb przesyłania strumieniowego jest również przydatne, gdy wiadomość jest zbyt duża, aby być całkowicie buforowane.  
  
 Aby włączyć przesyłanie `OperationContract` strumieniowe, należy zdefiniować odpowiednio i włączyć przesyłanie strumieniowe na poziomie transportu.  
  
### <a name="to-stream-data"></a>Aby przesyłać strumieniowo dane  
  
1. Aby przesyłać `OperationContract` strumieniowo dane, usługa musi spełniać dwa wymagania:  
  
    1. Parametr, który przechowuje dane do przesyłania strumieniowego musi być jedynym parametrem w metodzie. Na przykład jeśli komunikat wejściowy jest ten, który ma być przesyłany strumieniowo, operacja musi mieć dokładnie jeden parametr wejściowy. Podobnie jeśli komunikat wyjściowy ma być przesyłany strumieniowo, operacja musi mieć dokładnie jeden parametr wyjściowy lub wartość zwracaną.  
  
    2. Co najmniej jeden z typów parametru i wartości <xref:System.IO.Stream> <xref:System.ServiceModel.Channels.Message>zwracanej <xref:System.Xml.Serialization.IXmlSerializable>musi być albo , lub .  
  
     Poniżej przedstawiono przykład kontraktu dla przesyłanych strumieniowo danych.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     Operacja `GetStream` odbiera niektóre buforowane dane `string`wejściowe jako , który `Stream`jest buforowany i zwraca , który jest przesyłany strumieniowo. Z `UploadStream` drugiej strony `Stream` przyjmuje (przesyłane `bool` strumieniowo) i zwraca (buforowane). `EchoStream`pobiera i `Stream` zwraca i jest przykładem operacji, której komunikaty wejściowe i wyjściowe są przesyłane strumieniowo. Na koniec `GetReversedStream` nie pobiera żadnych `Stream` danych wejściowych i zwraca (przesyłane strumieniowo).  
  
2. Przesyłanie strumieniowe musi być włączone w powiązaniu. Można ustawić `TransferMode` właściwość, która może przyjmować jedną z następujących wartości:  
  
    1. `Buffered`,  
  
    2. `Streamed`, który umożliwia przesyłanie strumieniowe w obu kierunkach.  
  
    3. `StreamedRequest`, który umożliwia przesyłanie strumieniowe tylko żądania.  
  
    4. `StreamedResponse`, który umożliwia przesyłanie strumieniowe tylko odpowiedzi.  
  
     Udostępnia `BasicHttpBinding` `TransferMode` właściwość na powiązanie, `NetTcpBinding` podobnie `NetNamedPipeBinding`jak i . Właściwość `TransferMode` można również ustawić na element wiązania transportu i używane w niestandardowe powiązanie.  
  
     Poniższe przykłady pokazują, `TransferMode` jak ustawić za pomocą kodu i zmieniając plik konfiguracji. Przykłady również ustawić `maxReceivedMessageSize` właściwość do 64 MB, co umieszcza limit na maksymalny dozwolony rozmiar wiadomości na odbieranie. Wartość `maxReceivedMessageSize` domyślna to 64 KB, która jest zwykle zbyt niska dla scenariuszy przesyłania strumieniowego. Ustaw to ustawienie przydziału jako odpowiednie w zależności od maksymalnego rozmiaru wiadomości, które aplikacja oczekuje od otrzymania. Należy również `maxBufferSize` zauważyć, że kontroluje maksymalny rozmiar, który jest buforowany i ustawić go odpowiednio.  
  
    1. Poniższy fragment kodu konfiguracji z przykładu `TransferMode` pokazuje ustawienie `basicHttpBinding` właściwości do przesyłania strumieniowego na i niestandardowe powiązanie HTTP.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]
  
    2. Poniższy fragment kodu pokazuje ustawienie `TransferMode` właściwości do `basicHttpBinding` przesyłania strumieniowego na i niestandardowe powiązanie HTTP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. Poniższy fragment kodu pokazuje ustawienie `TransferMode` właściwości do przesyłania strumieniowego na niestandardowe powiązanie TCP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. Operacje `GetStream`, `UploadStream`i `EchoStream` wszystkie zajmują się wysyłaniem danych bezpośrednio z pliku lub zapisywania odebranych danych bezpośrednio do pliku. Poniższy kod `GetStream`jest dla .  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Zapisywanie strumienia niestandardowego  
  
1. Aby wykonać specjalne przetwarzanie na każdym fragmencie strumienia danych, który jest <xref:System.IO.Stream>wysyłany lub odbierany, należy wyprowadzić niestandardową klasę strumienia z pliku . Jako przykład strumienia niestandardowego poniższy `GetReversedStream` kod zawiera `ReverseStream` metodę i klasę.  
  
     `GetReversedStream`tworzy i zwraca nowe `ReverseStream`wystąpienie . Rzeczywiste przetwarzanie odbywa się w `ReverseStream` systemie odczytuje z obiektu. Metoda `ReverseStream.Read` odczytuje fragment bajtów z pliku źródłowego, odwraca je, a następnie zwraca odwrócone bajty. Ta metoda nie odwraca całej zawartości pliku; odwraca jeden fragment bajtów naraz. W tym przykładzie pokazano, jak można wykonać przetwarzanie strumienia, jak zawartość jest odczytywany lub zapisywany ze strumienia.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Duże ilości danych i przesyłanie strumieniowe](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
- [Strumień](../../../../docs/framework/wcf/samples/stream.md)
