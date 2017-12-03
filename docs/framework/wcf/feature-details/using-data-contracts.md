---
title: "Używanie kontraktów danych"
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
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: acbe1fc52cec011863dea8f3ae81492e3661cd97
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="using-data-contracts"></a>Używanie kontraktów danych
A *kontraktu danych* jest umową posiadanie między usługą i klienta, który abstrakcyjnie opisuje dane były wymieniane. Oznacza to, że do komunikacji, klient i usługa nie masz do udostępniania tego samego typu, tylko tej samej kontraktów danych. Mówiąc definiuje kontrakt danych, dla każdego typu parametr lub zwracane, jakie dane jest serializowany (zamieniło XML) aby wymienić.  
  
## <a name="data-contract-basics"></a>Podstawy kontraktu danych  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]mechanizm serializacji, o nazwie serializator kontraktu danych domyślnie używa do serializowania i deserializowania danych (przekonwertować go do i z pliku XML). Wszystkie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy pierwotne, takie jak liczby całkowite i ciągi, a także pewnych typów traktowane jako typów podstawowych, takich jak <xref:System.DateTime> i <xref:System.Xml.XmlElement>, może być Zserializowany bez innych przygotowań i mających kontraktów danych domyślne. Wiele [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy również mieć istniejących kontraktów danych. Aby uzyskać pełną listę typów możliwych do serializacji, zobacz [typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 Nowe typy złożone tworzonych musi mieć zdefiniowane dla nich jako możliwy do serializacji kontraktu danych. Domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> wnioskuje kontraktu danych i serializuje wszystkich typów publicznie widoczna. Wszystkie właściwości publiczne odczytu/zapisu i pól typu są serializowane. Można zrezygnować z elementami członkowskimi z serializacji przy użyciu <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>. Można również jawnie tworzenie kontraktu danych przy użyciu <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów. Zazwyczaj jest to realizowane przez stosowanie <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu typu. Ten atrybut można stosować do klasy, struktury i wyliczenia. <xref:System.Runtime.Serialization.DataMemberAttribute> Następnie musi zostać zastosowany atrybut do każdego elementu członkowskiego typu kontraktu danych, aby wskazać, że *element członkowski danych*, to znaczy powinny być serializowane. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono kontrakt usługi (interface), do którego <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> jawnie zastosowano atrybutów. W przykładzie pokazano, że typy pierwotne nie wymagają kontraktu danych, gdy jest typem złożonym.  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 W poniższym przykładzie przedstawiono sposób kontraktu danych dla `MyTypes.PurchaseOrder` typ jest tworzony przez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty do klasy i jej elementów członkowskich.  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a>Uwagi  
 Poniższe uwagi zawierają elementów do uwzględnienia podczas tworzenia kontraktów danych:  
  
-   <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> Atrybut jest honorowane tylko, gdy jest używany z nieoznaczone typy. Obejmuje to typy, które nie są oznaczone ikoną z jednego z <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.SerializableAttribute>, <xref:System.Runtime.Serialization.CollectionDataContractAttribute>, lub <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutów lub oznaczony jako możliwy do serializacji w inny sposób (takie jak <xref:System.Xml.Serialization.IXmlSerializable>).  
  
-   Możesz zastosować <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu pola i właściwości.  
  
-   Poziomy ułatwień dostępu elementu członkowskiego (wewnętrznego, prywatnych, chronionych lub publicznego) nie wpływają na kontraktu danych, w dowolny sposób.  
  
-   <xref:System.Runtime.Serialization.DataMemberAttribute> Atrybut jest ignorowana, jeśli jest on stosowany statycznych elementów członkowskich.  
  
-   Podczas serializacji kod get właściwości jest nazywany właściwości elementów członkowskich danych można uzyskać wartość właściwości, które mają być serializowane.  
  
-   Podczas deserializacji Niezainicjowany obiekt utworzenia bez wywoływania żadnych konstruktorów dla typu. Następnie deserializowany są wszystkie elementy członkowskie danych.  
  
-   Podczas deserializacji kod zestawu właściwości jest nazywany właściwości elementów członkowskich danych można ustawić właściwości na wartość deserializowany.  
  
-   Kontrakt danych jest nieprawidłowy musi być możliwy do serializacji wszystkich jego elementów członkowskich danych. Aby uzyskać pełną listę typów możliwych do serializacji, zobacz [typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
     Typy ogólne są obsługiwane w taki sam sposób, jak inny niż ogólny typów. Nie ma żadnych specjalnych wymagań dla parametrów ogólnych. Rozważmy na przykład następujący typ.  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 Ten typ jest możliwy do serializacji, czy typ używany dla parametru typu ogólnego (`T`) lub nie jest możliwy do serializacji. Ponieważ musi on być możliwy do serializacji wszystkie elementy członkowskie danych, następujący typ jest możliwy do serializacji tylko jeśli parametr typu ogólnego jest również serializacji, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 Kompletny kod przykładowy usługi WCF, która definiuje kontrakt danych [podstawowego kontraktu danych](../../../../docs/framework/wcf/samples/basic-data-contract.md) próbki.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [Typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md)  
 [Nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [Równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md)  
 [Znane typy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Kontrakty danych zgodne z nowszymi](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)  
 [Przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [Wywołania zwrotne serializacji z tolerancją dla wersji](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)  
 [Domyślne wartości elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-default-values.md)  
 [Typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)  
 [Porady: Tworzenie podstawowego kontraktu danych dla klasy lub struktury](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
