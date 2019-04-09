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
ms.openlocfilehash: 28033e3e90c5010eee63f35791b0c3c77e64d1ec
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129938"
---
# <a name="using-data-contracts"></a>Używanie kontraktów danych
A *kontraktu danych* jest formalną umowę między usługą i klienta, który opisuje abstrakcyjnie danych wymienianych. Oznacza to, do komunikowania się, klienta i usługi nie muszą udostępniać te same typy tylko tych samych kontraktów danych. Dokładnie definiuje kontraktu danych, dla każdego parametr lub zwracany typ danych jest serializowana (przekształcane w XML) do wymiany.  
  
## <a name="data-contract-basics"></a>Podstawy kontraktu danych  
 Windows Communication Foundation (WCF) używa mechanizm serializacji, o nazwie serializator kontraktu danych domyślnie do serializacji i deserializacji danych (przekonwertować go do i z pliku XML). Wszystkie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów pierwotnych, takich jak liczby całkowite i ciągów, a także niektórych typów traktowane jako podstawowych, takich jak <xref:System.DateTime> i <xref:System.Xml.XmlElement>, może być serializowany z nie innych przygotowania i mających kontraktów danych domyślne. Wiele [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy mają również istniejące kontraktów danych. Aby uzyskać pełną listę typów możliwych do serializacji, zobacz [typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 Nowe typy złożone, które tworzysz, musi mieć zdefiniowany jako możliwy do serializacji kontrakt danych. Domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> wnioskuje kontraktu danych i serializuje wszystkich typów publicznie widoczne. Wszystkie właściwości publiczne odczytu/zapisu i pola tego typu są serializowane. Możesz zrezygnować z elementami członkowskimi z serializacji przy użyciu <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>. Można także jawnie tworzenie kontraktu danych za pomocą <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów. Zazwyczaj jest to realizowane przez stosowanie <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu typu. Ten atrybut można zastosować do klasy, struktury i wyliczenia. <xref:System.Runtime.Serialization.DataMemberAttribute> Następnie należy zastosować atrybut do każdego członka typu kontraktu danych, aby wskazać, że *element członkowski danych*, oznacza to, powinien zostać Zserializowany. Aby uzyskać więcej informacji, zobacz [typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano kontraktu usługi (interfejs), do którego <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> jawnie zastosowano atrybutów. W przykładzie pokazano, że typy pierwotne nie wymagają kontraktu danych, gdy jest to typ złożony.  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 W poniższym przykładzie pokazano, jak kontraktu danych dla `MyTypes.PurchaseOrder` typ jest tworzony przez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów do klasy i jej elementów członkowskich.  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a>Uwagi  
 Poniższe informacje o zapewniają kwestii do rozważenia podczas tworzenia kontraktów danych:  
  
-   <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> Atrybut jest tylko honorowane, gdy jest używana z typami nieoznaczone. Obejmuje to typy, które nie są oznaczone przy użyciu jednego z <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.SerializableAttribute>, <xref:System.Runtime.Serialization.CollectionDataContractAttribute>, lub <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutów lub oznaczony jako możliwy do serializacji w inny sposób (takie jak <xref:System.Xml.Serialization.IXmlSerializable>).  
  
-   Można zastosować <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do pola i właściwości.  
  
-   Poziomy ułatwień dostępu elementu członkowskiego (wewnętrznego, prywatnych, chronionych lub publicznego) nie wpływają na kontraktu danych w jakikolwiek sposób.  
  
-   <xref:System.Runtime.Serialization.DataMemberAttribute> Atrybut jest ignorowany, jeśli zostanie zastosowany do statycznych elementów członkowskich.  
  
-   Podczas serializacji kod pobieraniem właściwości jest wywoływana dla elementów członkowskich danych właściwości można pobrać wartości właściwości, które mają być serializowane.  
  
-   Podczas deserializacji niezainicjowanego obiektu utworzenia bez wywoływania żadnych konstruktorów typu. Następnie wszystkie elementy członkowskie danych są deserializacji.  
  
-   Podczas deserializacji kodu zestawu właściwości jest wywoływana dla elementów członkowskich danych właściwości można ustawić właściwości wartość deserializowany.  
  
-   Dla kontraktu danych był prawidłowy musi być możliwe do serializacji wszystkich jego składowych danych. Aby uzyskać pełną listę typów możliwych do serializacji, zobacz [typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
     Typy ogólne są obsługiwane w taki sam sposób, jak typy ogólne. Istnieją specjalne wymagania dotyczące parametrów ogólnych. Na przykład rozważmy następujący typ.  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 Ten typ jest możliwy do serializacji, czy typ jest używany dla parametru typu ogólnego (`T`) jest możliwy do serializacji, czy nie. Ponieważ muszą być możliwe do serializacji wszystkie składowe danych, następujący typ jest możliwy do serializacji tylko jeśli parametr typu ogólnego jest również możliwe do serializacji, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 Aby uzyskać kompletny przykład kodu usługi WCF, który definiuje kontrakt danych zobacz [podstawowego kontraktu danych](../../../../docs/framework/wcf/samples/basic-data-contract.md) próbki.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Typy z możliwością serializowania](../../../../docs/framework/wcf/feature-details/serializable-types.md)
- [Nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
- [Równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md)
- [Znane typy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Kontrakty danych zgodne z nowszymi wersjami](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
- [Przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
- [Wywołania zwrotne serializacji z tolerancją dla wersji](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
- [Domyślne wartości elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-default-values.md)
- [Typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
- [Instrukcje: tworzenie podstawowego kontraktu danych dla klasy lub struktury](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
