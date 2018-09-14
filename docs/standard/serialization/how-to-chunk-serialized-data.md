---
title: 'Porady: Podziel zserializowane dane'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
ms.openlocfilehash: 4b83e841db1afc898c5c3c99ed4186fd264ed2ef
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45585502"
---
# <a name="how-to-chunk-serialized-data"></a><span data-ttu-id="8c06a-102">Porady: Podziel zserializowane dane</span><span class="sxs-lookup"><span data-stu-id="8c06a-102">How to: chunk serialized data</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="8c06a-103">Są dwa problemy, które występują podczas wysyłania dużych zestawach danych w wiadomości usługi sieci Web:</span><span class="sxs-lookup"><span data-stu-id="8c06a-103">Two issues that occur when sending large data sets in Web service messages are:</span></span>  
  
1.  <span data-ttu-id="8c06a-104">Duży zestaw roboczy (pamięć) z powodu buforowania przez aparat serializacji.</span><span class="sxs-lookup"><span data-stu-id="8c06a-104">A large working set (memory) due to buffering by the serialization engine.</span></span>  
  
2.  <span data-ttu-id="8c06a-105">Długi przepustowości z powodu inflacji procent 33 po związanych z kodowaniem Base64.</span><span class="sxs-lookup"><span data-stu-id="8c06a-105">Inordinate bandwidth consumption due to 33 percent inflation after Base64 encoding.</span></span>  
  
 <span data-ttu-id="8c06a-106">Aby rozwiązać te problemy, należy zaimplementować <xref:System.Xml.Serialization.IXmlSerializable> interfejs do sterowania serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="8c06a-106">To solve these problems, implement the <xref:System.Xml.Serialization.IXmlSerializable> interface to control the serialization and deserialization.</span></span> <span data-ttu-id="8c06a-107">W szczególności zaimplementować <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> i <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody służące do bryłkach danych.</span><span class="sxs-lookup"><span data-stu-id="8c06a-107">Specifically, implement the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> methods to chunk the data.</span></span>  
  
### <a name="to-implement-server-side-chunking"></a><span data-ttu-id="8c06a-108">Do zaimplementowania segmentu po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="8c06a-108">To implement server-side chunking</span></span>  
  
1.  <span data-ttu-id="8c06a-109">Na komputerze z serwerem, Metoda sieci Web należy wyłączyć buforowanie ASP.NET i zwracany typ, który implementuje <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="8c06a-109">On the server machine, the Web method must turn off ASP.NET buffering and return a type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
2.  <span data-ttu-id="8c06a-110">Typ, który implementuje <xref:System.Xml.Serialization.IXmlSerializable> chunks dane w <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8c06a-110">The type that implements <xref:System.Xml.Serialization.IXmlSerializable> chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
### <a name="to-implement-client-side-processing"></a><span data-ttu-id="8c06a-111">Do zaimplementowania przetwarzania po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="8c06a-111">To implement client-side processing</span></span>  
  
1.  <span data-ttu-id="8c06a-112">Zmienić metodę sieci Web na serwerze proxy klienta do zwrócenia typu, który implementuje <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="8c06a-112">Alter the Web method on the client proxy to return the type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="8c06a-113">Możesz użyć <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> można to zrobić automatycznie, ale nie jest to pokazane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="8c06a-113">You can use a <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> to do this automatically, but this isn't shown here.</span></span>  
  
2.  <span data-ttu-id="8c06a-114">Implementowanie <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metodę w celu odczytania danych podzielonego strumienia i Bajty zapisu dysku.</span><span class="sxs-lookup"><span data-stu-id="8c06a-114">Implement the <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> method to read the chunked data stream and write the bytes to disk.</span></span> <span data-ttu-id="8c06a-115">Ta implementacja wywołuje również zdarzenia postępu, które mogą być używane przez formant graficzny, takich jak pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="8c06a-115">This implementation also raises progress events that can be used by a graphic control, such as a progress bar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c06a-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c06a-116">Example</span></span>  
<span data-ttu-id="8c06a-117">Poniższy przykład kodu przedstawia metodę sieci Web na komputerze klienckim, który powoduje wyłączenie buforowania programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8c06a-117">The following code example shows the Web method on the client that turns off ASP.NET buffering.</span></span> <span data-ttu-id="8c06a-118">Zawiera również wykonania po stronie klienta <xref:System.Xml.Serialization.IXmlSerializable> interfejs, który chunks dane w <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="8c06a-118">It also shows the client-side implementation of the <xref:System.Xml.Serialization.IXmlSerializable> interface that chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8c06a-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="8c06a-119">Compiling the code</span></span>  
  
-   <span data-ttu-id="8c06a-120">W kodzie za pomocą następujących przestrzeni nazw: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, i <xref:System.Xml.Schema>.</span><span class="sxs-lookup"><span data-stu-id="8c06a-120">The code uses the following namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, and <xref:System.Xml.Schema>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c06a-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c06a-121">See also</span></span>

- [<span data-ttu-id="8c06a-122">Serializacja niestandardowa</span><span class="sxs-lookup"><span data-stu-id="8c06a-122">Custom Serialization</span></span>](custom-serialization.md)
