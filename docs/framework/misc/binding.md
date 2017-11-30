---
title: "&lt;Powiązanie&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 874a3766a64a9abb7c35efd5ac0a0f698707281e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltbindinggt"></a><span data-ttu-id="b6340-102">&lt;Powiązanie&gt;</span><span class="sxs-lookup"><span data-stu-id="b6340-102">&lt;binding&gt;</span></span>
<span data-ttu-id="b6340-103">Można użyć `binding` elementu do konfigurowania różnych typów wstępnie zdefiniowanych powiązań dostarczonych przez Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b6340-103">You can use the `binding` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="b6340-104">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="b6340-104">System-Provided Binding</span></span>  
 <span data-ttu-id="b6340-105">Powiązania dostarczane przez system neutralizują złożoność platformy WCF stosem obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b6340-105">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="b6340-106">Nie wymagają pełną kontrolę nad stosu aplikacji za pomocą powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="b6340-106">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="b6340-107">Atrybuty widoczne dla każdego powiązania dostarczane przez system są najbardziej odpowiednie dla scenariusza użycia adresów powiązania.</span><span class="sxs-lookup"><span data-stu-id="b6340-107">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="b6340-108">Sekcja konfiguracji dla każdego powiązania dostarczane przez system można określić kilka konfiguracje używane do konfigurowania wiązania.</span><span class="sxs-lookup"><span data-stu-id="b6340-108">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="b6340-109">Każdej konfiguracji jest identyfikowany przez unikatową nazwę.</span><span class="sxs-lookup"><span data-stu-id="b6340-109">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="b6340-110">Nie jest możliwe do dodawania elementów lub atrybutów do powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="b6340-110">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="b6340-111">Aby to zrobić, należy zaimplementować niestandardowego powiązania, zgodnie z opisem w sekcji "Niestandardowego powiązania" tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b6340-111">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="b6340-112">Istnieje możliwość definiowania niestandardowego powiązania, który naśladuje dostarczane przez system powiązanie doskonale i dodaje kilka ustawień aplikacji użytkownik chce mają kontrolę nad.</span><span class="sxs-lookup"><span data-stu-id="b6340-112">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="b6340-113">Powiązanie niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b6340-113">Custom Binding</span></span>  
 <span data-ttu-id="b6340-114">Powiązania niestandardowe zapewniają pełną kontrolę nad stosem obsługi wiadomości WCF.</span><span class="sxs-lookup"><span data-stu-id="b6340-114">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="b6340-115">Powiązanie poszczególnych definiuje stosu wiadomości, określając elementy konfiguracji dla elementów stosu w kolejności, w jakiej znajdują się na stosie.</span><span class="sxs-lookup"><span data-stu-id="b6340-115">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="b6340-116">Każdy element definiuje i konfiguruje jeden element stosu.</span><span class="sxs-lookup"><span data-stu-id="b6340-116">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="b6340-117">Musi istnieć jeden i tylko jeden `transport` element w każdym niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b6340-117">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="b6340-118">Bez tego elementu stosem obsługi wiadomości jest niekompletna.</span><span class="sxs-lookup"><span data-stu-id="b6340-118">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="b6340-119">Kolejność wyświetlania elementów w stosie ma znaczenie, ponieważ jest on kolejność, w której operacji są stosowane do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b6340-119">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="b6340-120">Zalecana kolejność elementów stosu jest następujący:</span><span class="sxs-lookup"><span data-stu-id="b6340-120">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="b6340-121">Transakcje (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="b6340-121">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="b6340-122">Niezawodnej obsługi komunikatów (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="b6340-122">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="b6340-123">Zabezpieczeń (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="b6340-123">Security (optional)</span></span>  
  
4.  <span data-ttu-id="b6340-124">Koder</span><span class="sxs-lookup"><span data-stu-id="b6340-124">Encoder</span></span>  
  
5.  <span data-ttu-id="b6340-125">Transportu</span><span class="sxs-lookup"><span data-stu-id="b6340-125">Transport</span></span>  
  
 <span data-ttu-id="b6340-126">Powiązania niestandardowe są identyfikowane za pomocą ich `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b6340-126">Custom bindings are identified by their `name` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6340-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6340-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [<span data-ttu-id="b6340-128">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b6340-128">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b6340-129">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b6340-129">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b6340-130">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b6340-130">\<customBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
