---
title: 'Instrukcje: Tworzenie podstawowego kontraktu danych dla klasy lub struktury'
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
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6241df0fd5a0b6ee532691eee2279f618be25a56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a>Instrukcje: Tworzenie podstawowego kontraktu danych dla klasy lub struktury
W tym temacie przedstawiono podstawowe kroki, aby utworzyć kontrakt danych przy użyciu klasy lub struktury. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]dane umów i korzystania z nich, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Samouczek, który przeprowadzi Cię przez kroki tworzenia podstawowego [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi i klienta, zobacz [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md). Dla aplikacji przykładowej pracy, który składa się z podstawowej usługi i klienta, zobacz [podstawowego kontraktu danych](../../../../docs/framework/wcf/samples/basic-data-contract.md).  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a>Aby utworzyć podstawowego kontraktu danych dla klasy lub struktury  
  
1.  Deklaruje, że typ ma kontraktu danych poprzez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> do klasy atrybutu. Należy zauważyć, że wszystkie typy publiczne, w tym użytkownicy bez atrybutów, które można serializować. <xref:System.Runtime.Serialization.DataContractSerializer> Wnioskuje kontraktu danych, jeśli <xref:System.Runtime.Serialization.DataContractAttribute> nie jest obecny atrybut. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
2.  Zdefiniuj członków (właściwości, pola lub zdarzeń), które są serializowane, stosując <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do każdego elementu członkowskiego. Elementy te są określane jako elementy członkowskie danych. Domyślnie wszystkie typy publiczne jest możliwy do serializacji. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
    > [!NOTE]
    >  Możesz zastosować <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu pola prywatne, powodując danych mają być uwidaczniane w innym. Pamiętaj, że element członkowski nie zawiera danych poufnych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia kontraktu danych dla `Person` typu stosując <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty do klasy i jej elementów członkowskich.  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [Wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md)
