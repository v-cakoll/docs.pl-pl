---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 1292bc38ce1e542086edac5539c1b29e619e2a32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926385"
---
# <a name="bindings"></a><span data-ttu-id="ab754-101">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="ab754-101">\<bindings></span></span>

<span data-ttu-id="ab754-102">Można użyć elementu, `bindings` aby skonfigurować kolekcję powiązań standardowych i niestandardowych dla Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ab754-102">You can use the `bindings` element to configure a collection of standard and custom bindings for Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="ab754-103">Każdy wpis jest `binding` elementem, który może być identyfikowany przez jego `name`unikatowy.</span><span class="sxs-lookup"><span data-stu-id="ab754-103">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="ab754-104">Usługi używają powiązań przez łączenie ich przy użyciu `name`.</span><span class="sxs-lookup"><span data-stu-id="ab754-104">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="ab754-105">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="ab754-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="ab754-106">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="ab754-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="system-provided-bindings"></a><span data-ttu-id="ab754-107">Powiązania dostarczone przez system</span><span class="sxs-lookup"><span data-stu-id="ab754-107">System-provided bindings</span></span>
 
 <span data-ttu-id="ab754-108">Powiązania dostarczane przez system ukrywają złożoność stosu komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="ab754-108">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="ab754-109">Aplikacje korzystające z powiązań dostarczonych przez system nie wymagają pełnej kontroli nad stosem.</span><span class="sxs-lookup"><span data-stu-id="ab754-109">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="ab754-110">Atrybuty uwidocznione dla każdego powiązania dostarczonego przez system są najbardziej odpowiednie dla scenariusza użycia.</span><span class="sxs-lookup"><span data-stu-id="ab754-110">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="ab754-111">Sekcja konfiguracji dla każdego powiązania dostarczonego przez system może definiować kilka konfiguracji używanych do konfigurowania powiązania.</span><span class="sxs-lookup"><span data-stu-id="ab754-111">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="ab754-112">Każda konfiguracja jest identyfikowana przy użyciu unikatowej nazwy.</span><span class="sxs-lookup"><span data-stu-id="ab754-112">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="ab754-113">Nie jest możliwe dodawanie elementów lub atrybutów do powiązania dostarczonego przez system.</span><span class="sxs-lookup"><span data-stu-id="ab754-113">It isn't possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="ab754-114">Aby to zrobić, należy zaimplementować niestandardowe powiązanie zgodnie z opisem w sekcji [powiązania niestandardowe](#custom-bindings) .</span><span class="sxs-lookup"><span data-stu-id="ab754-114">To do so, you should implement a custom binding as described in the [Custom bindings](#custom-bindings) section.</span></span> <span data-ttu-id="ab754-115">Istnieje możliwość zdefiniowania niestandardowego powiązania, które naśladuje powiązanie dostarczone przez system i dodaje kilka ustawień, które aplikacja użytkownika chce mieć kontrolę.</span><span class="sxs-lookup"><span data-stu-id="ab754-115">It's possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
 <span data-ttu-id="ab754-116">Aby uzyskać listę powiązań dostarczanych przez system, zobacz [powiązania dostarczone przez system](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="ab754-116">For a list of system-provided bindings, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>  
  
## <a name="custom-bindings"></a><span data-ttu-id="ab754-117">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ab754-117">Custom bindings</span></span>

 <span data-ttu-id="ab754-118">Niestandardowe powiązania zapewniają pełną kontrolę nad stosem obsługi komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="ab754-118">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="ab754-119">Pojedyncze powiązanie definiuje stos komunikatów przez określenie elementów konfiguracji dla elementów stosu w kolejności, w jakiej występują na stosie.</span><span class="sxs-lookup"><span data-stu-id="ab754-119">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="ab754-120">Każdy element definiuje i konfiguruje jeden element stosu.</span><span class="sxs-lookup"><span data-stu-id="ab754-120">Each element defines and configures one element of the stack.</span></span> <span data-ttu-id="ab754-121">Musi istnieć jeden i tylko jeden `transport` element w każdym powiązaniu niestandardowym.</span><span class="sxs-lookup"><span data-stu-id="ab754-121">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="ab754-122">Bez tego elementu stos komunikatów jest niekompletny.</span><span class="sxs-lookup"><span data-stu-id="ab754-122">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="ab754-123">Kolejność, w której elementy pojawiają się w kwestiach stosu, ponieważ jest to kolejność, w której operacje są stosowane do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ab754-123">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="ab754-124">Wymagana kolejność elementów stosu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="ab754-124">The required order of stack elements is the following:</span></span>  
  
1. <span data-ttu-id="ab754-125">Transakcje (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="ab754-125">Transactions (optional)</span></span>  
  
2. <span data-ttu-id="ab754-126">Niezawodna obsługa komunikatów (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="ab754-126">Reliable messaging (optional)</span></span>  
  
3. <span data-ttu-id="ab754-127">Zabezpieczenia (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="ab754-127">Security (optional)</span></span>  
  
4. <span data-ttu-id="ab754-128">Pomocą</span><span class="sxs-lookup"><span data-stu-id="ab754-128">Encoder</span></span>  
  
5. <span data-ttu-id="ab754-129">Transportu</span><span class="sxs-lookup"><span data-stu-id="ab754-129">Transport</span></span>  
  
 <span data-ttu-id="ab754-130">Niestandardowe powiązania są identyfikowane przez `name` ich atrybut.</span><span class="sxs-lookup"><span data-stu-id="ab754-130">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="ab754-131">Aby uzyskać więcej informacji na temat powiązań niestandardowych, zobacz [niestandardowe powiązania](../../../wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="ab754-131">For more information on custom bindings, see [Custom Bindings](../../../wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab754-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab754-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>  
- [<span data-ttu-id="ab754-133">Powiązania</span><span class="sxs-lookup"><span data-stu-id="ab754-133">Bindings</span></span>](../../../wcf/bindings.md)  
- [<span data-ttu-id="ab754-134">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="ab754-134">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)  
- [<span data-ttu-id="ab754-135">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ab754-135">\<customBinding></span></span>](custombinding.md)  
- [<span data-ttu-id="ab754-136">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="ab754-136">\<binding></span></span>](../../../misc/binding.md)
