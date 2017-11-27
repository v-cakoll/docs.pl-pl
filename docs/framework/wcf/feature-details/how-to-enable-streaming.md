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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8436ceefea936ddbf708aa3f79c5f7bd8153ac66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-streaming"></a><span data-ttu-id="7c2b6-102">Instrukcje: Włączanie przesyłania strumieniowego</span><span class="sxs-lookup"><span data-stu-id="7c2b6-102">How to: Enable Streaming</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="7c2b6-103">można wysyłać wiadomości przy użyciu transferu buforowane lub przesyłany strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-103"> can send messages using either buffered or streamed transfers.</span></span> <span data-ttu-id="7c2b6-104">W domyślnym trybie buforowane transferu wiadomości musi być całkowicie dostarczana przed odbiorca może go odczytać.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-104">In the default buffered-transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="7c2b6-105">W tryb przesyłania strumieniowego odbiornika można rozpocząć przetworzyć komunikatu przed przekazaniem całkowicie.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-105">In streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="7c2b6-106">Tryb strumieniowy jest przydatne, gdy informacje przekazywane jest obszerne i mogą być przetwarzane pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-106">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="7c2b6-107">Tryb strumieniowy jest również przydatne, gdy komunikat jest zbyt duży, aby całkowicie buforowany.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-107">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
 <span data-ttu-id="7c2b6-108">Do przesyłania strumieniowego, zdefiniuj `OperationContract` odpowiednio i przesyłania strumieniowego na poziomie transportu.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-108">To enable streaming, define the `OperationContract` appropriately and enable streaming at the transport level.</span></span>  
  
### <a name="to-stream-data"></a><span data-ttu-id="7c2b6-109">Do transmisji danych</span><span class="sxs-lookup"><span data-stu-id="7c2b6-109">To stream data</span></span>  
  
