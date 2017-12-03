---
title: ClientCredentials
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55f7ef12f67bd719f72f158a1fca6f120b4f448a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="clientcredentials"></a><span data-ttu-id="bf770-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="bf770-102">ClientCredentials</span></span>
<span data-ttu-id="bf770-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="bf770-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf770-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf770-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="bf770-105">Metody</span><span class="sxs-lookup"><span data-stu-id="bf770-105">Methods</span></span>  
 <span data-ttu-id="bf770-106">Klasa ClientCredentials nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="bf770-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bf770-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="bf770-107">Properties</span></span>  
 <span data-ttu-id="bf770-108">Klasa ClientCredentials ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="bf770-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="bf770-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="bf770-109">ClientCertificate</span></span>  
 <span data-ttu-id="bf770-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="bf770-110">Data type: string</span></span>  
  
 <span data-ttu-id="bf770-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="bf770-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf770-112">Certyfikat X.509 klient używa do uwierzytelnienia w usłudze.</span><span class="sxs-lookup"><span data-stu-id="bf770-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="bf770-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="bf770-113">HttpDigest</span></span>  
 <span data-ttu-id="bf770-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="bf770-114">Data type: string</span></span>  
  
 <span data-ttu-id="bf770-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="bf770-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf770-116">Bieżące poświadczenie Http Digest.</span><span class="sxs-lookup"><span data-stu-id="bf770-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="bf770-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="bf770-117">IssuedToken</span></span>  
 <span data-ttu-id="bf770-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="bf770-118">Data type: string</span></span>  
  
 <span data-ttu-id="bf770-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="bf770-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf770-120">Adres punktu końcowego i powiązanie używane do kontaktu z usługą tokenu zabezpieczeń lokalnych.</span><span class="sxs-lookup"><span data-stu-id="bf770-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="bf770-121">elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="bf770-121">Peer</span></span>  
 <span data-ttu-id="bf770-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="bf770-122">Data type: string</span></span>  
  
 <span data-ttu-id="bf770-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="bf770-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf770-124">Poświadczenia używane przez węzeł elementu równorzędnego do samodzielnego uwierzytelnienia w innych węzłach w sieci.</span><span class="sxs-lookup"><span data-stu-id="bf770-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="bf770-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="bf770-125">ServiceCertificate</span></span>  
 <span data-ttu-id="bf770-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="bf770-126">Data type: string</span></span>  
  
 <span data-ttu-id="bf770-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="bf770-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf770-128">Certyfikat X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="bf770-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="bf770-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="bf770-129">SupportInteractive</span></span>  
 <span data-ttu-id="bf770-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="bf770-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="bf770-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="bf770-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf770-132">Wartość logiczna określająca, czy poświadczenie obsługuje interaktywną negocjację.</span><span class="sxs-lookup"><span data-stu-id="bf770-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="bf770-133">UserName</span><span class="sxs-lookup"><span data-stu-id="bf770-133">UserName</span></span>  
 <span data-ttu-id="bf770-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="bf770-134">Data type: string</span></span>  
  
 <span data-ttu-id="bf770-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="bf770-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf770-136">Nazwa użytkownika i hasło, którego klient używa do samodzielnego uwierzytelnienia usługi.</span><span class="sxs-lookup"><span data-stu-id="bf770-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="bf770-137">Windows</span><span class="sxs-lookup"><span data-stu-id="bf770-137">Windows</span></span>  
 <span data-ttu-id="bf770-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="bf770-138">Data type: string</span></span>  
  
 <span data-ttu-id="bf770-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="bf770-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf770-140">Poświadczenia systemu windows używa klienta do samodzielnego uwierzytelnienia usługi.</span><span class="sxs-lookup"><span data-stu-id="bf770-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf770-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf770-141">Requirements</span></span>  
  
|<span data-ttu-id="bf770-142">MOF</span><span class="sxs-lookup"><span data-stu-id="bf770-142">MOF</span></span>|<span data-ttu-id="bf770-143">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="bf770-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bf770-144">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="bf770-144">Namespace</span></span>|<span data-ttu-id="bf770-145">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bf770-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf770-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf770-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
