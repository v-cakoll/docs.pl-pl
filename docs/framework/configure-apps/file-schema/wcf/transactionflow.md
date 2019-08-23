---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 206a684e1279871eee4aed95a087921123f8efb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918658"
---
# <a name="transactionflow"></a><span data-ttu-id="f7da8-101">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="f7da8-101">\<transactionFlow></span></span>
<span data-ttu-id="f7da8-102">Określa obsługę przepływu transakcji dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f7da8-102">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="f7da8-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="f7da8-103">\<system.serviceModel></span></span>  
<span data-ttu-id="f7da8-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="f7da8-104">\<bindings></span></span>  
<span data-ttu-id="f7da8-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f7da8-105">\<customBinding></span></span>  
<span data-ttu-id="f7da8-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="f7da8-106">\<binding></span></span>  
<span data-ttu-id="f7da8-107">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="f7da8-107">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7da8-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7da8-108">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7da8-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f7da8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f7da8-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f7da8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7da8-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f7da8-111">Attributes</span></span>  
  
|<span data-ttu-id="f7da8-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f7da8-112">Attribute</span></span>|<span data-ttu-id="f7da8-113">Opis</span><span class="sxs-lookup"><span data-stu-id="f7da8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f7da8-114">Element TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="f7da8-114">transactionProtocol</span></span>|<span data-ttu-id="f7da8-115">Określa protokół transakcji, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="f7da8-115">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="f7da8-116">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="f7da8-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f7da8-117">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="f7da8-117">-   OleTransactions</span></span><br /><span data-ttu-id="f7da8-118">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="f7da8-118">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="f7da8-119">Wartość domyślna to OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="f7da8-119">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="f7da8-120">Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="f7da8-120">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7da8-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f7da8-121">Child Elements</span></span>  
 <span data-ttu-id="f7da8-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="f7da8-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f7da8-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f7da8-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f7da8-124">Element</span><span class="sxs-lookup"><span data-stu-id="f7da8-124">Element</span></span>|<span data-ttu-id="f7da8-125">Opis</span><span class="sxs-lookup"><span data-stu-id="f7da8-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7da8-126">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="f7da8-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="f7da8-127">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f7da8-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7da8-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f7da8-128">Remarks</span></span>  
 <span data-ttu-id="f7da8-129">Ten element umożliwia włączenie lub wyłączenie przychodzącego przepływu transakcji w ustawieniach powiązań punktu końcowego, a także określenie żądanego formatu protokołu dla transakcji przychodzących.</span><span class="sxs-lookup"><span data-stu-id="f7da8-129">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="f7da8-130">Aby uzyskać więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [Konfiguracja transakcji ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) i [Włączanie przepływu transakcji](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="f7da8-130">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f7da8-131">W przypadku korzystania `OleTransactions` z protokołu do przepływu transakcji z punktu końcowego do punktu końcowego limit czasu transakcji może zostać utracony, jeśli docelowy punkt końcowy próbuje ponownie przepływać `OleTransactions`przy użyciu dowolnego protokołu innego niż.</span><span class="sxs-lookup"><span data-stu-id="f7da8-131">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="f7da8-132">Może to spowodować, że wszystkie węzły wyższego poziomu po przejściu OleTransactions do limitu czasu później niż oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="f7da8-132">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7da8-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7da8-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f7da8-134">Konfiguracja transakcji modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f7da8-134">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="f7da8-135">Włączanie przepływu transakcji</span><span class="sxs-lookup"><span data-stu-id="f7da8-135">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="f7da8-136">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f7da8-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f7da8-137">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f7da8-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f7da8-138">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f7da8-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f7da8-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f7da8-139">\<customBinding></span></span>](custombinding.md)
