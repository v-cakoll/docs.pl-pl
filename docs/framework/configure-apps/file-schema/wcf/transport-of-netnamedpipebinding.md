---
title: '&lt;transport&gt; w &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 7177dda08e1ce5b4f8adb072dce6155df714979d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556093"
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="461e5-102">&lt;transport&gt; w &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="461e5-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="461e5-103">Określa ustawienia zabezpieczenia transportu nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="461e5-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="461e5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="461e5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="461e5-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="461e5-105">\<bindings></span></span>  
<span data-ttu-id="461e5-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="461e5-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="461e5-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="461e5-107">\<binding></span></span>  
<span data-ttu-id="461e5-108">\<security></span><span class="sxs-lookup"><span data-stu-id="461e5-108">\<security></span></span>  
<span data-ttu-id="461e5-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="461e5-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="461e5-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="461e5-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="461e5-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="461e5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="461e5-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="461e5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="461e5-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="461e5-113">Attributes</span></span>  
  
|<span data-ttu-id="461e5-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="461e5-114">Attribute</span></span>|<span data-ttu-id="461e5-115">Opis</span><span class="sxs-lookup"><span data-stu-id="461e5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="461e5-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="461e5-116">protectionLevel</span></span>|<span data-ttu-id="461e5-117">Definiuje poziom ochrony nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="461e5-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="461e5-118">Podpisywania wiadomości zmniejsza ryzyko związane z innej naruszeniu komunikat, gdy są przesyłane.</span><span class="sxs-lookup"><span data-stu-id="461e5-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="461e5-119">Szyfrowanie zapewnia ochronę poufności poziom danych, podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="461e5-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="461e5-120">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="461e5-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="461e5-121">-Brak: Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="461e5-121">-   None: No protection.</span></span><br /><span data-ttu-id="461e5-122">— Logowanie: Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="461e5-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="461e5-123">-EncryptAndSign: Komunikaty są szyfrowane i podpisany.</span><span class="sxs-lookup"><span data-stu-id="461e5-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="461e5-124">Wartość domyślna to EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="461e5-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="461e5-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="461e5-125">Child Elements</span></span>  
 <span data-ttu-id="461e5-126">Brak</span><span class="sxs-lookup"><span data-stu-id="461e5-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="461e5-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="461e5-127">Parent Elements</span></span>  
  
|<span data-ttu-id="461e5-128">Element</span><span class="sxs-lookup"><span data-stu-id="461e5-128">Element</span></span>|<span data-ttu-id="461e5-129">Opis</span><span class="sxs-lookup"><span data-stu-id="461e5-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="461e5-130">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="461e5-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="461e5-131">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="461e5-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="461e5-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="461e5-132">See also</span></span>
- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="461e5-133">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="461e5-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="461e5-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="461e5-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="461e5-135">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="461e5-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="461e5-136">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="461e5-136">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="461e5-137">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="461e5-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
