---
title: "Porównywanie transakcji w modelach COM+ i ServiceModel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5229c872c4843df916cf538b7f2e88e451dc6b9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a><span data-ttu-id="24990-102">Porównywanie transakcji w modelach COM+ i ServiceModel</span><span class="sxs-lookup"><span data-stu-id="24990-102">Comparing Transactions in COM+ and ServiceModel</span></span>
<span data-ttu-id="24990-103">W tym temacie omówiono sposób symulować transakcyjne COM + usługi za pomocą [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] atrybuty <xref:System.ServiceModel> zawiera przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="24990-103">This topic discusses how to simulate the behavior of a transactional COM+ service using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
## <a name="emulating-com-using-servicemodel-attributes"></a><span data-ttu-id="24990-104">Emulowanie COM + przy użyciu atrybuty elementu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="24990-104">Emulating COM+ Using ServiceModel Attributes</span></span>  
 <span data-ttu-id="24990-105">W poniższej tabeli porównuje <xref:System.EnterpriseServices.TransactionOption> używany do tworzenia wyliczenia `EnterpriseServices` transakcji i sposób ich skorelowany [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] atrybuty <xref:System.ServiceModel> przestrzeń nazw zawiera.</span><span class="sxs-lookup"><span data-stu-id="24990-105">The following table compares the <xref:System.EnterpriseServices.TransactionOption> enumeration used to create an `EnterpriseServices` transaction and how they correlate to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
|<span data-ttu-id="24990-106">Atrybut modelu COM +</span><span class="sxs-lookup"><span data-stu-id="24990-106">COM+ attribute</span></span>|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="24990-107">atrybuty</span><span class="sxs-lookup"><span data-stu-id="24990-107"> attributes</span></span>|  
|---------------------|------------------------------------------------------------------------|  
|<span data-ttu-id="24990-108">RequiresNew</span><span class="sxs-lookup"><span data-stu-id="24990-108">RequiresNew</span></span>|<span data-ttu-id="24990-109"><xref:System.ServiceModel.TransactionFlowAttribute>ustawiono <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span><span class="sxs-lookup"><span data-stu-id="24990-109"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span></span><br /><br /> <span data-ttu-id="24990-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>jest `true`.</span><span class="sxs-lookup"><span data-stu-id="24990-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="24990-111">`TransactionFlow` w elemencie powiązania jest `false`.</span><span class="sxs-lookup"><span data-stu-id="24990-111">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="24990-112">Wymagane</span><span class="sxs-lookup"><span data-stu-id="24990-112">Required</span></span>|<span data-ttu-id="24990-113"><xref:System.ServiceModel.TransactionFlowAttribute>ustawiono <xref:System.ServiceModel.TransactionFlowOption.Allowed>.</span><span class="sxs-lookup"><span data-stu-id="24990-113"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.Allowed>.</span></span><br /><br /> <span data-ttu-id="24990-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>jest `true`.</span><span class="sxs-lookup"><span data-stu-id="24990-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="24990-115">`TransactionFlow` w elemencie powiązania jest `true`.</span><span class="sxs-lookup"><span data-stu-id="24990-115">The `TransactionFlow` attribute in the binding element is `true`.</span></span>|  
|<span data-ttu-id="24990-116">Obsługiwane</span><span class="sxs-lookup"><span data-stu-id="24990-116">Supported</span></span>|<span data-ttu-id="24990-117">Nie ma odpowiednika bezpośredniego.</span><span class="sxs-lookup"><span data-stu-id="24990-117">There is no direct equivalent.</span></span> <span data-ttu-id="24990-118">Ogólnie rzecz biorąc, powinna przyjąć zachowania nieaktywności `Required` zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="24990-118">In general, you should adopt the behavior specified for `Required` instead.</span></span>|  
|<span data-ttu-id="24990-119">NotSupported</span><span class="sxs-lookup"><span data-stu-id="24990-119">NotSupported</span></span>|<span data-ttu-id="24990-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>jest `false`.</span><span class="sxs-lookup"><span data-stu-id="24990-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `false`.</span></span><br /><br /> <span data-ttu-id="24990-121">`TransactionFlow` w elemencie powiązania jest `false`.</span><span class="sxs-lookup"><span data-stu-id="24990-121">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="24990-122">Wyłączone</span><span class="sxs-lookup"><span data-stu-id="24990-122">Disabled</span></span>|<span data-ttu-id="24990-123">Nie ma odpowiednika bezpośredniego.</span><span class="sxs-lookup"><span data-stu-id="24990-123">There is no direct equivalent.</span></span> <span data-ttu-id="24990-124">Ogólnie rzecz biorąc, powinna przyjąć zachowania nieaktywności `NotSupported` zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="24990-124">In general, you should adopt the behavior specified for `NotSupported` instead.</span></span>|
