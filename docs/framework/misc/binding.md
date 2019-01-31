---
title: <binding>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: fb51eb1962603439b89a203eb668dfb543049170
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271476"
---
# <a name="binding"></a><span data-ttu-id="73fce-101">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="73fce-101">\<binding></span></span>
<span data-ttu-id="73fce-102">Możesz użyć `binding` elementu do konfigurowania różnych typów wstępnie zdefiniowanych powiązań dostarczonych przez Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="73fce-102">You can use the `binding` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="73fce-103">System-Provided Binding</span><span class="sxs-lookup"><span data-stu-id="73fce-103">System-Provided Binding</span></span>  
 <span data-ttu-id="73fce-104">Powiązania dostarczane przez system ukrywają złożoność architektury WCF stosem obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="73fce-104">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="73fce-105">Aplikacje przy użyciu powiązania dostarczane przez system nie wymagają pełną kontrolę nad stosu.</span><span class="sxs-lookup"><span data-stu-id="73fce-105">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="73fce-106">Atrybuty narażonych na każdego powiązania dostarczane przez system są tymi najbardziej odpowiednie dla scenariusza użycia adresów powiązania.</span><span class="sxs-lookup"><span data-stu-id="73fce-106">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="73fce-107">Sekcja konfiguracji dla każdego powiązania dostarczane przez system, można zdefiniować kilka konfiguracji używane do konfigurowania wiązania.</span><span class="sxs-lookup"><span data-stu-id="73fce-107">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="73fce-108">Każdej konfiguracji jest identyfikowane przez unikatową nazwę.</span><span class="sxs-lookup"><span data-stu-id="73fce-108">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="73fce-109">Nie jest możliwe dodać elementy lub atrybuty do powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="73fce-109">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="73fce-110">Aby to zrobić, należy zaimplementować niestandardowego powiązania, zgodnie z opisem w sekcji "Niestandardowego powiązania" tego tematu.</span><span class="sxs-lookup"><span data-stu-id="73fce-110">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="73fce-111">Istnieje możliwość zdefiniowania niestandardowego powiązania, który naśladuje dostarczane przez system powiązań doskonale i dodaje kilka ustawień aplikacji użytkownik chce, aby mieć kontrolę nad.</span><span class="sxs-lookup"><span data-stu-id="73fce-111">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="73fce-112">Powiązanie niestandardowe</span><span class="sxs-lookup"><span data-stu-id="73fce-112">Custom Binding</span></span>  
 <span data-ttu-id="73fce-113">Powiązania niestandardowe zapewniają pełną kontrolę nad stosem obsługi wiadomości usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="73fce-113">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="73fce-114">Powiązanie poszczególnych definiuje stosu wiadomości, określając elementów konfiguracji dla elementów stosu w kolejności, w jakiej znajdują się na stosie.</span><span class="sxs-lookup"><span data-stu-id="73fce-114">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="73fce-115">Każdy element definiuje i konfiguruje jeden element stosu.</span><span class="sxs-lookup"><span data-stu-id="73fce-115">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="73fce-116">Musi istnieć jeden i tylko jeden `transport` elementu w każdej niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="73fce-116">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="73fce-117">Bez tego elementu stosem obsługi wiadomości jest niekompletna.</span><span class="sxs-lookup"><span data-stu-id="73fce-117">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="73fce-118">Kolejność wyświetlania elementów w stosie ma znaczenie, ponieważ jest on kolejność, w której operacje są stosowane do wiadomości.</span><span class="sxs-lookup"><span data-stu-id="73fce-118">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="73fce-119">Zalecana kolejność elementów stosu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="73fce-119">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="73fce-120">Transakcje (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="73fce-120">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="73fce-121">Niezawodna obsługa komunikatów (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="73fce-121">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="73fce-122">Zabezpieczenia (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="73fce-122">Security (optional)</span></span>  
  
4.  <span data-ttu-id="73fce-123">Koder</span><span class="sxs-lookup"><span data-stu-id="73fce-123">Encoder</span></span>  
  
5.  <span data-ttu-id="73fce-124">Transport</span><span class="sxs-lookup"><span data-stu-id="73fce-124">Transport</span></span>  
  
 <span data-ttu-id="73fce-125">Powiązania niestandardowe są identyfikowane przez ich `name` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="73fce-125">Custom bindings are identified by their `name` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73fce-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73fce-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- [<span data-ttu-id="73fce-127">Powiązania</span><span class="sxs-lookup"><span data-stu-id="73fce-127">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="73fce-128">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="73fce-128">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="73fce-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="73fce-129">\<customBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
