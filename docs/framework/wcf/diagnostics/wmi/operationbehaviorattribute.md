---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 4f731d146885265d9f956c182f1bebdba5db924b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486874"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="a1820-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="a1820-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="a1820-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="a1820-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1820-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1820-104">Syntax</span></span>  
  
```  
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a1820-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a1820-105">Methods</span></span>  
 <span data-ttu-id="a1820-106">Klasa OperationBehaviorAttribute nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="a1820-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a1820-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a1820-107">Properties</span></span>  
 <span data-ttu-id="a1820-108">Klasa OperationBehaviorAttribute ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="a1820-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="a1820-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="a1820-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="a1820-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a1820-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1820-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1820-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1820-112">Stan funkcji automatycznego usuwania parametrów.</span><span class="sxs-lookup"><span data-stu-id="a1820-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="a1820-113">Personifikacja</span><span class="sxs-lookup"><span data-stu-id="a1820-113">Impersonation</span></span>  
 <span data-ttu-id="a1820-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="a1820-114">Data type: string</span></span>  
  
 <span data-ttu-id="a1820-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1820-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1820-116">Wskazuje poziom personifikacji wywołującego obsługiwany przez operację.</span><span class="sxs-lookup"><span data-stu-id="a1820-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="a1820-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="a1820-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="a1820-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="a1820-118">Data type: string</span></span>  
  
 <span data-ttu-id="a1820-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1820-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1820-120">Wskazuje, kiedy ma wywołania operacji ponowne przetworzenie obiektu.</span><span class="sxs-lookup"><span data-stu-id="a1820-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="a1820-121">Wartość TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="a1820-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="a1820-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a1820-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1820-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1820-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1820-124">Wskazuje, czy ma być automatycznie przekazywana bieżącej transakcji, jeśli wystąpi żaden nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="a1820-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="a1820-125">Właściwości TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="a1820-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="a1820-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a1820-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="a1820-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a1820-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a1820-128">Wskazuje, czy operacja wymaga transakcji.</span><span class="sxs-lookup"><span data-stu-id="a1820-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1820-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1820-129">Requirements</span></span>  
  
|<span data-ttu-id="a1820-130">MOF</span><span class="sxs-lookup"><span data-stu-id="a1820-130">MOF</span></span>|<span data-ttu-id="a1820-131">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a1820-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a1820-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="a1820-132">Namespace</span></span>|<span data-ttu-id="a1820-133">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a1820-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a1820-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1820-134">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
