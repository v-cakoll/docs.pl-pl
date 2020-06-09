---
title: Możliwości zabezpieczeń wiązań niestandardowych
ms.date: 03/30/2017
ms.assetid: a2425679-484a-4e6c-9c98-7da7304f1516
ms.openlocfilehash: 48d17543f2b133c74bcfa82cfe1a2a0de28b1d01
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595196"
---
# <a name="security-capabilities-with-custom-bindings"></a><span data-ttu-id="a32e1-102">Możliwości zabezpieczeń wiązań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="a32e1-102">Security Capabilities with Custom Bindings</span></span>
<span data-ttu-id="a32e1-103">Większość typowych zadań związanych z zabezpieczeniami można wykonać przy użyciu jednego z powiązań dostarczonych przez system.</span><span class="sxs-lookup"><span data-stu-id="a32e1-103">You can perform most common security tasks by using one of the system-provided bindings.</span></span> <span data-ttu-id="a32e1-104">Jeśli potrzebujesz więcej kontroli, możesz jednak utworzyć niestandardowe powiązanie z <xref:System.ServiceModel.Channels.SecurityBindingElement> , zgodnie z opisem w poniższych tematach.</span><span class="sxs-lookup"><span data-stu-id="a32e1-104">If you need more control, however, you can create a custom binding with a <xref:System.ServiceModel.Channels.SecurityBindingElement>, as explained in these topics.</span></span> <span data-ttu-id="a32e1-105">Aby uzyskać więcej informacji na temat powiązań niestandardowych, zobacz [niestandardowe powiązania](../extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="a32e1-105">For more information about custom bindings, see [Custom Bindings](../extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a32e1-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a32e1-106">In This Section</span></span>  
 [<span data-ttu-id="a32e1-107">Tryby uwierzytelniania elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a32e1-107">SecurityBindingElement Authentication Modes</span></span>](securitybindingelement-authentication-modes.md)  
 <span data-ttu-id="a32e1-108">Zawiera opis trybów uwierzytelniania, które są możliwe przy użyciu niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="a32e1-108">Describes the authentication modes that are possible with a custom binding.</span></span>  
  
 [<span data-ttu-id="a32e1-109">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a32e1-109">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 <span data-ttu-id="a32e1-110">Opisuje podstawowe kroki tworzenia powiązania niestandardowego z elementem zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="a32e1-110">Describes the basic steps for creating a custom binding with a security element.</span></span>  
  
 [<span data-ttu-id="a32e1-111">Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="a32e1-111">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)  
 <span data-ttu-id="a32e1-112">Opisuje sposób tworzenia elementu zabezpieczeń dla określonego trybu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a32e1-112">Describes how to create a security element for a specified authentication mode.</span></span>  
  
 [<span data-ttu-id="a32e1-113">Instrukcje: Wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a32e1-113">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="a32e1-114">Opisuje sposób wyłączania bezpiecznych sesji podczas tworzenia usługi federacyjnej.</span><span class="sxs-lookup"><span data-stu-id="a32e1-114">Describes how to disable secure sessions when creating a federation service.</span></span>  
  
 [<span data-ttu-id="a32e1-115">Instrukcje: Włączanie wykrywania powtarzania komunikatu</span><span class="sxs-lookup"><span data-stu-id="a32e1-115">How to: Enable Message Replay Detection</span></span>](how-to-enable-message-replay-detection.md)  
 <span data-ttu-id="a32e1-116">Opisuje sposób określania, kiedy występuje atak powtarzający się.</span><span class="sxs-lookup"><span data-stu-id="a32e1-116">Describes how to determine when a replay attack occurs.</span></span>  
  
 [<span data-ttu-id="a32e1-117">Instrukcje: tworzenie poświadczeń pomocniczych</span><span class="sxs-lookup"><span data-stu-id="a32e1-117">How to: Create a Supporting Credential</span></span>](how-to-create-a-supporting-credential.md)  
 <span data-ttu-id="a32e1-118">Zawiera opis sposobu dostarczania poświadczenie pomocnicze do usługi, jeśli jest to wymagane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="a32e1-118">Describes how to supply a supporting credential to a service, if the service requires it.</span></span>  
  
 [<span data-ttu-id="a32e1-119">Instrukcje: konfigurowanie potwierdzenia sygnatury</span><span class="sxs-lookup"><span data-stu-id="a32e1-119">How to: Set Up a Signature Confirmation</span></span>](how-to-set-up-a-signature-confirmation.md)  
 <span data-ttu-id="a32e1-120">W tym artykule opisano kroki umożliwiające potwierdzenie podpisów podczas cyfrowego podpisywania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a32e1-120">Describes the steps to confirm signatures when digitally signing messages.</span></span>  
  
 [<span data-ttu-id="a32e1-121">Instrukcje: ustawianie maksymalnego przesunięcia czasowego zegara</span><span class="sxs-lookup"><span data-stu-id="a32e1-121">How to: Set a Max Clock Skew</span></span>](how-to-set-a-max-clock-skew.md)  
 <span data-ttu-id="a32e1-122">Opisuje sposób ustawienia maksymalnej dozwolonej różnicy czasu między usługą a klientem.</span><span class="sxs-lookup"><span data-stu-id="a32e1-122">Describes how to set the maximum allowed time difference between a service and a client.</span></span>  
  
 [<span data-ttu-id="a32e1-123">Instrukcje: wyłączanie szyfrowania podpisów cyfrowych</span><span class="sxs-lookup"><span data-stu-id="a32e1-123">How to: Disable Encryption of Digital Signatures</span></span>](how-to-disable-encryption-of-digital-signatures.md)  
 <span data-ttu-id="a32e1-124">Opisuje, jak wyłączenie szyfrowania podpisów cyfrowych może przynieść korzyści z wydajności.</span><span class="sxs-lookup"><span data-stu-id="a32e1-124">Describes how disabling encryption of digital signatures can have a performance benefit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a32e1-125">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="a32e1-125">Reference</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>  
  
 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md)  
  
## <a name="related-sections"></a><span data-ttu-id="a32e1-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a32e1-126">Related Sections</span></span>  
 [<span data-ttu-id="a32e1-127">Omówienie poziomów ochrony</span><span class="sxs-lookup"><span data-stu-id="a32e1-127">Understanding Protection Level</span></span>](../understanding-protection-level.md)  
  
 [<span data-ttu-id="a32e1-128">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="a32e1-128">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="a32e1-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a32e1-129">See also</span></span>

- [<span data-ttu-id="a32e1-130">Wiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="a32e1-130">Bindings and Security</span></span>](bindings-and-security.md)
- [<span data-ttu-id="a32e1-131">Przegląd zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="a32e1-131">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="a32e1-132">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="a32e1-132">System-Provided Bindings</span></span>](../system-provided-bindings.md)
