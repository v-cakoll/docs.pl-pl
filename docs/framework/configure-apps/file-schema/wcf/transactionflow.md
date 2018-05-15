---
title: '&lt;TransactionFlow&gt;'
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: c708098676e5634281e29c17639304a1a9cf5afe
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="lttransactionflowgt"></a><span data-ttu-id="a188f-102">&lt;TransactionFlow&gt;</span><span class="sxs-lookup"><span data-stu-id="a188f-102">&lt;transactionFlow&gt;</span></span>
<span data-ttu-id="a188f-103">Określa obsługę przepływu transakcji dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a188f-103">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="a188f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a188f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a188f-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="a188f-105">\<bindings></span></span>  
<span data-ttu-id="a188f-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a188f-106">\<customBinding></span></span>  
<span data-ttu-id="a188f-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a188f-107">\<binding></span></span>  
<span data-ttu-id="a188f-108">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="a188f-108">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a188f-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a188f-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a188f-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a188f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a188f-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a188f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a188f-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a188f-112">Attributes</span></span>  
  
|<span data-ttu-id="a188f-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a188f-113">Attribute</span></span>|<span data-ttu-id="a188f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a188f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a188f-115">Element TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="a188f-115">transactionProtocol</span></span>|<span data-ttu-id="a188f-116">Określa protokół transakcji do użycia.</span><span class="sxs-lookup"><span data-stu-id="a188f-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="a188f-117">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="a188f-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a188f-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="a188f-118">-   OleTransactions</span></span><br /><span data-ttu-id="a188f-119">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="a188f-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="a188f-120">Wartość domyślna to OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="a188f-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="a188f-121">Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="a188f-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a188f-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a188f-122">Child Elements</span></span>  
 <span data-ttu-id="a188f-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="a188f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a188f-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a188f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a188f-125">Element</span><span class="sxs-lookup"><span data-stu-id="a188f-125">Element</span></span>|<span data-ttu-id="a188f-126">Opis</span><span class="sxs-lookup"><span data-stu-id="a188f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a188f-127">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="a188f-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a188f-128">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a188f-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a188f-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a188f-129">Remarks</span></span>  
 <span data-ttu-id="a188f-130">Ten element pozwala włączyć lub wyłączyć przychodzący transakcji w ustawienia powiązania punktu końcowego, a także określić format odpowiedni protokół dla przychodzących transakcji.</span><span class="sxs-lookup"><span data-stu-id="a188f-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="a188f-131">Aby uzyskać więcej informacji na temat używania tego elementu konfiguracji, zobacz [Konfiguracja transakcji modelu ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) i [Włączanie przepływu transakcji](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="a188f-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a188f-132">Korzystając z `OleTransactions` protokołu przepływ transakcji punktu końcowego endpoint, limit czasu transakcji mogą zostać utracone, jeśli docelowy punkt końcowy podejmie próbę przepływu ponownie przy użyciu protokołów innych niż `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="a188f-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="a188f-133">Może to spowodować wszystkich węzłów na niższym poziomie po przeskoku OleTransactions limit później niż oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="a188f-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a188f-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a188f-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactionFlowElement>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="a188f-135">Konfiguracja transakcji modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a188f-135">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 [<span data-ttu-id="a188f-136">Włączanie przepływu transakcji</span><span class="sxs-lookup"><span data-stu-id="a188f-136">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 [<span data-ttu-id="a188f-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a188f-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a188f-138">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="a188f-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="a188f-139">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a188f-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="a188f-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a188f-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
