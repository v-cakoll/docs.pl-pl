---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: aa852ff82c44a3b5009dbc70e1067face44cbbe9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486379"
---
# <a name="clientcredentials"></a><span data-ttu-id="e327f-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="e327f-102">ClientCredentials</span></span>
<span data-ttu-id="e327f-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="e327f-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e327f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e327f-104">Syntax</span></span>  
  
```  
class ClientCredentials : Behavior  
{  
  string ClientCertificate;  
  string HttpDigest;  
  string IssuedToken;  
  string Peer;  
  string ServiceCertificate;  
  boolean SupportInteractive;  
  string UserName;  
  string Windows;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e327f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e327f-105">Methods</span></span>  
 <span data-ttu-id="e327f-106">Klasa ClientCredentials nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="e327f-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e327f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e327f-107">Properties</span></span>  
 <span data-ttu-id="e327f-108">Klasa ClientCredentials ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="e327f-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="e327f-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="e327f-109">ClientCertificate</span></span>  
 <span data-ttu-id="e327f-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="e327f-110">Data type: string</span></span>  
  
 <span data-ttu-id="e327f-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e327f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e327f-112">Certyfikat X.509 klient używa do uwierzytelnienia w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e327f-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="e327f-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="e327f-113">HttpDigest</span></span>  
 <span data-ttu-id="e327f-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="e327f-114">Data type: string</span></span>  
  
 <span data-ttu-id="e327f-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e327f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e327f-116">Bieżące poświadczenie Http Digest.</span><span class="sxs-lookup"><span data-stu-id="e327f-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="e327f-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="e327f-117">IssuedToken</span></span>  
 <span data-ttu-id="e327f-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="e327f-118">Data type: string</span></span>  
  
 <span data-ttu-id="e327f-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e327f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e327f-120">Adres punktu końcowego i powiązanie używane do kontaktu z usługą tokenu zabezpieczeń lokalnych.</span><span class="sxs-lookup"><span data-stu-id="e327f-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="e327f-121">elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="e327f-121">Peer</span></span>  
 <span data-ttu-id="e327f-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="e327f-122">Data type: string</span></span>  
  
 <span data-ttu-id="e327f-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e327f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e327f-124">Poświadczenia używane przez węzeł elementu równorzędnego do samodzielnego uwierzytelnienia w innych węzłach w sieci.</span><span class="sxs-lookup"><span data-stu-id="e327f-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="e327f-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="e327f-125">ServiceCertificate</span></span>  
 <span data-ttu-id="e327f-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="e327f-126">Data type: string</span></span>  
  
 <span data-ttu-id="e327f-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e327f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e327f-128">Certyfikat X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="e327f-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="e327f-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="e327f-129">SupportInteractive</span></span>  
 <span data-ttu-id="e327f-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="e327f-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="e327f-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e327f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e327f-132">Wartość logiczna określająca, czy poświadczenie obsługuje interaktywną negocjację.</span><span class="sxs-lookup"><span data-stu-id="e327f-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="e327f-133">UserName</span><span class="sxs-lookup"><span data-stu-id="e327f-133">UserName</span></span>  
 <span data-ttu-id="e327f-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="e327f-134">Data type: string</span></span>  
  
 <span data-ttu-id="e327f-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e327f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e327f-136">Nazwa użytkownika i hasło, którego klient używa do samodzielnego uwierzytelnienia usługi.</span><span class="sxs-lookup"><span data-stu-id="e327f-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="e327f-137">Windows</span><span class="sxs-lookup"><span data-stu-id="e327f-137">Windows</span></span>  
 <span data-ttu-id="e327f-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="e327f-138">Data type: string</span></span>  
  
 <span data-ttu-id="e327f-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e327f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e327f-140">Poświadczenia systemu windows używa klienta do samodzielnego uwierzytelnienia usługi.</span><span class="sxs-lookup"><span data-stu-id="e327f-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e327f-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e327f-141">Requirements</span></span>  
  
|<span data-ttu-id="e327f-142">MOF</span><span class="sxs-lookup"><span data-stu-id="e327f-142">MOF</span></span>|<span data-ttu-id="e327f-143">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e327f-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e327f-144">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="e327f-144">Namespace</span></span>|<span data-ttu-id="e327f-145">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e327f-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e327f-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e327f-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
