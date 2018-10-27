---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: e8b24877c2d76a3f2f90c27ae83374c7bca1328b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181163"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="138d2-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="138d2-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="138d2-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="138d2-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="138d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="138d2-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="138d2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="138d2-105">Methods</span></span>  
 <span data-ttu-id="138d2-106">Klasa ServiceSecurityAuditBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="138d2-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="138d2-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="138d2-107">Properties</span></span>  
 <span data-ttu-id="138d2-108">Klasa ServiceSecurityAuditBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="138d2-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="138d2-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="138d2-109">AuditLogLocation</span></span>  
 <span data-ttu-id="138d2-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="138d2-110">Data type: string</span></span>  
  
 <span data-ttu-id="138d2-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="138d2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="138d2-112">Lokalizacja dziennika inspekcji.</span><span class="sxs-lookup"><span data-stu-id="138d2-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="138d2-113">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="138d2-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="138d2-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="138d2-114">Data type: string</span></span>  
  
 <span data-ttu-id="138d2-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="138d2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="138d2-116">Typ poziom uwierzytelniania wiadomości, która jest używana do rejestrowania zdarzeń inspekcji.</span><span class="sxs-lookup"><span data-stu-id="138d2-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="138d2-117">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="138d2-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="138d2-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="138d2-118">Data type: string</span></span>  
  
 <span data-ttu-id="138d2-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="138d2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="138d2-120">Typy zdarzeń autoryzacji, które są rejestrowane w dzienniku inspekcji.</span><span class="sxs-lookup"><span data-stu-id="138d2-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="138d2-121">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="138d2-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="138d2-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="138d2-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="138d2-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="138d2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="138d2-124">Wartość logiczna określająca zachowanie w sytuacji pominięcia błędów zapisu do dziennika inspekcji.</span><span class="sxs-lookup"><span data-stu-id="138d2-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="138d2-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="138d2-125">Requirements</span></span>  
  
|<span data-ttu-id="138d2-126">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="138d2-126">MOF</span></span>|<span data-ttu-id="138d2-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="138d2-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="138d2-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="138d2-128">Namespace</span></span>|<span data-ttu-id="138d2-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="138d2-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="138d2-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="138d2-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
