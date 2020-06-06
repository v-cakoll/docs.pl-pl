---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: c3bae4dfee36e9de62c27bbccecd9a31a5b7d459
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736775"
---
# \<compositeDuplex>
<span data-ttu-id="6fa0c-101">Definiuje element powiązania, który jest używany, gdy klient musi uwidocznić punkt końcowy dla usługi w celu wysłania komunikatów z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-101">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**  
  
## <a name="syntax"></a><span data-ttu-id="6fa0c-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fa0c-102">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fa0c-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6fa0c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="6fa0c-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fa0c-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6fa0c-105">Attributes</span></span>  
  
|<span data-ttu-id="6fa0c-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6fa0c-106">Attribute</span></span>|<span data-ttu-id="6fa0c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6fa0c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6fa0c-108">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="6fa0c-108">clientBaseAddress</span></span>|<span data-ttu-id="6fa0c-109">Identyfikator URI, który ustawia adres kanału zwrotnego w trybie dupleksu.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-109">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="6fa0c-110">Usługa używa tego adresu do nawiązywania kontaktu i nawiązania połączenia z klientem.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-110">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="6fa0c-111">Jeśli ten atrybut nie jest ustawiony, zostanie wygenerowany domyślny adres " `full qualified name+default port\TemporaryIndigoAddress\guid` ".</span><span class="sxs-lookup"><span data-stu-id="6fa0c-111">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="6fa0c-112">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-112">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6fa0c-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6fa0c-113">Child Elements</span></span>  
 <span data-ttu-id="6fa0c-114">Brak</span><span class="sxs-lookup"><span data-stu-id="6fa0c-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6fa0c-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6fa0c-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6fa0c-116">Element</span><span class="sxs-lookup"><span data-stu-id="6fa0c-116">Element</span></span>|<span data-ttu-id="6fa0c-117">Opis</span><span class="sxs-lookup"><span data-stu-id="6fa0c-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="6fa0c-118">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fa0c-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6fa0c-119">Remarks</span></span>  
 <span data-ttu-id="6fa0c-120">Ten element konfiguracji jest używany z transportami, które nie zezwalają na natywną komunikację bezstronną, na przykład HTTP.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-120">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="6fa0c-121">Protokół TCP, w przeciwieństwie, umożliwia natywną komunikację bezstronną i nie wymaga użycia tego elementu powiązania dla usługi do wysyłania komunikatów z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-121">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="6fa0c-122">Klient musi uwidocznić adres usługi, aby nawiązać kontakt i nawiązać połączenie.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-122">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="6fa0c-123">Ten adres klienta jest dostarczany przez `clientBaseAddress` atrybut.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-123">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="6fa0c-124">Należy pamiętać, że Windows Communication Foundation (WCF) automatycznie generuje element ClientBaseAddress, jeśli nie został jawnie ustawiony przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6fa0c-124">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fa0c-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="6fa0c-125">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="6fa0c-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fa0c-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="6fa0c-127">Powiązania</span><span class="sxs-lookup"><span data-stu-id="6fa0c-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6fa0c-128">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="6fa0c-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6fa0c-129">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="6fa0c-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
