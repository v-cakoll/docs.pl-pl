---
title: '&lt;compositeDuplex&gt;'
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: 4b84b4f2816dc68b7dcee784d957189728e5a4b2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149054"
---
# <a name="ltcompositeduplexgt"></a><span data-ttu-id="9711e-102">&lt;compositeDuplex&gt;</span><span class="sxs-lookup"><span data-stu-id="9711e-102">&lt;compositeDuplex&gt;</span></span>
<span data-ttu-id="9711e-103">Definiuje element powiązania, który jest używany, gdy klient musi ujawniać punkt końcowy usługi by wysłać wiadomości do klienta.</span><span class="sxs-lookup"><span data-stu-id="9711e-103">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="9711e-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9711e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9711e-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="9711e-105">\<bindings></span></span>  
<span data-ttu-id="9711e-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9711e-106">\<customBinding></span></span>  
<span data-ttu-id="9711e-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="9711e-107">\<binding></span></span>  
<span data-ttu-id="9711e-108">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="9711e-108">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9711e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="9711e-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9711e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9711e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9711e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9711e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9711e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9711e-112">Attributes</span></span>  
  
|<span data-ttu-id="9711e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9711e-113">Attribute</span></span>|<span data-ttu-id="9711e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9711e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9711e-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="9711e-115">clientBaseAddress</span></span>|<span data-ttu-id="9711e-116">Identyfikator URI, który ustawia adres kanału zwrotnego w tryb dupleks.</span><span class="sxs-lookup"><span data-stu-id="9711e-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="9711e-117">Usługa używa tego adresu, skontaktuj się z pomocą i nawiąż połączenie z klientem.</span><span class="sxs-lookup"><span data-stu-id="9711e-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="9711e-118">Jeśli ten atrybut nie jest ustawiony, domyślnego adresu "`full qualified name+default port\TemporaryIndigoAddress\guid`" jest generowany.</span><span class="sxs-lookup"><span data-stu-id="9711e-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="9711e-119">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="9711e-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9711e-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9711e-120">Child Elements</span></span>  
 <span data-ttu-id="9711e-121">Brak</span><span class="sxs-lookup"><span data-stu-id="9711e-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9711e-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9711e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="9711e-123">Element</span><span class="sxs-lookup"><span data-stu-id="9711e-123">Element</span></span>|<span data-ttu-id="9711e-124">Opis</span><span class="sxs-lookup"><span data-stu-id="9711e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9711e-125">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="9711e-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="9711e-126">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="9711e-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9711e-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9711e-127">Remarks</span></span>  
 <span data-ttu-id="9711e-128">Ten element konfiguracji jest używany z transportów, które nie zezwalają na komunikację dwukierunkowego natywnie, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="9711e-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="9711e-129">TCP, z drugiej strony, natywnie umożliwia dwukierunkowe komunikacji i nie wymaga użycia tego elementu powiązania usługi można wysłać wiadomości zwrotnie do klienta.</span><span class="sxs-lookup"><span data-stu-id="9711e-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="9711e-130">Klient musi ujawniać adres korespondencyjny upewnić się, skontaktuj się z pomocą i nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="9711e-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="9711e-131">Ten adres klienta są dostarczane przez `clientBaseAddress` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9711e-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="9711e-132">Należy pamiętać, że usługi Windows Communication Foundation (WCF) automatycznie generuje ClientBaseAddress Jeśli jeden nie jest jawnie ustawiona przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9711e-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9711e-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="9711e-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="9711e-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9711e-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="9711e-135">Powiązania</span><span class="sxs-lookup"><span data-stu-id="9711e-135">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9711e-136">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="9711e-136">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="9711e-137">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="9711e-137">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="9711e-138">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9711e-138">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
