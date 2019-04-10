---
title: 'Instrukcje: konfigurowanie potwierdzenia sygnatury'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 56e8720a6130d2908fbfb83bd243a54fae9a2406
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315819"
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="1c205-102">Instrukcje: konfigurowanie potwierdzenia sygnatury</span><span class="sxs-lookup"><span data-stu-id="1c205-102">How to: Set Up a Signature Confirmation</span></span>
<span data-ttu-id="1c205-103">*Potwierdzenie podpisu* jest mechanizm dla inicjatora wiadomości upewnić się, czy odebrano odpowiedź został wygenerowany w odpowiedzi na pierwotny komunikat nadawcy.</span><span class="sxs-lookup"><span data-stu-id="1c205-103">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="1c205-104">Potwierdzenie podpisu jest zdefiniowana w specyfikacji WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="1c205-104">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="1c205-105">Jeśli punkt końcowy obsługuje WS-Security w wersji 1.0, nie można użyć potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="1c205-105">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>  
  
 <span data-ttu-id="1c205-106">Poniższych procedur Określ sposób umożliwić używanie potwierdzenia podpisu <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="1c205-106">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="1c205-107">Można użyć tej samej procedury z <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="1c205-107">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="1c205-108">Procedura opiera się na podstawowe czynności opisane w [jak: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="1c205-108">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="1c205-109">Aby włączyć potwierdzenia podpisu w kodzie</span><span class="sxs-lookup"><span data-stu-id="1c205-109">To enable signature confirmation in code</span></span>  
  
1. <span data-ttu-id="1c205-110">Utworzenie wystąpienia <xref:System.ServiceModel.Channels.BindingElementCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="1c205-110">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>  
  
2. <span data-ttu-id="1c205-111">Utwórz wystąpienie obiektu <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="1c205-111">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>  
  
3. <span data-ttu-id="1c205-112">Ustaw <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> do `true`.</span><span class="sxs-lookup"><span data-stu-id="1c205-112">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>  
  
4. <span data-ttu-id="1c205-113">Dodaj element zabezpieczeń do kolekcji powiązania.</span><span class="sxs-lookup"><span data-stu-id="1c205-113">Add the security element to the binding collection.</span></span>  
  
5. <span data-ttu-id="1c205-114">Tworzenie niestandardowego powiązania, jak to określono w [jak: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="1c205-114">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="1c205-115">Aby włączyć potwierdzenia podpisu w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1c205-115">To enable signature confirmation in configuration</span></span>  
  
1. <span data-ttu-id="1c205-116">Dodaj `<customBinding>` elementu `<bindings>` sekcję pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1c205-116">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>  
  
2. <span data-ttu-id="1c205-117">Dodaj `<binding>` element i ustaw nazwę atrybutu do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="1c205-117">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="1c205-118">Dodaj odpowiedni element kodowania.</span><span class="sxs-lookup"><span data-stu-id="1c205-118">Add an appropriate encoding element.</span></span> <span data-ttu-id="1c205-119">W poniższym przykładzie dodano `<TextMessageEncoding>` elementu.</span><span class="sxs-lookup"><span data-stu-id="1c205-119">The following example adds a `<TextMessageEncoding>` element.</span></span>  
  
4. <span data-ttu-id="1c205-120">Dodaj `<security>` element podrzędny i ustaw `requireSignatureConfirmation` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="1c205-120">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>  
  
5. <span data-ttu-id="1c205-121">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1c205-121">Optional.</span></span> <span data-ttu-id="1c205-122">Aby włączyć potwierdzenia podpisu podczas uruchamiania, należy dodać [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element podrzędny i ustaw `equireSignatureConfirmation` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="1c205-122">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `equireSignatureConfirmation` attribute to `true`.</span></span>  
  
6. <span data-ttu-id="1c205-123">Dodaj element odpowiednie transportu.</span><span class="sxs-lookup"><span data-stu-id="1c205-123">Add an appropriate transport element.</span></span> <span data-ttu-id="1c205-124">W poniższym przykładzie dodano [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span><span class="sxs-lookup"><span data-stu-id="1c205-124">The following example adds an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="1c205-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c205-125">Example</span></span>  
 <span data-ttu-id="1c205-126">Poniższy kod tworzy wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i ustawia <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="1c205-126">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="1c205-127">Należy zauważyć, że w tym przykładzie nie używa `<secureConversationBootstrap>` widocznego w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1c205-127">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="1c205-128">W przykładzie pokazano potwierdzenia podpisu, używając tokenu Windows (protokół Kerberos).</span><span class="sxs-lookup"><span data-stu-id="1c205-128">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="1c205-129">W takim przypadku podpis klienta jest zwracany w odpowiedzi na wszystkie usługi i został potwierdzony przez klienta.</span><span class="sxs-lookup"><span data-stu-id="1c205-129">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1c205-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c205-130">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [<span data-ttu-id="1c205-131">Instrukcje: tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="1c205-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="1c205-132">Instrukcje: tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="1c205-132">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
