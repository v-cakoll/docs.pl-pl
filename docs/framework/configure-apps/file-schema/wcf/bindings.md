---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: fe8f620668e35183890b8bba1f254a74c962f8d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139664"
---
# \<bindings>

<span data-ttu-id="0175a-101">Można użyć elementu, `bindings` Aby skonfigurować kolekcję powiązań standardowych i niestandardowych dla Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0175a-101">You can use the `bindings` element to configure a collection of standard and custom bindings for Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="0175a-102">Każdy wpis jest `binding` elementem, który może być identyfikowany przez jego unikatowy `name` .</span><span class="sxs-lookup"><span data-stu-id="0175a-102">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="0175a-103">Usługi używają powiązań przez łączenie ich przy użyciu `name` .</span><span class="sxs-lookup"><span data-stu-id="0175a-103">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="0175a-104">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="0175a-104">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0175a-105">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0175a-105">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="system-provided-bindings"></a><span data-ttu-id="0175a-106">Powiązania dostarczone przez system</span><span class="sxs-lookup"><span data-stu-id="0175a-106">System-provided bindings</span></span>

<span data-ttu-id="0175a-107">Powiązania dostarczane przez system ukrywają złożoność stosu komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="0175a-107">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="0175a-108">Aplikacje korzystające z powiązań dostarczonych przez system nie wymagają pełnej kontroli nad stosem.</span><span class="sxs-lookup"><span data-stu-id="0175a-108">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="0175a-109">Atrybuty uwidocznione dla każdego powiązania dostarczonego przez system są najbardziej odpowiednie dla scenariusza użycia.</span><span class="sxs-lookup"><span data-stu-id="0175a-109">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>

<span data-ttu-id="0175a-110">Sekcja konfiguracji dla każdego powiązania dostarczonego przez system może definiować kilka konfiguracji używanych do konfigurowania powiązania.</span><span class="sxs-lookup"><span data-stu-id="0175a-110">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="0175a-111">Każda konfiguracja jest identyfikowana przy użyciu unikatowej nazwy.</span><span class="sxs-lookup"><span data-stu-id="0175a-111">Each configuration is identified by a unique name.</span></span>

<span data-ttu-id="0175a-112">Nie jest możliwe dodawanie elementów lub atrybutów do powiązania dostarczonego przez system.</span><span class="sxs-lookup"><span data-stu-id="0175a-112">It isn't possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="0175a-113">Aby to zrobić, należy zaimplementować niestandardowe powiązanie zgodnie z opisem w sekcji [powiązania niestandardowe](#custom-bindings) .</span><span class="sxs-lookup"><span data-stu-id="0175a-113">To do so, you should implement a custom binding as described in the [Custom bindings](#custom-bindings) section.</span></span> <span data-ttu-id="0175a-114">Istnieje możliwość zdefiniowania niestandardowego powiązania, które naśladuje powiązanie dostarczone przez system i dodaje kilka ustawień, które aplikacja użytkownika chce mieć kontrolę.</span><span class="sxs-lookup"><span data-stu-id="0175a-114">It's possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  

<span data-ttu-id="0175a-115">Aby uzyskać listę powiązań dostarczanych przez system, zobacz [powiązania dostarczone przez system](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="0175a-115">For a list of system-provided bindings, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>

## <a name="custom-bindings"></a><span data-ttu-id="0175a-116">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="0175a-116">Custom bindings</span></span>

<span data-ttu-id="0175a-117">Niestandardowe powiązania zapewniają pełną kontrolę nad stosem obsługi komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="0175a-117">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="0175a-118">Pojedyncze powiązanie definiuje stos komunikatów przez określenie elementów konfiguracji dla elementów stosu w kolejności, w jakiej występują na stosie.</span><span class="sxs-lookup"><span data-stu-id="0175a-118">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="0175a-119">Każdy element definiuje i konfiguruje jeden element stosu.</span><span class="sxs-lookup"><span data-stu-id="0175a-119">Each element defines and configures one element of the stack.</span></span> <span data-ttu-id="0175a-120">Musi istnieć jeden i tylko jeden `transport` element w każdym powiązaniu niestandardowym.</span><span class="sxs-lookup"><span data-stu-id="0175a-120">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="0175a-121">Bez tego elementu stos komunikatów jest niekompletny.</span><span class="sxs-lookup"><span data-stu-id="0175a-121">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="0175a-122">Kolejność, w której elementy pojawiają się w kwestiach stosu, ponieważ jest to kolejność, w której operacje są stosowane do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0175a-122">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="0175a-123">Wymagana kolejność elementów stosu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="0175a-123">The required order of stack elements is the following:</span></span>  

1. <span data-ttu-id="0175a-124">Transakcje (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="0175a-124">Transactions (optional)</span></span>  

2. <span data-ttu-id="0175a-125">Niezawodna obsługa komunikatów (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="0175a-125">Reliable messaging (optional)</span></span>  

3. <span data-ttu-id="0175a-126">Zabezpieczenia (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="0175a-126">Security (optional)</span></span>  

4. <span data-ttu-id="0175a-127">Pomocą</span><span class="sxs-lookup"><span data-stu-id="0175a-127">Encoder</span></span>  

5. <span data-ttu-id="0175a-128">Transport</span><span class="sxs-lookup"><span data-stu-id="0175a-128">Transport</span></span>  

 <span data-ttu-id="0175a-129">Niestandardowe powiązania są identyfikowane przez ich `name` atrybut.</span><span class="sxs-lookup"><span data-stu-id="0175a-129">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="0175a-130">Aby uzyskać więcej informacji na temat powiązań niestandardowych, zobacz [niestandardowe powiązania](../../../wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="0175a-130">For more information on custom bindings, see [Custom Bindings](../../../wcf/extending/custom-bindings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0175a-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0175a-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [<span data-ttu-id="0175a-132">Powiązania</span><span class="sxs-lookup"><span data-stu-id="0175a-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0175a-133">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="0175a-133">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
