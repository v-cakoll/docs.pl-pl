---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 19a04b6432f1ecc38a3b906b7e677175863134db
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188836"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="26dcc-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="26dcc-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="26dcc-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="26dcc-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26dcc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26dcc-104">Syntax</span></span>  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="26dcc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="26dcc-105">Methods</span></span>  
 <span data-ttu-id="26dcc-106">Klasa elementu ServiceMetadataBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="26dcc-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="26dcc-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="26dcc-107">Properties</span></span>  
 <span data-ttu-id="26dcc-108">Klasa elementu ServiceMetadataBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="26dcc-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="26dcc-109">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="26dcc-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="26dcc-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="26dcc-110">Data type: string</span></span>  
  
 <span data-ttu-id="26dcc-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="26dcc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="26dcc-112">Ustawia lokalizację, do której usługa przekierowuje żądania metadanych.</span><span class="sxs-lookup"><span data-stu-id="26dcc-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="26dcc-113">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="26dcc-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="26dcc-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="26dcc-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="26dcc-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="26dcc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="26dcc-116">Określa, czy usługi jego WSDL pod adresem w wartości clientauthtrustmode `HttpGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="26dcc-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="26dcc-117">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="26dcc-117">HttpGetUrl</span></span>  
 <span data-ttu-id="26dcc-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="26dcc-118">Data type: string</span></span>  
  
 <span data-ttu-id="26dcc-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="26dcc-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="26dcc-120">Ustawia lokalizację, jaką usługa WSDL jest publikowany dla pobierania za pomocą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="26dcc-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="26dcc-121">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="26dcc-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="26dcc-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="26dcc-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="26dcc-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="26dcc-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="26dcc-124">Określa, czy usługa jego WSDL za pośrednictwem protokołu HTTPS z adresem w wartości clientauthtrustmode `HttpsGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="26dcc-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="26dcc-125">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="26dcc-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="26dcc-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="26dcc-126">Data type: string</span></span>  
  
 <span data-ttu-id="26dcc-127">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="26dcc-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="26dcc-128">Ustawia lokalizację, jaką usługa WSDL jest publikowany do pobrania przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="26dcc-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26dcc-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26dcc-129">Requirements</span></span>  
  
|<span data-ttu-id="26dcc-130">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="26dcc-130">MOF</span></span>|<span data-ttu-id="26dcc-131">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="26dcc-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="26dcc-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="26dcc-132">Namespace</span></span>|<span data-ttu-id="26dcc-133">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="26dcc-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26dcc-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26dcc-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
