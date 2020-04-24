---
title: 'Instrukcje: fragment serializowanych danych'
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
ms.openlocfilehash: 6a39997d8854d525146c044ed4bbf939de615d3f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602419"
---
# <a name="how-to-chunk-serialized-data"></a>Instrukcje: fragment serializowanych danych

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Są dwa problemy, które występują podczas wysyłania dużych zestawach danych w wiadomości usługi sieci Web:  
  
1. Duży zestaw roboczy (pamięć) z powodu buforowania przez aparat serializacji.  
  
2. Długi przepustowości z powodu inflacji procent 33 po związanych z kodowaniem Base64.  
  
 Aby rozwiązać te problemy, zaimplementuj <xref:System.Xml.Serialization.IXmlSerializable> interfejs w celu kontrolowania serializacji i deserializacji. Zaimplementuj metody <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> i <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> , aby rozfragmentować dane.  
  
### <a name="to-implement-server-side-chunking"></a>Aby zaimplementować fragmentowanie po stronie serwera  
  
1. Na komputerze serwera Metoda sieci Web musi wyłączyć buforowanie ASP.NET i zwrócić typ, który implementuje <xref:System.Xml.Serialization.IXmlSerializable>.  
  
2. Typ, który implementuje <xref:System.Xml.Serialization.IXmlSerializable> fragmenty danych w <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metodzie.  
  
### <a name="to-implement-client-side-processing"></a>Aby zaimplementować przetwarzanie po stronie klienta  
  
1. Zmień metodę sieci Web na serwerze proxy klienta, aby zwracała typ, <xref:System.Xml.Serialization.IXmlSerializable>który implementuje. Możesz użyć, <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> aby to zrobić automatycznie, ale nie jest to tutaj pokazane.  
  
2. Zaimplementuj <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metodę, aby odczytać strumień danych podzielonych i zapisać bajty na dysku. Ta implementacja podnosi także zdarzenia postępu, które mogą być używane przez formant graficzny, taki jak pasek postępu.  
  
## <a name="example"></a>Przykład  
Poniższy przykład kodu przedstawia metodę sieci Web na kliencie, która wyłącza buforowanie ASP.NET. Pokazuje także implementację <xref:System.Xml.Serialization.IXmlSerializable> interfejsu po stronie klienta, który fragmentuje dane w <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metodzie.  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- W kodzie za pomocą następujących przestrzeni nazw: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, i <xref:System.Xml.Schema>.  
  
## <a name="see-also"></a>Zobacz też

- [Serializacja niestandardowa](custom-serialization.md)
