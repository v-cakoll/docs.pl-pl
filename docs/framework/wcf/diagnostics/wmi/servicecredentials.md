---
title: ServiceCredentials
ms.date: 03/30/2017
ms.assetid: 9c780793-4785-46f7-add9-ac1ebeadb614
ms.openlocfilehash: 18100ac36b5116c2373171ff795fc23b75bbd6f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572123"
---
# <a name="servicecredentials"></a><span data-ttu-id="81963-102">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="81963-102">ServiceCredentials</span></span>
<span data-ttu-id="81963-103">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="81963-103">ServiceCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81963-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81963-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="81963-105">Metody</span><span class="sxs-lookup"><span data-stu-id="81963-105">Methods</span></span>  
 <span data-ttu-id="81963-106">Klasa ServiceCredentials nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="81963-106">The ServiceCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="81963-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="81963-107">Properties</span></span>  
 <span data-ttu-id="81963-108">Klasa ServiceCredentials ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="81963-108">The ServiceCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="81963-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="81963-109">ClientCertificate</span></span>  
 <span data-ttu-id="81963-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81963-110">Data type: string</span></span>  
  
 <span data-ttu-id="81963-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81963-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81963-112">Certyfikat uwierzytelniania i inicjowania obsługi ustawień klienta dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="81963-112">The client certificate authentication and provisioning settings for this service.</span></span>  
  
### <a name="issuedtokenauthentication"></a><span data-ttu-id="81963-113">issuedTokenAuthentication</span><span class="sxs-lookup"><span data-stu-id="81963-113">IssuedTokenAuthentication</span></span>  
 <span data-ttu-id="81963-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81963-114">Data type: string</span></span>  
  
 <span data-ttu-id="81963-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81963-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81963-116">Bieżący wystawiony token uwierzytelniania ustawienia dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="81963-116">The current issued token authentication settings for this service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="81963-117">Elementu równorzędnego</span><span class="sxs-lookup"><span data-stu-id="81963-117">Peer</span></span>  
 <span data-ttu-id="81963-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81963-118">Data type: string</span></span>  
  
 <span data-ttu-id="81963-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81963-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81963-120">Bieżący poświadczeń uwierzytelniania i inicjowania obsługi ustawienia używane przez punkty końcowe transport elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="81963-120">The current credential authentication and provisioning settings to be used by peer transport endpoints.</span></span>  
  
### <a name="secureconversationauthentication"></a><span data-ttu-id="81963-121">SecureConversationAuthentication</span><span class="sxs-lookup"><span data-stu-id="81963-121">SecureConversationAuthentication</span></span>  
 <span data-ttu-id="81963-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81963-122">Data type: string</span></span>  
  
 <span data-ttu-id="81963-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81963-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81963-124">Określa bieżące ustawienia bezpiecznej konwersacji.</span><span class="sxs-lookup"><span data-stu-id="81963-124">Specifies the current secure conversation settings.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="81963-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="81963-125">ServiceCertificate</span></span>  
 <span data-ttu-id="81963-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81963-126">Data type: string</span></span>  
  
 <span data-ttu-id="81963-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81963-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81963-128">Certyfikat skojarzony z tą usługą.</span><span class="sxs-lookup"><span data-stu-id="81963-128">The certificate associated with this service.</span></span>  
  
### <a name="usernameauthentication"></a><span data-ttu-id="81963-129">UserNameAuthentication</span><span class="sxs-lookup"><span data-stu-id="81963-129">UserNameAuthentication</span></span>  
 <span data-ttu-id="81963-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81963-130">Data type: string</span></span>  
  
 <span data-ttu-id="81963-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81963-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81963-132">Ustawienia nazwy użytkownika i hasła dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="81963-132">The username/password settings for this service.</span></span>  
  
### <a name="windowsauthentication"></a><span data-ttu-id="81963-133">WindowsAuthentication</span><span class="sxs-lookup"><span data-stu-id="81963-133">WindowsAuthentication</span></span>  
 <span data-ttu-id="81963-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="81963-134">Data type: string</span></span>  
  
 <span data-ttu-id="81963-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="81963-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81963-136">Ustawienia uwierzytelniania Windows dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="81963-136">The Windows authentication settings for this service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81963-137">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81963-137">Requirements</span></span>  
  
|<span data-ttu-id="81963-138">MOF</span><span class="sxs-lookup"><span data-stu-id="81963-138">MOF</span></span>|<span data-ttu-id="81963-139">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="81963-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="81963-140">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="81963-140">Namespace</span></span>|<span data-ttu-id="81963-141">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="81963-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81963-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81963-142">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceCredentials>
