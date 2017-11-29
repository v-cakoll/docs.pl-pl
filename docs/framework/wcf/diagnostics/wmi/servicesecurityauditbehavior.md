---
title: ServiceSecurityAuditBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 1ce712bbdb258c477a2ee56f47281b1a1d09ec54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="3c765-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="3c765-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="3c765-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="3c765-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c765-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c765-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3c765-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3c765-105">Methods</span></span>  
 <span data-ttu-id="3c765-106">Klasa ServiceSecurityAuditBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="3c765-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3c765-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3c765-107">Properties</span></span>  
 <span data-ttu-id="3c765-108">Klasa ServiceSecurityAuditBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="3c765-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="3c765-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="3c765-109">AuditLogLocation</span></span>  
 <span data-ttu-id="3c765-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3c765-110">Data type: string</span></span>  
  
 <span data-ttu-id="3c765-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3c765-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3c765-112">Lokalizacja dziennika inspekcji.</span><span class="sxs-lookup"><span data-stu-id="3c765-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="3c765-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="3c765-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="3c765-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3c765-114">Data type: string</span></span>  
  
 <span data-ttu-id="3c765-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3c765-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3c765-116">Typ poziomu uwierzytelniania komunikatu używany do rejestrowania zdarzeń inspekcji.</span><span class="sxs-lookup"><span data-stu-id="3c765-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="3c765-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="3c765-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="3c765-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3c765-118">Data type: string</span></span>  
  
 <span data-ttu-id="3c765-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3c765-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3c765-120">Typy zdarzeń autoryzacji, które są rejestrowane w dzienniku inspekcji.</span><span class="sxs-lookup"><span data-stu-id="3c765-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="3c765-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="3c765-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="3c765-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="3c765-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="3c765-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3c765-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3c765-124">Wartość logiczna określająca zachowanie w sytuacji wystąpienia błędów zapisu do dziennika inspekcji.</span><span class="sxs-lookup"><span data-stu-id="3c765-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c765-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c765-125">Requirements</span></span>  
  
|<span data-ttu-id="3c765-126">MOF</span><span class="sxs-lookup"><span data-stu-id="3c765-126">MOF</span></span>|<span data-ttu-id="3c765-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3c765-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3c765-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="3c765-128">Namespace</span></span>|<span data-ttu-id="3c765-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3c765-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3c765-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c765-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
