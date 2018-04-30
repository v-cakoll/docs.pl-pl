---
title: Szyfrowanie podpisów cyfrowych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 630465367eb4cee164a222bb5449070ac0726d5e
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="encryption-of-digital-signatures"></a><span data-ttu-id="7a31b-102">Szyfrowanie podpisów cyfrowych</span><span class="sxs-lookup"><span data-stu-id="7a31b-102">Encryption of Digital Signatures</span></span>
<span data-ttu-id="7a31b-103">Domyślnie komunikat jest podpisane i zaszyfrowane i podpisu cyfrowego jest zaszyfrowany.</span><span class="sxs-lookup"><span data-stu-id="7a31b-103">By default, a message is signed and encrypted, and the signature is digitally encrypted.</span></span> <span data-ttu-id="7a31b-104">Można to kontrolowane przez utworzenie niestandardowego powiązania z wystąpieniem <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> lub <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> , a następnie ustawienie `MessageProtectionOrder` właściwości każdej klasy do <xref:System.ServiceModel.Security.MessageProtectionOrder> wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7a31b-104">You can control this by creating a custom binding with an instance of the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> or the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and then setting the `MessageProtectionOrder` property of either class to a <xref:System.ServiceModel.Security.MessageProtectionOrder> enumeration value.</span></span> <span data-ttu-id="7a31b-105">Wartość domyślna to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>.</span><span class="sxs-lookup"><span data-stu-id="7a31b-105">The default is <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>.</span></span> <span data-ttu-id="7a31b-106">Ten proces trwa dłużej niż zwykłe podpisywania i szyfrowania 10 do 40 procent.</span><span class="sxs-lookup"><span data-stu-id="7a31b-106">This process takes 10 to 40 percent longer than simply signing and encrypting.</span></span> <span data-ttu-id="7a31b-107">Wyłączenie szyfrowania podpisu, jednak osoba atakująca może mieć odgadnąć treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7a31b-107">Disabling encryption of the signature, however, might allow an attacker to guess the contents of the message.</span></span> <span data-ttu-id="7a31b-108">Jest to możliwe, ponieważ wartość skrótu zwykły tekst każdej części podpisanych wiadomości zawiera element podpisu.</span><span class="sxs-lookup"><span data-stu-id="7a31b-108">This is possible because the signature element contains the hash code of the plain text of every signed part in the message.</span></span> <span data-ttu-id="7a31b-109">Mimo że treść komunikatu jest domyślnie szyfrowane, niezaszyfrowane podpis zawiera skrótu treści wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7a31b-109">For example, although the message body is encrypted by default, the unencrypted signature contains the hash code of the message body.</span></span> <span data-ttu-id="7a31b-110">Jeśli komunikat jest mały, osoba atakująca może mieć możliwość wywnioskować zawartość.</span><span class="sxs-lookup"><span data-stu-id="7a31b-110">If the message is small, an attacker might be able to deduce the contents.</span></span> <span data-ttu-id="7a31b-111">Szyfrowanie podpis ograniczyć lub eliminuje tej możliwości.</span><span class="sxs-lookup"><span data-stu-id="7a31b-111">Encrypting the signature reduces or eliminates this possibility.</span></span>  
  
 <span data-ttu-id="7a31b-112">Dlatego należy wyłączyć szyfrowanie podpisu, tylko wtedy, gdy wartość zawartości jest niski i bardziej wydajne będzie istotne, na przykład podczas wysyłania dużych plików binarnych, które mają wpływ na bezpieczeństwo.</span><span class="sxs-lookup"><span data-stu-id="7a31b-112">Therefore, disable encryption of the signature only when the value of the content is low, and the performance gain will be significant, for example, when sending large binary files that have no security implications.</span></span>  
  
### <a name="to-disable-digital-signing"></a><span data-ttu-id="7a31b-113">Aby wyłączyć podpisów cyfrowych</span><span class="sxs-lookup"><span data-stu-id="7a31b-113">To disable digital signing</span></span>  
  
1.  <span data-ttu-id="7a31b-114">Utwórz <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="7a31b-114">Create a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="7a31b-115">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie niestandardowego powiązania przy użyciu elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="7a31b-115">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
2.  <span data-ttu-id="7a31b-116">Dodaj albo <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> lub <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> do kolekcji powiązania.</span><span class="sxs-lookup"><span data-stu-id="7a31b-116">Add either an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> or a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> to the binding collection.</span></span>  
  
3.  <span data-ttu-id="7a31b-117">Ustaw <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, lub ustaw <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> właściwości <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.</span><span class="sxs-lookup"><span data-stu-id="7a31b-117">Set the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> property to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, or set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> property to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.</span></span>  
  
 <span data-ttu-id="7a31b-118">Aby uzyskać więcej informacji o tworzeniu niestandardowych powiązań, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="7a31b-118">For more information about creating custom bindings, see [Creating User-Defined Bindings](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).</span></span> <span data-ttu-id="7a31b-119">Aby uzyskać więcej informacji na temat tworzenia niestandardowego powiązania dla trybu uwierzytelniania określonych zobacz [porady: Tworzenie elementu SecurityBindingElement dla trybu uwierzytelniania określone](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).</span><span class="sxs-lookup"><span data-stu-id="7a31b-119">For more information about creating a custom binding for a specific authentication mode, see [How to: Create a SecurityBindingElement for a Specified Authentication Mode](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a31b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a31b-120">See Also</span></span>  
 <xref:System.ServiceModel.Security.MessageProtectionOrder>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 [<span data-ttu-id="7a31b-121">Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="7a31b-121">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="7a31b-122">Tworzenie powiązań zdefiniowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="7a31b-122">Creating User-Defined Bindings</span></span>](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)  
 [<span data-ttu-id="7a31b-123">Instrukcje: tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania</span><span class="sxs-lookup"><span data-stu-id="7a31b-123">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
