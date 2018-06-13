---
title: '&lt;compositeDuplex&gt;'
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: ce04eb96868da9760412e37d2335d020cc768ac9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748350"
---
# <a name="ltcompositeduplexgt"></a><span data-ttu-id="502db-102">&lt;compositeDuplex&gt;</span><span class="sxs-lookup"><span data-stu-id="502db-102">&lt;compositeDuplex&gt;</span></span>
<span data-ttu-id="502db-103">Definiuje element powiązania, który jest używany, gdy klient musi ujawniać punkt końcowy usługi by wysłać wiadomości do klienta.</span><span class="sxs-lookup"><span data-stu-id="502db-103">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="502db-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="502db-104">\<system.serviceModel></span></span>  
<span data-ttu-id="502db-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="502db-105">\<bindings></span></span>  
<span data-ttu-id="502db-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="502db-106">\<customBinding></span></span>  
<span data-ttu-id="502db-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="502db-107">\<binding></span></span>  
<span data-ttu-id="502db-108">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="502db-108">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="502db-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="502db-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="502db-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="502db-110">Attributes and Elements</span></span>  
 <span data-ttu-id="502db-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="502db-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="502db-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="502db-112">Attributes</span></span>  
  
|<span data-ttu-id="502db-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="502db-113">Attribute</span></span>|<span data-ttu-id="502db-114">Opis</span><span class="sxs-lookup"><span data-stu-id="502db-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="502db-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="502db-115">clientBaseAddress</span></span>|<span data-ttu-id="502db-116">Identyfikator URI, który ustawia adres kanału powrotnego w trybie duplex.</span><span class="sxs-lookup"><span data-stu-id="502db-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="502db-117">Usługa używa ten adres, aby upewnić się, skontaktuj się z pomocą i nawiązania połączenia z klientem.</span><span class="sxs-lookup"><span data-stu-id="502db-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="502db-118">Jeśli ten atrybut nie jest ustawiona, domyślny adres "`full qualified name+default port\TemporaryIndigoAddress\guid`" jest generowany.</span><span class="sxs-lookup"><span data-stu-id="502db-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="502db-119">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="502db-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="502db-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="502db-120">Child Elements</span></span>  
 <span data-ttu-id="502db-121">Brak</span><span class="sxs-lookup"><span data-stu-id="502db-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="502db-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="502db-122">Parent Elements</span></span>  
  
|<span data-ttu-id="502db-123">Element</span><span class="sxs-lookup"><span data-stu-id="502db-123">Element</span></span>|<span data-ttu-id="502db-124">Opis</span><span class="sxs-lookup"><span data-stu-id="502db-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="502db-125">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="502db-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="502db-126">Definiuje wszystkie możliwości powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="502db-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="502db-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="502db-127">Remarks</span></span>  
 <span data-ttu-id="502db-128">Ten element konfiguracji jest używany z transportu, które nie zezwalają na komunikacji dupleksowej natywnie, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="502db-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="502db-129">TCP, natomiast natywnie umożliwia komunikacji dupleksowej i nie wymaga użycia tego elementu powiązania dla usługi wysłać wiadomości zwrotnie do klienta.</span><span class="sxs-lookup"><span data-stu-id="502db-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="502db-130">Klient musi ujawniać adres usługi upewnić się, skontaktuj się z pomocą i nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="502db-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="502db-131">Ten adres klienta jest zapewniana przez `clientBaseAddress` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="502db-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="502db-132">Należy pamiętać, że Windows Communication Foundation (WCF) auto generuje ClientBaseAddress Jeśli jeden nie jest jawnie ustawiona przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="502db-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="502db-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="502db-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="502db-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="502db-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="502db-135">Powiązania</span><span class="sxs-lookup"><span data-stu-id="502db-135">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="502db-136">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="502db-136">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="502db-137">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="502db-137">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="502db-138">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="502db-138">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
