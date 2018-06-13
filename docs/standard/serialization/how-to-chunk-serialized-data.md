---
title: 'Porady: bryłkach danych serializacji.'
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
ms.openlocfilehash: ce3d60e6d74594f93be44ae46d36b8ea2212d4bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582704"
---
# <a name="how-to-chunk-serialized-data"></a>Porady: bryłkach danych serializacji.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Są dwa problemy, które występują podczas wysyłania dużych zestawach danych w wiadomości usługi sieci Web:  
  
1.  Duży zestaw roboczy (pamięć) z powodu buforowania przez aparat serializacji.  
  
2.  Długi przepustowości z powodu inflacji procent 33 po związanych z kodowaniem Base64.  
  
 Aby rozwiązać te problemy, zaimplementuj <xref:System.Xml.Serialization.IXmlSerializable> interfejsu do sterowania serializacji i deserializacji. W szczególności zaimplementować <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> i <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody bryłkach danych.  
  
### <a name="to-implement-server-side-chunking"></a>Aby zaimplementować podziału po stronie serwera  
  
1.  Na komputerze z serwerem, metody sieci Web należy wyłączyć buforowanie ASP.NET i zwracany typ, który implementuje <xref:System.Xml.Serialization.IXmlSerializable>.  
  
2.  Typ, który implementuje <xref:System.Xml.Serialization.IXmlSerializable> chunks dane w <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody.  
  
### <a name="to-implement-client-side-processing"></a>Aby zaimplementować przetwarzania po stronie klienta  
  
1.  Metoda sieci Web na serwerze proxy klienta, aby zwracany typ, który implementuje ALTER <xref:System.Xml.Serialization.IXmlSerializable>. Można użyć <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> aby zrobić to automatycznie, ale to nie jest widoczne w tym miejscu.  
  
2.  Implementowanie <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody odczytać podzielony danych strumienia i zapisać bajtów na dysku. Ta implementacja wywołuje również zdarzenia postępu, które mogą być używane przez formant graficznych, takich jak pasek postępu.  
  
## <a name="example"></a>Przykład  
Poniższy przykład kodu pokazuje metody sieci Web na komputerze klienckim, który powoduje wyłączenie buforowania platformy ASP.NET. Przedstawiono również implementacja po stronie klienta <xref:System.Xml.Serialization.IXmlSerializable> interfejs, który chunks dane w <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody.  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   W kodzie za pomocą następujących przestrzeni nazw: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, i <xref:System.Xml.Schema>.  
  
## <a name="see-also"></a>Zobacz także  
 [Serializacja niestandardowa](custom-serialization.md)
