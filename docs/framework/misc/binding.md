---
title: '&lt;Powiązanie&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: d72b3a34e0696df944b2338c89f167c8bfa06400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392255"
---
# <a name="ltbindinggt"></a><span data-ttu-id="f8cb1-102">&lt;Powiązanie&gt;</span><span class="sxs-lookup"><span data-stu-id="f8cb1-102">&lt;binding&gt;</span></span>
<span data-ttu-id="f8cb1-103">Można użyć `binding` elementu do konfigurowania różnych typów wstępnie zdefiniowanych powiązań dostarczonych przez Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f8cb1-103">You can use the `binding` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="f8cb1-104">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="f8cb1-104">System-Provided Binding</span></span>  
 <span data-ttu-id="f8cb1-105">Powiązania dostarczane przez system neutralizują złożoność platformy WCF stosem obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-105">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="f8cb1-106">Nie wymagają pełną kontrolę nad stosu aplikacji za pomocą powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-106">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="f8cb1-107">Atrybuty widoczne dla każdego powiązania dostarczane przez system są najbardziej odpowiednie dla scenariusza użycia adresów powiązania.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-107">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="f8cb1-108">Sekcja konfiguracji dla każdego powiązania dostarczane przez system można określić kilka konfiguracje używane do konfigurowania wiązania.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-108">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="f8cb1-109">Każdej konfiguracji jest identyfikowany przez unikatową nazwę.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-109">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="f8cb1-110">Nie jest możliwe do dodawania elementów lub atrybutów do powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-110">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="f8cb1-111">Aby to zrobić, należy zaimplementować niestandardowego powiązania, zgodnie z opisem w sekcji "Niestandardowego powiązania" tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-111">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="f8cb1-112">Istnieje możliwość definiowania niestandardowego powiązania, który naśladuje dostarczane przez system powiązanie doskonale i dodaje kilka ustawień aplikacji użytkownik chce mają kontrolę nad.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-112">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="f8cb1-113">Powiązanie niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f8cb1-113">Custom Binding</span></span>  
 <span data-ttu-id="f8cb1-114">Powiązania niestandardowe zapewniają pełną kontrolę nad stosem obsługi wiadomości WCF.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-114">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="f8cb1-115">Powiązanie poszczególnych definiuje stosu wiadomości, określając elementy konfiguracji dla elementów stosu w kolejności, w jakiej znajdują się na stosie.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-115">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="f8cb1-116">Każdy element definiuje i konfiguruje jeden element stosu.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-116">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="f8cb1-117">Musi istnieć jeden i tylko jeden `transport` element w każdym niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-117">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="f8cb1-118">Bez tego elementu stosem obsługi wiadomości jest niekompletna.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-118">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="f8cb1-119">Kolejność wyświetlania elementów w stosie ma znaczenie, ponieważ jest on kolejność, w której operacji są stosowane do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-119">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="f8cb1-120">Zalecana kolejność elementów stosu jest następujący:</span><span class="sxs-lookup"><span data-stu-id="f8cb1-120">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="f8cb1-121">Transakcje (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="f8cb1-121">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="f8cb1-122">Niezawodnej obsługi komunikatów (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="f8cb1-122">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="f8cb1-123">Zabezpieczeń (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="f8cb1-123">Security (optional)</span></span>  
  
4.  <span data-ttu-id="f8cb1-124">Koder</span><span class="sxs-lookup"><span data-stu-id="f8cb1-124">Encoder</span></span>  
  
5.  <span data-ttu-id="f8cb1-125">Transportu</span><span class="sxs-lookup"><span data-stu-id="f8cb1-125">Transport</span></span>  
  
 <span data-ttu-id="f8cb1-126">Powiązania niestandardowe są identyfikowane za pomocą ich `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f8cb1-126">Custom bindings are identified by their `name` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8cb1-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8cb1-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [<span data-ttu-id="f8cb1-128">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f8cb1-128">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f8cb1-129">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f8cb1-129">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="f8cb1-130">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f8cb1-130">\<customBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
