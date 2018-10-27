---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: 26bd0c95f930bf7859ae6409d797afbb596844fa
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180670"
---
# <a name="servicecredentials"></a><span data-ttu-id="9668b-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="9668b-102">ServiceCredentials</span></span>
<span data-ttu-id="9668b-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="9668b-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9668b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9668b-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="9668b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9668b-105">Methods</span></span>  
 <span data-ttu-id="9668b-106">Klasa ServiceCredentials nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="9668b-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9668b-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9668b-107">Properties</span></span>  
 <span data-ttu-id="9668b-108">Klasa ServiceCredentials ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="9668b-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="9668b-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="9668b-109">ClientCertificate</span></span>  
 <span data-ttu-id="9668b-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9668b-110">Data type: string</span></span>  
  
 <span data-ttu-id="9668b-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9668b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9668b-112">Certyfikat uwierzytelniania i inicjowania obsługi ustawień klienta dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="9668b-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="9668b-113">issuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="9668b-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="9668b-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9668b-114">Data type: string</span></span>  
  
 <span data-ttu-id="9668b-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9668b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9668b-116">Bieżący wystawiony token uwierzytelniania ustawienia dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="9668b-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="9668b-117">Elementu równorzędnego</span><span class="sxs-lookup"><span data-stu-id="9668b-117">Peer</span></span>  
 <span data-ttu-id="9668b-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9668b-118">Data type: string</span></span>  
  
 <span data-ttu-id="9668b-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9668b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9668b-120">Bieżący poświadczeń uwierzytelniania i inicjowania obsługi ustawienia używane przez punkty końcowe transport elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="9668b-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="9668b-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="9668b-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="9668b-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9668b-122">Data type: string</span></span>  
  
 <span data-ttu-id="9668b-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9668b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9668b-124">Określa bieżące ustawienia bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="9668b-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="9668b-125">serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="9668b-125">ServiceCertificate</span></span>  
 <span data-ttu-id="9668b-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9668b-126">Data type: string</span></span>  
  
 <span data-ttu-id="9668b-127">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9668b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9668b-128">Certyfikat skojarzony z tą usługą.</span><span class="sxs-lookup"><span data-stu-id="9668b-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="9668b-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="9668b-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="9668b-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9668b-130">Data type: string</span></span>  
  
 <span data-ttu-id="9668b-131">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9668b-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9668b-132">Ustawienia nazwy użytkownika i hasła dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="9668b-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="9668b-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="9668b-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="9668b-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9668b-134">Data type: string</span></span>  
  
 <span data-ttu-id="9668b-135">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9668b-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9668b-136">Ustawienia uwierzytelniania Windows dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="9668b-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9668b-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9668b-137">Requirements</span></span>  
  
|<span data-ttu-id="9668b-138">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="9668b-138">MOF</span></span>|<span data-ttu-id="9668b-139">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9668b-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9668b-140">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="9668b-140">Namespace</span></span>|<span data-ttu-id="9668b-141">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9668b-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9668b-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9668b-142">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceCredentials>
