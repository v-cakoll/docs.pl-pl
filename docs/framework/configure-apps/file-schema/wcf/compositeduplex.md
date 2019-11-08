---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: c3bae4dfee36e9de62c27bbccecd9a31a5b7d459
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736775"
---
# <a name="compositeduplex"></a><span data-ttu-id="b5228-101">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="b5228-101">\<compositeDuplex></span></span>
<span data-ttu-id="b5228-102">Definiuje element powiązania, który jest używany, gdy klient musi uwidocznić punkt końcowy dla usługi w celu wysłania komunikatów z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="b5228-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
<span data-ttu-id="b5228-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b5228-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b5228-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="b5228-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b5228-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="b5228-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b5228-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="b5228-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="b5228-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="b5228-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b5228-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<compositeDuplex >**</span><span class="sxs-lookup"><span data-stu-id="b5228-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5228-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b5228-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b5228-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b5228-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b5228-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b5228-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b5228-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b5228-112">Attributes</span></span>  
  
|<span data-ttu-id="b5228-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b5228-113">Attribute</span></span>|<span data-ttu-id="b5228-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b5228-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b5228-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="b5228-115">clientBaseAddress</span></span>|<span data-ttu-id="b5228-116">Identyfikator URI, który ustawia adres kanału zwrotnego w trybie dupleksu.</span><span class="sxs-lookup"><span data-stu-id="b5228-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="b5228-117">Usługa używa tego adresu do nawiązywania kontaktu i nawiązania połączenia z klientem.</span><span class="sxs-lookup"><span data-stu-id="b5228-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="b5228-118">Jeśli ten atrybut nie jest ustawiony, zostanie wygenerowany domyślny adres "`full qualified name+default port\TemporaryIndigoAddress\guid`".</span><span class="sxs-lookup"><span data-stu-id="b5228-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="b5228-119">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="b5228-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b5228-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b5228-120">Child Elements</span></span>  
 <span data-ttu-id="b5228-121">Brak</span><span class="sxs-lookup"><span data-stu-id="b5228-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b5228-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b5228-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b5228-123">Element</span><span class="sxs-lookup"><span data-stu-id="b5228-123">Element</span></span>|<span data-ttu-id="b5228-124">Opis</span><span class="sxs-lookup"><span data-stu-id="b5228-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b5228-125">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="b5228-125">\<binding></span></span>](bindings.md)|<span data-ttu-id="b5228-126">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="b5228-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5228-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b5228-127">Remarks</span></span>  
 <span data-ttu-id="b5228-128">Ten element konfiguracji jest używany z transportami, które nie zezwalają na natywną komunikację bezstronną, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="b5228-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="b5228-129">Protokół TCP, w przeciwieństwie, umożliwia natywną komunikację bezstronną i nie wymaga użycia tego elementu powiązania dla usługi do wysyłania komunikatów z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="b5228-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="b5228-130">Klient musi uwidocznić adres usługi, aby nawiązać kontakt i nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="b5228-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="b5228-131">Ten adres klienta jest dostarczany przez atrybut `clientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="b5228-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="b5228-132">Należy pamiętać, że Windows Communication Foundation (WCF) automatycznie generuje element ClientBaseAddress, jeśli nie został jawnie ustawiony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b5228-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5228-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="b5228-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="b5228-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5228-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b5228-135">Powiązania</span><span class="sxs-lookup"><span data-stu-id="b5228-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b5228-136">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="b5228-136">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b5228-137">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="b5228-137">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b5228-138">\<niestandardowebinding ></span><span class="sxs-lookup"><span data-stu-id="b5228-138">\<customBinding></span></span>](custombinding.md)
