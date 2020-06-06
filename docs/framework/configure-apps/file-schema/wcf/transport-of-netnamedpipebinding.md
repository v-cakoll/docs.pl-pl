---
title: <transport> dla <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: d40178e59b89c2912123e1927e9e960f6d880871
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735960"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="f1a06-102">\<transport> dla \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="f1a06-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="f1a06-103">Definiuje ustawienia zabezpieczeń transportu dla nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="f1a06-103">Defines the transport security settings for a named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="f1a06-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1a06-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1a06-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f1a06-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f1a06-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f1a06-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1a06-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f1a06-107">Attributes</span></span>  
  
|<span data-ttu-id="f1a06-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f1a06-108">Attribute</span></span>|<span data-ttu-id="f1a06-109">Opis</span><span class="sxs-lookup"><span data-stu-id="f1a06-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1a06-110">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="f1a06-110">protectionLevel</span></span>|<span data-ttu-id="f1a06-111">Definiuje poziom ochrony nazwanego potoku.</span><span class="sxs-lookup"><span data-stu-id="f1a06-111">Defines protection level of the named pipe.</span></span> <span data-ttu-id="f1a06-112">Komunikaty podpisywania zmniejszają ryzyko naruszenia przez osobę trzecią komunikatu podczas jego przesyłania.</span><span class="sxs-lookup"><span data-stu-id="f1a06-112">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="f1a06-113">Szyfrowanie zapewnia prywatność na poziomie danych podczas transportu.</span><span class="sxs-lookup"><span data-stu-id="f1a06-113">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="f1a06-114">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="f1a06-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f1a06-115">-Brak: brak ochrony.</span><span class="sxs-lookup"><span data-stu-id="f1a06-115">-   None: No protection.</span></span><br /><span data-ttu-id="f1a06-116">-Sign: komunikaty są podpisane.</span><span class="sxs-lookup"><span data-stu-id="f1a06-116">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="f1a06-117">-EncryptAndSign: komunikaty są szyfrowane i podpisane.</span><span class="sxs-lookup"><span data-stu-id="f1a06-117">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="f1a06-118">Wartość domyślna to EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="f1a06-118">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1a06-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f1a06-119">Child Elements</span></span>  
 <span data-ttu-id="f1a06-120">Brak</span><span class="sxs-lookup"><span data-stu-id="f1a06-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1a06-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f1a06-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f1a06-122">Element</span><span class="sxs-lookup"><span data-stu-id="f1a06-122">Element</span></span>|<span data-ttu-id="f1a06-123">Opis</span><span class="sxs-lookup"><span data-stu-id="f1a06-123">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="f1a06-124">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="f1a06-124">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1a06-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1a06-125">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="f1a06-126">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="f1a06-126">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f1a06-127">Powiązania</span><span class="sxs-lookup"><span data-stu-id="f1a06-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f1a06-128">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="f1a06-128">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f1a06-129">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="f1a06-129">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
