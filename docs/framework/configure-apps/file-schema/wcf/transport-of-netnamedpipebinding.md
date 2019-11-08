---
title: <transport> dla <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: d40178e59b89c2912123e1927e9e960f6d880871
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735960"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="7df01-102">\<Transport > \<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="7df01-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="7df01-103">Definiuje ustawienia zabezpieczeń transportu dla nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="7df01-103">Defines the transport security settings for a named pipe.</span></span>  
  
<span data-ttu-id="7df01-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7df01-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7df01-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="7df01-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7df01-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<powiązań**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="7df01-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7df01-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<NetNamedPipeBinding**](netnamedpipebinding.md) ></span><span class="sxs-lookup"><span data-stu-id="7df01-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="7df01-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<powiązania >** </span><span class="sxs-lookup"><span data-stu-id="7df01-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7df01-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpieczeń**](security-of-netnamedpipebinding.md) ></span><span class="sxs-lookup"><span data-stu-id="7df01-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)</span></span>\
<span data-ttu-id="7df01-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**</span><span class="sxs-lookup"><span data-stu-id="7df01-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7df01-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="7df01-111">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7df01-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7df01-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7df01-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7df01-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7df01-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7df01-114">Attributes</span></span>  
  
|<span data-ttu-id="7df01-115">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7df01-115">Attribute</span></span>|<span data-ttu-id="7df01-116">Opis</span><span class="sxs-lookup"><span data-stu-id="7df01-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7df01-117">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="7df01-117">protectionLevel</span></span>|<span data-ttu-id="7df01-118">Definiuje poziom ochrony nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="7df01-118">Defines protection level of the named pipe.</span></span> <span data-ttu-id="7df01-119">Komunikaty podpisywania zmniejszają ryzyko naruszenia przez osobę trzecią komunikatu podczas jego przesyłania.</span><span class="sxs-lookup"><span data-stu-id="7df01-119">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="7df01-120">Szyfrowanie zapewnia prywatność na poziomie danych podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="7df01-120">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="7df01-121">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="7df01-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7df01-122">-Brak: brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="7df01-122">-   None: No protection.</span></span><br /><span data-ttu-id="7df01-123">-Sign: komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="7df01-123">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="7df01-124">-EncryptAndSign: komunikaty są szyfrowane i podpisane.</span><span class="sxs-lookup"><span data-stu-id="7df01-124">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="7df01-125">Wartość domyślna to EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="7df01-125">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7df01-126">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7df01-126">Child Elements</span></span>  
 <span data-ttu-id="7df01-127">Brak</span><span class="sxs-lookup"><span data-stu-id="7df01-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7df01-128">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7df01-128">Parent Elements</span></span>  
  
|<span data-ttu-id="7df01-129">Element</span><span class="sxs-lookup"><span data-stu-id="7df01-129">Element</span></span>|<span data-ttu-id="7df01-130">Opis</span><span class="sxs-lookup"><span data-stu-id="7df01-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7df01-131">> zabezpieczeń \<</span><span class="sxs-lookup"><span data-stu-id="7df01-131">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="7df01-132">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="7df01-132">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7df01-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7df01-133">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="7df01-134">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="7df01-134">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7df01-135">Powiązania</span><span class="sxs-lookup"><span data-stu-id="7df01-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7df01-136">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="7df01-136">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7df01-137">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="7df01-137">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7df01-138">> powiązań \<</span><span class="sxs-lookup"><span data-stu-id="7df01-138">\<binding></span></span>](bindings.md)
