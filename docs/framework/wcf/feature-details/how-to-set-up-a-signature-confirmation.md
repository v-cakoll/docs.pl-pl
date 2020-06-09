---
title: 'Instrukcje: Konfigurowanie potwierdzenia sygnatury'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 9423922753efee7aac32e430f97307c715e43464
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586926"
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="47f6a-102">Instrukcje: Konfigurowanie potwierdzenia sygnatury</span><span class="sxs-lookup"><span data-stu-id="47f6a-102">How to: Set Up a Signature Confirmation</span></span>

<span data-ttu-id="47f6a-103">*Potwierdzenie podpisu* jest mechanizmem inicjatora komunikatów w celu upewnienia się, że odebrana odpowiedź została wygenerowana w odpowiedzi na oryginalny komunikat nadawcy.</span><span class="sxs-lookup"><span data-stu-id="47f6a-103">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="47f6a-104">Potwierdzenie podpisu jest zdefiniowane w specyfikacji WS-Security 1,1.</span><span class="sxs-lookup"><span data-stu-id="47f6a-104">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="47f6a-105">Jeśli punkt końcowy obsługuje WS-Security 1,0, nie można użyć potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="47f6a-105">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>

<span data-ttu-id="47f6a-106">Poniższe procedury określają, jak włączyć potwierdzenie podpisu przy użyciu <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="47f6a-106">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="47f6a-107">Tej samej procedury można użyć z <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="47f6a-107">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="47f6a-108">Procedura ta kompiluje się z podstawowymi krokami opisanymi w [instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="47f6a-108">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="47f6a-109">Aby włączyć potwierdzenie podpisu w kodzie</span><span class="sxs-lookup"><span data-stu-id="47f6a-109">To enable signature confirmation in code</span></span>

1. <span data-ttu-id="47f6a-110">Utworzenie wystąpienia <xref:System.ServiceModel.Channels.BindingElementCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="47f6a-110">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>

2. <span data-ttu-id="47f6a-111">Utwórz wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="47f6a-111">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>

3. <span data-ttu-id="47f6a-112">Ustaw wartość <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> na `true` .</span><span class="sxs-lookup"><span data-stu-id="47f6a-112">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>

4. <span data-ttu-id="47f6a-113">Dodaj element zabezpieczeń do kolekcji powiązań.</span><span class="sxs-lookup"><span data-stu-id="47f6a-113">Add the security element to the binding collection.</span></span>

5. <span data-ttu-id="47f6a-114">Utwórz niestandardowe powiązanie, zgodnie z opisem w [instrukcje: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="47f6a-114">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="47f6a-115">Aby włączyć potwierdzenie podpisu w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="47f6a-115">To enable signature confirmation in configuration</span></span>

1. <span data-ttu-id="47f6a-116">Dodaj `<customBinding>` element do sekcji w `<bindings>` pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="47f6a-116">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>

2. <span data-ttu-id="47f6a-117">Dodaj `<binding>` element i ustaw odpowiednią wartość atrybutu Name.</span><span class="sxs-lookup"><span data-stu-id="47f6a-117">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>

3. <span data-ttu-id="47f6a-118">Dodaj odpowiedni element kodowania.</span><span class="sxs-lookup"><span data-stu-id="47f6a-118">Add an appropriate encoding element.</span></span> <span data-ttu-id="47f6a-119">Poniższy przykład dodaje `<TextMessageEncoding>` element.</span><span class="sxs-lookup"><span data-stu-id="47f6a-119">The following example adds a `<TextMessageEncoding>` element.</span></span>

4. <span data-ttu-id="47f6a-120">Dodaj `<security>` element podrzędny i ustaw `requireSignatureConfirmation` atrybut na `true` .</span><span class="sxs-lookup"><span data-stu-id="47f6a-120">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>

5. <span data-ttu-id="47f6a-121">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="47f6a-121">Optional.</span></span> <span data-ttu-id="47f6a-122">Aby włączyć potwierdzenie podpisu podczas ładowania, należy dodać [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element podrzędny i ustawić `requireSignatureConfirmation` atrybut na `true` .</span><span class="sxs-lookup"><span data-stu-id="47f6a-122">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>

6. <span data-ttu-id="47f6a-123">Dodaj odpowiedni element transportowy.</span><span class="sxs-lookup"><span data-stu-id="47f6a-123">Add an appropriate transport element.</span></span> <span data-ttu-id="47f6a-124">Poniższy przykład dodaje [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) :</span><span class="sxs-lookup"><span data-stu-id="47f6a-124">The following example adds an [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md):</span></span>

    ```xml
    <bindings>
      <customBinding>
        <binding name="SignatureConfirmationBinding">
          <security requireSignatureConfirmation="true">
            <secureConversationBootstrap requireSignatureConfirmation="true" />
              </security>
           <textMessageEncoding />
             <httpTransport />
        </binding>
      </customBinding>
    </bindings>
    ```

## <a name="example"></a><span data-ttu-id="47f6a-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="47f6a-125">Example</span></span>

<span data-ttu-id="47f6a-126">Poniższy kod tworzy wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i ustawia <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> Właściwość na `true` .</span><span class="sxs-lookup"><span data-stu-id="47f6a-126">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="47f6a-127">Należy zauważyć, że w tym przykładzie nie jest używany `<secureConversationBootstrap>` element przedstawiony w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="47f6a-127">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="47f6a-128">Ten przykład ilustruje potwierdzenie podpisu w przypadku korzystania z tokenu systemu Windows (protokół Kerberos).</span><span class="sxs-lookup"><span data-stu-id="47f6a-128">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="47f6a-129">W takim przypadku podpis klienta jest zwracany we wszystkich odpowiedziach usługi i zostaje potwierdzony przez klienta.</span><span class="sxs-lookup"><span data-stu-id="47f6a-129">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>

[!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
[!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]

## <a name="see-also"></a><span data-ttu-id="47f6a-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47f6a-130">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [<span data-ttu-id="47f6a-131">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="47f6a-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="47f6a-132">Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="47f6a-132">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
