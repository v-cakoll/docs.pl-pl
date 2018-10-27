---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 68b2350f257bc95d8e17f4b9049d67c7f67becae
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452865"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="29a4e-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="29a4e-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="29a4e-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="29a4e-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29a4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29a4e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="29a4e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="29a4e-105">Methods</span></span>  
 <span data-ttu-id="29a4e-106">Klasa ServiceDebugBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="29a4e-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="29a4e-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="29a4e-107">Properties</span></span>  
 <span data-ttu-id="29a4e-108">Klasa ServiceDebugBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="29a4e-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="29a4e-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="29a4e-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="29a4e-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="29a4e-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="29a4e-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="29a4e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29a4e-112">Określa, czy usługi jego WSDL pod adresem w wartości clientauthtrustmode `HttpGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="29a4e-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="29a4e-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="29a4e-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="29a4e-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="29a4e-114">Data type: string</span></span>  
  
 <span data-ttu-id="29a4e-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="29a4e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29a4e-116">Ustawia lokalizację, jaką usługa WSDL jest publikowany dla pobierania za pomocą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="29a4e-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="29a4e-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="29a4e-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="29a4e-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="29a4e-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="29a4e-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="29a4e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29a4e-120">Określa, czy usługa jego WSDL za pośrednictwem protokołu HTTPS z adresem w wartości clientauthtrustmode `HttpsGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="29a4e-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="29a4e-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="29a4e-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="29a4e-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="29a4e-122">Data type: string</span></span>  
  
 <span data-ttu-id="29a4e-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="29a4e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29a4e-124">Ustawia lokalizację, jaką usługa WSDL jest publikowany do pobrania przy użyciu protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="29a4e-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="29a4e-125">Parametr IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="29a4e-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="29a4e-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="29a4e-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="29a4e-127">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="29a4e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29a4e-128">Określa, czy chcesz uwzględnić informacje o zarządzanym wyjątku w szczegółowych informacji o błędach SOAP zwracanych do klientów na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="29a4e-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29a4e-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29a4e-129">Requirements</span></span>  
  
|<span data-ttu-id="29a4e-130">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="29a4e-130">MOF</span></span>|<span data-ttu-id="29a4e-131">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="29a4e-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="29a4e-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="29a4e-132">Namespace</span></span>|<span data-ttu-id="29a4e-133">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="29a4e-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29a4e-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29a4e-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
