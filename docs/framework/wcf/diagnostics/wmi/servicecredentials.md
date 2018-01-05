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
ms.workload: dotnet
ms.openlocfilehash: 73fad36b5bf14745ca70d297fa988b90d46990df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="servicecredentials"></a><span data-ttu-id="4d570-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="4d570-102">ServiceCredentials</span></span>
<span data-ttu-id="4d570-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="4d570-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d570-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d570-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="4d570-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4d570-105">Methods</span></span>  
 <span data-ttu-id="4d570-106">Klasa ServiceCredentials nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="4d570-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4d570-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4d570-107">Properties</span></span>  
 <span data-ttu-id="4d570-108">Klasa ServiceCredentials ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="4d570-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="4d570-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="4d570-109">ClientCertificate</span></span>  
 <span data-ttu-id="4d570-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4d570-110">Data type: string</span></span>  
  
 <span data-ttu-id="4d570-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d570-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d570-112">Certyfikat uwierzytelniania i dostarczania ustawień klienta dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="4d570-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="4d570-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="4d570-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="4d570-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4d570-114">Data type: string</span></span>  
  
 <span data-ttu-id="4d570-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d570-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d570-116">Bieżący wystawiony token uwierzytelniania ustawienia dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="4d570-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="4d570-117">elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="4d570-117">Peer</span></span>  
 <span data-ttu-id="4d570-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4d570-118">Data type: string</span></span>  
  
 <span data-ttu-id="4d570-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d570-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d570-120">Bieżące poświadczenia uwierzytelniania i dostarczania ustawienia używane przez punkty końcowego transportów elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="4d570-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="4d570-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="4d570-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="4d570-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4d570-122">Data type: string</span></span>  
  
 <span data-ttu-id="4d570-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d570-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d570-124">Określa bieżące ustawienia bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="4d570-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="4d570-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="4d570-125">ServiceCertificate</span></span>  
 <span data-ttu-id="4d570-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4d570-126">Data type: string</span></span>  
  
 <span data-ttu-id="4d570-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d570-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d570-128">Certyfikat skojarzony z tą usługą.</span><span class="sxs-lookup"><span data-stu-id="4d570-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="4d570-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="4d570-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="4d570-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4d570-130">Data type: string</span></span>  
  
 <span data-ttu-id="4d570-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d570-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d570-132">Ustawienia nazwy użytkownika i hasła dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="4d570-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="4d570-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="4d570-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="4d570-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4d570-134">Data type: string</span></span>  
  
 <span data-ttu-id="4d570-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d570-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d570-136">Ustawienia uwierzytelniania systemu Windows dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="4d570-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d570-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d570-137">Requirements</span></span>  
  
|<span data-ttu-id="4d570-138">MOF</span><span class="sxs-lookup"><span data-stu-id="4d570-138">MOF</span></span>|<span data-ttu-id="4d570-139">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4d570-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4d570-140">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4d570-140">Namespace</span></span>|<span data-ttu-id="4d570-141">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4d570-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d570-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d570-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
