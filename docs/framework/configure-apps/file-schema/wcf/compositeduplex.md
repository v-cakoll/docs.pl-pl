---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: a73085320eaf248887422316e1b7787b8654d71d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400490"
---
# <a name="compositeduplex"></a><span data-ttu-id="f9a0e-101">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="f9a0e-101">\<compositeDuplex></span></span>
<span data-ttu-id="f9a0e-102">Definiuje element powiązania, który jest używany, gdy klient musi uwidocznić punkt końcowy dla usługi w celu wysłania komunikatów z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="f9a0e-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
<span data-ttu-id="f9a0e-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f9a0e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f9a0e-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f9a0e-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f9a0e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f9a0e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f9a0e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="f9a0e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="f9a0e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="f9a0e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f9a0e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<compositeDuplex >**</span><span class="sxs-lookup"><span data-stu-id="f9a0e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9a0e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9a0e-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9a0e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f9a0e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f9a0e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f9a0e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9a0e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f9a0e-112">Attributes</span></span>  
  
|<span data-ttu-id="f9a0e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f9a0e-113">Attribute</span></span>|<span data-ttu-id="f9a0e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f9a0e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f9a0e-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="f9a0e-115">clientBaseAddress</span></span>|<span data-ttu-id="f9a0e-116">Identyfikator URI, który ustawia adres kanału zwrotnego w trybie dupleksu.</span><span class="sxs-lookup"><span data-stu-id="f9a0e-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="f9a0e-117">Usługa używa tego adresu do nawiązywania kontaktu i nawiązania połączenia z klientem.</span><span class="sxs-lookup"><span data-stu-id="f9a0e-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="f9a0e-118">Jeśli ten atrybut nie jest ustawiony, zostanie wygenerowany domyślny adres`full qualified name+default port\TemporaryIndigoAddress\guid`"".</span><span class="sxs-lookup"><span data-stu-id="f9a0e-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="f9a0e-119">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="f9a0e-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9a0e-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f9a0e-120">Child Elements</span></span>  
 <span data-ttu-id="f9a0e-121">Brak</span><span class="sxs-lookup"><span data-stu-id="f9a0e-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9a0e-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f9a0e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="f9a0e-123">Element</span><span class="sxs-lookup"><span data-stu-id="f9a0e-123">Element</span></span>|<span data-ttu-id="f9a0e-124">Opis</span><span class="sxs-lookup"><span data-stu-id="f9a0e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9a0e-125">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="f9a0e-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="f9a0e-126">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f9a0e-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9a0e-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9a0e-127">Remarks</span></span>  
 <span data-ttu-id="f9a0e-128">Ten element konfiguracji jest używany z transportami, które nie zezwalają na natywną komunikację bezstronną, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="f9a0e-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="f9a0e-129">Protokół TCP, w przeciwieństwie, umożliwia natywną komunikację bezstronną i nie wymaga użycia tego elementu powiązania dla usługi do wysyłania komunikatów z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="f9a0e-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="f9a0e-130">Klient musi uwidocznić adres usługi, aby nawiązać kontakt i nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="f9a0e-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="f9a0e-131">Ten adres klienta jest dostarczany przez `clientBaseAddress` atrybut.</span><span class="sxs-lookup"><span data-stu-id="f9a0e-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="f9a0e-132">Należy pamiętać, że Windows Communication Foundation (WCF) automatycznie generuje element ClientBaseAddress, jeśli nie został jawnie ustawiony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f9a0e-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9a0e-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9a0e-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="f9a0e-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9a0e-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="f9a0e-135">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f9a0e-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f9a0e-136">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="f9a0e-136">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="f9a0e-137">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="f9a0e-137">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="f9a0e-138">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="f9a0e-138">\<customBinding></span></span>](custombinding.md)
