---
title: ServiceSecurityAuditBehavior
ms.date: 03/30/2017
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
ms.openlocfilehash: 30679e1f67c6943bf674a6bbd8bf12be090765a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956900"
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="88fb6-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="88fb6-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="88fb6-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="88fb6-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88fb6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88fb6-104">Syntax</span></span>  
  
```csharp  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="88fb6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="88fb6-105">Methods</span></span>  
 <span data-ttu-id="88fb6-106">Klasa ServiceSecurityAuditBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="88fb6-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="88fb6-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="88fb6-107">Properties</span></span>  
 <span data-ttu-id="88fb6-108">Klasa ServiceSecurityAuditBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="88fb6-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="88fb6-109">auditLogLocation</span><span class="sxs-lookup"><span data-stu-id="88fb6-109">AuditLogLocation</span></span>  
 <span data-ttu-id="88fb6-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="88fb6-110">Data type: string</span></span>  
  
 <span data-ttu-id="88fb6-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="88fb6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="88fb6-112">Lokalizacja dziennika inspekcji.</span><span class="sxs-lookup"><span data-stu-id="88fb6-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="88fb6-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="88fb6-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="88fb6-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="88fb6-114">Data type: string</span></span>  
  
 <span data-ttu-id="88fb6-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="88fb6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="88fb6-116">Typ poziom uwierzytelniania wiadomości, która jest używana do rejestrowania zdarzeń inspekcji.</span><span class="sxs-lookup"><span data-stu-id="88fb6-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="88fb6-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="88fb6-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="88fb6-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="88fb6-118">Data type: string</span></span>  
  
 <span data-ttu-id="88fb6-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="88fb6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="88fb6-120">Typy zdarzeń autoryzacji, które są rejestrowane w dzienniku inspekcji.</span><span class="sxs-lookup"><span data-stu-id="88fb6-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="88fb6-121">suppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="88fb6-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="88fb6-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="88fb6-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="88fb6-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="88fb6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="88fb6-124">Wartość logiczna określająca zachowanie w sytuacji pominięcia błędów zapisu do dziennika inspekcji.</span><span class="sxs-lookup"><span data-stu-id="88fb6-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88fb6-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88fb6-125">Requirements</span></span>  
  
|<span data-ttu-id="88fb6-126">MOF</span><span class="sxs-lookup"><span data-stu-id="88fb6-126">MOF</span></span>|<span data-ttu-id="88fb6-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="88fb6-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="88fb6-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="88fb6-128">Namespace</span></span>|<span data-ttu-id="88fb6-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="88fb6-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="88fb6-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88fb6-130">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
