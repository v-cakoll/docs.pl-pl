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
ms.openlocfilehash: 4e5e6b77cdb13c17557f176a37fbb9e7d42ab667
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047792"
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="4beac-102">Instrukcje: tworzenie podstawowego kontraktu danych dla klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="4beac-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="4beac-103">W tym temacie przedstawiono podstawowe kroki, aby utworzyć kontraktu danych za pomocą klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="4beac-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="4beac-104">Aby uzyskać więcej informacji na temat kontraktów danych i sposobu ich używania, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="4beac-104">For more information about data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="4beac-105">Aby uzyskać samouczek, który przeprowadzi kroki tworzenia podstawowych usług Windows Communication Foundation (WCF) i klienta, zobacz [Samouczek wprowadzający](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="4beac-105">For a tutorial that walks through the steps of creating a basic Windows Communication Foundation (WCF) service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="4beac-106">Pracy przykładowej aplikacji składający się z podstawowej usługi i klienta, zobacz [podstawowego kontraktu danych](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="4beac-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="4beac-107">Do utworzenia podstawowego kontraktu danych dla klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="4beac-107">To create a basic data contract for a class or structure</span></span>  
  
1. <span data-ttu-id="4beac-108">Zadeklaruj, że typ ma kontraktu danych, stosując <xref:System.Runtime.Serialization.DataContractAttribute> do klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4beac-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="4beac-109">Należy zauważyć, że wszystkie typy publiczne, w tym użytkownicy bez atrybuty, które można serializować.</span><span class="sxs-lookup"><span data-stu-id="4beac-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="4beac-110"><xref:System.Runtime.Serialization.DataContractSerializer> Wnioskuje kontraktu danych, jeśli <xref:System.Runtime.Serialization.DataContractAttribute> atrybut jest nieobecne.</span><span class="sxs-lookup"><span data-stu-id="4beac-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="4beac-111">Aby uzyskać więcej informacji, zobacz [typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="4beac-111">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2. <span data-ttu-id="4beac-112">Definiowanie elementów członkowskich (właściwości, pola lub zdarzenia), które są serializowane, stosując <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do każdego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="4beac-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="4beac-113">Te elementy członkowskie są nazywane składowych danych.</span><span class="sxs-lookup"><span data-stu-id="4beac-113">These members are called data members.</span></span> <span data-ttu-id="4beac-114">Domyślnie wszystkie typy publiczne są możliwe do serializacji.</span><span class="sxs-lookup"><span data-stu-id="4beac-114">By default, all public types are serializable.</span></span> <span data-ttu-id="4beac-115">Aby uzyskać więcej informacji, zobacz [typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="4beac-115">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4beac-116">Można zastosować <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do pola prywatne, powodując dane, które mają być widoczne dla innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="4beac-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="4beac-117">Pamiętaj, elementu członkowskiego nie zawiera poufnych danych.</span><span class="sxs-lookup"><span data-stu-id="4beac-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4beac-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="4beac-118">Example</span></span>  
 <span data-ttu-id="4beac-119">Poniższy przykład pokazuje, jak tworzenie kontraktu danych dla `Person` typu przez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutów do klasy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="4beac-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4beac-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4beac-120">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [<span data-ttu-id="4beac-121">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="4beac-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="4beac-122">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="4beac-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="4beac-123">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="4beac-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
