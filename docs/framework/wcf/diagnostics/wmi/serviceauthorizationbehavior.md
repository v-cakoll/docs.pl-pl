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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: eb02a02557a88bf53ca1a8e5b30fe66d6995e545
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="3c472-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="3c472-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="3c472-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="3c472-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c472-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c472-104">Syntax</span></span>  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3c472-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3c472-105">Methods</span></span>  
 <span data-ttu-id="3c472-106">Klasa ServiceAuthorizationBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="3c472-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3c472-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3c472-107">Properties</span></span>  
 <span data-ttu-id="3c472-108">Klasa ServiceAuthorizationBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="3c472-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="3c472-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="3c472-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="3c472-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="3c472-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="3c472-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3c472-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3c472-112">Wartość, która kontroluje, czy usługa próbuje dokonać personifikacji, używając poświadczeń dostarczonych w komunikacie przychodzącym.</span><span class="sxs-lookup"><span data-stu-id="3c472-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="3c472-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="3c472-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="3c472-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3c472-114">Data type: string</span></span>  
  
 <span data-ttu-id="3c472-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3c472-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3c472-116">Podmiot zabezpieczeń używany do wykonywania operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="3c472-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="3c472-117">Element RoleProvider</span><span class="sxs-lookup"><span data-stu-id="3c472-117">RoleProvider</span></span>  
 <span data-ttu-id="3c472-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3c472-118">Data type: string</span></span>  
  
 <span data-ttu-id="3c472-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3c472-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3c472-120">Nazwa dostawcy ról ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3c472-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="3c472-121">Obiekt ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="3c472-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="3c472-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3c472-122">Data type: string</span></span>  
  
 <span data-ttu-id="3c472-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3c472-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3c472-124">Menedżer autoryzacji używany do przeprowadzania niestandardowej autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="3c472-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c472-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c472-125">Requirements</span></span>  
  
|<span data-ttu-id="3c472-126">MOF</span><span class="sxs-lookup"><span data-stu-id="3c472-126">MOF</span></span>|<span data-ttu-id="3c472-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3c472-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3c472-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="3c472-128">Namespace</span></span>|<span data-ttu-id="3c472-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3c472-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c472-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c472-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
