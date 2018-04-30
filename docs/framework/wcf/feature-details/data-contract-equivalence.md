---
title: Równoważność kontraktów danych
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
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aebd21186f7d038dfa5d7c3c65f833d41f4a1f71
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="data-contract-equivalence"></a><span data-ttu-id="d780d-102">Równoważność kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="d780d-102">Data Contract Equivalence</span></span>
<span data-ttu-id="d780d-103">Klient pomyślnie wysyłania danych określonego typu usługi lub usług pomyślnie wysyłać dane do klienta wysłane typu nie zawsze musi istnieje po stronie odbiorczej.</span><span class="sxs-lookup"><span data-stu-id="d780d-103">For a client to successfully send data of a certain type to a service, or a service to successfully send data to a client, the sent type does not necessarily have to exist on the receiving end.</span></span> <span data-ttu-id="d780d-104">Jedynym wymaganiem jest równoważne kontraktów danych obu typów.</span><span class="sxs-lookup"><span data-stu-id="d780d-104">The only requirement is that the data contracts of both types be equivalent.</span></span> <span data-ttu-id="d780d-105">(Czasami strict równoważność nie jest wymagana, zgodnie z opisem w [przechowywanie wersji kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)</span><span class="sxs-lookup"><span data-stu-id="d780d-105">(Sometimes, strict equivalence is not required, as discussed in [Data Contract Versioning](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)</span></span>  
  
 <span data-ttu-id="d780d-106">Dla kontraktów danych jako równoważne muszą mieć taką samą przestrzeń nazw i nazwę.</span><span class="sxs-lookup"><span data-stu-id="d780d-106">For data contracts to be equivalent, they must have the same namespace and name.</span></span> <span data-ttu-id="d780d-107">Ponadto każdy element członkowski danych na jednej stronie musi mieć element członkowski danych równoważne z drugiej strony.</span><span class="sxs-lookup"><span data-stu-id="d780d-107">Additionally, each data member on one side must have an equivalent data member on the other side.</span></span>  
  
 <span data-ttu-id="d780d-108">Elementów członkowskich danych jako równoważne muszą mieć taką samą nazwę.</span><span class="sxs-lookup"><span data-stu-id="d780d-108">For data members to be equivalent, they must have the same name.</span></span> <span data-ttu-id="d780d-109">Ponadto musi reprezentować ten sam typ danych. oznacza to, że ich kontraktów danych musi być taka sama.</span><span class="sxs-lookup"><span data-stu-id="d780d-109">Additionally, they must represent the same type of data; that is, their data contracts must be equivalent.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d780d-110">Należy pamiętać, że kontraktu danych, nazwy i przestrzeni nazw, jak również nazwy elementów członkowskich danych, jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="d780d-110">Note that data contract names and namespaces, as well as data member names, are case-sensitive.</span></span>  
  
 <span data-ttu-id="d780d-111">Aby uzyskać więcej informacji na temat nazw kontraktu danych i przestrzenie nazw, jak również nazwy elementów członkowskich danych, zobacz [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md).</span><span class="sxs-lookup"><span data-stu-id="d780d-111">For more information about data contract names and namespaces, as well as data member names, see [Data Contract Names](../../../../docs/framework/wcf/feature-details/data-contract-names.md).</span></span>  
  
 <span data-ttu-id="d780d-112">Jeśli istnieją dwa typy na tej samej stronie (nadawcy i adresata) i ich kontraktów danych nie są równoważne (na przykład użytkownicy mają elementy członkowskie danych różnych), nie należy nadawać je taką samą nazwę i przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="d780d-112">If two types exist on the same side (sender or receiver) and their data contracts are not equivalent (for example, they have different data members), you should not give them the same name and namespace.</span></span> <span data-ttu-id="d780d-113">W ten sposób może spowodować wyjątki zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="d780d-113">Doing so may cause exceptions to be thrown.</span></span>  
  
 <span data-ttu-id="d780d-114">Kontrakty danych dla następujących typów są równoważne:</span><span class="sxs-lookup"><span data-stu-id="d780d-114">The data contracts for the following types are equivalent:</span></span>  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a><span data-ttu-id="d780d-115">Równoważność kolejność elementów członkowskich danych i kontraktu danych</span><span class="sxs-lookup"><span data-stu-id="d780d-115">Data Member Order and Data Contract equivalence</span></span>  
 <span data-ttu-id="d780d-116">Przy użyciu <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> właściwość <xref:System.Runtime.Serialization.DataMemberAttribute> klasy może mieć wpływ na równoważność kontraktów danych.</span><span class="sxs-lookup"><span data-stu-id="d780d-116">Using the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> class may affect data contract equivalence.</span></span> <span data-ttu-id="d780d-117">Kontrakty danych musi mieć elementy członkowskie, które pojawiają się w tej samej kolejności równoważne.</span><span class="sxs-lookup"><span data-stu-id="d780d-117">The data contracts must have members that appear in the same order to be equivalent.</span></span> <span data-ttu-id="d780d-118">Domyślna kolejność to alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="d780d-118">The default order is alphabetical.</span></span> <span data-ttu-id="d780d-119">Aby uzyskać więcej informacji, zobacz [kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="d780d-119">For more information, see [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="d780d-120">Na przykład następujący kod powoduje kontraktów danych równoważne.</span><span class="sxs-lookup"><span data-stu-id="d780d-120">For example, the following code results in equivalent data contracts.</span></span>  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 <span data-ttu-id="d780d-121">Jednak następujące nie powoduje kontraktu danych równoważne.</span><span class="sxs-lookup"><span data-stu-id="d780d-121">However, the following does not result in an equivalent data contract.</span></span>  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a><span data-ttu-id="d780d-122">Dziedziczenie, interfejsów i równoważność kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="d780d-122">Inheritance, Interfaces, and Data Contract Equivalence</span></span>  
 <span data-ttu-id="d780d-123">Podczas określania równoważność, kontraktu danych, która dziedziczy inny kontrakt danych jest traktowana tak, jakby była tylko jeden kontrakt danych obejmuje wszystkie elementy członkowskie danych z typu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="d780d-123">When determining equivalence, a data contract that inherits from another data contract is treated as if it is just one data contract that includes all of the data members from the base type.</span></span> <span data-ttu-id="d780d-124">Należy pamiętać, że kolejność elementów członkowskich danych muszą być zgodne oraz że poprzedzają elementów członkowskich typu podstawowego uzyskane elementy członkowskie typu w kolejności.</span><span class="sxs-lookup"><span data-stu-id="d780d-124">Keep in mind that the order of the data members must match and that base type members precede derived type members in the order.</span></span> <span data-ttu-id="d780d-125">Ponadto jeśli jak w poniższym przykładzie kodu, elementy członkowskie danych dwa mają taką samą wartość kolejności, kolejność elementów członkowskich tych danych jest alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="d780d-125">Furthermore, if, as in the following code example, two data members have the same order value, the ordering for those data members is alphabetical.</span></span> <span data-ttu-id="d780d-126">Aby uzyskać więcej informacji, zobacz [kolejność elementów członkowskich danych](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="d780d-126">For more information, see [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="d780d-127">W poniższym przykładzie dla typu kontraktu danych `Employee` jest odpowiednikiem kontraktu danych dla typu `Worker`.</span><span class="sxs-lookup"><span data-stu-id="d780d-127">In the following example, the data contract for type `Employee` is equivalent to the data contract for the type `Worker`.</span></span>  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 <span data-ttu-id="d780d-128">Podczas przekazywania parametrów i zwracanych wartości między klientem a usługą, kontrakt danych z klasy podstawowej nie można wysłać podczas odbierania punkt końcowy oczekuje kontraktu danych z klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="d780d-128">When passing parameters and return values between a client and a service, a data contract from a base class cannot be sent when the receiving endpoint expects a data contract from a derived class.</span></span> <span data-ttu-id="d780d-129">Jest to zgodne z zorientowane obiektowo programowania rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="d780d-129">This is in accordance with object-oriented programming tenets.</span></span> <span data-ttu-id="d780d-130">W poprzednim przykładzie, typu obiektu `Person` nie mogą być wysyłane podczas `Employee` jest oczekiwany.</span><span class="sxs-lookup"><span data-stu-id="d780d-130">In the previous example, an object of type `Person` cannot be sent when an `Employee` is expected.</span></span>  
  
 <span data-ttu-id="d780d-131">Kontrakt danych z klasy pochodnej mogą być wysyłane, gdy kontrakt danych z klasy podstawowej jest oczekiwany, ale tylko w przypadku odbierania punktu końcowego "wie" użycia typu pochodnego <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d780d-131">A data contract from a derived class can be sent when a data contract from a base class is expected, but only if the receiving endpoint "knows" of the derived type using the <xref:System.Runtime.Serialization.KnownTypeAttribute>.</span></span> <span data-ttu-id="d780d-132">Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="d780d-132">For more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span> <span data-ttu-id="d780d-133">W poprzednim przykładzie, typu obiektu `Employee` mogą być wysyłane podczas `Person` jest oczekiwany, ale tylko wtedy, gdy kod odbiornika wykorzystuje <xref:System.Runtime.Serialization.KnownTypeAttribute> należeć listy znanych typów.</span><span class="sxs-lookup"><span data-stu-id="d780d-133">In the previous example, an object of type `Employee` can be sent when a `Person` is expected, but only if the receiver code employs the <xref:System.Runtime.Serialization.KnownTypeAttribute> to include it in the list of known types.</span></span>  
  
 <span data-ttu-id="d780d-134">Podczas przekazywania parametrów i zwracanych wartości między aplikacjami, jeśli oczekiwany typ to interfejs, jest odpowiednikiem oczekiwanym typem jest typu <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="d780d-134">When passing parameters and return values between applications, if the expected type is an interface, it is equivalent to the expected type being of type <xref:System.Object>.</span></span> <span data-ttu-id="d780d-135">Ponieważ każdy typ ostatecznie pochodną <xref:System.Object>, kontrakt danych, co ostatecznie pochodną kontraktu danych dla <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="d780d-135">Because every type ultimately derives from <xref:System.Object>, every data contract ultimately derives from the data contract for <xref:System.Object>.</span></span> <span data-ttu-id="d780d-136">W związku z tym dowolnego typu kontraktu danych mogą być przekazywane, gdy interfejs.</span><span class="sxs-lookup"><span data-stu-id="d780d-136">Thus, any data contract type can be passed when an interface is expected.</span></span> <span data-ttu-id="d780d-137">Dodatkowe kroki są wymagane do pomyślnie pracy z interfejsami; Aby uzyskać więcej informacji, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="d780d-137">Additional steps are required to successfully work with interfaces; for more information, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d780d-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d780d-138">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="d780d-139">Kolejność elementów członkowskich danych</span><span class="sxs-lookup"><span data-stu-id="d780d-139">Data Member Order</span></span>](../../../../docs/framework/wcf/feature-details/data-member-order.md)  
 [<span data-ttu-id="d780d-140">Znane typy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="d780d-140">Data Contract Known Types</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="d780d-141">Nazwy kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="d780d-141">Data Contract Names</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-names.md)
