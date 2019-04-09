---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 2e38eb2c2d42ffc5436562b254a42215ccabbab2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090917"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="9a627-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="9a627-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="9a627-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="9a627-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a627-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a627-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="9a627-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9a627-105">Methods</span></span>  
 <span data-ttu-id="9a627-106">Klasa ServiceDebugBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="9a627-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9a627-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9a627-107">Properties</span></span>  
 <span data-ttu-id="9a627-108">Klasa ServiceDebugBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="9a627-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="9a627-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="9a627-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="9a627-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="9a627-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="9a627-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9a627-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a627-112">Określa, czy usługi jego WSDL pod adresem w wartości clientauthtrustmode `HttpGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9a627-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="9a627-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="9a627-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="9a627-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9a627-114">Data type: string</span></span>  
  
 <span data-ttu-id="9a627-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9a627-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a627-116">Ustawia lokalizację, jaką usługa WSDL jest publikowany dla pobierania za pomocą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="9a627-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="9a627-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="9a627-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="9a627-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="9a627-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="9a627-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9a627-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a627-120">Określa, czy usługa jego WSDL za pośrednictwem protokołu HTTPS z adresem w wartości clientauthtrustmode `HttpsGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9a627-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="9a627-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="9a627-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="9a627-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9a627-122">Data type: string</span></span>  
  
 <span data-ttu-id="9a627-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9a627-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a627-124">Ustawia lokalizację, jaką usługa WSDL jest publikowany do pobrania przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9a627-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="9a627-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="9a627-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="9a627-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="9a627-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="9a627-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9a627-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a627-128">Określa, czy chcesz uwzględnić informacje o zarządzanym wyjątku w szczegółowych informacji o błędach SOAP zwracanych do klientów na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="9a627-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a627-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a627-129">Requirements</span></span>  
  
|<span data-ttu-id="9a627-130">MOF</span><span class="sxs-lookup"><span data-stu-id="9a627-130">MOF</span></span>|<span data-ttu-id="9a627-131">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9a627-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9a627-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="9a627-132">Namespace</span></span>|<span data-ttu-id="9a627-133">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9a627-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a627-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a627-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
