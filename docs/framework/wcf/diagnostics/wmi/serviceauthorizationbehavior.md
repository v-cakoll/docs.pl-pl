---
title: ServiceAuthorizationBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62f3e32e886f49ac8dde6af5c37a4e57373c9576
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="6fe7d-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="6fe7d-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="6fe7d-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="6fe7d-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fe7d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fe7d-104">Syntax</span></span>  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6fe7d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6fe7d-105">Methods</span></span>  
 <span data-ttu-id="6fe7d-106">Klasa ServiceAuthorizationBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6fe7d-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6fe7d-107">Properties</span></span>  
 <span data-ttu-id="6fe7d-108">Klasa ServiceAuthorizationBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="6fe7d-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="6fe7d-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="6fe7d-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="6fe7d-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="6fe7d-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="6fe7d-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6fe7d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6fe7d-112">Wartość, która kontroluje, czy usługa próbuje dokonać personifikacji, używając poświadczeń dostarczonych w komunikacie przychodzącym.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="6fe7d-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="6fe7d-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="6fe7d-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="6fe7d-114">Data type: string</span></span>  
  
 <span data-ttu-id="6fe7d-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6fe7d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6fe7d-116">Podmiot zabezpieczeń używany do wykonywania operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="6fe7d-117">Element RoleProvider</span><span class="sxs-lookup"><span data-stu-id="6fe7d-117">RoleProvider</span></span>  
 <span data-ttu-id="6fe7d-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="6fe7d-118">Data type: string</span></span>  
  
 <span data-ttu-id="6fe7d-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6fe7d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6fe7d-120">Nazwa dostawcy ról ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="6fe7d-121">Obiekt ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="6fe7d-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="6fe7d-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="6fe7d-122">Data type: string</span></span>  
  
 <span data-ttu-id="6fe7d-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6fe7d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6fe7d-124">Menedżer autoryzacji używany do przeprowadzania niestandardowej autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fe7d-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6fe7d-125">Requirements</span></span>  
  
|<span data-ttu-id="6fe7d-126">MOF</span><span class="sxs-lookup"><span data-stu-id="6fe7d-126">MOF</span></span>|<span data-ttu-id="6fe7d-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6fe7d-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6fe7d-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="6fe7d-128">Namespace</span></span>|<span data-ttu-id="6fe7d-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6fe7d-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6fe7d-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6fe7d-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
