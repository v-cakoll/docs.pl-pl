---
title: '&lt;transport&gt; w &lt;netNamedPipeBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 15489d2f5447fc2d3d4fb5173bcc94b5fb68e1c6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="d0637-102">&lt;transport&gt; w &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="d0637-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="d0637-103">Definiuje ustawienia zabezpieczeń transportu nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="d0637-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="d0637-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d0637-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d0637-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="d0637-105">\<bindings></span></span>  
<span data-ttu-id="d0637-106">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="d0637-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="d0637-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d0637-107">\<binding></span></span>  
<span data-ttu-id="d0637-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="d0637-108">\<security></span></span>  
<span data-ttu-id="d0637-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="d0637-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0637-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0637-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0637-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d0637-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d0637-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d0637-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0637-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d0637-113">Attributes</span></span>  
  
|<span data-ttu-id="d0637-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d0637-114">Attribute</span></span>|<span data-ttu-id="d0637-115">Opis</span><span class="sxs-lookup"><span data-stu-id="d0637-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0637-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="d0637-116">protectionLevel</span></span>|<span data-ttu-id="d0637-117">Określa poziom ochrony nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="d0637-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="d0637-118">Podpisywanie wiadomości zmniejsza ryzyko innych firm, manipulowanie wiadomości, gdy są przesyłane.</span><span class="sxs-lookup"><span data-stu-id="d0637-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="d0637-119">Szyfrowanie zapewnia ochronę poufności poziom danych podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="d0637-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="d0637-120">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="d0637-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="d0637-121">-Brak: Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="d0637-121">-   None: No protection.</span></span><br /><span data-ttu-id="d0637-122">-Znak: Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="d0637-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="d0637-123">-EncryptAndSign: Komunikaty są zaszyfrowana i podpisana.</span><span class="sxs-lookup"><span data-stu-id="d0637-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="d0637-124">Wartość domyślna to EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="d0637-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0637-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d0637-125">Child Elements</span></span>  
 <span data-ttu-id="d0637-126">Brak</span><span class="sxs-lookup"><span data-stu-id="d0637-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0637-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d0637-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d0637-128">Element</span><span class="sxs-lookup"><span data-stu-id="d0637-128">Element</span></span>|<span data-ttu-id="d0637-129">Opis</span><span class="sxs-lookup"><span data-stu-id="d0637-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0637-130">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="d0637-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="d0637-131">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="d0637-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0637-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0637-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="d0637-133">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="d0637-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="d0637-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="d0637-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="d0637-135">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="d0637-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="d0637-136">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="d0637-136">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="d0637-137">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="d0637-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
