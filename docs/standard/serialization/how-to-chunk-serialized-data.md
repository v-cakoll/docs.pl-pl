---
title: 'Instrukcje: fragment serializowanych danych'
description: Dane można fragmentować, aby uniknąć problemów z dużymi zestawami danych. Zaimplementuj interfejs IXmlSerializable w celu kontrolowania serializacji i deserializacji.
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
ms.openlocfilehash: 860fdcae0d1937f53ee964d9d4631ec812b3d379
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379139"
---
# <a name="how-to-chunk-serialized-data"></a><span data-ttu-id="15bc9-104">Instrukcje: fragment serializowanych danych</span><span class="sxs-lookup"><span data-stu-id="15bc9-104">How to: chunk serialized data</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="15bc9-105">Są dwa problemy, które występują podczas wysyłania dużych zestawach danych w wiadomości usługi sieci Web:</span><span class="sxs-lookup"><span data-stu-id="15bc9-105">Two issues that occur when sending large data sets in Web service messages are:</span></span>  
  
1. <span data-ttu-id="15bc9-106">Duży zestaw roboczy (pamięć) z powodu buforowania przez aparat serializacji.</span><span class="sxs-lookup"><span data-stu-id="15bc9-106">A large working set (memory) due to buffering by the serialization engine.</span></span>  
  
2. <span data-ttu-id="15bc9-107">Długi przepustowości z powodu inflacji procent 33 po związanych z kodowaniem Base64.</span><span class="sxs-lookup"><span data-stu-id="15bc9-107">Inordinate bandwidth consumption due to 33 percent inflation after Base64 encoding.</span></span>  
  
 <span data-ttu-id="15bc9-108">Aby rozwiązać te problemy, zaimplementuj <xref:System.Xml.Serialization.IXmlSerializable> interfejs w celu kontrolowania serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="15bc9-108">To solve these problems, implement the <xref:System.Xml.Serialization.IXmlSerializable> interface to control the serialization and deserialization.</span></span> <span data-ttu-id="15bc9-109">Zaimplementuj <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody i, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> Aby rozfragmentować dane.</span><span class="sxs-lookup"><span data-stu-id="15bc9-109">Specifically, implement the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> methods to chunk the data.</span></span>  
  
### <a name="to-implement-server-side-chunking"></a><span data-ttu-id="15bc9-110">Aby zaimplementować fragmentowanie po stronie serwera</span><span class="sxs-lookup"><span data-stu-id="15bc9-110">To implement server-side chunking</span></span>  
  
1. <span data-ttu-id="15bc9-111">Na komputerze serwera Metoda sieci Web musi wyłączyć buforowanie ASP.NET i zwrócić typ, który implementuje <xref:System.Xml.Serialization.IXmlSerializable> .</span><span class="sxs-lookup"><span data-stu-id="15bc9-111">On the server machine, the Web method must turn off ASP.NET buffering and return a type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
2. <span data-ttu-id="15bc9-112">Typ, który implementuje <xref:System.Xml.Serialization.IXmlSerializable> fragmenty danych w <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metodzie.</span><span class="sxs-lookup"><span data-stu-id="15bc9-112">The type that implements <xref:System.Xml.Serialization.IXmlSerializable> chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
### <a name="to-implement-client-side-processing"></a><span data-ttu-id="15bc9-113">Aby zaimplementować przetwarzanie po stronie klienta</span><span class="sxs-lookup"><span data-stu-id="15bc9-113">To implement client-side processing</span></span>  
  
1. <span data-ttu-id="15bc9-114">Zmień metodę sieci Web na serwerze proxy klienta, aby zwracała typ, który implementuje <xref:System.Xml.Serialization.IXmlSerializable> .</span><span class="sxs-lookup"><span data-stu-id="15bc9-114">Alter the Web method on the client proxy to return the type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="15bc9-115">Możesz użyć, <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> Aby to zrobić automatycznie, ale nie jest to tutaj pokazane.</span><span class="sxs-lookup"><span data-stu-id="15bc9-115">You can use a <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> to do this automatically, but this isn't shown here.</span></span>  
  
2. <span data-ttu-id="15bc9-116">Zaimplementuj <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metodę, aby odczytać strumień danych podzielonych i zapisać bajty na dysku.</span><span class="sxs-lookup"><span data-stu-id="15bc9-116">Implement the <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> method to read the chunked data stream and write the bytes to disk.</span></span> <span data-ttu-id="15bc9-117">Ta implementacja podnosi także zdarzenia postępu, które mogą być używane przez formant graficzny, taki jak pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="15bc9-117">This implementation also raises progress events that can be used by a graphic control, such as a progress bar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15bc9-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="15bc9-118">Example</span></span>  
<span data-ttu-id="15bc9-119">Poniższy przykład kodu przedstawia metodę sieci Web na kliencie, która wyłącza buforowanie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="15bc9-119">The following code example shows the Web method on the client that turns off ASP.NET buffering.</span></span> <span data-ttu-id="15bc9-120">Pokazuje także implementację interfejsu po stronie klienta <xref:System.Xml.Serialization.IXmlSerializable> , który fragmentuje dane w <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metodzie.</span><span class="sxs-lookup"><span data-stu-id="15bc9-120">It also shows the client-side implementation of the <xref:System.Xml.Serialization.IXmlSerializable> interface that chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="15bc9-121">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="15bc9-121">Compiling the code</span></span>  
  
- <span data-ttu-id="15bc9-122">W kodzie za pomocą następujących przestrzeni nazw: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, i <xref:System.Xml.Schema>.</span><span class="sxs-lookup"><span data-stu-id="15bc9-122">The code uses the following namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, and <xref:System.Xml.Schema>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15bc9-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15bc9-123">See also</span></span>

- [<span data-ttu-id="15bc9-124">Serializacja niestandardowa</span><span class="sxs-lookup"><span data-stu-id="15bc9-124">Custom Serialization</span></span>](custom-serialization.md)