1.  <span data-ttu-id="7c2b6-110">Do transmisji danych `OperationContract` dla usługi muszą spełniać dwóch wymagań:</span><span class="sxs-lookup"><span data-stu-id="7c2b6-110">To stream data, the `OperationContract` for the service must satisfy two requirements:</span></span>  
  
    1.  <span data-ttu-id="7c2b6-111">Parametr, która przechowuje dane przesyłane strumieniowo musi być tylko parametru w metodzie.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-111">The parameter that holds the data to be streamed must be the only parameter in the method.</span></span> <span data-ttu-id="7c2b6-112">Na przykład jeśli komunikat wejściowy jest przesyłane strumieniowo, operacja musi mieć dokładnie jeden parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-112">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="7c2b6-113">Podobnie w przypadku komunikatu wyjściowego strumieniowe przesyłanie, operacja musi mieć dokładnie jeden wyjściowy parametru lub wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-113">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span>  
  
    2.  <span data-ttu-id="7c2b6-114">Co najmniej jeden z typów parametru i zwracane wartości musi być równa albo <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, lub <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-114">At least one of the types of the parameter and return value must be either <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, or <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
     <span data-ttu-id="7c2b6-115">Oto przykład kontraktu danych przesyłany strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-115">The following is an example of a contract for streamed data.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     <span data-ttu-id="7c2b6-116">`GetStream` Operacji odbiera niektórych buforowanych danych wejściowych jako `string`, które są buforowane oraz zwraca `Stream`, który przesyłane strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-116">The `GetStream` operation receives some buffered input data as a `string`, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="7c2b6-117">Z drugiej strony `UploadStream` przyjmuje `Stream` (przesyłane strumieniowo) i zwraca `bool` (buforowanej).</span><span class="sxs-lookup"><span data-stu-id="7c2b6-117">Conversely `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="7c2b6-118">`EchoStream`pobiera i zwraca `Stream` jest przykładem operacji których dane wejściowe i komunikaty wyjściowe zarówno strumieniowo.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-118">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="7c2b6-119">Na koniec `GetReversedStream` przyjmuje nie dane wejściowe i zwraca `Stream` (przesyłane strumieniowo).</span><span class="sxs-lookup"><span data-stu-id="7c2b6-119">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
2.  <span data-ttu-id="7c2b6-120">Przesyłania strumieniowego musi być włączony dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-120">Streaming must be enabled on the binding.</span></span> <span data-ttu-id="7c2b6-121">Możesz ustawić `TransferMode` właściwości, które można wykonać jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="7c2b6-121">You set a `TransferMode` property, which can take one of the following values:</span></span>  
  
    1.  <span data-ttu-id="7c2b6-122">`Buffered`,</span><span class="sxs-lookup"><span data-stu-id="7c2b6-122">`Buffered`,</span></span>  
  
    2.  <span data-ttu-id="7c2b6-123">`Streamed`, które umożliwia komunikację przesyłania strumieniowego w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-123">`Streamed`, which enables streaming communication in both directions.</span></span>  
  
    3.  <span data-ttu-id="7c2b6-124">`StreamedRequest`, która umożliwia strumieniowe przesyłanie tylko żądania.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-124">`StreamedRequest`, which enables streaming the request only.</span></span>  
  
    4.  <span data-ttu-id="7c2b6-125">`StreamedResponse`, która umożliwia strumieniowe przesyłanie tylko odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-125">`StreamedResponse`, which enables streaming the response only.</span></span>  
  
     <span data-ttu-id="7c2b6-126">`BasicHttpBinding` Przedstawia `TransferMode` właściwość powiązanie, tak jak w przypadku `NetTcpBinding` i `NetNamedPipeBinding`.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-126">The `BasicHttpBinding` exposes the `TransferMode` property on the binding, as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="7c2b6-127">`TransferMode` Właściwości można także ustawić w elemencie powiązania transportu i używane do niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-127">The `TransferMode` property can also be set on the transport binding element and used in a custom binding.</span></span>  
  
     <span data-ttu-id="7c2b6-128">Poniższe przykłady pokazują, jak ustawić `TransferMode` przez kod i zmieniając pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-128">The following samples show how to set `TransferMode` by code and by changing the configuration file.</span></span> <span data-ttu-id="7c2b6-129">Przykłady również ustawione `maxReceivedMessageSize` odbierania właściwości 64 MB, co powoduje zakończenie na maksymalny dozwolony rozmiar wiadomości w.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-129">The samples also both set the `maxReceivedMessageSize` property to 64 MB, which places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="7c2b6-130">Wartość domyślna `maxReceivedMessageSize` wynosi 64 KB, który zazwyczaj jest zbyt stara przesyłania strumieniowego scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-130">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span> <span data-ttu-id="7c2b6-131">Określ odpowiednie w zależności od maksymalny rozmiar wiadomości, których aplikacja oczekuje na odbieranie to ustawienie limitu przydziału.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-131">Set this quota setting as appropriate depending on the maximum size of messages your application expects to receive.</span></span> <span data-ttu-id="7c2b6-132">Należy również zauważyć, że `maxBufferSize` określa maksymalny rozmiar, który jest buforowany i odpowiednio ją ustawić.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-132">Also note that `maxBufferSize` controls the maximum size that is buffered, and set it appropriately.</span></span>  
  
    1.  <span data-ttu-id="7c2b6-133">Poniższy fragment konfiguracji z próbki pokazuje ustawienie `TransferMode` właściwości do przesyłania strumieniowego na `basicHttpBinding` i niestandardowego powiązania protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-133">The following configuration snippet from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]   
  
    2.  <span data-ttu-id="7c2b6-134">Poniższy fragment kodu przedstawia ustawienie `TransferMode` właściwości do przesyłania strumieniowego na `basicHttpBinding` i niestandardowego powiązania protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-134">The following code snippet shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3.  <span data-ttu-id="7c2b6-135">Poniższy fragment kodu przedstawia ustawienie `TransferMode` właściwości do przesyłania strumieniowego na niestandardowego powiązania protokołu TCP.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-135">The following code snippet shows setting the `TransferMode` property to streaming on a custom TCP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3.  <span data-ttu-id="7c2b6-136">Operacje `GetStream`, `UploadStream`, i `EchoStream` wszystkie postępowania w przypadku wysyłania danych bezpośrednio z pliku lub zapisywanie odebranych danych bezpośrednio w pliku.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-136">The operations `GetStream`, `UploadStream`, and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="7c2b6-137">Poniższy kod jest przeznaczony dla `GetStream`.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-137">The following code is for `GetStream`.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a><span data-ttu-id="7c2b6-138">Pisanie niestandardowych strumieni</span><span class="sxs-lookup"><span data-stu-id="7c2b6-138">Writing a custom stream</span></span>  
  
1.  <span data-ttu-id="7c2b6-139">Aby wykonywać specjalnego przetwarzania dla każdego fragmentu strumień danych jest wysyłane lub odbierane, klasa wyprowadzona z niestandardowych strumieni <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-139">To do special processing on each chunk of a data stream as it is being sent or received, derive a custom stream class from <xref:System.IO.Stream>.</span></span> <span data-ttu-id="7c2b6-140">Na przykład niestandardowych strumieni poniższy kod zawiera `GetReversedStream` — metoda i `ReverseStream` klasy —.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-140">As an example of a custom stream, the following code contains a `GetReversedStream` method and a `ReverseStream` class-.</span></span>  
  
     <span data-ttu-id="7c2b6-141">`GetReversedStream`Tworzy i zwraca nowe wystąpienie klasy `ReverseStream`.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-141">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="7c2b6-142">Aktualnie przetwarzanego się stanie, jak system odczytuje z `ReverseStream` obiektu.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-142">The actual processing happens as the system reads from the `ReverseStream` object.</span></span> <span data-ttu-id="7c2b6-143">`ReverseStream.Read` Metoda odczytuje fragmentu bajtów z pliku źródłowego, odwraca je, a następnie zwraca odwróconej bajtów.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-143">The `ReverseStream.Read` method reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="7c2b6-144">Ta metoda nie wstecznego zawartości całego pliku; Odwraca ono jednym fragmencie bajtów w czasie.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-144">This method does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="7c2b6-145">W tym przykładzie pokazano, jak wykonać przetwarzającym strumień zawartości jest do odczytu lub zapisu ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="7c2b6-145">This example shows how you can perform stream processing as the content is being read to or written from the stream.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7c2b6-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c2b6-146">See Also</span></span>  
 [<span data-ttu-id="7c2b6-147">Duże ilości danych i przesyłania strumieniowego</span><span class="sxs-lookup"><span data-stu-id="7c2b6-147">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 [<span data-ttu-id="7c2b6-148">Strumień</span><span class="sxs-lookup"><span data-stu-id="7c2b6-148">Stream</span></span>](../../../../docs/framework/wcf/samples/stream.md)
