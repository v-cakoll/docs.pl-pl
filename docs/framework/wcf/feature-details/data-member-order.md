---
title: Kolejność elementów członkowskich danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 717d7014f4c4a56249ead0c839cf05f4f83a6f5f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593467"
---
# <a name="data-member-order"></a><span data-ttu-id="bed90-102">Kolejność elementów członkowskich danych</span><span class="sxs-lookup"><span data-stu-id="bed90-102">Data Member Order</span></span>
<span data-ttu-id="bed90-103">W niektórych aplikacjach warto znać kolejność, w jakiej dane z różnych składowych danych są wysyłane lub oczekuje się ich odbioru (na przykład kolejności, w której dane są wyświetlane w serializowanym kodzie XML).</span><span class="sxs-lookup"><span data-stu-id="bed90-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="bed90-104">Czasami może być konieczne zmiana tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="bed90-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="bed90-105">W tym temacie objaśniono reguły określania kolejności.</span><span class="sxs-lookup"><span data-stu-id="bed90-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="bed90-106">Podstawowe reguły</span><span class="sxs-lookup"><span data-stu-id="bed90-106">Basic Rules</span></span>  
 <span data-ttu-id="bed90-107">Podstawowe reguły określania kolejności danych obejmują:</span><span class="sxs-lookup"><span data-stu-id="bed90-107">The basic rules for data ordering include:</span></span>  
  
- <span data-ttu-id="bed90-108">Jeśli typ kontraktu danych jest częścią hierarchii dziedziczenia, składowe danych jego typów podstawowych są zawsze najpierw w kolejności.</span><span class="sxs-lookup"><span data-stu-id="bed90-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
- <span data-ttu-id="bed90-109">Dalej w kolejności są elementami członkowskimi danych bieżącego typu, które nie mają <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwości <xref:System.Runtime.Serialization.DataMemberAttribute> ustawionej w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="bed90-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
- <span data-ttu-id="bed90-110">Następnie są dowolnymi elementami członkowskimi danych, które mają <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> Właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> ustawioną dla atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bed90-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="bed90-111">Są one uporządkowane według wartości `Order` pierwszej właściwości, a następnie alfabetycznie, jeśli istnieje więcej niż jeden element członkowski określonej `Order` wartości.</span><span class="sxs-lookup"><span data-stu-id="bed90-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="bed90-112">Można pominąć wartości kolejności.</span><span class="sxs-lookup"><span data-stu-id="bed90-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="bed90-113">Kolejność alfabetyczna jest ustalana przez wywołanie <xref:System.String.CompareOrdinal%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bed90-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="bed90-114">Przykłady</span><span class="sxs-lookup"><span data-stu-id="bed90-114">Examples</span></span>  
 <span data-ttu-id="bed90-115">Rozważmy następujący kod.</span><span class="sxs-lookup"><span data-stu-id="bed90-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="bed90-116">Utworzony kod XML jest podobny do poniższego.</span><span class="sxs-lookup"><span data-stu-id="bed90-116">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bed90-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bed90-117">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="bed90-118">Równoważność kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="bed90-118">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="bed90-119">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="bed90-119">Using Data Contracts</span></span>](using-data-contracts.md)
