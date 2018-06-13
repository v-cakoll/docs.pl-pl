---
title: Możliwości zabezpieczeń powiązań niestandardowych
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2cfe5a18dd0fc7f8a8f54559d1d5b57e52cefa8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497428"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="169b1-102">Możliwości zabezpieczeń powiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="169b1-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="169b1-103">Najbardziej typowych zadań zabezpieczeń można wykonać za pomocą jednego powiązania dostarczane przez system.</span><span class="sxs-lookup"><span data-stu-id="169b1-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="169b1-104">Jeśli potrzebujesz większej kontroli, jednak można utworzyć niestandardowego powiązania z <xref:System.ServiceModel.Channels.SecurityBindingElement>, zgodnie z objaśnieniem w tych tematach.</span><span class="sxs-lookup"><span data-stu-id="169b1-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="169b1-105">Aby uzyskać więcej informacji dotyczących powiązań niestandardowych, zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="169b1-105">For more information about custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="169b1-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="169b1-106">In This Section</span></span>  
 [<span data-ttu-id="169b1-107">Tryby uwierzytelniania elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="169b1-107">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="169b1-108">W tym artykule opisano tryby uwierzytelniania, które są możliwe za pomocą niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="169b1-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="169b1-109">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="169b1-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="169b1-110">Opisuje podstawowe kroki tworzenia niestandardowego powiązania z elementem zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="169b1-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="169b1-111">Instrukcje: tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="169b1-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="169b1-112">Opisuje sposób tworzenia elementu zabezpieczeń dla określonego trybu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="169b1-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="169b1-113">Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="169b1-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="169b1-114">Opisuje sposób wyłączania bezpiecznej sesji podczas tworzenia usługi federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="169b1-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="169b1-115">Instrukcje: włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="169b1-115">How to: Enable Message Replay Detection</span></span>](../../../../docs/framework/wcf/feature-details/how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="169b1-116">Opisuje sposób określania, gdy wystąpi atak powtarzania.</span><span class="sxs-lookup"><span data-stu-id="169b1-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="169b1-117">Instrukcje: tworzenie poświadczeń pomocniczych</span><span class="sxs-lookup"><span data-stu-id="169b1-117">How to: Create a Supporting Credential</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="169b1-118">Opisuje sposób dostarczania obsługi poświadczeń z usługą, jeśli usługa wymaga.</span><span class="sxs-lookup"><span data-stu-id="169b1-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="169b1-119">Instrukcje: konfigurowanie potwierdzenia sygnatury</span><span class="sxs-lookup"><span data-stu-id="169b1-119">How to: Set Up a Signature Confirmation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="169b1-120">Opisuje czynności, aby potwierdzić podpisów do cyfrowego podpisywania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="169b1-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="169b1-121">Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara</span><span class="sxs-lookup"><span data-stu-id="169b1-121">How to: Set a Max Clock Skew</span></span>](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="169b1-122">Opisuje sposób ustawiania maksymalny dozwolony czas różnica między usługą i klienta.</span><span class="sxs-lookup"><span data-stu-id="169b1-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="169b1-123">Instrukcje: wyłączanie szyfrowania podpisów cyfrowych</span><span class="sxs-lookup"><span data-stu-id="169b1-123">How to: Disable Encryption of Digital Signatures</span></span>](../../../../docs/framework/wcf/feature-details/how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="169b1-124">W tym artykule opisano, jak wyłączyć szyfrowanie podpisów cyfrowych może mieć poprawiać wydajność.</span><span class="sxs-lookup"><span data-stu-id="169b1-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="169b1-125">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="169b1-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [<span data-ttu-id="169b1-126">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="169b1-126">\<security></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="169b1-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="169b1-127">Related Sections</span></span>  
 [<span data-ttu-id="169b1-128">Omówienie poziomów ochrony</span><span class="sxs-lookup"><span data-stu-id="169b1-128">Understanding Protection Level</span></span>](../../../../docs/framework/wcf/understanding-protection-level.md)  
  
 [<span data-ttu-id="169b1-129">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="169b1-129">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="169b1-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="169b1-130">See Also</span></span>  
 [<span data-ttu-id="169b1-131">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="169b1-131">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
 [<span data-ttu-id="169b1-132">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="169b1-132">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="169b1-133">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="169b1-133">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)
