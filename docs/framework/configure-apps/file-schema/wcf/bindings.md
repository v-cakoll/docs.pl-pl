---
title: "&lt;powiązania&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d89fc465c1e82fab638b57dbf712f1396385f80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltbindingsgt"></a><span data-ttu-id="a8bc0-102">&lt;powiązania&gt;</span><span class="sxs-lookup"><span data-stu-id="a8bc0-102">&lt;bindings&gt;</span></span>
<span data-ttu-id="a8bc0-103">Ta sekcja przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-103">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="a8bc0-104">Każdy wpis jest `binding` element, który można zidentyfikować przez jego unikatowy `name`.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-104">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="a8bc0-105">Usługi używają powiązania łącząc je za pomocą `name`.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-105">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="a8bc0-106">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a8bc0-107">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a8bc0-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="a8bc0-108">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="a8bc0-108">System-Provided Binding</span></span>  
 <span data-ttu-id="a8bc0-109">Powiązania dostarczane przez system neutralizują złożoność platformy WCF stosem obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-109">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="a8bc0-110">Nie wymagają pełną kontrolę nad stosu aplikacji za pomocą powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-110">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="a8bc0-111">Atrybuty widoczne dla każdego powiązania dostarczane przez system są najbardziej odpowiednie dla scenariusza użycia adresów powiązania.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-111">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="a8bc0-112">Sekcja konfiguracji dla każdego powiązania dostarczane przez system można określić kilka konfiguracje używane do konfigurowania wiązania.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-112">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="a8bc0-113">Każdej konfiguracji jest identyfikowany przez unikatową nazwę.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-113">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="a8bc0-114">Nie jest możliwe do dodawania elementów lub atrybutów do powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-114">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="a8bc0-115">Aby to zrobić, należy zaimplementować niestandardowego powiązania, zgodnie z opisem w sekcji "Niestandardowego powiązania" tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-115">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="a8bc0-116">Istnieje możliwość definiowania niestandardowego powiązania, który naśladuje dostarczane przez system powiązanie doskonale i dodaje kilka ustawień aplikacji użytkownik chce mają kontrolę nad.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-116">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
 <span data-ttu-id="a8bc0-117">Aby uzyskać listę powiązania dostarczane przez system, zobacz [powiązania System-Provided](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="a8bc0-117">For a list of system-provided bindings, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="a8bc0-118">Powiązanie niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a8bc0-118">Custom Binding</span></span>  
 <span data-ttu-id="a8bc0-119">Powiązania niestandardowe zapewniają pełną kontrolę nad stosem obsługi wiadomości WCF.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-119">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="a8bc0-120">Powiązanie poszczególnych definiuje stosu wiadomości, określając elementy konfiguracji dla elementów stosu w kolejności, w jakiej znajdują się na stosie.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-120">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="a8bc0-121">Każdy element definiuje i konfiguruje jeden element stosu.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-121">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="a8bc0-122">Musi istnieć jeden i tylko jeden `transport` element w każdym niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-122">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="a8bc0-123">Bez tego elementu stosem obsługi wiadomości jest niekompletna.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-123">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="a8bc0-124">Kolejność wyświetlania elementów w stosie ma znaczenie, ponieważ jest on kolejność, w której operacji są stosowane do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-124">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="a8bc0-125">Wymagana kolejność elementów stosu jest następujący:</span><span class="sxs-lookup"><span data-stu-id="a8bc0-125">The required order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="a8bc0-126">Transakcje (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="a8bc0-126">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="a8bc0-127">Niezawodnej obsługi komunikatów (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="a8bc0-127">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="a8bc0-128">Zabezpieczeń (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="a8bc0-128">Security (optional)</span></span>  
  
4.  <span data-ttu-id="a8bc0-129">Koder</span><span class="sxs-lookup"><span data-stu-id="a8bc0-129">Encoder</span></span>  
  
5.  <span data-ttu-id="a8bc0-130">Transportu</span><span class="sxs-lookup"><span data-stu-id="a8bc0-130">Transport</span></span>  
  
 <span data-ttu-id="a8bc0-131">Powiązania niestandardowe są identyfikowane za pomocą ich `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a8bc0-131">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="a8bc0-132">Aby uzyskać więcej informacji na powiązań niestandardowych, zobacz [niestandardowego powiązania](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="a8bc0-132">For more information on custom bindings, see [Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8bc0-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8bc0-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [<span data-ttu-id="a8bc0-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a8bc0-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a8bc0-135">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a8bc0-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a8bc0-136">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a8bc0-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="a8bc0-137">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a8bc0-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
