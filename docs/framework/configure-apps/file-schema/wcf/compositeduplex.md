---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: f8615637a0fa6d0fff594ef1970711ac408f02f3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264508"
---
# <a name="compositeduplex"></a><span data-ttu-id="c363f-101">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="c363f-101">\<compositeDuplex></span></span>
<span data-ttu-id="c363f-102">Definiuje element powiązania, który jest używany, gdy klient musi ujawniać punkt końcowy usługi by wysłać wiadomości do klienta.</span><span class="sxs-lookup"><span data-stu-id="c363f-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="c363f-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c363f-103">\<system.serviceModel></span></span>  
<span data-ttu-id="c363f-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="c363f-104">\<bindings></span></span>  
<span data-ttu-id="c363f-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c363f-105">\<customBinding></span></span>  
<span data-ttu-id="c363f-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c363f-106">\<binding></span></span>  
<span data-ttu-id="c363f-107">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="c363f-107">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c363f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c363f-108">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c363f-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c363f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c363f-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c363f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c363f-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c363f-111">Attributes</span></span>  
  
|<span data-ttu-id="c363f-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c363f-112">Attribute</span></span>|<span data-ttu-id="c363f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c363f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c363f-114">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="c363f-114">clientBaseAddress</span></span>|<span data-ttu-id="c363f-115">Identyfikator URI, który ustawia adres kanału zwrotnego w tryb dupleks.</span><span class="sxs-lookup"><span data-stu-id="c363f-115">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="c363f-116">Usługa używa tego adresu, skontaktuj się z pomocą i nawiąż połączenie z klientem.</span><span class="sxs-lookup"><span data-stu-id="c363f-116">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="c363f-117">Jeśli ten atrybut nie jest ustawiony, domyślnego adresu "`full qualified name+default port\TemporaryIndigoAddress\guid`" jest generowany.</span><span class="sxs-lookup"><span data-stu-id="c363f-117">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="c363f-118">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="c363f-118">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c363f-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c363f-119">Child Elements</span></span>  
 <span data-ttu-id="c363f-120">Brak</span><span class="sxs-lookup"><span data-stu-id="c363f-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c363f-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c363f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c363f-122">Element</span><span class="sxs-lookup"><span data-stu-id="c363f-122">Element</span></span>|<span data-ttu-id="c363f-123">Opis</span><span class="sxs-lookup"><span data-stu-id="c363f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c363f-124">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="c363f-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c363f-125">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c363f-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c363f-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c363f-126">Remarks</span></span>  
 <span data-ttu-id="c363f-127">Ten element konfiguracji jest używany z transportów, które nie zezwalają na komunikację dwukierunkowego natywnie, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="c363f-127">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="c363f-128">TCP, z drugiej strony, natywnie umożliwia dwukierunkowe komunikacji i nie wymaga użycia tego elementu powiązania usługi można wysłać wiadomości zwrotnie do klienta.</span><span class="sxs-lookup"><span data-stu-id="c363f-128">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="c363f-129">Klient musi ujawniać adres korespondencyjny upewnić się, skontaktuj się z pomocą i nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="c363f-129">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="c363f-130">Ten adres klienta są dostarczane przez `clientBaseAddress` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c363f-130">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="c363f-131">Należy pamiętać, że usługi Windows Communication Foundation (WCF) automatycznie generuje ClientBaseAddress Jeśli jeden nie jest jawnie ustawiona przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c363f-131">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c363f-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="c363f-132">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="c363f-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c363f-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c363f-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c363f-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="c363f-135">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="c363f-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c363f-136">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="c363f-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="c363f-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="c363f-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
