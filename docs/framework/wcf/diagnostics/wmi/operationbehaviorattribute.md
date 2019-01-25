---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: d0bf59e6064748a045f761777a2f8f3e88f1cb5a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504330"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="a4079-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="a4079-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="a4079-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="a4079-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4079-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4079-104">Syntax</span></span>  
  
```csharp
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a4079-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a4079-105">Methods</span></span>  
 <span data-ttu-id="a4079-106">Gdy klasa nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="a4079-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a4079-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a4079-107">Properties</span></span>  
 <span data-ttu-id="a4079-108">Gdy klasa ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="a4079-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="a4079-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="a4079-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="a4079-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a4079-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="a4079-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a4079-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4079-112">Stan funkcji automatycznego usuwania dla parametrów.</span><span class="sxs-lookup"><span data-stu-id="a4079-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="a4079-113">Personifikacja</span><span class="sxs-lookup"><span data-stu-id="a4079-113">Impersonation</span></span>  
 <span data-ttu-id="a4079-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="a4079-114">Data type: string</span></span>  
  
 <span data-ttu-id="a4079-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a4079-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4079-116">Wskazuje poziom personifikacji obiekt wywołujący, który obsługuje operację.</span><span class="sxs-lookup"><span data-stu-id="a4079-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="a4079-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="a4079-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="a4079-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="a4079-118">Data type: string</span></span>  
  
 <span data-ttu-id="a4079-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a4079-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4079-120">Wskazuje, że w trakcie wywołania operacji odtworzenie obiektu.</span><span class="sxs-lookup"><span data-stu-id="a4079-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="a4079-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="a4079-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="a4079-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a4079-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="a4079-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a4079-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4079-124">Wskazuje, czy można zatwierdzić bieżącej transakcji automatycznie, jeśli wystąpi żaden nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a4079-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="a4079-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="a4079-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="a4079-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a4079-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="a4079-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a4079-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4079-128">Wskazuje, czy operacja wymaga transakcji.</span><span class="sxs-lookup"><span data-stu-id="a4079-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4079-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a4079-129">Requirements</span></span>  
  
|<span data-ttu-id="a4079-130">MOF</span><span class="sxs-lookup"><span data-stu-id="a4079-130">MOF</span></span>|<span data-ttu-id="a4079-131">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a4079-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a4079-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="a4079-132">Namespace</span></span>|<span data-ttu-id="a4079-133">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a4079-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4079-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4079-134">See also</span></span>
- <xref:System.ServiceModel.OperationBehaviorAttribute>
