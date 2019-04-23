---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1d99af064205447c2f11f6f19258551c1e88d386
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976140"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="91a3e-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="91a3e-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="91a3e-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="91a3e-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91a3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91a3e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="91a3e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="91a3e-105">Methods</span></span>  
 <span data-ttu-id="91a3e-106">Klasa elementu ServiceMetadataBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="91a3e-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="91a3e-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="91a3e-107">Properties</span></span>  
 <span data-ttu-id="91a3e-108">Klasa elementu ServiceMetadataBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="91a3e-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="91a3e-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="91a3e-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="91a3e-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="91a3e-110">Data type: string</span></span>  
  
 <span data-ttu-id="91a3e-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="91a3e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="91a3e-112">Ustawia lokalizację, do której usługa przekierowuje żądania metadanych.</span><span class="sxs-lookup"><span data-stu-id="91a3e-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="91a3e-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="91a3e-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="91a3e-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="91a3e-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="91a3e-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="91a3e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="91a3e-116">Określa, czy usługi jego WSDL pod adresem w wartości clientauthtrustmode `HttpGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="91a3e-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="91a3e-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="91a3e-117">HttpGetUrl</span></span>  
 <span data-ttu-id="91a3e-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="91a3e-118">Data type: string</span></span>  
  
 <span data-ttu-id="91a3e-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="91a3e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="91a3e-120">Ustawia lokalizację, jaką usługa WSDL jest publikowany dla pobierania za pomocą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="91a3e-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="91a3e-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="91a3e-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="91a3e-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="91a3e-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="91a3e-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="91a3e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="91a3e-124">Określa, czy usługa jego WSDL za pośrednictwem protokołu HTTPS z adresem w wartości clientauthtrustmode `HttpsGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="91a3e-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="91a3e-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="91a3e-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="91a3e-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="91a3e-126">Data type: string</span></span>  
  
 <span data-ttu-id="91a3e-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="91a3e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="91a3e-128">Ustawia lokalizację, jaką usługa WSDL jest publikowany do pobrania przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="91a3e-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91a3e-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91a3e-129">Requirements</span></span>  
  
|<span data-ttu-id="91a3e-130">MOF</span><span class="sxs-lookup"><span data-stu-id="91a3e-130">MOF</span></span>|<span data-ttu-id="91a3e-131">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="91a3e-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="91a3e-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="91a3e-132">Namespace</span></span>|<span data-ttu-id="91a3e-133">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="91a3e-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91a3e-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91a3e-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
