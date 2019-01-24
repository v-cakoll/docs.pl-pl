---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: d6f0e4741aa10bff450a29cfd7a9e63e226c6495
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498885"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="41833-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="41833-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="41833-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="41833-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41833-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41833-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="41833-105">Metody</span><span class="sxs-lookup"><span data-stu-id="41833-105">Methods</span></span>  
 <span data-ttu-id="41833-106">Klasa ServiceDebugBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="41833-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="41833-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="41833-107">Properties</span></span>  
 <span data-ttu-id="41833-108">Klasa ServiceDebugBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="41833-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="41833-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="41833-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="41833-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="41833-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="41833-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="41833-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="41833-112">Określa, czy usługi jego WSDL pod adresem w wartości clientauthtrustmode `HttpGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="41833-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="41833-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="41833-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="41833-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="41833-114">Data type: string</span></span>  
  
 <span data-ttu-id="41833-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="41833-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="41833-116">Ustawia lokalizację, jaką usługa WSDL jest publikowany dla pobierania za pomocą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="41833-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="41833-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="41833-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="41833-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="41833-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="41833-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="41833-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="41833-120">Określa, czy usługa jego WSDL za pośrednictwem protokołu HTTPS z adresem w wartości clientauthtrustmode `HttpsGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="41833-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="41833-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="41833-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="41833-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="41833-122">Data type: string</span></span>  
  
 <span data-ttu-id="41833-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="41833-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="41833-124">Ustawia lokalizację, jaką usługa WSDL jest publikowany do pobrania przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="41833-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="41833-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="41833-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="41833-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="41833-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="41833-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="41833-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="41833-128">Określa, czy chcesz uwzględnić informacje o zarządzanym wyjątku w szczegółowych informacji o błędach SOAP zwracanych do klientów na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="41833-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41833-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41833-129">Requirements</span></span>  
  
|<span data-ttu-id="41833-130">MOF</span><span class="sxs-lookup"><span data-stu-id="41833-130">MOF</span></span>|<span data-ttu-id="41833-131">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="41833-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="41833-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="41833-132">Namespace</span></span>|<span data-ttu-id="41833-133">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="41833-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41833-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41833-134">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>
