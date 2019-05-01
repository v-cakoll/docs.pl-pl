---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: d9563bd3bfe067ad83bfa03e7c6375a9db933f14
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956984"
---
# <a name="servicecredentials"></a><span data-ttu-id="4446c-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="4446c-102">ServiceCredentials</span></span>
<span data-ttu-id="4446c-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="4446c-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4446c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4446c-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="4446c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4446c-105">Methods</span></span>  
 <span data-ttu-id="4446c-106">Klasa ServiceCredentials nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="4446c-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4446c-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4446c-107">Properties</span></span>  
 <span data-ttu-id="4446c-108">Klasa ServiceCredentials ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="4446c-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="4446c-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="4446c-109">ClientCertificate</span></span>  
 <span data-ttu-id="4446c-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4446c-110">Data type: string</span></span>  
  
 <span data-ttu-id="4446c-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4446c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4446c-112">Certyfikat uwierzytelniania i inicjowania obsługi ustawień klienta dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="4446c-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="4446c-113">issuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="4446c-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="4446c-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4446c-114">Data type: string</span></span>  
  
 <span data-ttu-id="4446c-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4446c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4446c-116">Bieżący wystawiony token uwierzytelniania ustawienia dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="4446c-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="4446c-117">Elementu równorzędnego</span><span class="sxs-lookup"><span data-stu-id="4446c-117">Peer</span></span>  
 <span data-ttu-id="4446c-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4446c-118">Data type: string</span></span>  
  
 <span data-ttu-id="4446c-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4446c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4446c-120">Bieżący poświadczeń uwierzytelniania i inicjowania obsługi ustawienia używane przez punkty końcowe transport elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="4446c-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="4446c-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="4446c-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="4446c-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4446c-122">Data type: string</span></span>  
  
 <span data-ttu-id="4446c-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4446c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4446c-124">Określa bieżące ustawienia bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="4446c-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="4446c-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="4446c-125">ServiceCertificate</span></span>  
 <span data-ttu-id="4446c-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4446c-126">Data type: string</span></span>  
  
 <span data-ttu-id="4446c-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4446c-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4446c-128">Certyfikat skojarzony z tą usługą.</span><span class="sxs-lookup"><span data-stu-id="4446c-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="4446c-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="4446c-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="4446c-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4446c-130">Data type: string</span></span>  
  
 <span data-ttu-id="4446c-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4446c-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4446c-132">Ustawienia nazwy użytkownika i hasła dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="4446c-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="4446c-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="4446c-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="4446c-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4446c-134">Data type: string</span></span>  
  
 <span data-ttu-id="4446c-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4446c-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4446c-136">Ustawienia uwierzytelniania Windows dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="4446c-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4446c-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4446c-137">Requirements</span></span>  
  
|<span data-ttu-id="4446c-138">MOF</span><span class="sxs-lookup"><span data-stu-id="4446c-138">MOF</span></span>|<span data-ttu-id="4446c-139">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4446c-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4446c-140">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4446c-140">Namespace</span></span>|<span data-ttu-id="4446c-141">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4446c-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4446c-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4446c-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceCredentials>
