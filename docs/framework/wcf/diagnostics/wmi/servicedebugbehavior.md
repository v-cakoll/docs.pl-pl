---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 2e38eb2c2d42ffc5436562b254a42215ccabbab2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768660"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="e72ab-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="e72ab-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="e72ab-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="e72ab-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e72ab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e72ab-104">Syntax</span></span>  
  
```csharp
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e72ab-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e72ab-105">Methods</span></span>  
 <span data-ttu-id="e72ab-106">Klasa ServiceDebugBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="e72ab-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e72ab-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e72ab-107">Properties</span></span>  
 <span data-ttu-id="e72ab-108">Klasa ServiceDebugBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="e72ab-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="e72ab-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="e72ab-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="e72ab-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="e72ab-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="e72ab-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e72ab-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e72ab-112">Określa, czy usługi jego WSDL pod adresem w wartości clientauthtrustmode `HttpGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e72ab-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="e72ab-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="e72ab-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="e72ab-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="e72ab-114">Data type: string</span></span>  
  
 <span data-ttu-id="e72ab-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e72ab-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e72ab-116">Ustawia lokalizację, jaką usługa WSDL jest publikowany dla pobierania za pomocą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="e72ab-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="e72ab-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="e72ab-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="e72ab-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="e72ab-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="e72ab-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e72ab-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e72ab-120">Określa, czy usługa jego WSDL za pośrednictwem protokołu HTTPS z adresem w wartości clientauthtrustmode `HttpsGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e72ab-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="e72ab-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="e72ab-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="e72ab-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="e72ab-122">Data type: string</span></span>  
  
 <span data-ttu-id="e72ab-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e72ab-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e72ab-124">Ustawia lokalizację, jaką usługa WSDL jest publikowany do pobrania przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e72ab-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="e72ab-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="e72ab-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="e72ab-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="e72ab-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="e72ab-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e72ab-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e72ab-128">Określa, czy chcesz uwzględnić informacje o zarządzanym wyjątku w szczegółowych informacji o błędach SOAP zwracanych do klientów na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="e72ab-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e72ab-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e72ab-129">Requirements</span></span>  
  
|<span data-ttu-id="e72ab-130">MOF</span><span class="sxs-lookup"><span data-stu-id="e72ab-130">MOF</span></span>|<span data-ttu-id="e72ab-131">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e72ab-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e72ab-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="e72ab-132">Namespace</span></span>|<span data-ttu-id="e72ab-133">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e72ab-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e72ab-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e72ab-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
