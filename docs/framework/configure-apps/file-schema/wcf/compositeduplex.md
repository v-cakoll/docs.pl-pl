---
title: '&lt;compositeDuplex&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f9f82d4b6ac69e0edc0a2ad2cddfd89ee6ac72db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompositeduplexgt"></a><span data-ttu-id="4a44a-102">&lt;compositeDuplex&gt;</span><span class="sxs-lookup"><span data-stu-id="4a44a-102">&lt;compositeDuplex&gt;</span></span>
<span data-ttu-id="4a44a-103">Definiuje element powiązania, który jest używany, gdy klient musi ujawniać punkt końcowy usługi by wysłać wiadomości do klienta.</span><span class="sxs-lookup"><span data-stu-id="4a44a-103">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="4a44a-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="4a44a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="4a44a-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="4a44a-105">\<bindings></span></span>  
<span data-ttu-id="4a44a-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4a44a-106">\<customBinding></span></span>  
<span data-ttu-id="4a44a-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4a44a-107">\<binding></span></span>  
<span data-ttu-id="4a44a-108">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="4a44a-108">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a44a-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a44a-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a44a-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4a44a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4a44a-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4a44a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a44a-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4a44a-112">Attributes</span></span>  
  
|<span data-ttu-id="4a44a-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4a44a-113">Attribute</span></span>|<span data-ttu-id="4a44a-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4a44a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4a44a-115">ClientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="4a44a-115">clientBaseAddress</span></span>|<span data-ttu-id="4a44a-116">Identyfikator URI, który ustawia adres kanału powrotnego w trybie duplex.</span><span class="sxs-lookup"><span data-stu-id="4a44a-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="4a44a-117">Usługa używa ten adres, aby upewnić się, skontaktuj się z pomocą i nawiązania połączenia z klientem.</span><span class="sxs-lookup"><span data-stu-id="4a44a-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="4a44a-118">Jeśli ten atrybut nie jest ustawiona, domyślny adres "`full qualified name+default port\TemporaryIndigoAddress\guid`" jest generowany.</span><span class="sxs-lookup"><span data-stu-id="4a44a-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="4a44a-119">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="4a44a-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a44a-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4a44a-120">Child Elements</span></span>  
 <span data-ttu-id="4a44a-121">Brak</span><span class="sxs-lookup"><span data-stu-id="4a44a-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a44a-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4a44a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4a44a-123">Element</span><span class="sxs-lookup"><span data-stu-id="4a44a-123">Element</span></span>|<span data-ttu-id="4a44a-124">Opis</span><span class="sxs-lookup"><span data-stu-id="4a44a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a44a-125">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4a44a-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="4a44a-126">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="4a44a-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a44a-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a44a-127">Remarks</span></span>  
 <span data-ttu-id="4a44a-128">Ten element konfiguracji jest używany z transportu, które nie zezwalają na komunikacji dupleksowej natywnie, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="4a44a-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="4a44a-129">TCP, natomiast natywnie umożliwia komunikacji dupleksowej i nie wymaga użycia tego elementu powiązania dla usługi wysłać wiadomości zwrotnie do klienta.</span><span class="sxs-lookup"><span data-stu-id="4a44a-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="4a44a-130">Klient musi ujawniać adres usługi upewnić się, skontaktuj się z pomocą i nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="4a44a-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="4a44a-131">Ten adres klienta jest zapewniana przez `clientBaseAddress` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4a44a-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="4a44a-132">Należy pamiętać, że Windows Communication Foundation (WCF) auto generuje ClientBaseAddress Jeśli jeden nie jest jawnie ustawiona przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4a44a-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a44a-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a44a-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="4a44a-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a44a-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="4a44a-135">Powiązania</span><span class="sxs-lookup"><span data-stu-id="4a44a-135">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4a44a-136">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="4a44a-136">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="4a44a-137">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="4a44a-137">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="4a44a-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="4a44a-138">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
