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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e4cc9d7d7d46157b7df202c6daffb31b90fa98c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="servicecredentials"></a><span data-ttu-id="1f3fa-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="1f3fa-102">ServiceCredentials</span></span>
<span data-ttu-id="1f3fa-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="1f3fa-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f3fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f3fa-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1f3fa-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1f3fa-105">Methods</span></span>  
 <span data-ttu-id="1f3fa-106">Klasa ServiceCredentials nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="1f3fa-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1f3fa-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1f3fa-107">Properties</span></span>  
 <span data-ttu-id="1f3fa-108">Klasa ServiceCredentials ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="1f3fa-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="1f3fa-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="1f3fa-109">ClientCertificate</span></span>  
 <span data-ttu-id="1f3fa-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1f3fa-110">Data type: string</span></span>  
  
 <span data-ttu-id="1f3fa-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1f3fa-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f3fa-112">Certyfikat uwierzytelniania i dostarczania ustawień klienta dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="1f3fa-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="1f3fa-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="1f3fa-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="1f3fa-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1f3fa-114">Data type: string</span></span>  
  
 <span data-ttu-id="1f3fa-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1f3fa-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f3fa-116">Bieżący wystawiony token uwierzytelniania ustawienia dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="1f3fa-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="1f3fa-117">elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="1f3fa-117">Peer</span></span>  
 <span data-ttu-id="1f3fa-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1f3fa-118">Data type: string</span></span>  
  
 <span data-ttu-id="1f3fa-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1f3fa-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f3fa-120">Bieżące poświadczenia uwierzytelniania i dostarczania ustawienia używane przez punkty końcowego transportów elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="1f3fa-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="1f3fa-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="1f3fa-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="1f3fa-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1f3fa-122">Data type: string</span></span>  
  
 <span data-ttu-id="1f3fa-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1f3fa-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f3fa-124">Określa bieżące ustawienia bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="1f3fa-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="1f3fa-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="1f3fa-125">ServiceCertificate</span></span>  
 <span data-ttu-id="1f3fa-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1f3fa-126">Data type: string</span></span>  
  
 <span data-ttu-id="1f3fa-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1f3fa-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f3fa-128">Certyfikat skojarzony z tą usługą.</span><span class="sxs-lookup"><span data-stu-id="1f3fa-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="1f3fa-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="1f3fa-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="1f3fa-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1f3fa-130">Data type: string</span></span>  
  
 <span data-ttu-id="1f3fa-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1f3fa-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f3fa-132">Ustawienia nazwy użytkownika i hasła dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="1f3fa-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="1f3fa-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="1f3fa-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="1f3fa-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1f3fa-134">Data type: string</span></span>  
  
 <span data-ttu-id="1f3fa-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1f3fa-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f3fa-136">Ustawienia uwierzytelniania systemu Windows dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="1f3fa-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f3fa-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f3fa-137">Requirements</span></span>  
  
|<span data-ttu-id="1f3fa-138">MOF</span><span class="sxs-lookup"><span data-stu-id="1f3fa-138">MOF</span></span>|<span data-ttu-id="1f3fa-139">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1f3fa-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1f3fa-140">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="1f3fa-140">Namespace</span></span>|<span data-ttu-id="1f3fa-141">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1f3fa-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f3fa-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f3fa-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
