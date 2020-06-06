---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: dab8505a9ddb348a6f7fe16ae9acb3a0119a8b06
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735895"
---
# \<windowsStreamSecurity>
<span data-ttu-id="c3ff0-101">Określ ustawienia zabezpieczeń strumienia systemu Windows niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-101">Specify Windows stream security settings of the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="c3ff0-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3ff0-102">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3ff0-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c3ff0-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c3ff0-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3ff0-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3ff0-105">Attributes</span></span>  
  
|<span data-ttu-id="c3ff0-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c3ff0-106">Attribute</span></span>|<span data-ttu-id="c3ff0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c3ff0-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c3ff0-108">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="c3ff0-108">protectionLevel</span></span>|<span data-ttu-id="c3ff0-109">Definiuje zabezpieczenia na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-109">Defines message-level security.</span></span> <span data-ttu-id="c3ff0-110">Komunikaty podpisywania zmniejszają ryzyko naruszenia przez osobę trzecią komunikatu podczas jego przesyłania.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-110">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="c3ff0-111">Szyfrowanie zapewnia prywatność na poziomie danych podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-111">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="c3ff0-112">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="c3ff0-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c3ff0-113">-Brak: brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-113">-   None: No protection.</span></span><br /><span data-ttu-id="c3ff0-114">-Sign: komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-114">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="c3ff0-115">-EncryptAndSign: komunikaty są podpisane i szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-115">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="c3ff0-116">Wartość domyślna to EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-116">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="c3ff0-117">Ten atrybut jest typu <xref:System.Net.Security.ProtectionLevel> .</span><span class="sxs-lookup"><span data-stu-id="c3ff0-117">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3ff0-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c3ff0-118">Child Elements</span></span>  
 <span data-ttu-id="c3ff0-119">Brak</span><span class="sxs-lookup"><span data-stu-id="c3ff0-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c3ff0-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c3ff0-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c3ff0-121">Element</span><span class="sxs-lookup"><span data-stu-id="c3ff0-121">Element</span></span>|<span data-ttu-id="c3ff0-122">Opis</span><span class="sxs-lookup"><span data-stu-id="c3ff0-122">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="c3ff0-123">Definiuje wszystkie możliwości powiązań niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3ff0-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3ff0-124">Remarks</span></span>  
 <span data-ttu-id="c3ff0-125">Transporty korzystające z protokołu opartego na strumieniu, takiego jak TCP i nazwane potoki, obsługują uaktualnienia transportu na podstawie strumienia.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-125">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="c3ff0-126">W programie WCF dostępne są uaktualnienia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="c3ff0-126">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="c3ff0-127">Konfiguracja tego zabezpieczenia transportu jest hermetyzowana przez ten element konfiguracji, a także przez [\<sslStreamSecurity>](sslstreamsecurity.md) , który można skonfigurować i dodać do niestandardowego powiązania</span><span class="sxs-lookup"><span data-stu-id="c3ff0-127">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ff0-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3ff0-128">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="c3ff0-129">Powiązania</span><span class="sxs-lookup"><span data-stu-id="c3ff0-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c3ff0-130">Rozszerzanie powiązań</span><span class="sxs-lookup"><span data-stu-id="c3ff0-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c3ff0-131">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="c3ff0-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
