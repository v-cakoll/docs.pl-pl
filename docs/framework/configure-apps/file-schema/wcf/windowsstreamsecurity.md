---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: cddd9f0c1dda982c1795500723c21546bd58c92b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399094"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="a6bad-101">\<windowsStreamSecurity></span><span class="sxs-lookup"><span data-stu-id="a6bad-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="a6bad-102">Określ ustawienia zabezpieczeń strumienia systemu Windows niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a6bad-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
<span data-ttu-id="a6bad-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a6bad-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a6bad-104">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a6bad-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a6bad-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> powiązań**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="a6bad-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="a6bad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<niestandardowy >Binding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="a6bad-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="a6bad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> powiązania**</span><span class="sxs-lookup"><span data-stu-id="a6bad-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="a6bad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<windowsStreamSecurity >**</span><span class="sxs-lookup"><span data-stu-id="a6bad-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6bad-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6bad-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6bad-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a6bad-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a6bad-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a6bad-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6bad-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a6bad-112">Attributes</span></span>  
  
|<span data-ttu-id="a6bad-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a6bad-113">Attribute</span></span>|<span data-ttu-id="a6bad-114">Opis</span><span class="sxs-lookup"><span data-stu-id="a6bad-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6bad-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="a6bad-115">protectionLevel</span></span>|<span data-ttu-id="a6bad-116">Definiuje zabezpieczenia na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a6bad-116">Defines message-level security.</span></span> <span data-ttu-id="a6bad-117">Komunikaty podpisywania zmniejszają ryzyko naruszenia przez osobę trzecią komunikatu podczas jego przesyłania.</span><span class="sxs-lookup"><span data-stu-id="a6bad-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="a6bad-118">Szyfrowanie zapewnia prywatność na poziomie danych podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="a6bad-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="a6bad-119">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="a6bad-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a6bad-120">Dawaj Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="a6bad-120">-   None: No protection.</span></span><br /><span data-ttu-id="a6bad-121">Zapis Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="a6bad-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="a6bad-122">EncryptAndSign Komunikaty są podpisane i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="a6bad-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="a6bad-123">Wartość domyślna to EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="a6bad-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="a6bad-124">Ten atrybut jest typu <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="a6bad-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6bad-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a6bad-125">Child Elements</span></span>  
 <span data-ttu-id="a6bad-126">Brak</span><span class="sxs-lookup"><span data-stu-id="a6bad-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6bad-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a6bad-127">Parent Elements</span></span>  
  
|<span data-ttu-id="a6bad-128">Element</span><span class="sxs-lookup"><span data-stu-id="a6bad-128">Element</span></span>|<span data-ttu-id="a6bad-129">Opis</span><span class="sxs-lookup"><span data-stu-id="a6bad-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6bad-130">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="a6bad-130">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="a6bad-131">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a6bad-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6bad-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6bad-132">Remarks</span></span>  
 <span data-ttu-id="a6bad-133">Transporty korzystające z protokołu opartego na strumieniu, takiego jak TCP i nazwane potoki, obsługują uaktualnienia transportu na podstawie strumienia.</span><span class="sxs-lookup"><span data-stu-id="a6bad-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="a6bad-134">W programie WCF dostępne są uaktualnienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="a6bad-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="a6bad-135">Konfiguracja tego zabezpieczenia transportu jest hermetyzowana przez ten element konfiguracji, a także przez [ \<sslStreamSecurity >](sslstreamsecurity.md), który można skonfigurować i dodać do niestandardowego powiązania</span><span class="sxs-lookup"><span data-stu-id="a6bad-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6bad-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6bad-136">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="a6bad-137">Powiązania</span><span class="sxs-lookup"><span data-stu-id="a6bad-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a6bad-138">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="a6bad-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a6bad-139">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a6bad-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a6bad-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a6bad-140">\<customBinding></span></span>](custombinding.md)
