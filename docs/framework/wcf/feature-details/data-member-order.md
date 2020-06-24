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
# <a name="data-member-order"></a><span data-ttu-id="f3e1c-104">Kolejność elementów członkowskich danych</span><span class="sxs-lookup"><span data-stu-id="f3e1c-104">Data Member Order</span></span>
<span data-ttu-id="f3e1c-105">W niektórych aplikacjach warto znać kolejność, w jakiej dane z różnych składowych danych są wysyłane lub oczekuje się ich odbioru (na przykład kolejności, w której dane są wyświetlane w serializowanym kodzie XML).</span><span class="sxs-lookup"><span data-stu-id="f3e1c-105">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="f3e1c-106">Czasami może być konieczne zmiana tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="f3e1c-106">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="f3e1c-107">W tym temacie objaśniono reguły określania kolejności.</span><span class="sxs-lookup"><span data-stu-id="f3e1c-107">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="f3e1c-108">Podstawowe reguły</span><span class="sxs-lookup"><span data-stu-id="f3e1c-108">Basic Rules</span></span>  
 <span data-ttu-id="f3e1c-109">Podstawowe reguły określania kolejności danych obejmują:</span><span class="sxs-lookup"><span data-stu-id="f3e1c-109">The basic rules for data ordering include:</span></span>  
  
- <span data-ttu-id="f3e1c-110">Jeśli typ kontraktu danych jest częścią hierarchii dziedziczenia, składowe danych jego typów podstawowych są zawsze najpierw w kolejności.</span><span class="sxs-lookup"><span data-stu-id="f3e1c-110">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
- <span data-ttu-id="f3e1c-111">Dalej w kolejności są elementami członkowskimi danych bieżącego typu, które nie mają <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwości <xref:System.Runtime.Serialization.DataMemberAttribute> ustawionej w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="f3e1c-111">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
- <span data-ttu-id="f3e1c-112">Następnie są dowolnymi elementami członkowskimi danych, które mają <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> Właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> ustawioną dla atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f3e1c-112">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="f3e1c-113">Są one uporządkowane według wartości `Order` pierwszej właściwości, a następnie alfabetycznie, jeśli istnieje więcej niż jeden element członkowski określonej `Order` wartości.</span><span class="sxs-lookup"><span data-stu-id="f3e1c-113">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="f3e1c-114">Można pominąć wartości kolejności.</span><span class="sxs-lookup"><span data-stu-id="f3e1c-114">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="f3e1c-115">Kolejność alfabetyczna jest ustalana przez wywołanie <xref:System.String.CompareOrdinal%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f3e1c-115">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f3e1c-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f3e1c-116">Examples</span></span>  
 <span data-ttu-id="f3e1c-117">Rozważmy następujący kod.</span><span class="sxs-lookup"><span data-stu-id="f3e1c-117">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="f3e1c-118">Utworzony kod XML jest podobny do poniższego.</span><span class="sxs-lookup"><span data-stu-id="f3e1c-118">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3e1c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3e1c-119">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="f3e1c-120">Równoważność kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="f3e1c-120">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="f3e1c-121">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="f3e1c-121">Using Data Contracts</span></span>](using-data-contracts.md)
