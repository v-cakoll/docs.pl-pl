---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 76c4992c5364ed9800e58d120c099aceedb2799c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485684"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="527fc-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="527fc-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="527fc-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="527fc-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="527fc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="527fc-104">Syntax</span></span>  
  
```  
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="527fc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="527fc-105">Methods</span></span>  
 <span data-ttu-id="527fc-106">Klasa ServiceDebugBehavior nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="527fc-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="527fc-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="527fc-107">Properties</span></span>  
 <span data-ttu-id="527fc-108">Klasa ServiceDebugBehavior ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="527fc-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="527fc-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="527fc-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="527fc-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="527fc-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="527fc-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="527fc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="527fc-112">Określa, czy opis WSDL pod adresem określanym przez usługę `HttpGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="527fc-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="527fc-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="527fc-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="527fc-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="527fc-114">Data type: string</span></span>  
  
 <span data-ttu-id="527fc-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="527fc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="527fc-116">Określa położenie, w którym publikowany jest opis WSDL usługi, dla pobierania za pomocą protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="527fc-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="527fc-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="527fc-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="527fc-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="527fc-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="527fc-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="527fc-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="527fc-120">Określa, czy opis WSDL usługi za pośrednictwem protokołu HTTPS pod adresem określanym przez `HttpsGetUrl` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="527fc-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="527fc-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="527fc-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="527fc-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="527fc-122">Data type: string</span></span>  
  
 <span data-ttu-id="527fc-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="527fc-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="527fc-124">Określa położenie, w którym publikowany jest opis WSDL usługi, dla pobierania za pomocą protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="527fc-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="527fc-125">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="527fc-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="527fc-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="527fc-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="527fc-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="527fc-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="527fc-128">Określa, czy dołączać informacje o zarządzanym wyjątku w informacjach szczegółowych o błędach SOAP zwracanych do klientów na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="527fc-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="527fc-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="527fc-129">Requirements</span></span>  
  
|<span data-ttu-id="527fc-130">MOF</span><span class="sxs-lookup"><span data-stu-id="527fc-130">MOF</span></span>|<span data-ttu-id="527fc-131">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="527fc-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="527fc-132">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="527fc-132">Namespace</span></span>|<span data-ttu-id="527fc-133">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="527fc-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="527fc-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="527fc-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>
