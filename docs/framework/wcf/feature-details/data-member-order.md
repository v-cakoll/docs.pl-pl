---
title: Kolejność elementów członkowskich danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 93ec81d94d8133fc5a6d71d7f1b57b2e9a6aad21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659634"
---
# <a name="data-member-order"></a>Kolejność elementów członkowskich danych
W niektórych aplikacjach warto wiedzieć, kolejność, w którym są wysyłane dane z różnych składowych danych, lub powinien być otrzymane (na przykład kolejność, w którym dane są wyświetlane w serializacji XML). Czasami może być konieczna zmiana tej kolejności. W tym temacie opisano reguły sortowania.  
  
## <a name="basic-rules"></a>Podstawowe zasady  
 Podstawowe reguły do ustalania kolejności danych obejmują:  
  
-   Typ kontraktu danych jest częścią hierarchii dziedziczenia, elementy członkowskie danych z jej typów podstawowych są zawsze pierwszy w kolejności.  
  
-   Następnie w kolejności należą do bieżącego typu danych, które nie mają <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut, w kolejności alfabetycznej.  
  
-   Następnie są elementy członkowskie danych, które mają <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut. Te są uporządkowane według wartości `Order` właściwość pierwszy i następnie alfabetycznie, jeśli istnieje więcej niż jeden element członkowski określonej `Order` wartość. Wartości kolejności może zostać pominięta.  
  
 Kolejności alfabetycznej zostanie nawiązane, wywołując <xref:System.String.CompareOrdinal%2A> metody.  
  
## <a name="examples"></a>Przykłady  
 Rozważmy poniższy kod.  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 Plik XML, generowany jest podobny do następującego.  
  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
