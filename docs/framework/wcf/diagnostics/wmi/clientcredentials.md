---
title: ClientCredentials
ms.date: 03/30/2017
ms.assetid: 41dffd6b-8f14-4fed-aefb-2a1bb168efb3
ms.openlocfilehash: c3adc675bb6c1e9011459a88fd7dc8e8cf63a880
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963981"
---
# <a name="clientcredentials"></a><span data-ttu-id="ea8be-102">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="ea8be-102">ClientCredentials</span></span>
<span data-ttu-id="ea8be-103">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="ea8be-103">ClientCredentials</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea8be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea8be-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="ea8be-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ea8be-105">Methods</span></span>  
 <span data-ttu-id="ea8be-106">Klasa ClientCredentials nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="ea8be-106">The ClientCredentials class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ea8be-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="ea8be-107">Properties</span></span>  
 <span data-ttu-id="ea8be-108">Klasa ClientCredentials ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="ea8be-108">The ClientCredentials class has the following properties:</span></span>  
  
### <a name="clientcertificate"></a><span data-ttu-id="ea8be-109">ClientCertificate</span><span class="sxs-lookup"><span data-stu-id="ea8be-109">ClientCertificate</span></span>  
 <span data-ttu-id="ea8be-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="ea8be-110">Data type: string</span></span>  
  
 <span data-ttu-id="ea8be-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ea8be-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ea8be-112">Certyfikat X.509, klient używa do uwierzytelnienia w usłudze.</span><span class="sxs-lookup"><span data-stu-id="ea8be-112">The X.509 certificate the client uses to authenticate to the service.</span></span>  
  
### <a name="httpdigest"></a><span data-ttu-id="ea8be-113">HttpDigest</span><span class="sxs-lookup"><span data-stu-id="ea8be-113">HttpDigest</span></span>  
 <span data-ttu-id="ea8be-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="ea8be-114">Data type: string</span></span>  
  
 <span data-ttu-id="ea8be-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ea8be-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ea8be-116">Bieżące poświadczenie Http Digest.</span><span class="sxs-lookup"><span data-stu-id="ea8be-116">The current Http Digest credential.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="ea8be-117">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="ea8be-117">IssuedToken</span></span>  
 <span data-ttu-id="ea8be-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="ea8be-118">Data type: string</span></span>  
  
 <span data-ttu-id="ea8be-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ea8be-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ea8be-120">Adres punktu końcowego i powiązania używanego do kontaktowania się z usługi tokenu zabezpieczeń lokalnych.</span><span class="sxs-lookup"><span data-stu-id="ea8be-120">The endpoint address and binding used to contact the local security token service.</span></span>  
  
### <a name="peer"></a><span data-ttu-id="ea8be-121">Elementu równorzędnego</span><span class="sxs-lookup"><span data-stu-id="ea8be-121">Peer</span></span>  
 <span data-ttu-id="ea8be-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="ea8be-122">Data type: string</span></span>  
  
 <span data-ttu-id="ea8be-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ea8be-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ea8be-124">Poświadczenia używane przez węzeł równorzędny uwierzytelnienie na innych węzłach w sieci.</span><span class="sxs-lookup"><span data-stu-id="ea8be-124">The credentials that the peer node uses to authenticate itself to other nodes in the mesh.</span></span>  
  
### <a name="servicecertificate"></a><span data-ttu-id="ea8be-125">ServiceCertificate</span><span class="sxs-lookup"><span data-stu-id="ea8be-125">ServiceCertificate</span></span>  
 <span data-ttu-id="ea8be-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="ea8be-126">Data type: string</span></span>  
  
 <span data-ttu-id="ea8be-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ea8be-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ea8be-128">Certyfikat X.509 dla usługi.</span><span class="sxs-lookup"><span data-stu-id="ea8be-128">The service's X.509 certificate.</span></span>  
  
### <a name="supportinteractive"></a><span data-ttu-id="ea8be-129">SupportInteractive</span><span class="sxs-lookup"><span data-stu-id="ea8be-129">SupportInteractive</span></span>  
 <span data-ttu-id="ea8be-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="ea8be-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="ea8be-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ea8be-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ea8be-132">Wartość logiczna określająca, czy poświadczenia obsługuje interakcyjne negocjacji.</span><span class="sxs-lookup"><span data-stu-id="ea8be-132">A Boolean value that specifies whether the credential supports interactive negotiation.</span></span>  
  
### <a name="username"></a><span data-ttu-id="ea8be-133">UserName</span><span class="sxs-lookup"><span data-stu-id="ea8be-133">UserName</span></span>  
 <span data-ttu-id="ea8be-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="ea8be-134">Data type: string</span></span>  
  
 <span data-ttu-id="ea8be-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ea8be-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ea8be-136">Nazwa użytkownika i hasło, którego klient używa do samodzielnego uwierzytelnienia usługi.</span><span class="sxs-lookup"><span data-stu-id="ea8be-136">The username and password the client uses to authenticate itself to the service.</span></span>  
  
### <a name="windows"></a><span data-ttu-id="ea8be-137">Windows</span><span class="sxs-lookup"><span data-stu-id="ea8be-137">Windows</span></span>  
 <span data-ttu-id="ea8be-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="ea8be-138">Data type: string</span></span>  
  
 <span data-ttu-id="ea8be-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="ea8be-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ea8be-140">Windows poświadczeń używa klienta do samodzielnego uwierzytelnienia usługi.</span><span class="sxs-lookup"><span data-stu-id="ea8be-140">The windows credentials the client uses to authenticate itself to the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea8be-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea8be-141">Requirements</span></span>  
  
|<span data-ttu-id="ea8be-142">MOF</span><span class="sxs-lookup"><span data-stu-id="ea8be-142">MOF</span></span>|<span data-ttu-id="ea8be-143">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ea8be-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ea8be-144">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="ea8be-144">Namespace</span></span>|<span data-ttu-id="ea8be-145">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ea8be-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea8be-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea8be-146">See also</span></span>

- <xref:System.ServiceModel.Description.ClientCredentials>
