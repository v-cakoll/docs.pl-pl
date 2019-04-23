---
title: ServiceAuthorizationBehavior
ms.date: 03/30/2017
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
ms.openlocfilehash: 51555e3357b8c33a53261c4894d97798b0a05656
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59972839"
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="49822-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="49822-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="49822-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="49822-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49822-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49822-104">Syntax</span></span>  
  
```csharp
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="49822-105">Metody</span><span class="sxs-lookup"><span data-stu-id="49822-105">Methods</span></span>  
 <span data-ttu-id="49822-106">Klasa ServiceAuthorizationBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="49822-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="49822-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="49822-107">Properties</span></span>  
 <span data-ttu-id="49822-108">Klasa ServiceAuthorizationBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="49822-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="49822-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="49822-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="49822-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="49822-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="49822-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="49822-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49822-112">Wartość, która kontroluje, czy usługa próbuje personifikować przy użyciu poświadczeń dostarczonych przez wiadomości przychodzącej.</span><span class="sxs-lookup"><span data-stu-id="49822-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="49822-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="49822-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="49822-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="49822-114">Data type: string</span></span>  
  
 <span data-ttu-id="49822-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="49822-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49822-116">Podmiot zabezpieczeń używany do wykonywania operacji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="49822-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="49822-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="49822-117">RoleProvider</span></span>  
 <span data-ttu-id="49822-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="49822-118">Data type: string</span></span>  
  
 <span data-ttu-id="49822-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="49822-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49822-120">Nazwa dostawcy ról ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="49822-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="49822-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="49822-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="49822-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="49822-122">Data type: string</span></span>  
  
 <span data-ttu-id="49822-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="49822-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49822-124">Menedżer autoryzacji używanych na potrzeby autoryzacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="49822-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49822-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49822-125">Requirements</span></span>  
  
|<span data-ttu-id="49822-126">MOF</span><span class="sxs-lookup"><span data-stu-id="49822-126">MOF</span></span>|<span data-ttu-id="49822-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="49822-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="49822-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="49822-128">Namespace</span></span>|<span data-ttu-id="49822-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="49822-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49822-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49822-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
