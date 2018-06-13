---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: c2fb32c4c693cbfc487ce89b36f013398cbdb703
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485623"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="7a164-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="7a164-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="7a164-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="7a164-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a164-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a164-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7a164-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7a164-105">Methods</span></span>  
 <span data-ttu-id="7a164-106">Klasa TransactionFlowBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="7a164-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7a164-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7a164-107">Properties</span></span>  
 <span data-ttu-id="7a164-108">Klasa TransactionFlowBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="7a164-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="7a164-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="7a164-109">IssuedTokens</span></span>  
 <span data-ttu-id="7a164-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="7a164-110">Data type: string</span></span>  
  
 <span data-ttu-id="7a164-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7a164-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7a164-112">Określa wymaganie zabezpieczeń wystawionych tokenów nagłówka (IssuedTokens z protokołu WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="7a164-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="7a164-113">Element TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="7a164-113">TransactionProtocol</span></span>  
 <span data-ttu-id="7a164-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="7a164-114">Data type: string</span></span>  
  
 <span data-ttu-id="7a164-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7a164-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7a164-116">Protokół transakcji używany przez usługę przepływ transakcji.</span><span class="sxs-lookup"><span data-stu-id="7a164-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="7a164-117">Transakcje</span><span class="sxs-lookup"><span data-stu-id="7a164-117">Transactions</span></span>  
 <span data-ttu-id="7a164-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="7a164-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="7a164-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7a164-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7a164-120">Wskazuje, czy obsługiwane jest transakcją przychodzącą.</span><span class="sxs-lookup"><span data-stu-id="7a164-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a164-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7a164-121">Requirements</span></span>  
  
|<span data-ttu-id="7a164-122">MOF</span><span class="sxs-lookup"><span data-stu-id="7a164-122">MOF</span></span>|<span data-ttu-id="7a164-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7a164-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7a164-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="7a164-124">Namespace</span></span>|<span data-ttu-id="7a164-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7a164-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a164-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a164-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
