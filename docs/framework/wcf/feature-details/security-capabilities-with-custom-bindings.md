---
title: Możliwości zabezpieczeń wiązań niestandardowych
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 25d203fa706eeb0d0ccf1eaf4367ffa5bd7b83aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157277"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="653f8-102">Możliwości zabezpieczeń wiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="653f8-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="653f8-103">Najbardziej typowe zadania zabezpieczeń można wykonać przy użyciu jednej z powiązań dostarczanych przez system.</span><span class="sxs-lookup"><span data-stu-id="653f8-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="653f8-104">Jeśli potrzebujesz większej kontroli, jednak można utworzyć niestandardowego powiązania za pomocą <xref:System.ServiceModel.Channels.SecurityBindingElement>, zgodnie z opisem w następujących tematach.</span><span class="sxs-lookup"><span data-stu-id="653f8-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="653f8-105">Aby uzyskać więcej informacji na temat powiązania niestandardowej zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="653f8-105">For more information about custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="653f8-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="653f8-106">In This Section</span></span>  
 [<span data-ttu-id="653f8-107">Tryby uwierzytelniania elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="653f8-107">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="653f8-108">W tym artykule opisano tryby uwierzytelniania, które można wykonać za pomocą niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="653f8-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="653f8-109">Instrukcje: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="653f8-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="653f8-110">W tym artykule opisano podstawowe kroki tworzenia niestandardowego powiązania za pomocą elementu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="653f8-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="653f8-111">Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="653f8-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="653f8-112">W tym artykule opisano, jak utworzyć element zabezpieczeń dla określonego trybu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="653f8-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="653f8-113">Instrukcje: Wyłączanie bezpiecznej sesji WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="653f8-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="653f8-114">Opisuje sposób wyłączanie bezpiecznej sesji podczas tworzenia usługi federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="653f8-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="653f8-115">Instrukcje: Włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="653f8-115">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="653f8-116">W tym artykule opisano, jak określić, gdy wystąpi atak metodą powtórzeń.</span><span class="sxs-lookup"><span data-stu-id="653f8-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="653f8-117">Instrukcje: Tworzenie poświadczeń pomocniczych</span><span class="sxs-lookup"><span data-stu-id="653f8-117">How to: Create a Supporting Credential</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="653f8-118">Zawiera opis sposobu dostarczania pomocnicze poświadczeń z usługą, jeśli usługa wymaga.</span><span class="sxs-lookup"><span data-stu-id="653f8-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="653f8-119">Instrukcje: Konfigurowanie potwierdzenia sygnatury</span><span class="sxs-lookup"><span data-stu-id="653f8-119">How to: Set Up a Signature Confirmation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="653f8-120">W tym artykule opisano kroki, aby potwierdzić podpisów w przypadku, gdy cyfrowe podpisywanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="653f8-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="653f8-121">Instrukcje: Zestaw maksymalnego przesunięcia czasowego zegara</span><span class="sxs-lookup"><span data-stu-id="653f8-121">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="653f8-122">W tym artykule opisano, jak ustawić maksymalny dozwolony czas różnią się usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="653f8-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="653f8-123">Instrukcje: Wyłączanie szyfrowania podpisów cyfrowych</span><span class="sxs-lookup"><span data-stu-id="653f8-123">How to: Disable Encryption of Digital Signatures</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="653f8-124">W tym artykule opisano, jak wyłączanie szyfrowania podpisów cyfrowych może mieć korzyści wydajności.</span><span class="sxs-lookup"><span data-stu-id="653f8-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="653f8-125">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="653f8-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [<span data-ttu-id="653f8-126">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="653f8-126">\<security></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="653f8-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="653f8-127">Related Sections</span></span>  
 [<span data-ttu-id="653f8-128">Omówienie poziomów ochrony</span><span class="sxs-lookup"><span data-stu-id="653f8-128">Understanding Protection Level</span></span>](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [<span data-ttu-id="653f8-129">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="653f8-129">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="653f8-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="653f8-130">See also</span></span>

- [<span data-ttu-id="653f8-131">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="653f8-131">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
- [<span data-ttu-id="653f8-132">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="653f8-132">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="653f8-133">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="653f8-133">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
