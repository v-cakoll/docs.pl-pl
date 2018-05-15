---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: bf906e09ae71d26f8e95877f1c545c0724d57b9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="servicecredentials"></a><span data-ttu-id="1e635-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="1e635-102">ServiceCredentials</span></span>
<span data-ttu-id="1e635-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="1e635-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e635-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1e635-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1e635-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1e635-105">Methods</span></span>  
 <span data-ttu-id="1e635-106">Klasa ServiceCredentials nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="1e635-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1e635-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1e635-107">Properties</span></span>  
 <span data-ttu-id="1e635-108">Klasa ServiceCredentials ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="1e635-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="1e635-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="1e635-109">ClientCertificate</span></span>  
 <span data-ttu-id="1e635-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1e635-110">Data type: string</span></span>  
  
 <span data-ttu-id="1e635-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1e635-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e635-112">Certyfikat uwierzytelniania i dostarczania ustawień klienta dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="1e635-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="1e635-113">IssuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="1e635-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="1e635-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1e635-114">Data type: string</span></span>  
  
 <span data-ttu-id="1e635-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1e635-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e635-116">Bieżący wystawiony token uwierzytelniania ustawienia dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="1e635-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="1e635-117">elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="1e635-117">Peer</span></span>  
 <span data-ttu-id="1e635-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1e635-118">Data type: string</span></span>  
  
 <span data-ttu-id="1e635-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1e635-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e635-120">Bieżące poświadczenia uwierzytelniania i dostarczania ustawienia używane przez punkty końcowego transportów elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="1e635-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="1e635-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="1e635-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="1e635-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1e635-122">Data type: string</span></span>  
  
 <span data-ttu-id="1e635-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1e635-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e635-124">Określa bieżące ustawienia bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="1e635-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="1e635-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="1e635-125">ServiceCertificate</span></span>  
 <span data-ttu-id="1e635-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1e635-126">Data type: string</span></span>  
  
 <span data-ttu-id="1e635-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1e635-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e635-128">Certyfikat skojarzony z tą usługą.</span><span class="sxs-lookup"><span data-stu-id="1e635-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="1e635-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="1e635-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="1e635-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1e635-130">Data type: string</span></span>  
  
 <span data-ttu-id="1e635-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1e635-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e635-132">Ustawienia nazwy użytkownika i hasła dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="1e635-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="1e635-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="1e635-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="1e635-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1e635-134">Data type: string</span></span>  
  
 <span data-ttu-id="1e635-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1e635-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e635-136">Ustawienia uwierzytelniania systemu Windows dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="1e635-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e635-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1e635-137">Requirements</span></span>  
  
|<span data-ttu-id="1e635-138">MOF</span><span class="sxs-lookup"><span data-stu-id="1e635-138">MOF</span></span>|<span data-ttu-id="1e635-139">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1e635-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1e635-140">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="1e635-140">Namespace</span></span>|<span data-ttu-id="1e635-141">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1e635-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e635-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1e635-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
