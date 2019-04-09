---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 626ae03d622221ab3e956bd03898b6cc30482c98
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179156"
---
# <a name="transactionflow"></a><span data-ttu-id="12ae6-101">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="12ae6-101">\<transactionFlow></span></span>
<span data-ttu-id="12ae6-102">Określa obsługę przepływu transakcji dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="12ae6-102">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="12ae6-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="12ae6-103">\<system.serviceModel></span></span>  
<span data-ttu-id="12ae6-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="12ae6-104">\<bindings></span></span>  
<span data-ttu-id="12ae6-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="12ae6-105">\<customBinding></span></span>  
<span data-ttu-id="12ae6-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="12ae6-106">\<binding></span></span>  
<span data-ttu-id="12ae6-107">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="12ae6-107">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12ae6-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="12ae6-108">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12ae6-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="12ae6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="12ae6-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="12ae6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12ae6-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="12ae6-111">Attributes</span></span>  
  
|<span data-ttu-id="12ae6-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="12ae6-112">Attribute</span></span>|<span data-ttu-id="12ae6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="12ae6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12ae6-114">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="12ae6-114">transactionProtocol</span></span>|<span data-ttu-id="12ae6-115">Określa protokół transakcji do użycia.</span><span class="sxs-lookup"><span data-stu-id="12ae6-115">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="12ae6-116">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="12ae6-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="12ae6-117">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="12ae6-117">-   OleTransactions</span></span><br /><span data-ttu-id="12ae6-118">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="12ae6-118">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="12ae6-119">Wartość domyślna to OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="12ae6-119">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="12ae6-120">Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="12ae6-120">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12ae6-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="12ae6-121">Child Elements</span></span>  
 <span data-ttu-id="12ae6-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="12ae6-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="12ae6-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="12ae6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="12ae6-124">Element</span><span class="sxs-lookup"><span data-stu-id="12ae6-124">Element</span></span>|<span data-ttu-id="12ae6-125">Opis</span><span class="sxs-lookup"><span data-stu-id="12ae6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12ae6-126">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="12ae6-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="12ae6-127">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="12ae6-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12ae6-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="12ae6-128">Remarks</span></span>  
 <span data-ttu-id="12ae6-129">Ten element pozwala włączyć lub wyłączyć przychodzącego przepływu transakcji w ustawieniach powiązania punktu końcowego, a także określić format odpowiedni protokół dla transakcji przychodzących.</span><span class="sxs-lookup"><span data-stu-id="12ae6-129">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="12ae6-130">Aby uzyskać więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [Konfiguracja transakcji modelu ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) i [Włączanie przepływu transakcji](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="12ae6-130">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="12ae6-131">Korzystając z `OleTransactions` protokołu przepływ transakcji z punktu końcowego do endpoint, limit czasu transakcji mogą zostać utracone, jeśli docelowy punkt końcowy podejmie próbę przepływ ponownie przy użyciu dowolnego protokołu innego niż `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="12ae6-131">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="12ae6-132">Może to spowodować wszystkich węzłów niskiego poziomu po przeskoku OleTransactions przekroczenie limitu czasu później niż oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="12ae6-132">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ae6-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12ae6-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="12ae6-134">Konfiguracja transakcji modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="12ae6-134">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="12ae6-135">Włączanie przepływu transakcji</span><span class="sxs-lookup"><span data-stu-id="12ae6-135">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="12ae6-136">Powiązania</span><span class="sxs-lookup"><span data-stu-id="12ae6-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="12ae6-137">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="12ae6-137">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="12ae6-138">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="12ae6-138">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="12ae6-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="12ae6-139">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
