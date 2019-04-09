---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: a58d5620abbb636480ceea3020552246ae284842
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150088"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="ba341-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="ba341-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="ba341-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="ba341-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba341-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba341-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ba341-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ba341-105">Methods</span></span>  
 <span data-ttu-id="ba341-106">Klasa TransactionFlowBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="ba341-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ba341-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ba341-107">Properties</span></span>  
 <span data-ttu-id="ba341-108">Klasa TransactionFlowBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="ba341-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="ba341-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="ba341-109">IssuedTokens</span></span>  
 <span data-ttu-id="ba341-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="ba341-110">Data type: string</span></span>  
  
 <span data-ttu-id="ba341-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ba341-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba341-112">Określa wymagania dla nagłówka tokenów zabezpieczeń (IssuedTokens z protokołu WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="ba341-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="ba341-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="ba341-113">TransactionProtocol</span></span>  
 <span data-ttu-id="ba341-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="ba341-114">Data type: string</span></span>  
  
 <span data-ttu-id="ba341-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ba341-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba341-116">Protokół transakcji, używane przez usługę przepływ transakcji.</span><span class="sxs-lookup"><span data-stu-id="ba341-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="ba341-117">Transakcje</span><span class="sxs-lookup"><span data-stu-id="ba341-117">Transactions</span></span>  
 <span data-ttu-id="ba341-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="ba341-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="ba341-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ba341-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba341-120">Wskazuje, czy przychodzące transakcji jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="ba341-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba341-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ba341-121">Requirements</span></span>  
  
|<span data-ttu-id="ba341-122">MOF</span><span class="sxs-lookup"><span data-stu-id="ba341-122">MOF</span></span>|<span data-ttu-id="ba341-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ba341-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ba341-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="ba341-124">Namespace</span></span>|<span data-ttu-id="ba341-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ba341-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba341-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba341-126">See also</span></span>

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
