---
title: Kolejność elementów członkowskich danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 2a5d7430953bdc31644e92b9207cd2865209cce5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185196"
---
# <a name="data-member-order"></a>Kolejność elementów członkowskich danych
W niektórych aplikacjach warto znać kolejność wysyłania danych z różnych elementów członkowskich danych lub oczekuje się ich otrzymania (takich jak kolejność, w jakiej dane są wyświetlane w seryjnym kodzie XML). Czasami może być konieczna zmiana tego zamówienia. W tym temacie opisano reguły zamawiania.  
  
## <a name="basic-rules"></a>Podstawowe zasady  
 Podstawowe zasady zamawiania danych obejmują:  
  
- Jeśli typ kontraktu danych jest częścią hierarchii dziedziczenia, elementy członkowskie danych jego typów podstawowych są zawsze na pierwszym miejscu w kolejności.  
  
- Następna w kolejności są elementy członkowskie danych bieżącego typu, które nie mają <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwości zestawu <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów w kolejności alfabetycznej.  
  
- Następnie są wszystkie elementy <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> członkowskie danych, które mają właściwość zestawu <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów. Są one uporządkowane według `Order` wartości właściwości, a następnie alfabetycznie, jeśli `Order` istnieje więcej niż jeden element członkowski określonej wartości. Wartości zamówienia mogą zostać pominięte.  
  
 Kolejność alfabetyczna jest ustanawiana przez wywołanie <xref:System.String.CompareOrdinal%2A> metody.  
  
## <a name="examples"></a>Przykłady  
 Należy wziąć pod uwagę następujący kod.  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 Wyprodukowany kod XML jest podobny do następującego.  
  
```xml  
<DerivedType>  
    <!-- Zebra is a base data member, and appears first. -->  
    <zebra/>
  
    <!-- Cat has no Order, appears alphabetically first. -->  
    <cat/>  
  
   <!-- Dog has no Order, appears alphabetically last. -->  
    <dog/>
  
    <!-- Bird is the member with the smallest Order value -->  
    <bird/>  
  
    <!-- Albatross has the next Order value, alphabetically first. -->  
    <albatross/>  
  
    <!-- Parrot, with the next Order value, alphabetically last. -->  
     <parrot/>  
  
    <!-- Antelope is the member with the highest Order value. Note that   
    Order=2 is skipped -->  
     <antelope/>
</DerivedType>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
