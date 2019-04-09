---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: 51555e3357b8c33a53261c4894d97798b0a05656
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102937"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="81dd7-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="81dd7-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="81dd7-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="81dd7-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81dd7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81dd7-104">Syntax</span></span>  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="81dd7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="81dd7-105">Methods</span></span>  
 <span data-ttu-id="81dd7-106">Klasa ServiceAuthorizationBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="81dd7-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="81dd7-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="81dd7-107">Properties</span></span>  
 <span data-ttu-id="81dd7-108">Klasa ServiceAuthorizationBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="81dd7-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="81dd7-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="81dd7-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="81dd7-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="81dd7-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="81dd7-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81dd7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81dd7-112">Wartość, która kontroluje, czy usługa próbuje personifikować przy użyciu poświadczeń dostarczonych przez wiadomości przychodzącej.</span><span class="sxs-lookup"><span data-stu-id="81dd7-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="81dd7-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="81dd7-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="81dd7-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81dd7-114">Data type: string</span></span>  
  
 <span data-ttu-id="81dd7-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81dd7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81dd7-116">Podmiot zabezpieczeń używany do wykonywania operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="81dd7-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="81dd7-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="81dd7-117">RoleProvider</span></span>  
 <span data-ttu-id="81dd7-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81dd7-118">Data type: string</span></span>  
  
 <span data-ttu-id="81dd7-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81dd7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81dd7-120">Nazwa dostawcy ról ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="81dd7-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="81dd7-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="81dd7-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="81dd7-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81dd7-122">Data type: string</span></span>  
  
 <span data-ttu-id="81dd7-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81dd7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81dd7-124">Menedżer autoryzacji używanych na potrzeby autoryzacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="81dd7-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81dd7-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81dd7-125">Requirements</span></span>  
  
|<span data-ttu-id="81dd7-126">MOF</span><span class="sxs-lookup"><span data-stu-id="81dd7-126">MOF</span></span>|<span data-ttu-id="81dd7-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="81dd7-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="81dd7-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="81dd7-128">Namespace</span></span>|<span data-ttu-id="81dd7-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="81dd7-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81dd7-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81dd7-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
