---
title: <transport> dla <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 1e76d0962ea7b4714ef6ca1f9d4c4c3e23df5b6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934669"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="1ae65-102">\<Transport > \<NetNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="1ae65-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="1ae65-103">Definiuje ustawienia zabezpieczeń transportu dla nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="1ae65-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="1ae65-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1ae65-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1ae65-105">\<> powiązań</span><span class="sxs-lookup"><span data-stu-id="1ae65-105">\<bindings></span></span>  
<span data-ttu-id="1ae65-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="1ae65-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="1ae65-107">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="1ae65-107">\<binding></span></span>  
<span data-ttu-id="1ae65-108">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="1ae65-108">\<security></span></span>  
<span data-ttu-id="1ae65-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="1ae65-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae65-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ae65-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ae65-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1ae65-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1ae65-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1ae65-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ae65-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1ae65-113">Attributes</span></span>  
  
|<span data-ttu-id="1ae65-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1ae65-114">Attribute</span></span>|<span data-ttu-id="1ae65-115">Opis</span><span class="sxs-lookup"><span data-stu-id="1ae65-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ae65-116">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="1ae65-116">protectionLevel</span></span>|<span data-ttu-id="1ae65-117">Definiuje poziom ochrony nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="1ae65-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="1ae65-118">Komunikaty podpisywania zmniejszają ryzyko naruszenia przez osobę trzecią komunikatu podczas jego przesyłania.</span><span class="sxs-lookup"><span data-stu-id="1ae65-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="1ae65-119">Szyfrowanie zapewnia prywatność na poziomie danych podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="1ae65-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="1ae65-120">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="1ae65-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1ae65-121">Dawaj Brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="1ae65-121">-   None: No protection.</span></span><br /><span data-ttu-id="1ae65-122">Zapis Komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="1ae65-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="1ae65-123">EncryptAndSign Komunikaty są szyfrowane i podpisane.</span><span class="sxs-lookup"><span data-stu-id="1ae65-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="1ae65-124">Wartość domyślna to EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="1ae65-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ae65-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1ae65-125">Child Elements</span></span>  
 <span data-ttu-id="1ae65-126">Brak</span><span class="sxs-lookup"><span data-stu-id="1ae65-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ae65-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1ae65-127">Parent Elements</span></span>  
  
|<span data-ttu-id="1ae65-128">Element</span><span class="sxs-lookup"><span data-stu-id="1ae65-128">Element</span></span>|<span data-ttu-id="1ae65-129">Opis</span><span class="sxs-lookup"><span data-stu-id="1ae65-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ae65-130">\<> zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="1ae65-130">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="1ae65-131">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="1ae65-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ae65-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ae65-132">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="1ae65-133">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="1ae65-133">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1ae65-134">Powiązania</span><span class="sxs-lookup"><span data-stu-id="1ae65-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1ae65-135">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="1ae65-135">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1ae65-136">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="1ae65-136">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1ae65-137">\<> powiązania</span><span class="sxs-lookup"><span data-stu-id="1ae65-137">\<binding></span></span>](../../../misc/binding.md)
