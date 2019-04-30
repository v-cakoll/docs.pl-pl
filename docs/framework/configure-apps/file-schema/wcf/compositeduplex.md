---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: 1e5ecc2b937aa0cdb159a6cbd1222fe6d4af79fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704183"
---
# <a name="compositeduplex"></a><span data-ttu-id="b5366-101">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="b5366-101">\<compositeDuplex></span></span>
<span data-ttu-id="b5366-102">Definiuje element powiązania, który jest używany, gdy klient musi ujawniać punkt końcowy usługi by wysłać wiadomości do klienta.</span><span class="sxs-lookup"><span data-stu-id="b5366-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="b5366-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="b5366-103">\<system.serviceModel></span></span>  
<span data-ttu-id="b5366-104">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="b5366-104">\<bindings></span></span>  
<span data-ttu-id="b5366-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b5366-105">\<customBinding></span></span>  
<span data-ttu-id="b5366-106">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b5366-106">\<binding></span></span>  
<span data-ttu-id="b5366-107">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="b5366-107">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5366-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5366-108">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5366-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b5366-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b5366-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b5366-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5366-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b5366-111">Attributes</span></span>  
  
|<span data-ttu-id="b5366-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b5366-112">Attribute</span></span>|<span data-ttu-id="b5366-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b5366-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5366-114">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="b5366-114">clientBaseAddress</span></span>|<span data-ttu-id="b5366-115">Identyfikator URI, który ustawia adres kanału zwrotnego w tryb dupleks.</span><span class="sxs-lookup"><span data-stu-id="b5366-115">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="b5366-116">Usługa używa tego adresu, skontaktuj się z pomocą i nawiąż połączenie z klientem.</span><span class="sxs-lookup"><span data-stu-id="b5366-116">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="b5366-117">Jeśli ten atrybut nie jest ustawiony, domyślnego adresu "`full qualified name+default port\TemporaryIndigoAddress\guid`" jest generowany.</span><span class="sxs-lookup"><span data-stu-id="b5366-117">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="b5366-118">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="b5366-118">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5366-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b5366-119">Child Elements</span></span>  
 <span data-ttu-id="b5366-120">Brak</span><span class="sxs-lookup"><span data-stu-id="b5366-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5366-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b5366-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b5366-122">Element</span><span class="sxs-lookup"><span data-stu-id="b5366-122">Element</span></span>|<span data-ttu-id="b5366-123">Opis</span><span class="sxs-lookup"><span data-stu-id="b5366-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5366-124">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="b5366-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b5366-125">Definiuje wszystkie funkcje powiązania niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b5366-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5366-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5366-126">Remarks</span></span>  
 <span data-ttu-id="b5366-127">Ten element konfiguracji jest używany z transportów, które nie zezwalają na komunikację dwukierunkowego natywnie, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="b5366-127">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="b5366-128">TCP, z drugiej strony, natywnie umożliwia dwukierunkowe komunikacji i nie wymaga użycia tego elementu powiązania usługi można wysłać wiadomości zwrotnie do klienta.</span><span class="sxs-lookup"><span data-stu-id="b5366-128">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="b5366-129">Klient musi ujawniać adres korespondencyjny upewnić się, skontaktuj się z pomocą i nawiązania połączenia.</span><span class="sxs-lookup"><span data-stu-id="b5366-129">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="b5366-130">Ten adres klienta są dostarczane przez `clientBaseAddress` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b5366-130">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="b5366-131">Należy pamiętać, że usługi Windows Communication Foundation (WCF) automatycznie generuje ClientBaseAddress Jeśli jeden nie jest jawnie ustawiona przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b5366-131">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5366-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="b5366-132">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="b5366-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5366-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b5366-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b5366-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b5366-135">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b5366-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b5366-136">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b5366-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b5366-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b5366-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
