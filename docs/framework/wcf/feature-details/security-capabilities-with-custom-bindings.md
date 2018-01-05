---
title: "Możliwości zabezpieczeń powiązań niestandardowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2f26e68b9654ccd565328003596e324558f7505f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="64e6d-102">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="64e6d-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="64e6d-103">Najbardziej typowych zadań zabezpieczeń można wykonać za pomocą jednego powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="64e6d-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="64e6d-104">Jeśli potrzebujesz większej kontroli, jednak można utworzyć niestandardowego powiązania z <xref:System.ServiceModel.Channels.SecurityBindingElement>, zgodnie z objaśnieniem w tych tematach.</span><span class="sxs-lookup"><span data-stu-id="64e6d-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="64e6d-105">powiązania niestandardowe, zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="64e6d-105"> custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64e6d-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="64e6d-106">In This Section</span></span>  
 [<span data-ttu-id="64e6d-107">Tryby uwierzytelniania elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="64e6d-107">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="64e6d-108">W tym artykule opisano tryby uwierzytelniania, które są możliwe za pomocą niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="64e6d-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="64e6d-109">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="64e6d-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="64e6d-110">Opisuje podstawowe kroki tworzenia niestandardowego powiązania z elementem zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="64e6d-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="64e6d-111">Instrukcje: tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="64e6d-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="64e6d-112">Opisuje sposób tworzenia elementu zabezpieczeń dla określonego trybu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="64e6d-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="64e6d-113">Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="64e6d-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="64e6d-114">Opisuje sposób wyłączania bezpiecznej sesji podczas tworzenia usługi federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="64e6d-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="64e6d-115">Instrukcje: włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="64e6d-115">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="64e6d-116">Opisuje sposób określania, gdy wystąpi atak powtarzania.</span><span class="sxs-lookup"><span data-stu-id="64e6d-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="64e6d-117">Instrukcje: tworzenie poświadczeń pomocniczych</span><span class="sxs-lookup"><span data-stu-id="64e6d-117">How to: Create a Supporting Credential</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="64e6d-118">Opisuje sposób dostarczania obsługi poświadczeń z usługą, jeśli usługa wymaga.</span><span class="sxs-lookup"><span data-stu-id="64e6d-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="64e6d-119">Instrukcje: konfigurowanie potwierdzenia sygnatury</span><span class="sxs-lookup"><span data-stu-id="64e6d-119">How to: Set Up a Signature Confirmation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="64e6d-120">Opisuje czynności, aby potwierdzić podpisów do cyfrowego podpisywania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="64e6d-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="64e6d-121">Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara</span><span class="sxs-lookup"><span data-stu-id="64e6d-121">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="64e6d-122">Opisuje sposób ustawiania maksymalny dozwolony czas różnica między usługą i klienta.</span><span class="sxs-lookup"><span data-stu-id="64e6d-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="64e6d-123">Instrukcje: wyłączanie szyfrowania podpisów cyfrowych</span><span class="sxs-lookup"><span data-stu-id="64e6d-123">How to: Disable Encryption of Digital Signatures</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="64e6d-124">W tym artykule opisano, jak wyłączyć szyfrowanie podpisów cyfrowych może mieć poprawiać wydajność.</span><span class="sxs-lookup"><span data-stu-id="64e6d-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="64e6d-125">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="64e6d-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [<span data-ttu-id="64e6d-126">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="64e6d-126">\<security></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="64e6d-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="64e6d-127">Related Sections</span></span>  
 [<span data-ttu-id="64e6d-128">Omówienie poziomów ochrony</span><span class="sxs-lookup"><span data-stu-id="64e6d-128">Understanding Protection Level</span></span>](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [<span data-ttu-id="64e6d-129">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="64e6d-129">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="64e6d-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64e6d-130">See Also</span></span>  
 [<span data-ttu-id="64e6d-131">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="64e6d-131">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [<span data-ttu-id="64e6d-132">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="64e6d-132">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="64e6d-133">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="64e6d-133">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
