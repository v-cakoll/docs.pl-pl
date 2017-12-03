---
title: "Wywołania zwrotne serializacji z tolerancją dla wersji"
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
helpviewer_keywords:
- OnDeserializedAttribute [WCF]
- OnDeserializingAttribute [WCF]
- OnSerializingAttribute [WCF]
- serialization [WCF], setting default values
- OnSerializedAttribute [WCF]
ms.assetid: aa4a3a6f-05ec-4efd-bdbf-2181e13e6468
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 70b89ff741d2a2036d5684ebc4526a6cb7ec49d4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="version-tolerant-serialization-callbacks"></a>Wywołania zwrotne serializacji z tolerancją dla wersji
Model programowania kontraktu danych w pełni obsługuje metody wywołania zwrotnego serializacji z tolerancją dla wersji który <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> klas pomocy technicznej.  
  
## <a name="version-tolerant-attributes"></a>Atrybuty tolerancją dla wersji  
 Istnieją cztery atrybuty wywołania zwrotnego. Każdy atrybut można stosować do metody, która wywołuje aparat serializacji/deserializacji w różnym czasie. W poniższej tabeli opisano, kiedy należy używać każdego atrybutu.  
  
|Atrybut|Gdy jest wywoływana odpowiedniej metody|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Wywołuje się przed rozpoczęciem serializacji typu.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Wywoływana po wykonaniu serializacji typu.|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Wywoływana przed deserializacji typu.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Wywołuje się po deserializacji typu.|  
  
 Musisz zaakceptować metody <xref:System.Runtime.Serialization.StreamingContext> parametru.  
  
 Te metody są przeznaczone głównie do użytku z wersji lub inicjowania. Podczas deserializacji są nazywane ma konstruktorów. W związku z tym elementy członkowskie danych nie można prawidłowo zainicjować (do wartości domyślnych zamierzone) Jeśli dla tych elementów członkowskich brakuje danych w strumieniu przychodzącego, na przykład, jeśli dane pochodzą z poprzedniej wersji typu, który nie ma niektórych elementów członkowskich danych. Aby rozwiązać ten problem, należy użyć metody wywołania zwrotnego oznaczonej jako <xref:System.Runtime.Serialization.OnDeserializingAttribute>, jak pokazano w poniższym przykładzie.  
  
 Można określić tylko jedną metodę według typu z każdą z powyższych atrybuty wywołania zwrotnego.  
  
### <a name="example"></a>Przykład  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.OnSerializingAttribute>  
 <xref:System.Runtime.Serialization.OnSerializedAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
 <xref:System.Runtime.Serialization.StreamingContext>  
 [Serializacji z tolerancją dla wersji](../../../../docs/standard/serialization/version-tolerant-serialization.md)
