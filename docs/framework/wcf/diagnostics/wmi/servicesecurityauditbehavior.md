---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3adc721dd8ad0fb706e172373e5da70fe6032db6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="9e1d4-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="9e1d4-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="9e1d4-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="9e1d4-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e1d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e1d4-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9e1d4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9e1d4-105">Methods</span></span>  
 <span data-ttu-id="9e1d4-106">Klasa ServiceSecurityAuditBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="9e1d4-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9e1d4-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9e1d4-107">Properties</span></span>  
 <span data-ttu-id="9e1d4-108">Klasa ServiceSecurityAuditBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="9e1d4-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="9e1d4-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="9e1d4-109">AuditLogLocation</span></span>  
 <span data-ttu-id="9e1d4-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9e1d4-110">Data type: string</span></span>  
  
 <span data-ttu-id="9e1d4-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9e1d4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e1d4-112">Lokalizacja dziennika inspekcji.</span><span class="sxs-lookup"><span data-stu-id="9e1d4-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="9e1d4-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="9e1d4-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="9e1d4-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9e1d4-114">Data type: string</span></span>  
  
 <span data-ttu-id="9e1d4-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9e1d4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e1d4-116">Typ poziomu uwierzytelniania komunikatu używany do rejestrowania zdarzeń inspekcji.</span><span class="sxs-lookup"><span data-stu-id="9e1d4-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="9e1d4-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="9e1d4-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="9e1d4-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9e1d4-118">Data type: string</span></span>  
  
 <span data-ttu-id="9e1d4-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9e1d4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e1d4-120">Typy zdarzeń autoryzacji, które są rejestrowane w dzienniku inspekcji.</span><span class="sxs-lookup"><span data-stu-id="9e1d4-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="9e1d4-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="9e1d4-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="9e1d4-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="9e1d4-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="9e1d4-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9e1d4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9e1d4-124">Wartość logiczna określająca zachowanie w sytuacji wystąpienia błędów zapisu do dziennika inspekcji.</span><span class="sxs-lookup"><span data-stu-id="9e1d4-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e1d4-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e1d4-125">Requirements</span></span>  
  
|<span data-ttu-id="9e1d4-126">MOF</span><span class="sxs-lookup"><span data-stu-id="9e1d4-126">MOF</span></span>|<span data-ttu-id="9e1d4-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9e1d4-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9e1d4-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="9e1d4-128">Namespace</span></span>|<span data-ttu-id="9e1d4-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9e1d4-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e1d4-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e1d4-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
