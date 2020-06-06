---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: f5bcd142fb2b032ea179bcbba68fee53b98d2d77
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736319"
---
# \<transactionFlow>
<span data-ttu-id="e894a-101">Określa obsługę przepływu transakcji dla niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e894a-101">Specifies transaction flow support for the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**  
  
## <a name="syntax"></a><span data-ttu-id="e894a-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="e894a-102">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e894a-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e894a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e894a-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e894a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e894a-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e894a-105">Attributes</span></span>  
  
|<span data-ttu-id="e894a-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e894a-106">Attribute</span></span>|<span data-ttu-id="e894a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e894a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e894a-108">Element TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="e894a-108">transactionProtocol</span></span>|<span data-ttu-id="e894a-109">Określa protokół transakcji, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="e894a-109">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="e894a-110">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="e894a-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e894a-111">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="e894a-111">-   OleTransactions</span></span><br /><span data-ttu-id="e894a-112">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="e894a-112">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="e894a-113">Wartość domyślna to OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="e894a-113">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="e894a-114">Ten atrybut jest typu <xref:System.ServiceModel.TransactionProtocol> .</span><span class="sxs-lookup"><span data-stu-id="e894a-114">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e894a-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e894a-115">Child Elements</span></span>  
 <span data-ttu-id="e894a-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="e894a-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e894a-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e894a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e894a-118">Element</span><span class="sxs-lookup"><span data-stu-id="e894a-118">Element</span></span>|<span data-ttu-id="e894a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="e894a-119">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="e894a-120">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="e894a-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e894a-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e894a-121">Remarks</span></span>  
 <span data-ttu-id="e894a-122">Ten element umożliwia włączenie lub wyłączenie przychodzącego przepływu transakcji w ustawieniach powiązań punktu końcowego, a także określenie żądanego formatu protokołu dla transakcji przychodzących.</span><span class="sxs-lookup"><span data-stu-id="e894a-122">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="e894a-123">Aby uzyskać więcej informacji na temat korzystania z tego elementu konfiguracji, zobacz [Konfiguracja transakcji ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) i [Włączanie przepływu transakcji](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="e894a-123">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="e894a-124">W przypadku korzystania z `OleTransactions` protokołu do przepływu transakcji z punktu końcowego do punktu końcowego limit czasu transakcji może zostać utracony, jeśli docelowy punkt końcowy próbuje ponownie przepływać przy użyciu dowolnego protokołu innego niż `OleTransactions` .</span><span class="sxs-lookup"><span data-stu-id="e894a-124">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="e894a-125">Może to spowodować, że wszystkie węzły wyższego poziomu po przejściu OleTransactions do limitu czasu później niż oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="e894a-125">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e894a-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e894a-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="e894a-127">Konfiguracja transakcji modelu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e894a-127">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="e894a-128">Włączanie przepływu transakcji</span><span class="sxs-lookup"><span data-stu-id="e894a-128">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="e894a-129">Powiązania</span><span class="sxs-lookup"><span data-stu-id="e894a-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e894a-130">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="e894a-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e894a-131">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="e894a-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
