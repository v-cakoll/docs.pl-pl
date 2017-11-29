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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 68a2fa36c8a4fa1fde3ca8d8aaf1898060ea972f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="clientcredentials"></a><span data-ttu-id="d2075-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="d2075-102">ClientCredentials</span></span>
<span data-ttu-id="d2075-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="d2075-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2075-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d2075-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="d2075-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d2075-105">Methods</span></span>  
 <span data-ttu-id="d2075-106">Klasa ClientCredentials nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="d2075-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d2075-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d2075-107">Properties</span></span>  
 <span data-ttu-id="d2075-108">Klasa ClientCredentials ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="d2075-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="d2075-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="d2075-109">ClientCertificate</span></span>  
 <span data-ttu-id="d2075-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d2075-110">Data type: string</span></span>  
  
 <span data-ttu-id="d2075-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d2075-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2075-112">Certyfikat X.509 klient używa do uwierzytelnienia w usłudze.</span><span class="sxs-lookup"><span data-stu-id="d2075-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="d2075-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="d2075-113">HttpDigest</span></span>  
 <span data-ttu-id="d2075-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d2075-114">Data type: string</span></span>  
  
 <span data-ttu-id="d2075-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d2075-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2075-116">Bieżące poświadczenie Http Digest.</span><span class="sxs-lookup"><span data-stu-id="d2075-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="d2075-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="d2075-117">IssuedToken</span></span>  
 <span data-ttu-id="d2075-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d2075-118">Data type: string</span></span>  
  
 <span data-ttu-id="d2075-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d2075-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2075-120">Adres punktu końcowego i powiązanie używane do kontaktu z usługą tokenu zabezpieczeń lokalnych.</span><span class="sxs-lookup"><span data-stu-id="d2075-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="d2075-121">elementów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="d2075-121">Peer</span></span>  
 <span data-ttu-id="d2075-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d2075-122">Data type: string</span></span>  
  
 <span data-ttu-id="d2075-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d2075-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2075-124">Poświadczenia używane przez węzeł elementu równorzędnego do samodzielnego uwierzytelnienia w innych węzłach w sieci.</span><span class="sxs-lookup"><span data-stu-id="d2075-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="d2075-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="d2075-125">ServiceCertificate</span></span>  
 <span data-ttu-id="d2075-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d2075-126">Data type: string</span></span>  
  
 <span data-ttu-id="d2075-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d2075-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2075-128">Certyfikat X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="d2075-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="d2075-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="d2075-129">SupportInteractive</span></span>  
 <span data-ttu-id="d2075-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="d2075-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="d2075-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d2075-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2075-132">Wartość logiczna określająca, czy poświadczenie obsługuje interaktywną negocjację.</span><span class="sxs-lookup"><span data-stu-id="d2075-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="d2075-133">UserName</span><span class="sxs-lookup"><span data-stu-id="d2075-133">UserName</span></span>  
 <span data-ttu-id="d2075-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d2075-134">Data type: string</span></span>  
  
 <span data-ttu-id="d2075-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d2075-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2075-136">Nazwa użytkownika i hasło, którego klient używa do samodzielnego uwierzytelnienia usługi.</span><span class="sxs-lookup"><span data-stu-id="d2075-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="d2075-137">Windows</span><span class="sxs-lookup"><span data-stu-id="d2075-137">Windows</span></span>  
 <span data-ttu-id="d2075-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d2075-138">Data type: string</span></span>  
  
 <span data-ttu-id="d2075-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d2075-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2075-140">Poświadczenia systemu windows używa klienta do samodzielnego uwierzytelnienia usługi.</span><span class="sxs-lookup"><span data-stu-id="d2075-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2075-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d2075-141">Requirements</span></span>  
  
|<span data-ttu-id="d2075-142">MOF</span><span class="sxs-lookup"><span data-stu-id="d2075-142">MOF</span></span>|<span data-ttu-id="d2075-143">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d2075-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d2075-144">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="d2075-144">Namespace</span></span>|<span data-ttu-id="d2075-145">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d2075-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2075-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2075-146">See Also</span></span>  
 <xref:System.ServiceModel.Description.ClientCredentials>
