---
title: Kolejność elementów członkowskich danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: e286b900d7647bcd5bc99b78164e6820c1417a63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="data-member-order"></a>Kolejność elementów członkowskich danych
W niektórych aplikacjach warto wiedzieć, kolejność, są wysyłane dane z różnych elementów członkowskich danych lub oczekiwano do odebrania (na przykład kolejności, w którym dane są wyświetlane w serializacji XML). Czasami może być konieczna zmiana tej kolejności. W tym temacie wyjaśniono reguły porządkowania.  
  
## <a name="basic-rules"></a>Podstawowe zasady  
 Podstawowe reguły porządkowania danych obejmują:  
  
-   Typ kontraktu danych jest częścią hierarchii dziedziczenia, elementy członkowskie danych z jego typów podstawowych są zawsze pierwszy w kolejności.  
  
-   Następnie w kolejności są bieżącego typu elementy członkowskie danych, które nie mają <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut, w kolejności alfabetycznej.  
  
-   Następnie są elementy członkowskie danych, które mają <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu. Są one uporządkowane według wartości `Order` właściwości pierwszy, a następnie alfabetycznie, jeśli istnieje więcej niż jeden element członkowski określony `Order` wartość. Kolejność wartości mogą być pominięte.  
  
 Alfabetycznie nawiązaniu przez wywołanie metody <xref:System.String.CompareOrdinal%2A> metody.  
  
## <a name="examples"></a>Przykłady  
 Rozważmy poniższy kod.  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 Kod XML, tworzone jest podobny do następującego.  
  
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
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [Równoważność kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
