---
title: '&lt;Powiązania&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: fb4fafda31205e2ce5efd01ab265fcacfa70bdf6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539197"
---
# <a name="ltbindinggt"></a><span data-ttu-id="a9023-102">&lt;Powiązania&gt;</span><span class="sxs-lookup"><span data-stu-id="a9023-102">&lt;binding&gt;</span></span>
<span data-ttu-id="a9023-103">Możesz użyć `binding` elementu do konfigurowania różnych typów wstępnie zdefiniowanych powiązań dostarczonych przez Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a9023-103">You can use the `binding` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="a9023-104">System-Provided Binding</span><span class="sxs-lookup"><span data-stu-id="a9023-104">System-Provided Binding</span></span>  
 <span data-ttu-id="a9023-105">Powiązania dostarczane przez system ukrywają złożoność architektury WCF stosem obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a9023-105">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="a9023-106">Aplikacje przy użyciu powiązania dostarczane przez system nie wymagają pełną kontrolę nad stosu.</span><span class="sxs-lookup"><span data-stu-id="a9023-106">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="a9023-107">Atrybuty narażonych na każdego powiązania dostarczane przez system są tymi najbardziej odpowiednie dla scenariusza użycia adresów powiązania.</span><span class="sxs-lookup"><span data-stu-id="a9023-107">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="a9023-108">Sekcja konfiguracji dla każdego powiązania dostarczane przez system, można zdefiniować kilka konfiguracji używane do konfigurowania wiązania.</span><span class="sxs-lookup"><span data-stu-id="a9023-108">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="a9023-109">Każdej konfiguracji jest identyfikowane przez unikatową nazwę.</span><span class="sxs-lookup"><span data-stu-id="a9023-109">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="a9023-110">Nie jest możliwe dodać elementy lub atrybuty do powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="a9023-110">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="a9023-111">Aby to zrobić, należy zaimplementować niestandardowego powiązania, zgodnie z opisem w sekcji "Niestandardowego powiązania" tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a9023-111">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="a9023-112">Istnieje możliwość zdefiniowania niestandardowego powiązania, który naśladuje dostarczane przez system powiązań doskonale i dodaje kilka ustawień aplikacji użytkownik chce, aby mieć kontrolę nad.</span><span class="sxs-lookup"><span data-stu-id="a9023-112">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="a9023-113">Powiązanie niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a9023-113">Custom Binding</span></span>  
 <span data-ttu-id="a9023-114">Powiązania niestandardowe zapewniają pełną kontrolę nad stosem obsługi wiadomości usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="a9023-114">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="a9023-115">Powiązanie poszczególnych definiuje stosu wiadomości, określając elementów konfiguracji dla elementów stosu w kolejności, w jakiej znajdują się na stosie.</span><span class="sxs-lookup"><span data-stu-id="a9023-115">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="a9023-116">Każdy element definiuje i konfiguruje jeden element stosu.</span><span class="sxs-lookup"><span data-stu-id="a9023-116">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="a9023-117">Musi istnieć jeden i tylko jeden `transport` elementu w każdej niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a9023-117">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="a9023-118">Bez tego elementu stosem obsługi wiadomości jest niekompletna.</span><span class="sxs-lookup"><span data-stu-id="a9023-118">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="a9023-119">Kolejność wyświetlania elementów w stosie ma znaczenie, ponieważ jest on kolejność, w której operacje są stosowane do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a9023-119">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="a9023-120">Zalecana kolejność elementów stosu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="a9023-120">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="a9023-121">Transakcje (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="a9023-121">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="a9023-122">Niezawodna obsługa komunikatów (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="a9023-122">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="a9023-123">Zabezpieczenia (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="a9023-123">Security (optional)</span></span>  
  
4.  <span data-ttu-id="a9023-124">Koder</span><span class="sxs-lookup"><span data-stu-id="a9023-124">Encoder</span></span>  
  
5.  <span data-ttu-id="a9023-125">Transport</span><span class="sxs-lookup"><span data-stu-id="a9023-125">Transport</span></span>  
  
 <span data-ttu-id="a9023-126">Powiązania niestandardowe są identyfikowane przez ich `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a9023-126">Custom bindings are identified by their `name` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9023-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9023-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- [<span data-ttu-id="a9023-128">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a9023-128">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a9023-129">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a9023-129">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a9023-130">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a9023-130">\<customBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
