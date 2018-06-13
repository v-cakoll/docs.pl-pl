---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: e03f83927ec5aef7f916b2262c9c8cff1db68ac9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486476"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="ae5bf-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="ae5bf-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="ae5bf-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="ae5bf-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae5bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ae5bf-104">Syntax</span></span>  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ae5bf-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ae5bf-105">Methods</span></span>  
 <span data-ttu-id="ae5bf-106">Klasa ServiceAuthorizationBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="ae5bf-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ae5bf-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ae5bf-107">Properties</span></span>  
 <span data-ttu-id="ae5bf-108">Klasa ServiceAuthorizationBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="ae5bf-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="ae5bf-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="ae5bf-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="ae5bf-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="ae5bf-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="ae5bf-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ae5bf-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ae5bf-112">Wartość, która kontroluje, czy usługa próbuje dokonać personifikacji, używając poświadczeń dostarczonych w komunikacie przychodzącym.</span><span class="sxs-lookup"><span data-stu-id="ae5bf-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="ae5bf-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="ae5bf-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="ae5bf-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="ae5bf-114">Data type: string</span></span>  
  
 <span data-ttu-id="ae5bf-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ae5bf-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ae5bf-116">Podmiot zabezpieczeń używany do wykonywania operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="ae5bf-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="ae5bf-117">Element RoleProvider</span><span class="sxs-lookup"><span data-stu-id="ae5bf-117">RoleProvider</span></span>  
 <span data-ttu-id="ae5bf-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="ae5bf-118">Data type: string</span></span>  
  
 <span data-ttu-id="ae5bf-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ae5bf-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ae5bf-120">Nazwa dostawcy ról ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ae5bf-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="ae5bf-121">Obiekt ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="ae5bf-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="ae5bf-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="ae5bf-122">Data type: string</span></span>  
  
 <span data-ttu-id="ae5bf-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ae5bf-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ae5bf-124">Menedżer autoryzacji używany do przeprowadzania niestandardowej autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="ae5bf-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae5bf-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ae5bf-125">Requirements</span></span>  
  
|<span data-ttu-id="ae5bf-126">MOF</span><span class="sxs-lookup"><span data-stu-id="ae5bf-126">MOF</span></span>|<span data-ttu-id="ae5bf-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ae5bf-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ae5bf-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="ae5bf-128">Namespace</span></span>|<span data-ttu-id="ae5bf-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ae5bf-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae5bf-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae5bf-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
