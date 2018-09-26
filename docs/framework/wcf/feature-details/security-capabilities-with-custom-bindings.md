---
title: Możliwości zabezpieczeń powiązań niestandardowych
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
author: BrucePerlerMS
ms.openlocfilehash: 35d2477af3dc7ce6fdd075055fff9e687bdc2a60
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47110284"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="6f5d0-102">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="6f5d0-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="6f5d0-103">Najbardziej typowe zadania zabezpieczeń można wykonać przy użyciu jednej z powiązań dostarczanych przez system.</span><span class="sxs-lookup"><span data-stu-id="6f5d0-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="6f5d0-104">Jeśli potrzebujesz większej kontroli, jednak można utworzyć niestandardowego powiązania za pomocą <xref:System.ServiceModel.Channels.SecurityBindingElement>, zgodnie z opisem w następujących tematach.</span><span class="sxs-lookup"><span data-stu-id="6f5d0-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="6f5d0-105">Aby uzyskać więcej informacji na temat powiązania niestandardowej zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="6f5d0-105">For more information about custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f5d0-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6f5d0-106">In This Section</span></span>  
 [<span data-ttu-id="6f5d0-107">Tryby uwierzytelniania elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="6f5d0-107">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="6f5d0-108">W tym artykule opisano tryby uwierzytelniania, które można wykonać za pomocą niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="6f5d0-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="6f5d0-109">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="6f5d0-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="6f5d0-110">W tym artykule opisano podstawowe kroki tworzenia niestandardowego powiązania za pomocą elementu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="6f5d0-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="6f5d0-111">Instrukcje: tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="6f5d0-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="6f5d0-112">W tym artykule opisano, jak utworzyć element zabezpieczeń dla określonego trybu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6f5d0-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="6f5d0-113">Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="6f5d0-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="6f5d0-114">Opisuje sposób wyłączanie bezpiecznej sesji podczas tworzenia usługi federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="6f5d0-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="6f5d0-115">Instrukcje: włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="6f5d0-115">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="6f5d0-116">W tym artykule opisano, jak określić, gdy wystąpi atak metodą powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="6f5d0-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="6f5d0-117">Instrukcje: tworzenie poświadczeń pomocniczych</span><span class="sxs-lookup"><span data-stu-id="6f5d0-117">How to: Create a Supporting Credential</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="6f5d0-118">Zawiera opis sposobu dostarczania pomocnicze poświadczeń z usługą, jeśli usługa wymaga.</span><span class="sxs-lookup"><span data-stu-id="6f5d0-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="6f5d0-119">Instrukcje: konfigurowanie potwierdzenia sygnatury</span><span class="sxs-lookup"><span data-stu-id="6f5d0-119">How to: Set Up a Signature Confirmation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="6f5d0-120">W tym artykule opisano kroki, aby potwierdzić podpisów w przypadku, gdy cyfrowe podpisywanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="6f5d0-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="6f5d0-121">Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara</span><span class="sxs-lookup"><span data-stu-id="6f5d0-121">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="6f5d0-122">W tym artykule opisano, jak ustawić maksymalny dozwolony czas różnią się usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="6f5d0-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="6f5d0-123">Instrukcje: wyłączanie szyfrowania podpisów cyfrowych</span><span class="sxs-lookup"><span data-stu-id="6f5d0-123">How to: Disable Encryption of Digital Signatures</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="6f5d0-124">W tym artykule opisano, jak wyłączanie szyfrowania podpisów cyfrowych może mieć korzyści wydajności.</span><span class="sxs-lookup"><span data-stu-id="6f5d0-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6f5d0-125">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="6f5d0-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [<span data-ttu-id="6f5d0-126">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="6f5d0-126">\<security></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="6f5d0-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="6f5d0-127">Related Sections</span></span>  
 [<span data-ttu-id="6f5d0-128">Omówienie poziomów ochrony</span><span class="sxs-lookup"><span data-stu-id="6f5d0-128">Understanding Protection Level</span></span>](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [<span data-ttu-id="6f5d0-129">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="6f5d0-129">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="6f5d0-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f5d0-130">See Also</span></span>  
 [<span data-ttu-id="6f5d0-131">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="6f5d0-131">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [<span data-ttu-id="6f5d0-132">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="6f5d0-132">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="6f5d0-133">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="6f5d0-133">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
