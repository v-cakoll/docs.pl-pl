---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 76e28b18cd595a4a18f573dfe9539b646196c944
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720345"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="8f170-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="8f170-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="8f170-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="8f170-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f170-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f170-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="8f170-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8f170-105">Methods</span></span>  
 <span data-ttu-id="8f170-106">Klasa elementu ServiceMetadataBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="8f170-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8f170-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="8f170-107">Properties</span></span>  
 <span data-ttu-id="8f170-108">Klasa elementu ServiceMetadataBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="8f170-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="8f170-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="8f170-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="8f170-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="8f170-110">Data type: string</span></span>  
  
 <span data-ttu-id="8f170-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="8f170-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f170-112">Ustawia lokalizację, do której usługa przekierowuje żądania metadanych.</span><span class="sxs-lookup"><span data-stu-id="8f170-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="8f170-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="8f170-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="8f170-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="8f170-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="8f170-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="8f170-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f170-116">Określa, czy usługi jego WSDL pod adresem w wartości clientauthtrustmode `HttpGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8f170-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="8f170-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="8f170-117">HttpGetUrl</span></span>  
 <span data-ttu-id="8f170-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="8f170-118">Data type: string</span></span>  
  
 <span data-ttu-id="8f170-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="8f170-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f170-120">Ustawia lokalizację, jaką usługa WSDL jest publikowany dla pobierania za pomocą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="8f170-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="8f170-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="8f170-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="8f170-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="8f170-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="8f170-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="8f170-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f170-124">Określa, czy usługa jego WSDL za pośrednictwem protokołu HTTPS z adresem w wartości clientauthtrustmode `HttpsGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8f170-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="8f170-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="8f170-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="8f170-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="8f170-126">Data type: string</span></span>  
  
 <span data-ttu-id="8f170-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="8f170-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8f170-128">Ustawia lokalizację, jaką usługa WSDL jest publikowany do pobrania przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8f170-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f170-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f170-129">Requirements</span></span>  
  
|<span data-ttu-id="8f170-130">MOF</span><span class="sxs-lookup"><span data-stu-id="8f170-130">MOF</span></span>|<span data-ttu-id="8f170-131">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8f170-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8f170-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="8f170-132">Namespace</span></span>|<span data-ttu-id="8f170-133">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8f170-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f170-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f170-134">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
