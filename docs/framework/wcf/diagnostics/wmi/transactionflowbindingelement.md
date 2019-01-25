---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: d0311837ebb8112d9492fb548492bcd3e10230e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514575"
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="f3c62-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="f3c62-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="f3c62-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="f3c62-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3c62-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3c62-104">Syntax</span></span>  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f3c62-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f3c62-105">Methods</span></span>  
 <span data-ttu-id="f3c62-106">Klasa TransactionFlowBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="f3c62-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f3c62-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f3c62-107">Properties</span></span>  
 <span data-ttu-id="f3c62-108">Klasa TransactionFlowBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="f3c62-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="f3c62-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="f3c62-109">IssuedTokens</span></span>  
 <span data-ttu-id="f3c62-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f3c62-110">Data type: string</span></span>  
  
 <span data-ttu-id="f3c62-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f3c62-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3c62-112">Określa wymagania dla nagłówka tokenów zabezpieczeń (IssuedTokens z protokołu WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="f3c62-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="f3c62-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="f3c62-113">TransactionProtocol</span></span>  
 <span data-ttu-id="f3c62-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f3c62-114">Data type: string</span></span>  
  
 <span data-ttu-id="f3c62-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f3c62-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3c62-116">Protokół transakcji, używane przez usługę przepływ transakcji.</span><span class="sxs-lookup"><span data-stu-id="f3c62-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="f3c62-117">Transakcje</span><span class="sxs-lookup"><span data-stu-id="f3c62-117">Transactions</span></span>  
 <span data-ttu-id="f3c62-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="f3c62-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="f3c62-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f3c62-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3c62-120">Wskazuje, czy przychodzące transakcji jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f3c62-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3c62-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f3c62-121">Requirements</span></span>  
  
|<span data-ttu-id="f3c62-122">MOF</span><span class="sxs-lookup"><span data-stu-id="f3c62-122">MOF</span></span>|<span data-ttu-id="f3c62-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f3c62-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f3c62-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="f3c62-124">Namespace</span></span>|<span data-ttu-id="f3c62-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f3c62-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3c62-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3c62-126">See also</span></span>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
