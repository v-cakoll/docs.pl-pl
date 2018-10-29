---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: c916d0820a1eae333384deab7b0619abfbdc8167
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196820"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="b4b25-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="b4b25-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="b4b25-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="b4b25-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4b25-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4b25-104">Syntax</span></span>  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b4b25-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b4b25-105">Methods</span></span>  
 <span data-ttu-id="b4b25-106">Klasa ServiceAuthorizationBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="b4b25-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b4b25-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b4b25-107">Properties</span></span>  
 <span data-ttu-id="b4b25-108">Klasa ServiceAuthorizationBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="b4b25-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="b4b25-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="b4b25-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="b4b25-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="b4b25-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="b4b25-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b4b25-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4b25-112">Wartość, która kontroluje, czy usługa próbuje personifikować przy użyciu poświadczeń dostarczonych przez wiadomości przychodzącej.</span><span class="sxs-lookup"><span data-stu-id="b4b25-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="b4b25-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="b4b25-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="b4b25-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b4b25-114">Data type: string</span></span>  
  
 <span data-ttu-id="b4b25-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b4b25-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4b25-116">Podmiot zabezpieczeń używany do wykonywania operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="b4b25-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="b4b25-117">Element RoleProvider</span><span class="sxs-lookup"><span data-stu-id="b4b25-117">RoleProvider</span></span>  
 <span data-ttu-id="b4b25-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b4b25-118">Data type: string</span></span>  
  
 <span data-ttu-id="b4b25-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b4b25-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4b25-120">Nazwa dostawcy ról ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b4b25-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="b4b25-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="b4b25-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="b4b25-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b4b25-122">Data type: string</span></span>  
  
 <span data-ttu-id="b4b25-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b4b25-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4b25-124">Menedżer autoryzacji używanych na potrzeby autoryzacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="b4b25-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4b25-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4b25-125">Requirements</span></span>  
  
|<span data-ttu-id="b4b25-126">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="b4b25-126">MOF</span></span>|<span data-ttu-id="b4b25-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b4b25-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b4b25-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="b4b25-128">Namespace</span></span>|<span data-ttu-id="b4b25-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b4b25-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4b25-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4b25-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
