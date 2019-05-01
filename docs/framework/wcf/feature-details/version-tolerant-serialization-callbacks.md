---
title: Wywołania zwrotne serializacji z tolerancją dla wersji
ms.date: 03/30/2017
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
ms.openlocfilehash: da13f9989b427da047c4a94f77907847ed2ae4d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932629"
---
# <a name="version-tolerant-serialization-callbacks"></a>Wywołania zwrotne serializacji z tolerancją dla wersji
Model programowania kontraktu danych w pełni obsługuje serializacji z tolerancją wersji metody wywołania zwrotnego, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> klasy pomocy technicznej.  
  
## <a name="version-tolerant-attributes"></a>Atrybuty z tolerancją dla wersji  
 Istnieją cztery atrybuty wywołania zwrotnego. Każdy atrybut można stosować do metody wywołującej przez aparat serializacji/deserializacji w różnym czasie. W poniższej tabeli opisano, kiedy należy używać każdego atrybutu.  
  
|Atrybut|Gdy odpowiednia metoda jest wywoływana|  
|---------------|---------------------------------------------|  
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|Wywołuje się przed rozpoczęciem serializacji typu.|  
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|Wywoływane po serializacji typu.|  
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|Wywoływane przed deserializacji typie.|  
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|Wywoływane po deserializacji typie.|  
  
 Metody muszą zaakceptować <xref:System.Runtime.Serialization.StreamingContext> parametru.  
  
 Te metody są głównie przeznaczone do użytku z wersji lub inicjowania. Podczas deserializacji konstruktory nie są wywoływane. W związku z tym elementy członkowskie danych może nie być poprawnie zainicjować (do wartości domyślnych zamierzone) Jeśli dla tych członków brakuje danych w strumieniu przychodzące, na przykład, jeśli dane pochodzą z poprzedniej wersji typu, w którym brakuje niektórych elementów członkowskich danych. Aby rozwiązać ten problem, należy użyć metody wywołania zwrotnego oznaczone <xref:System.Runtime.Serialization.OnDeserializingAttribute>, jak pokazano w poniższym przykładzie.  
  
 Można oznaczyć tylko jednej metody na typ z każdym z poprzednich atrybutów wywołania zwrotnego.  
  
### <a name="example"></a>Przykład  
 [!code-csharp[C_DataContract#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#9)]
 [!code-vb[C_DataContract#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#9)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- [Serializacja z tolerancją wersji](../../../../docs/standard/serialization/version-tolerant-serialization.md)
