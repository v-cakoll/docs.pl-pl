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
# <a name="data-member-order"></a><span data-ttu-id="dc9e4-102">Kolejność elementów członkowskich danych</span><span class="sxs-lookup"><span data-stu-id="dc9e4-102">Data Member Order</span></span>
<span data-ttu-id="dc9e4-103">W niektórych aplikacjach warto wiedzieć, kolejność, w którym są wysyłane dane z różnych składowych danych, lub powinien być otrzymane (na przykład kolejność, w którym dane są wyświetlane w serializacji XML).</span><span class="sxs-lookup"><span data-stu-id="dc9e4-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="dc9e4-104">Czasami może być konieczna zmiana tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="dc9e4-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="dc9e4-105">W tym temacie opisano reguły sortowania.</span><span class="sxs-lookup"><span data-stu-id="dc9e4-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="dc9e4-106">Podstawowe zasady</span><span class="sxs-lookup"><span data-stu-id="dc9e4-106">Basic Rules</span></span>  
 <span data-ttu-id="dc9e4-107">Podstawowe reguły do ustalania kolejności danych obejmują:</span><span class="sxs-lookup"><span data-stu-id="dc9e4-107">The basic rules for data ordering include:</span></span>  
  
-   <span data-ttu-id="dc9e4-108">Typ kontraktu danych jest częścią hierarchii dziedziczenia, elementy członkowskie danych z jej typów podstawowych są zawsze pierwszy w kolejności.</span><span class="sxs-lookup"><span data-stu-id="dc9e4-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
-   <span data-ttu-id="dc9e4-109">Następnie w kolejności należą do bieżącego typu danych, które nie mają <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut, w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="dc9e4-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
-   <span data-ttu-id="dc9e4-110">Następnie są elementy członkowskie danych, które mają <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut.</span><span class="sxs-lookup"><span data-stu-id="dc9e4-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="dc9e4-111">Te są uporządkowane według wartości `Order` właściwość pierwszy i następnie alfabetycznie, jeśli istnieje więcej niż jeden element członkowski określonej `Order` wartość.</span><span class="sxs-lookup"><span data-stu-id="dc9e4-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="dc9e4-112">Wartości kolejności może zostać pominięta.</span><span class="sxs-lookup"><span data-stu-id="dc9e4-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="dc9e4-113">Kolejności alfabetycznej zostanie nawiązane, wywołując <xref:System.String.CompareOrdinal%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dc9e4-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="dc9e4-114">Przykłady</span><span class="sxs-lookup"><span data-stu-id="dc9e4-114">Examples</span></span>  
 <span data-ttu-id="dc9e4-115">Rozważmy poniższy kod.</span><span class="sxs-lookup"><span data-stu-id="dc9e4-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="dc9e4-116">Plik XML, generowany jest podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="dc9e4-116">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dc9e4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc9e4-117">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="dc9e4-118">Równoważność kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="dc9e4-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="dc9e4-119">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="dc9e4-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
