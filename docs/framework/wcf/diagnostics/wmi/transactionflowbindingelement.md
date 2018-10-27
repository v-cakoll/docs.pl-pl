---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: 027ace6ea9fc2a0e5ce63efa84e1a49c0ed2cd0a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188030"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="b1163-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="b1163-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="b1163-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="b1163-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1163-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1163-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b1163-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b1163-105">Methods</span></span>  
 <span data-ttu-id="b1163-106">Klasa TransactionFlowBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="b1163-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b1163-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b1163-107">Properties</span></span>  
 <span data-ttu-id="b1163-108">Klasa TransactionFlowBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="b1163-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="b1163-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="b1163-109">IssuedTokens</span></span>  
 <span data-ttu-id="b1163-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b1163-110">Data type: string</span></span>  
  
 <span data-ttu-id="b1163-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b1163-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1163-112">Określa wymagania dla nagłówka tokenów zabezpieczeń (IssuedTokens z protokołu WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="b1163-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="b1163-113">Element transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="b1163-113">TransactionProtocol</span></span>  
 <span data-ttu-id="b1163-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b1163-114">Data type: string</span></span>  
  
 <span data-ttu-id="b1163-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b1163-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1163-116">Protokół transakcji, używane przez usługę przepływ transakcji.</span><span class="sxs-lookup"><span data-stu-id="b1163-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="b1163-117">Transakcje</span><span class="sxs-lookup"><span data-stu-id="b1163-117">Transactions</span></span>  
 <span data-ttu-id="b1163-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="b1163-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="b1163-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b1163-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1163-120">Wskazuje, czy przychodzące transakcji jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="b1163-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1163-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1163-121">Requirements</span></span>  
  
|<span data-ttu-id="b1163-122">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="b1163-122">MOF</span></span>|<span data-ttu-id="b1163-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b1163-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b1163-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="b1163-124">Namespace</span></span>|<span data-ttu-id="b1163-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b1163-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1163-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1163-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
