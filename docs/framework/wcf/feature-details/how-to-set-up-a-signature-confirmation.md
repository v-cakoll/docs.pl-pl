---
title: 'Instrukcje: Konfigurowanie potwierdzenia sygnatury'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1cf2048a630b3556291577565bed47c40665b156
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="2b05f-102">Instrukcje: Konfigurowanie potwierdzenia sygnatury</span><span class="sxs-lookup"><span data-stu-id="2b05f-102">How to: Set Up a Signature Confirmation</span></span>
<span data-ttu-id="2b05f-103">*Potwierdzenie podpisu* jest mechanizm inicjatora komunikat upewnić się, że odebranej odpowiedzi został wygenerowany w odpowiedzi na nadawcy oryginalnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2b05f-103">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="2b05f-104">Potwierdzenie podpisu jest zdefiniowany w specyfikacji WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="2b05f-104">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="2b05f-105">Jeśli punkt końcowy obsługuje WS-Security 1.0, nie można użyć potwierdzenia podpisu.</span><span class="sxs-lookup"><span data-stu-id="2b05f-105">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>  
  
 <span data-ttu-id="2b05f-106">Poniższe procedury Określ sposób włączania potwierdzenie podpisu przy użyciu <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="2b05f-106">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="2b05f-107">Korzystając z tej samej procedury <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="2b05f-107">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="2b05f-108">Procedura bazując na podstawowe kroki w [jak: utworzyć niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="2b05f-108">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="2b05f-109">Aby włączyć potwierdzenia podpisu w kodzie</span><span class="sxs-lookup"><span data-stu-id="2b05f-109">To enable signature confirmation in code</span></span>  
  
1.  <span data-ttu-id="2b05f-110">Utworzenie wystąpienia <xref:System.ServiceModel.Channels.BindingElementCollection> klasy.</span><span class="sxs-lookup"><span data-stu-id="2b05f-110">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>  
  
2.  <span data-ttu-id="2b05f-111">Utwórz wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="2b05f-111">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>  
  
3.  <span data-ttu-id="2b05f-112">Ustaw <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> do `true`.</span><span class="sxs-lookup"><span data-stu-id="2b05f-112">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>  
  
4.  <span data-ttu-id="2b05f-113">Dodaj element zabezpieczeń do kolekcji powiązania.</span><span class="sxs-lookup"><span data-stu-id="2b05f-113">Add the security element to the binding collection.</span></span>  
  
5.  <span data-ttu-id="2b05f-114">Tworzenie niestandardowego powiązania, jak określono w [porady: Tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="2b05f-114">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="2b05f-115">Aby włączyć potwierdzenia podpisu w konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2b05f-115">To enable signature confirmation in configuration</span></span>  
  
1.  <span data-ttu-id="2b05f-116">Dodaj `<customBinding>` elementu `<bindings>` sekcji pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2b05f-116">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>  
  
2.  <span data-ttu-id="2b05f-117">Dodaj `<binding>` element i ustaw nazwę atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="2b05f-117">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="2b05f-118">Dodaj odpowiedni element kodowania.</span><span class="sxs-lookup"><span data-stu-id="2b05f-118">Add an appropriate encoding element.</span></span> <span data-ttu-id="2b05f-119">W poniższym przykładzie dodano `<TextMessageEncoding>` elementu.</span><span class="sxs-lookup"><span data-stu-id="2b05f-119">The following example adds a `<TextMessageEncoding>` element.</span></span>  
  
4.  <span data-ttu-id="2b05f-120">Dodaj `<security>` element podrzędny i zestaw `requireSignatureConfirmation` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="2b05f-120">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>  
  
5.  <span data-ttu-id="2b05f-121">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="2b05f-121">Optional.</span></span> <span data-ttu-id="2b05f-122">Aby włączyć potwierdzenia podpisu podczas ładowania początkowego programu, Dodaj [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element podrzędny i zestaw `equireSignatureConfirmation` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="2b05f-122">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `equireSignatureConfirmation` attribute to `true`.</span></span>  
  
6.  <span data-ttu-id="2b05f-123">Dodaj element odpowiednie transportu.</span><span class="sxs-lookup"><span data-stu-id="2b05f-123">Add an appropriate transport element.</span></span> <span data-ttu-id="2b05f-124">W poniższym przykładzie dodano [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span><span class="sxs-lookup"><span data-stu-id="2b05f-124">The following example adds an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="2b05f-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="2b05f-125">Example</span></span>  
 <span data-ttu-id="2b05f-126">Poniższy kod tworzy wystąpienie <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> i ustawia <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="2b05f-126">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="2b05f-127">Należy pamiętać, że w tym przykładzie nie używa `<secureConversationBootstrap>` elementu w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2b05f-127">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="2b05f-128">W przykładzie pokazano potwierdzenia podpisu, korzystając z tokenu systemu Windows (protokołu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="2b05f-128">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="2b05f-129">W takim przypadku podpisu klienta jest zwracany w odpowiedzi wszystkie usługi i został potwierdzony przez klienta.</span><span class="sxs-lookup"><span data-stu-id="2b05f-129">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2b05f-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b05f-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>  
 [<span data-ttu-id="2b05f-131">Porady: Tworzenie niestandardowego wiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2b05f-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="2b05f-132">Porady: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="2b05f-132">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
