---
title: OperationBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fd01c5c4d37f5c0ec5673dc9aa4a47cb8affbc29
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="7f674-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="7f674-102">OperationBehaviorAttribute</span></span>
<span data-ttu-id="7f674-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="7f674-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f674-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f674-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="7f674-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7f674-105">Methods</span></span>  
 <span data-ttu-id="7f674-106">Klasa OperationBehaviorAttribute nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="7f674-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7f674-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7f674-107">Properties</span></span>  
 <span data-ttu-id="7f674-108">Klasa OperationBehaviorAttribute ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="7f674-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="7f674-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="7f674-109">AutoDisposeParameters</span></span>  
 <span data-ttu-id="7f674-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="7f674-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="7f674-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7f674-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f674-112">Stan funkcji automatycznego usuwania parametrów.</span><span class="sxs-lookup"><span data-stu-id="7f674-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="7f674-113">Personifikacja</span><span class="sxs-lookup"><span data-stu-id="7f674-113">Impersonation</span></span>  
 <span data-ttu-id="7f674-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="7f674-114">Data type: string</span></span>  
  
 <span data-ttu-id="7f674-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7f674-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f674-116">Wskazuje poziom personifikacji wywołującego obsługiwany przez operację.</span><span class="sxs-lookup"><span data-stu-id="7f674-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="7f674-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="7f674-117">ReleaseInstanceMode</span></span>  
 <span data-ttu-id="7f674-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="7f674-118">Data type: string</span></span>  
  
 <span data-ttu-id="7f674-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7f674-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f674-120">Wskazuje, kiedy ma wywołania operacji ponowne przetworzenie obiektu.</span><span class="sxs-lookup"><span data-stu-id="7f674-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="7f674-121">Wartość TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="7f674-121">TransactionAutoComplete</span></span>  
 <span data-ttu-id="7f674-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="7f674-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="7f674-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7f674-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f674-124">Wskazuje, czy ma być automatycznie przekazywana bieżącej transakcji, jeśli wystąpi żaden nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7f674-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="7f674-125">Właściwości TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="7f674-125">TransactionScopeRequired</span></span>  
 <span data-ttu-id="7f674-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="7f674-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="7f674-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7f674-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f674-128">Wskazuje, czy operacja wymaga transakcji.</span><span class="sxs-lookup"><span data-stu-id="7f674-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f674-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f674-129">Requirements</span></span>  
  
|<span data-ttu-id="7f674-130">MOF</span><span class="sxs-lookup"><span data-stu-id="7f674-130">MOF</span></span>|<span data-ttu-id="7f674-131">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7f674-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7f674-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="7f674-132">Namespace</span></span>|<span data-ttu-id="7f674-133">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7f674-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f674-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f674-134">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>
