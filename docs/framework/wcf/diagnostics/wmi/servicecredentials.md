---
title: ServiceCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89aff21ed916e1b486a191f86dde5ed8b3e4ba22
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="servicecredentials"></a><span data-ttu-id="465d4-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="465d4-102">ServiceCredentials</span></span>
<span data-ttu-id="465d4-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="465d4-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="465d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="465d4-104">Syntax</span></span>  
  
```  
class ServiceCredentials : Behavior  
{  
  string ClientCertificate;  
  string IssuedTokenAuthentication;  
  string Peer;  
  string SecureConversationAuthentication;  
  string ServiceCertificate;  
  string UserNameAuthentication;  
  string WindowsAuthentication;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="465d4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="465d4-105">Methods</span></span>  
 <span data-ttu-id="465d4-106">Klasa ServiceCredentials nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="465d4-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="465d4-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="465d4-107">Properties</span></span>  
 <span data-ttu-id="465d4-108">Klasa ServiceCredentials ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="465d4-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="465d4-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="465d4-109">ClientCertificate</span></span>  
 <span data-ttu-id="465d4-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="465d4-110">Data type: string</span></span>  
  
 <span data-ttu-id="465d4-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="465d4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="465d4-112">Certyfikat uwierzytelniania i dostarczania ustawień klienta dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="465d4-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="465d4-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="465d4-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="465d4-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="465d4-114">Data type: string</span></span>  
  
 <span data-ttu-id="465d4-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="465d4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="465d4-116">Bieżący wystawiony token uwierzytelniania ustawienia dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="465d4-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="465d4-117">elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="465d4-117">Peer</span></span>  
 <span data-ttu-id="465d4-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="465d4-118">Data type: string</span></span>  
  
 <span data-ttu-id="465d4-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="465d4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="465d4-120">Bieżące poświadczenia uwierzytelniania i dostarczania ustawienia używane przez punkty końcowego transportów elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="465d4-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="465d4-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="465d4-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="465d4-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="465d4-122">Data type: string</span></span>  
  
 <span data-ttu-id="465d4-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="465d4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="465d4-124">Określa bieżące ustawienia bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="465d4-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="465d4-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="465d4-125">ServiceCertificate</span></span>  
 <span data-ttu-id="465d4-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="465d4-126">Data type: string</span></span>  
  
 <span data-ttu-id="465d4-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="465d4-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="465d4-128">Certyfikat skojarzony z tą usługą.</span><span class="sxs-lookup"><span data-stu-id="465d4-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="465d4-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="465d4-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="465d4-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="465d4-130">Data type: string</span></span>  
  
 <span data-ttu-id="465d4-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="465d4-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="465d4-132">Ustawienia nazwy użytkownika i hasła dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="465d4-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="465d4-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="465d4-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="465d4-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="465d4-134">Data type: string</span></span>  
  
 <span data-ttu-id="465d4-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="465d4-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="465d4-136">Ustawienia uwierzytelniania systemu Windows dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="465d4-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="465d4-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="465d4-137">Requirements</span></span>  
  
|<span data-ttu-id="465d4-138">MOF</span><span class="sxs-lookup"><span data-stu-id="465d4-138">MOF</span></span>|<span data-ttu-id="465d4-139">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="465d4-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="465d4-140">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="465d4-140">Namespace</span></span>|<span data-ttu-id="465d4-141">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="465d4-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="465d4-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="465d4-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
