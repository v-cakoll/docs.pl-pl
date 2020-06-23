---
title: 'Instrukcje: Tworzenie podstawowego kontraktu danych dla klasy lub struktury'
description: Postępuj zgodnie z tym przykładem, aby dowiedzieć się, jak utworzyć kontrakt danych przy użyciu klasy lub struktury w programie WCF przy użyciu atrybutu DataContractAttribute.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: a45fde58795947c3e46fa45750ae1a3faddd8849
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247172"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="87319-103">Instrukcje: Tworzenie podstawowego kontraktu danych dla klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="87319-103">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="87319-104">W tym temacie przedstawiono podstawowe kroki tworzenia kontraktu danych przy użyciu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="87319-104">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="87319-105">Aby uzyskać więcej informacji na temat kontraktów danych i sposobu ich użycia, zobacz [Używanie kontraktów danych](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="87319-105">For more information about data contracts and how they are used, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="87319-106">Aby zapoznać się z samouczkiem, który przeprowadzi Cię przez kroki tworzenia podstawowej usługi Windows Communication Foundation (WCF) i klienta programu, zobacz [samouczek wprowadzenie](../getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="87319-106">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../getting-started-tutorial.md).</span></span> <span data-ttu-id="87319-107">Aby uzyskać działającą przykładową aplikację, która składa się z podstawowej usługi i klienta, zobacz temat [Basic Data Contract](../samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="87319-107">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="87319-108">Tworzenie podstawowego kontraktu danych dla klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="87319-108">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="87319-109">Zadeklaruj, że typ ma kontrakt danych, stosując <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do klasy.</span><span class="sxs-lookup"><span data-stu-id="87319-109">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="87319-110">Należy zauważyć, że można serializować wszystkie typy publiczne, łącznie z tymi bez atrybutów.</span><span class="sxs-lookup"><span data-stu-id="87319-110">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="87319-111"><xref:System.Runtime.Serialization.DataContractSerializer>Jeśli <xref:System.Runtime.Serialization.DataContractAttribute> atrybut jest nieobecny, wnioskuje o umowę o dane.</span><span class="sxs-lookup"><span data-stu-id="87319-111">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="87319-112">Aby uzyskać więcej informacji, zobacz [typy serializacji](serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="87319-112">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
2. <span data-ttu-id="87319-113">Zdefiniuj elementy członkowskie (właściwości, pola lub zdarzenia), które są serializowane przez zastosowanie <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do każdego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="87319-113">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="87319-114">Te elementy członkowskie są nazywane elementami członkowskimi danych.</span><span class="sxs-lookup"><span data-stu-id="87319-114">These members are called data members.</span></span> <span data-ttu-id="87319-115">Domyślnie wszystkie typy publiczne są serializowane.</span><span class="sxs-lookup"><span data-stu-id="87319-115">By default, all public types are serializable.</span></span> <span data-ttu-id="87319-116">Aby uzyskać więcej informacji, zobacz [typy serializacji](serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="87319-116">For more information, see [Serializable Types](serializable-types.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="87319-117">Można zastosować <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut do pól prywatnych, co sprawia, że dane mają być widoczne dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="87319-117">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="87319-118">Upewnij się, że element członkowski nie zawiera poufnych danych.</span><span class="sxs-lookup"><span data-stu-id="87319-118">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87319-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="87319-119">Example</span></span>  
 <span data-ttu-id="87319-120">Poniższy przykład przedstawia sposób tworzenia kontraktu danych dla `Person` typu przez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów i do klasy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="87319-120">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="87319-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87319-121">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="87319-122">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="87319-122">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="87319-123">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="87319-123">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)
- [<span data-ttu-id="87319-124">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="87319-124">Getting Started</span></span>](../samples/getting-started-sample.md)
