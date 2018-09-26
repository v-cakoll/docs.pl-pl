---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
author: BrucePerlerMS
ms.openlocfilehash: 8f43ee752830d95db6bbbdbe311b6d77735e31b5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070152"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="49105-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="49105-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="49105-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="49105-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49105-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49105-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="49105-105">Metody</span><span class="sxs-lookup"><span data-stu-id="49105-105">Methods</span></span>  
 <span data-ttu-id="49105-106">Klasa ServiceSecurityAuditBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="49105-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="49105-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="49105-107">Properties</span></span>  
 <span data-ttu-id="49105-108">Klasa ServiceSecurityAuditBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="49105-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="49105-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="49105-109">AuditLogLocation</span></span>  
 <span data-ttu-id="49105-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="49105-110">Data type: string</span></span>  
  
 <span data-ttu-id="49105-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="49105-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49105-112">Lokalizacja dziennika inspekcji.</span><span class="sxs-lookup"><span data-stu-id="49105-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="49105-113">messageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="49105-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="49105-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="49105-114">Data type: string</span></span>  
  
 <span data-ttu-id="49105-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="49105-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49105-116">Typ poziom uwierzytelniania wiadomości, która jest używana do rejestrowania zdarzeń inspekcji.</span><span class="sxs-lookup"><span data-stu-id="49105-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="49105-117">serviceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="49105-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="49105-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="49105-118">Data type: string</span></span>  
  
 <span data-ttu-id="49105-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="49105-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49105-120">Typy zdarzeń autoryzacji, które są rejestrowane w dzienniku inspekcji.</span><span class="sxs-lookup"><span data-stu-id="49105-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="49105-121">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="49105-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="49105-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="49105-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="49105-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="49105-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="49105-124">Wartość logiczna określająca zachowanie w sytuacji pominięcia błędów zapisu do dziennika inspekcji.</span><span class="sxs-lookup"><span data-stu-id="49105-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49105-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49105-125">Requirements</span></span>  
  
|<span data-ttu-id="49105-126">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="49105-126">MOF</span></span>|<span data-ttu-id="49105-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="49105-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="49105-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="49105-128">Namespace</span></span>|<span data-ttu-id="49105-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="49105-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49105-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="49105-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
