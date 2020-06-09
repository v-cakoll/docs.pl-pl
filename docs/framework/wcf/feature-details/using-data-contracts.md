---
title: Używanie kontraktów danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
ms.openlocfilehash: 0d11b48d3021bf0d92d74ab67bc18c2bdd2bdd0e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595001"
---
# <a name="using-data-contracts"></a>Używanie kontraktów danych
*Kontrakt dotyczący danych* jest formalnym porozumieniem między usługą a klientem, który w sposób abstrakcyjny opisuje dane, które mają być wymieniane. Oznacza to, że w celu komunikacji klient i usługa nie muszą używać tych samych typów, tylko tych samych umów dotyczących danych. Dla każdego parametru lub typu zwracanego jest definiowana umowa dotycząca danych, która jest serializowana (w formacie XML) do wymiany.  
  
## <a name="data-contract-basics"></a>Podstawowe informacje dotyczące kontraktu danych  
 Windows Communication Foundation (WCF) używa aparatu serializacji o nazwie serializator kontraktu danych domyślnie do serializacji i deserializacji danych (Konwertuj je na i z XML). Wszystkie .NET Framework typy pierwotne, takie jak liczby całkowite i ciągi, a także niektóre typy traktowane jako elementy pierwotne, takie jak <xref:System.DateTime> i <xref:System.Xml.XmlElement> , mogą być serializowane bez innych przygotowań i są traktowane jako z domyślnymi kontraktami danych. Wiele typów .NET Framework ma także istniejące Kontrakty danych. Aby uzyskać pełną listę typów możliwych do serializacji, zobacz [Typy obsługiwane przez serializator kontraktu danych](types-supported-by-the-data-contract-serializer.md).  
  
 Nowe tworzone typy złożone muszą mieć kontrakt danych zdefiniowany dla nich, aby można było je serializować. Domyślnie program <xref:System.Runtime.Serialization.DataContractSerializer> wnioskuje o umowę danych i serializować wszystkie publicznie widoczne typy. Wszystkie publiczne właściwości odczytu/zapisu i pola typu są serializowane. Członków można zrezygnować z serializacji przy użyciu <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> . Możesz również jawnie utworzyć kontrakt danych przy użyciu <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów i. Jest to zwykle wykonywane przez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu do typu. Ten atrybut może być stosowany do klas, struktur i wyliczeń. Ten <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut musi następnie zostać zastosowany do każdego elementu członkowskiego typu kontraktu danych, aby wskazać, że jest to *element członkowski danych*, czyli powinien być serializowany. Aby uzyskać więcej informacji, zobacz [typy serializacji](serializable-types.md).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono kontrakt usługi (interfejs), do którego <xref:System.ServiceModel.ServiceContractAttribute> atrybuty i zostały <xref:System.ServiceModel.OperationContractAttribute> zastosowane jawnie. W przykładzie pokazano, że typy pierwotne nie wymagają kontraktu danych, podczas gdy typ złożony wykonuje.  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 W poniższym przykładzie przedstawiono sposób tworzenia kontraktu danych dla `MyTypes.PurchaseOrder` typu przez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów i do klasy i jej elementów członkowskich.  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a>Uwagi  
 Poniższe notatki zawierają elementy, które należy wziąć pod uwagę podczas tworzenia umów dotyczących danych:  
  
- Ten <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atrybut jest uznawany tylko w przypadku użycia z nieoznaczonymi typami. Obejmuje to typy, które nie są oznaczone jednym z <xref:System.Runtime.Serialization.DataContractAttribute> atrybutów, <xref:System.SerializableAttribute> , <xref:System.Runtime.Serialization.CollectionDataContractAttribute> , lub są <xref:System.Runtime.Serialization.EnumMemberAttribute> oznaczone jako możliwe do serializacji w inny sposób (na przykład <xref:System.Xml.Serialization.IXmlSerializable> ).  
  
- Można zastosować <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut do pól i właściwości.  
  
- Poziomy ułatwień dostępu członków (wewnętrzne, prywatne, chronione lub publiczne) nie wpływają na kontrakt danych w żaden sposób.  
  
- Ten <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut jest ignorowany, jeśli jest stosowany do statycznych elementów członkowskich.  
  
- Podczas serializacji właściwość Get Code jest wywoływana dla elementów członkowskich danych właściwości, aby uzyskać wartość właściwości, które mają być serializowane.  
  
- Podczas deserializacji, Niezainicjowany obiekt jest najpierw tworzony bez wywoływania żadnych konstruktorów tego typu. Następnie wszystkie elementy członkowskie danych są deserializowane.  
  
- Podczas deserializacji kod zestawu właściwości jest wywoływany dla elementów członkowskich danych właściwości, aby ustawić właściwości na deserializowaną wartość.  
  
- Aby umowa dotycząca danych była ważna, musi istnieć możliwość serializacji wszystkich elementów członkowskich danych. Aby uzyskać pełną listę typów możliwych do serializacji, zobacz [Typy obsługiwane przez serializator kontraktu danych](types-supported-by-the-data-contract-serializer.md).  
  
     Typy ogólne są obsługiwane w taki sam sposób jak typy nieogólne. Nie istnieją specjalne wymagania dotyczące parametrów ogólnych. Rozważmy na przykład następujący typ.  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 Ten typ jest możliwy do serializacji, niezależnie od tego, czy typ używany dla parametru typu ogólnego ( `T` ) jest możliwy do serializacji. Ponieważ musi być możliwe serializacji wszystkich elementów członkowskich danych, następujący typ jest możliwy do serializacji tylko wtedy, gdy parametr typu ogólnego jest również możliwy do serializacji, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 Aby uzyskać kompletny przykład kodu usługi WCF, która definiuje kontrakt danych, zobacz podstawowy przykład [kontraktu danych](../samples/basic-data-contract.md) .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Typy z możliwością serializowania](serializable-types.md)
- [Nazwy kontraktów danych](data-contract-names.md)
- [Równoważność kontraktów danych](data-contract-equivalence.md)
- [Kolejność elementów członkowskich danych](data-member-order.md)
- [Znane typy kontraktów danych](data-contract-known-types.md)
- [Kontrakty danych zgodne z nowszymi wersjami](forward-compatible-data-contracts.md)
- [Przechowywanie wersji kontraktów danych](data-contract-versioning.md)
- [Wywołania zwrotne serializacji z tolerancją dla wersji](version-tolerant-serialization-callbacks.md)
- [Domyślne wartości elementów członkowskich danych](data-member-default-values.md)
- [Typy obsługiwane przez serializator kontraktu danych](types-supported-by-the-data-contract-serializer.md)
- [Instrukcje: Tworzenie podstawowego kontraktu danych dla klasy lub struktury](how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
