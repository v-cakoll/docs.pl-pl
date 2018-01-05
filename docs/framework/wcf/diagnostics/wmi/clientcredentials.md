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
ms.workload: dotnet
ms.openlocfilehash: d6fba00dc98f6b5525e1cb9588ed52bc483a665e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="clientcredentials"></a><span data-ttu-id="fe7b5-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="fe7b5-102">ClientCredentials</span></span>
<span data-ttu-id="fe7b5-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="fe7b5-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe7b5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe7b5-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="fe7b5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fe7b5-105">Methods</span></span>  
 <span data-ttu-id="fe7b5-106">Klasa ClientCredentials nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="fe7b5-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fe7b5-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="fe7b5-107">Properties</span></span>  
 <span data-ttu-id="fe7b5-108">Klasa ClientCredentials ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="fe7b5-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="fe7b5-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="fe7b5-109">ClientCertificate</span></span>  
 <span data-ttu-id="fe7b5-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe7b5-110">Data type: string</span></span>  
  
 <span data-ttu-id="fe7b5-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7b5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7b5-112">Certyfikat X.509 klient używa do uwierzytelnienia w usłudze.</span><span class="sxs-lookup"><span data-stu-id="fe7b5-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="fe7b5-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="fe7b5-113">HttpDigest</span></span>  
 <span data-ttu-id="fe7b5-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe7b5-114">Data type: string</span></span>  
  
 <span data-ttu-id="fe7b5-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7b5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7b5-116">Bieżące poświadczenie Http Digest.</span><span class="sxs-lookup"><span data-stu-id="fe7b5-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="fe7b5-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="fe7b5-117">IssuedToken</span></span>  
 <span data-ttu-id="fe7b5-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe7b5-118">Data type: string</span></span>  
  
 <span data-ttu-id="fe7b5-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7b5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7b5-120">Adres punktu końcowego i powiązanie używane do kontaktu z usługą tokenu zabezpieczeń lokalnych.</span><span class="sxs-lookup"><span data-stu-id="fe7b5-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="fe7b5-121">elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="fe7b5-121">Peer</span></span>  
 <span data-ttu-id="fe7b5-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe7b5-122">Data type: string</span></span>  
  
 <span data-ttu-id="fe7b5-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7b5-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7b5-124">Poświadczenia używane przez węzeł elementu równorzędnego do samodzielnego uwierzytelnienia w innych węzłach w sieci.</span><span class="sxs-lookup"><span data-stu-id="fe7b5-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="fe7b5-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="fe7b5-125">ServiceCertificate</span></span>  
 <span data-ttu-id="fe7b5-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe7b5-126">Data type: string</span></span>  
  
 <span data-ttu-id="fe7b5-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7b5-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7b5-128">Certyfikat X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="fe7b5-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="fe7b5-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="fe7b5-129">SupportInteractive</span></span>  
 <span data-ttu-id="fe7b5-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="fe7b5-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="fe7b5-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7b5-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7b5-132">Wartość logiczna określająca, czy poświadczenie obsługuje interaktywną negocjację.</span><span class="sxs-lookup"><span data-stu-id="fe7b5-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="fe7b5-133">UserName</span><span class="sxs-lookup"><span data-stu-id="fe7b5-133">UserName</span></span>  
 <span data-ttu-id="fe7b5-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe7b5-134">Data type: string</span></span>  
  
 <span data-ttu-id="fe7b5-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7b5-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7b5-136">Nazwa użytkownika i hasło, którego klient używa do samodzielnego uwierzytelnienia usługi.</span><span class="sxs-lookup"><span data-stu-id="fe7b5-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="fe7b5-137">Windows</span><span class="sxs-lookup"><span data-stu-id="fe7b5-137">Windows</span></span>  
 <span data-ttu-id="fe7b5-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="fe7b5-138">Data type: string</span></span>  
  
 <span data-ttu-id="fe7b5-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fe7b5-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fe7b5-140">Poświadczenia systemu windows używa klienta do samodzielnego uwierzytelnienia usługi.</span><span class="sxs-lookup"><span data-stu-id="fe7b5-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe7b5-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe7b5-141">Requirements</span></span>  
  
|<span data-ttu-id="fe7b5-142">MOF</span><span class="sxs-lookup"><span data-stu-id="fe7b5-142">MOF</span></span>|<span data-ttu-id="fe7b5-143">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fe7b5-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fe7b5-144">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="fe7b5-144">Namespace</span></span>|<span data-ttu-id="fe7b5-145">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fe7b5-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fe7b5-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe7b5-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
