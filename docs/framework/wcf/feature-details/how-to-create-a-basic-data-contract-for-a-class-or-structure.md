---
title: 'Instrukcje: tworzenie podstawowego kontraktu danych dla klasy lub struktury'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
ms.openlocfilehash: 15c59f3ee7cbefafef7a304cfd1477685fff68f2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968462"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="b399c-102">Instrukcje: tworzenie podstawowego kontraktu danych dla klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="b399c-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="b399c-103">W tym temacie przedstawiono podstawowe kroki tworzenia kontraktu danych przy użyciu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="b399c-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="b399c-104">Aby uzyskać więcej informacji na temat kontraktów danych i sposobu ich użycia, zobacz [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="b399c-104">For more information about data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="b399c-105">Aby zapoznać się z samouczkiem, który przeprowadzi Cię przez kroki tworzenia podstawowej usługi Windows Communication Foundation (WCF) i klienta programu, zobacz [samouczek wprowadzenie](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="b399c-105">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="b399c-106">Aby uzyskać działającą przykładową aplikację, która składa się z podstawowej usługi i klienta, zobacz temat [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="b399c-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="b399c-107">Tworzenie podstawowego kontraktu danych dla klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="b399c-107">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="b399c-108">Zadeklaruj, że typ ma kontrakt danych, stosując <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do klasy.</span><span class="sxs-lookup"><span data-stu-id="b399c-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="b399c-109">Należy zauważyć, że można serializować wszystkie typy publiczne, łącznie z tymi bez atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b399c-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="b399c-110">Jeśli atrybut jest nieobecny, wnioskujeoumowęodane.<xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.DataContractAttribute></span><span class="sxs-lookup"><span data-stu-id="b399c-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="b399c-111">Aby uzyskać więcej informacji, zobacz [typy serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="b399c-111">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2. <span data-ttu-id="b399c-112">Zdefiniuj elementy członkowskie (właściwości, pola lub zdarzenia), które są serializowane przez zastosowanie <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do każdego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="b399c-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="b399c-113">Te elementy członkowskie są nazywane elementami członkowskimi danych.</span><span class="sxs-lookup"><span data-stu-id="b399c-113">These members are called data members.</span></span> <span data-ttu-id="b399c-114">Domyślnie wszystkie typy publiczne są serializowane.</span><span class="sxs-lookup"><span data-stu-id="b399c-114">By default, all public types are serializable.</span></span> <span data-ttu-id="b399c-115">Aby uzyskać więcej informacji, zobacz [typy serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="b399c-115">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b399c-116">Można zastosować <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut do pól prywatnych, co sprawia, że dane mają być widoczne dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="b399c-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="b399c-117">Upewnij się, że element członkowski nie zawiera poufnych danych.</span><span class="sxs-lookup"><span data-stu-id="b399c-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b399c-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="b399c-118">Example</span></span>  
 <span data-ttu-id="b399c-119">Poniższy przykład przedstawia sposób tworzenia kontraktu danych dla `Person` typu przez <xref:System.Runtime.Serialization.DataContractAttribute> zastosowanie atrybutów i <xref:System.Runtime.Serialization.DataMemberAttribute> do klasy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="b399c-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b399c-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b399c-120">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="b399c-121">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="b399c-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="b399c-122">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="b399c-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="b399c-123">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="b399c-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
