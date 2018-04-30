---
title: 'Instrukcje: Tworzenie podstawowego kontraktu danych dla klasy lub struktury'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataMemberAttribute
- DataContractAttribute class
- data contracts [WCF], creating for a class or structure
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 43fa318d2910fcd8b1d9ce75fc02d75bb39d4079
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="b2a34-102">Instrukcje: Tworzenie podstawowego kontraktu danych dla klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="b2a34-102">How to: Create a Basic Data Contract for a Class or Structure</span></span>
<span data-ttu-id="b2a34-103">W tym temacie przedstawiono podstawowe kroki, aby utworzyć kontrakt danych przy użyciu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="b2a34-103">This topic shows the basic steps to create a data contract using a class or structure.</span></span> <span data-ttu-id="b2a34-104">Aby uzyskać więcej informacji na temat kontraktów danych i sposobu ich używania, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="b2a34-104">For more information about data contracts and how they are used, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="b2a34-105">Samouczek, który przeprowadzi Cię przez kroki tworzenia podstawowego [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi i klienta, zobacz [Wprowadzenie — samouczek](../../../../docs/framework/wcf/getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="b2a34-105">For a tutorial that walks through the steps of creating a basic [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and client, see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md).</span></span> <span data-ttu-id="b2a34-106">Dla aplikacji przykładowej pracy, który składa się z podstawowej usługi i klienta, zobacz [podstawowego kontraktu danych](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span><span class="sxs-lookup"><span data-stu-id="b2a34-106">For a working sample application that consists of a basic service and client, see [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md).</span></span>  
  
### <a name="to-create-a-basic-data-contract-for-a-class-or-structure"></a><span data-ttu-id="b2a34-107">Aby utworzyć podstawowego kontraktu danych dla klasy lub struktury</span><span class="sxs-lookup"><span data-stu-id="b2a34-107">To create a basic data contract for a class or structure</span></span>  
  
1.  <span data-ttu-id="b2a34-108">Deklaruje, że typ ma kontraktu danych poprzez zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> do klasy atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b2a34-108">Declare that the type has a data contract by applying the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class.</span></span> <span data-ttu-id="b2a34-109">Należy zauważyć, że wszystkie typy publiczne, w tym użytkownicy bez atrybutów, które można serializować.</span><span class="sxs-lookup"><span data-stu-id="b2a34-109">Note that all public types, including those without attributes, are serializable.</span></span> <span data-ttu-id="b2a34-110"><xref:System.Runtime.Serialization.DataContractSerializer> Wnioskuje kontraktu danych, jeśli <xref:System.Runtime.Serialization.DataContractAttribute> nie jest obecny atrybut.</span><span class="sxs-lookup"><span data-stu-id="b2a34-110">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract if the <xref:System.Runtime.Serialization.DataContractAttribute> attribute is absent.</span></span> <span data-ttu-id="b2a34-111">Aby uzyskać więcej informacji, zobacz [typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="b2a34-111">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
2.  <span data-ttu-id="b2a34-112">Zdefiniuj członków (właściwości, pola lub zdarzeń), które są serializowane, stosując <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu do każdego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="b2a34-112">Define the members (properties, fields, or events) that are serialized by applying the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each member.</span></span> <span data-ttu-id="b2a34-113">Elementy te są określane jako elementy członkowskie danych.</span><span class="sxs-lookup"><span data-stu-id="b2a34-113">These members are called data members.</span></span> <span data-ttu-id="b2a34-114">Domyślnie wszystkie typy publiczne jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="b2a34-114">By default, all public types are serializable.</span></span> <span data-ttu-id="b2a34-115">Aby uzyskać więcej informacji, zobacz [typów możliwych do serializacji](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="b2a34-115">For more information, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b2a34-116">Możesz zastosować <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu pola prywatne, powodując danych mają być uwidaczniane w innym.</span><span class="sxs-lookup"><span data-stu-id="b2a34-116">You can apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to private fields, causing the data to be exposed to others.</span></span> <span data-ttu-id="b2a34-117">Pamiętaj, że element członkowski nie zawiera danych poufnych.</span><span class="sxs-lookup"><span data-stu-id="b2a34-117">Be sure that the member does not contain sensitive data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2a34-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2a34-118">Example</span></span>  
 <span data-ttu-id="b2a34-119">Poniższy przykład przedstawia sposób tworzenia kontraktu danych dla `Person` typu stosując <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty do klasy i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="b2a34-119">The following example shows how to create a data contract for the `Person` type by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the class and its members.</span></span>  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b2a34-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2a34-120">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="b2a34-121">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="b2a34-121">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="b2a34-122">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="b2a34-122">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="b2a34-123">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="b2a34-123">Getting Started</span></span>](../../../../docs/framework/wcf/samples/getting-started-sample.md)
