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
# <a name="data-member-order"></a><span data-ttu-id="86fb7-102">Kolejność elementów członkowskich danych</span><span class="sxs-lookup"><span data-stu-id="86fb7-102">Data Member Order</span></span>
<span data-ttu-id="86fb7-103">W niektórych aplikacjach warto znać kolejność wysyłania danych z różnych elementów członkowskich danych lub oczekuje się ich otrzymania (takich jak kolejność, w jakiej dane są wyświetlane w seryjnym kodzie XML).</span><span class="sxs-lookup"><span data-stu-id="86fb7-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="86fb7-104">Czasami może być konieczna zmiana tego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="86fb7-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="86fb7-105">W tym temacie opisano reguły zamawiania.</span><span class="sxs-lookup"><span data-stu-id="86fb7-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="86fb7-106">Podstawowe zasady</span><span class="sxs-lookup"><span data-stu-id="86fb7-106">Basic Rules</span></span>  
 <span data-ttu-id="86fb7-107">Podstawowe zasady zamawiania danych obejmują:</span><span class="sxs-lookup"><span data-stu-id="86fb7-107">The basic rules for data ordering include:</span></span>  
  
- <span data-ttu-id="86fb7-108">Jeśli typ kontraktu danych jest częścią hierarchii dziedziczenia, elementy członkowskie danych jego typów podstawowych są zawsze na pierwszym miejscu w kolejności.</span><span class="sxs-lookup"><span data-stu-id="86fb7-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
- <span data-ttu-id="86fb7-109">Następna w kolejności są elementy członkowskie danych bieżącego typu, które nie mają <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwości zestawu <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="86fb7-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
- <span data-ttu-id="86fb7-110">Następnie są wszystkie elementy <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> członkowskie danych, które mają właściwość zestawu <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów.</span><span class="sxs-lookup"><span data-stu-id="86fb7-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="86fb7-111">Są one uporządkowane według `Order` wartości właściwości, a następnie alfabetycznie, jeśli `Order` istnieje więcej niż jeden element członkowski określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="86fb7-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="86fb7-112">Wartości zamówienia mogą zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="86fb7-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="86fb7-113">Kolejność alfabetyczna jest ustanawiana przez wywołanie <xref:System.String.CompareOrdinal%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="86fb7-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="86fb7-114">Przykłady</span><span class="sxs-lookup"><span data-stu-id="86fb7-114">Examples</span></span>  
 <span data-ttu-id="86fb7-115">Należy wziąć pod uwagę następujący kod.</span><span class="sxs-lookup"><span data-stu-id="86fb7-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="86fb7-116">Wyprodukowany kod XML jest podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="86fb7-116">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="86fb7-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86fb7-117">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="86fb7-118">Równoważność kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="86fb7-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="86fb7-119">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="86fb7-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
