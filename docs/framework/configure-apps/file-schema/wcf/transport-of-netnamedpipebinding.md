---
title: '&lt;transport&gt; w &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 0006be71ee67d5f274d8af8087f2d111cddb12b2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407258"
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="4e9fa-102">&lt;transport&gt; w &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="4e9fa-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="4e9fa-103">Określa ustawienia zabezpieczenia transportu nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="4e9fa-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="4e9fa-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4e9fa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4e9fa-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="4e9fa-105">\<bindings></span></span>  
<span data-ttu-id="4e9fa-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="4e9fa-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="4e9fa-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4e9fa-107">\<binding></span></span>  
<span data-ttu-id="4e9fa-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="4e9fa-108">\<security></span></span>  
<span data-ttu-id="4e9fa-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="4e9fa-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e9fa-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e9fa-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e9fa-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4e9fa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4e9fa-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4e9fa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e9fa-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4e9fa-113">Attributes</span></span>  
  
|<span data-ttu-id="4e9fa-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4e9fa-114">Attribute</span></span>|<span data-ttu-id="4e9fa-115">Opis</span><span class="sxs-lookup"><span data-stu-id="4e9fa-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4e9fa-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="4e9fa-116">protectionLevel</span></span>|<span data-ttu-id="4e9fa-117">Definiuje poziom ochrony nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="4e9fa-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="4e9fa-118">Podpisywania wiadomości zmniejsza ryzyko związane z innej naruszeniu komunikat, gdy są przesyłane.</span><span class="sxs-lookup"><span data-stu-id="4e9fa-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="4e9fa-119">Szyfrowanie zapewnia ochronę poufności poziom danych, podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="4e9fa-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="4e9fa-120">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="4e9fa-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4e9fa-121">-Brak: Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="4e9fa-121">-   None: No protection.</span></span><br /><span data-ttu-id="4e9fa-122">— Logowanie: Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="4e9fa-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="4e9fa-123">-EncryptAndSign: Komunikaty są szyfrowane i podpisany.</span><span class="sxs-lookup"><span data-stu-id="4e9fa-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="4e9fa-124">Wartość domyślna to EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="4e9fa-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e9fa-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4e9fa-125">Child Elements</span></span>  
 <span data-ttu-id="4e9fa-126">Brak</span><span class="sxs-lookup"><span data-stu-id="4e9fa-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e9fa-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4e9fa-127">Parent Elements</span></span>  
  
|<span data-ttu-id="4e9fa-128">Element</span><span class="sxs-lookup"><span data-stu-id="4e9fa-128">Element</span></span>|<span data-ttu-id="4e9fa-129">Opis</span><span class="sxs-lookup"><span data-stu-id="4e9fa-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e9fa-130">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="4e9fa-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="4e9fa-131">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="4e9fa-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e9fa-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e9fa-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="4e9fa-133">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="4e9fa-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="4e9fa-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="4e9fa-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4e9fa-135">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="4e9fa-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="4e9fa-136">Konfigurowanie Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="4e9fa-136">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="4e9fa-137">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="4e9fa-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
