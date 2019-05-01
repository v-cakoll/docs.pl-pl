---
title: <useRequestHeadersForMetadataAddress>
ms.date: 03/30/2017
ms.assetid: 679f0eae-f353-44d1-b42d-a9e247509774
ms.openlocfilehash: 969461d0e5bdc9f8c49b7a019a6000af5af77eec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788729"
---
# <a name="userequestheadersformetadataaddress"></a><span data-ttu-id="25053-101">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="25053-101">\<useRequestHeadersForMetadataAddress></span></span>
<span data-ttu-id="25053-102">Umożliwia pobieranie informacji o adresie metadanych z nagłówków żądań wiadomości.</span><span class="sxs-lookup"><span data-stu-id="25053-102">Enables the retrieval of metadata address information from the request message headers.</span></span>  
  
<span data-ttu-id="25053-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="25053-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="25053-104">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="25053-104">\<behaviors></span></span>  
<span data-ttu-id="25053-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="25053-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="25053-106">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="25053-106">\<behavior></span></span>  
<span data-ttu-id="25053-107">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="25053-107">\<useRequestHeadersForMetadataAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25053-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="25053-108">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http"
         port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25053-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="25053-109">Attributes and Elements</span></span>  
 <span data-ttu-id="25053-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="25053-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25053-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="25053-111">Attributes</span></span>  
 <span data-ttu-id="25053-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="25053-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="25053-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="25053-113">Child Elements</span></span>  
  
|<span data-ttu-id="25053-114">Element</span><span class="sxs-lookup"><span data-stu-id="25053-114">Element</span></span>|<span data-ttu-id="25053-115">Opis</span><span class="sxs-lookup"><span data-stu-id="25053-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25053-116">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="25053-116">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="25053-117">Kolekcja portów domyślnych Wyświetla domyślne punktów końcowe komunikacji, które nasłuchuje aplikacja kliencka.</span><span class="sxs-lookup"><span data-stu-id="25053-117">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25053-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="25053-118">Parent Elements</span></span>  
  
|<span data-ttu-id="25053-119">Element</span><span class="sxs-lookup"><span data-stu-id="25053-119">Element</span></span>|<span data-ttu-id="25053-120">Opis</span><span class="sxs-lookup"><span data-stu-id="25053-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25053-121">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="25053-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="25053-122">Określa zachowanie elementu.</span><span class="sxs-lookup"><span data-stu-id="25053-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25053-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25053-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseRequestHeadersForMetadataAddressElement>
