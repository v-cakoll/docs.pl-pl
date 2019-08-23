---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: e79b3e1aeecc52bf41ae759dc15ebf1c8211beb2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926069"
---
# <a name="compositeduplex"></a><span data-ttu-id="3f5c0-101">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="3f5c0-101">\<compositeDuplex></span></span>
<span data-ttu-id="3f5c0-102">Definiuje element powiązania, który jest używany, gdy klient musi uwidocznić punkt końcowy dla usługi w celu wysłania komunikatów z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="3f5c0-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="3f5c0-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3f5c0-103">\<system.serviceModel></span></span>  
<span data-ttu-id="3f5c0-104">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="3f5c0-104">\<bindings></span></span>  
<span data-ttu-id="3f5c0-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3f5c0-105">\<customBinding></span></span>  
<span data-ttu-id="3f5c0-106">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="3f5c0-106">\<binding></span></span>  
<span data-ttu-id="3f5c0-107">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="3f5c0-107">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f5c0-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f5c0-108">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f5c0-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3f5c0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3f5c0-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3f5c0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f5c0-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3f5c0-111">Attributes</span></span>  
  
|<span data-ttu-id="3f5c0-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3f5c0-112">Attribute</span></span>|<span data-ttu-id="3f5c0-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3f5c0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3f5c0-114">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="3f5c0-114">clientBaseAddress</span></span>|<span data-ttu-id="3f5c0-115">Identyfikator URI, który ustawia adres kanału zwrotnego w trybie dupleksu.</span><span class="sxs-lookup"><span data-stu-id="3f5c0-115">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="3f5c0-116">Usługa używa tego adresu do nawiązywania kontaktu i nawiązania połączenia z klientem.</span><span class="sxs-lookup"><span data-stu-id="3f5c0-116">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="3f5c0-117">Jeśli ten atrybut nie jest ustawiony, zostanie wygenerowany domyślny adres`full qualified name+default port\TemporaryIndigoAddress\guid`"".</span><span class="sxs-lookup"><span data-stu-id="3f5c0-117">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="3f5c0-118">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="3f5c0-118">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3f5c0-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3f5c0-119">Child Elements</span></span>  
 <span data-ttu-id="3f5c0-120">Brak</span><span class="sxs-lookup"><span data-stu-id="3f5c0-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3f5c0-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3f5c0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3f5c0-122">Element</span><span class="sxs-lookup"><span data-stu-id="3f5c0-122">Element</span></span>|<span data-ttu-id="3f5c0-123">Opis</span><span class="sxs-lookup"><span data-stu-id="3f5c0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f5c0-124">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="3f5c0-124">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="3f5c0-125">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3f5c0-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f5c0-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f5c0-126">Remarks</span></span>  
 <span data-ttu-id="3f5c0-127">Ten element konfiguracji jest używany z transportami, które nie zezwalają na natywną komunikację bezstronną, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="3f5c0-127">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="3f5c0-128">Protokół TCP, w przeciwieństwie, umożliwia natywną komunikację bezstronną i nie wymaga użycia tego elementu powiązania dla usługi do wysyłania komunikatów z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="3f5c0-128">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="3f5c0-129">Klient musi uwidocznić adres usługi, aby nawiązać kontakt i nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="3f5c0-129">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="3f5c0-130">Ten adres klienta jest dostarczany przez `clientBaseAddress` atrybut.</span><span class="sxs-lookup"><span data-stu-id="3f5c0-130">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="3f5c0-131">Należy pamiętać, że Windows Communication Foundation (WCF) automatycznie generuje element ClientBaseAddress, jeśli nie został jawnie ustawiony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3f5c0-131">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f5c0-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f5c0-132">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="3f5c0-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f5c0-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3f5c0-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="3f5c0-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3f5c0-135">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="3f5c0-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3f5c0-136">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="3f5c0-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3f5c0-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3f5c0-137">\<customBinding></span></span>](custombinding.md)
