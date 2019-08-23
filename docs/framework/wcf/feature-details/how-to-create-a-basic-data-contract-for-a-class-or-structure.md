---
title: 'Instrukcje: tworzenie podstawowego kontraktu danych dla klasy lub struktury'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: 15c59f3ee7cbefafef7a304cfd1477685fff68f2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968462"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Instrukcje: tworzenie podstawowego kontraktu danych dla klasy lub struktury
W tym temacie przedstawiono podstawowe kroki tworzenia kontraktu danych przy użyciu klasy lub struktury. Aby uzyskać więcej informacji na temat kontraktów danych i sposobu ich użycia, zobacz [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Aby zapoznać się z samouczkiem, który przeprowadzi Cię przez kroki tworzenia podstawowej usługi Windows Communication Foundation (WCF) i klienta programu, zobacz [samouczek wprowadzenie](../../../../docs/framework/wcf/getting-started-tutorial.md). Aby uzyskać działającą przykładową aplikację, która składa się z podstawowej usługi i klienta, zobacz temat [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>Tworzenie podstawowego kontraktu danych dla klasy lub struktury  
  
1. Zadeklaruj, że typ ma kontrakt danych, stosując <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do klasy. Należy zauważyć, że można serializować wszystkie typy publiczne, łącznie z tymi bez atrybutów. Jeśli atrybut jest nieobecny, wnioskujeoumowęodane.<xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractAttribute> Aby uzyskać więcej informacji, zobacz [typy serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
2. Zdefiniuj elementy członkowskie (właściwości, pola lub zdarzenia), które są serializowane przez zastosowanie <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do każdego elementu członkowskiego. Te elementy członkowskie są nazywane elementami członkowskimi danych. Domyślnie wszystkie typy publiczne są serializowane. Aby uzyskać więcej informacji, zobacz [typy serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
    > [!NOTE]
    > Można zastosować <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut do pól prywatnych, co sprawia, że dane mają być widoczne dla innych użytkowników. Upewnij się, że element członkowski nie zawiera poufnych danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia kontraktu danych dla `Person` typu przez <xref:System.Runtime.Serialization.DataContractAttribute> zastosowanie atrybutów i <xref:System.Runtime.Serialization.DataMemberAttribute> do klasy i jej elementów członkowskich.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [Wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md)
