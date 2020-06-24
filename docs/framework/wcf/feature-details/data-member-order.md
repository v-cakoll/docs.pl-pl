---
title: Kolejność elementów członkowskich danych
description: Dowiedz się więcej o kolejności elementów członkowskich danych w programie WCF. Aplikacje mogą być niezbędne do poznania lub zmiany kolejności, w której elementy członkowskie danych są wysyłane lub oczekiwane.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 5c192d3bda65a7364345df4310dccd96cbe04056
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247367"
---
# <a name="data-member-order"></a>Kolejność elementów członkowskich danych
W niektórych aplikacjach warto znać kolejność, w jakiej dane z różnych składowych danych są wysyłane lub oczekuje się ich odbioru (na przykład kolejności, w której dane są wyświetlane w serializowanym kodzie XML). Czasami może być konieczne zmiana tej kolejności. W tym temacie objaśniono reguły określania kolejności.  
  
## <a name="basic-rules"></a>Podstawowe reguły  
 Podstawowe reguły określania kolejności danych obejmują:  
  
- Jeśli typ kontraktu danych jest częścią hierarchii dziedziczenia, składowe danych jego typów podstawowych są zawsze najpierw w kolejności.  
  
- Dalej w kolejności są elementami członkowskimi danych bieżącego typu, które nie mają <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwości <xref:System.Runtime.Serialization.DataMemberAttribute> ustawionej w kolejności alfabetycznej.  
  
- Następnie są dowolnymi elementami członkowskimi danych, które mają <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> Właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> ustawioną dla atrybutu. Są one uporządkowane według wartości `Order` pierwszej właściwości, a następnie alfabetycznie, jeśli istnieje więcej niż jeden element członkowski określonej `Order` wartości. Można pominąć wartości kolejności.  
  
 Kolejność alfabetyczna jest ustalana przez wywołanie <xref:System.String.CompareOrdinal%2A> metody.  
  
## <a name="examples"></a>Przykłady  
 Rozważmy następujący kod.  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 Utworzony kod XML jest podobny do poniższego.  
  
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
- [Równoważność kontraktów danych](data-contract-equivalence.md)
- [Używanie kontraktów danych](using-data-contracts.md)
