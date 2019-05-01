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
ms.openlocfilehash: 4e5e6b77cdb13c17557f176a37fbb9e7d42ab667
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047792"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Instrukcje: tworzenie podstawowego kontraktu danych dla klasy lub struktury
W tym temacie przedstawiono podstawowe kroki, aby utworzyć kontraktu danych za pomocą klasy lub struktury. Aby uzyskać więcej informacji na temat kontraktów danych i sposobu ich używania, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Aby uzyskać samouczek, który przeprowadzi kroki tworzenia podstawowych usług Windows Communication Foundation (WCF) i klienta, zobacz [Samouczek wprowadzający](../../../../docs/framework/wcf/getting-started-tutorial.md). Pracy przykładowej aplikacji składający się z podstawowej usługi i klienta, zobacz [podstawowego kontraktu danych](../../../../docs/framework/wcf/samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>Do utworzenia podstawowego kontraktu danych dla klasy lub struktury  
  
1. Zadeklaruj, że typ ma kontraktu danych, stosując <xref:System.Runtime.Serialization.DataContractAttribute> do klasy atrybutu. Należy zauważyć, że wszystkie typy publiczne, w tym użytkownicy bez atrybuty, które można serializować. <xref:System.Runtime.Serialization.DataContractSerializer> Wnioskuje kontraktu danych, jeśli <xref:System.Runtime.Serialization.DataContractAttribute> atrybut jest nieobecne. Aby uzyskać więcej informacji, zobacz [typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
2. Definiowanie elementów członkowskich (właściwości, pola lub zdarzenia), które są serializowane, stosując <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do każdego elementu członkowskiego. Te elementy członkowskie są nazywane składowych danych. Domyślnie wszystkie typy publiczne są możliwe do serializacji. Aby uzyskać więcej informacji, zobacz [typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
    > [!NOTE]
    >  Można zastosować <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do pola prywatne, powodując dane, które mają być widoczne dla innych użytkowników. Pamiętaj, elementu członkowskiego nie zawiera poufnych danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak tworzenie kontraktu danych dla `Person` typu przez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów do klasy i jej elementów członkowskich.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [Wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md)
