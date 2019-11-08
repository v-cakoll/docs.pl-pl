---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: f5bcd142fb2b032ea179bcbba68fee53b98d2d77
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736319"
---
# <a name="transactionflow"></a><span data-ttu-id="e1c8a-101">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="e1c8a-101">\<transactionFlow></span></span>
<span data-ttu-id="e1c8a-102">Określa obsługę przepływu transakcji dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e1c8a-102">Specifies transaction flow support for the custom binding.</span></span>  
  
<span data-ttu-id="e1c8a-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e1c8a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e1c8a-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="e1c8a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e1c8a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="e1c8a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e1c8a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="e1c8a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="e1c8a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="e1c8a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e1c8a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transactionFlow >**</span><span class="sxs-lookup"><span data-stu-id="e1c8a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1c8a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1c8a-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1c8a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e1c8a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e1c8a-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e1c8a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1c8a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e1c8a-112">Attributes</span></span>  
  
|<span data-ttu-id="e1c8a-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e1c8a-113">Attribute</span></span>|<span data-ttu-id="e1c8a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e1c8a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1c8a-115">Element TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="e1c8a-115">transactionProtocol</span></span>|<span data-ttu-id="e1c8a-116">Określa protokół transakcji, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="e1c8a-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="e1c8a-117">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="e1c8a-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e1c8a-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="e1c8a-118">-   OleTransactions</span></span><br /><span data-ttu-id="e1c8a-119">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="e1c8a-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="e1c8a-120">Wartość domyślna to OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="e1c8a-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="e1c8a-121">Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="e1c8a-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1c8a-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e1c8a-122">Child Elements</span></span>  
 <span data-ttu-id="e1c8a-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="e1c8a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1c8a-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e1c8a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e1c8a-125">Element</span><span class="sxs-lookup"><span data-stu-id="e1c8a-125">Element</span></span>|<span data-ttu-id="e1c8a-126">Opis</span><span class="sxs-lookup"><span data-stu-id="e1c8a-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e1c8a-127">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="e1c8a-127">\<binding></span></span>](bindings.md)|<span data-ttu-id="e1c8a-128">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e1c8a-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1c8a-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1c8a-129">Remarks</span></span>  
 <span data-ttu-id="e1c8a-130">Ten element umożliwia włączenie lub wyłączenie przychodzącego przepływu transakcji w ustawieniach powiązań punktu końcowego, a także określenie żądanego formatu protokołu dla transakcji przychodzących.</span><span class="sxs-lookup"><span data-stu-id="e1c8a-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="e1c8a-131">Aby uzyskać więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [Konfiguracja transakcji ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) i [Włączanie przepływu transakcji](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="e1c8a-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="e1c8a-132">W przypadku korzystania z protokołu `OleTransactions` do przepływu transakcji z punktu końcowego do punktu końcowego, limit czasu transakcji może zostać utracony, jeśli docelowy punkt końcowy próbuje ponownie przepływać przy użyciu dowolnego protokołu innego niż `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="e1c8a-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="e1c8a-133">Może to spowodować, że wszystkie węzły wyższego poziomu po przejściu OleTransactions do limitu czasu później niż oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="e1c8a-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c8a-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1c8a-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e1c8a-135">Konfiguracja transakcji modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e1c8a-135">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="e1c8a-136">Włączanie przepływu transakcji</span><span class="sxs-lookup"><span data-stu-id="e1c8a-136">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="e1c8a-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e1c8a-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e1c8a-138">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="e1c8a-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e1c8a-139">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="e1c8a-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="e1c8a-140">\<niestandardowebinding ></span><span class="sxs-lookup"><span data-stu-id="e1c8a-140">\<customBinding></span></span>](custombinding.md)
