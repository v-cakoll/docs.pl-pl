---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa5394e874e35b80b01796642e18d69c71e867dc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="c8665-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="c8665-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="c8665-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="c8665-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8665-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8665-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c8665-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c8665-105">Methods</span></span>  
 <span data-ttu-id="c8665-106">Klasa TransactionFlowBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="c8665-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c8665-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c8665-107">Properties</span></span>  
 <span data-ttu-id="c8665-108">Klasa TransactionFlowBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="c8665-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="c8665-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="c8665-109">IssuedTokens</span></span>  
 <span data-ttu-id="c8665-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="c8665-110">Data type: string</span></span>  
  
 <span data-ttu-id="c8665-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c8665-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8665-112">Określa wymaganie zabezpieczeń wystawionych tokenów nagłówka (IssuedTokens z protokołu WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="c8665-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="c8665-113">Element TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="c8665-113">TransactionProtocol</span></span>  
 <span data-ttu-id="c8665-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="c8665-114">Data type: string</span></span>  
  
 <span data-ttu-id="c8665-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c8665-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8665-116">Protokół transakcji używany przez usługę przepływ transakcji.</span><span class="sxs-lookup"><span data-stu-id="c8665-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="c8665-117">Transakcje</span><span class="sxs-lookup"><span data-stu-id="c8665-117">Transactions</span></span>  
 <span data-ttu-id="c8665-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="c8665-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="c8665-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c8665-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c8665-120">Wskazuje, czy obsługiwane jest transakcją przychodzącą.</span><span class="sxs-lookup"><span data-stu-id="c8665-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8665-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c8665-121">Requirements</span></span>  
  
|<span data-ttu-id="c8665-122">MOF</span><span class="sxs-lookup"><span data-stu-id="c8665-122">MOF</span></span>|<span data-ttu-id="c8665-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c8665-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c8665-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="c8665-124">Namespace</span></span>|<span data-ttu-id="c8665-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c8665-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c8665-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8665-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
