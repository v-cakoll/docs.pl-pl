---
title: 'Instrukcje: Wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
ms.openlocfilehash: df057d64feb89d1e43b938b36cb48f2f103b17d0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595391"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="3a26c-102">Instrukcje: Wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="3a26c-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>

<span data-ttu-id="3a26c-103">Niektóre usługi mogą wymagać poświadczeń federacyjnych, ale nie obsługują bezpiecznych sesji.</span><span class="sxs-lookup"><span data-stu-id="3a26c-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="3a26c-104">W takim przypadku należy wyłączyć funkcję bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="3a26c-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="3a26c-105">W przeciwieństwie do <xref:System.ServiceModel.WSHttpBinding> klasy, Klasa nie pozwala <xref:System.ServiceModel.WSFederationHttpBinding> na wyłączenie bezpiecznych sesji podczas komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="3a26c-105">Unlike the <xref:System.ServiceModel.WSHttpBinding>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="3a26c-106">Zamiast tego należy utworzyć niestandardowe powiązanie, które zastępuje ustawienia bezpiecznej sesji przy użyciu Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="3a26c-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>

<span data-ttu-id="3a26c-107">W tym temacie pokazano, jak modyfikować elementy powiązania zawarte w elemencie w <xref:System.ServiceModel.WSFederationHttpBinding> celu utworzenia niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3a26c-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="3a26c-108">Wynik jest identyczny z <xref:System.ServiceModel.WSFederationHttpBinding> tą różnicą, że nie używa bezpiecznych sesji.</span><span class="sxs-lookup"><span data-stu-id="3a26c-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="3a26c-109">Aby utworzyć niestandardowe powiązanie federacyjne bez bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="3a26c-109">To create a custom federated binding without secure session</span></span>

1. <span data-ttu-id="3a26c-110">Utwórz wystąpienie klasy jako bezwzględnie <xref:System.ServiceModel.WSFederationHttpBinding> w kodzie lub przez załadowanie jednego z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3a26c-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>

2. <span data-ttu-id="3a26c-111">Klonowanie <xref:System.ServiceModel.WSFederationHttpBinding> do <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="3a26c-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

3. <span data-ttu-id="3a26c-112">Znajdź <xref:System.ServiceModel.Channels.SecurityBindingElement> w <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="3a26c-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

4. <span data-ttu-id="3a26c-113">Znajdź <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> w <xref:System.ServiceModel.Channels.SecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="3a26c-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>

5. <span data-ttu-id="3a26c-114">Zastąp oryginał <xref:System.ServiceModel.Channels.SecurityBindingElement> elementem powiązania zabezpieczeń Bootstrap z <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> .</span><span class="sxs-lookup"><span data-stu-id="3a26c-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>

## <a name="example"></a><span data-ttu-id="3a26c-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a26c-115">Example</span></span>

<span data-ttu-id="3a26c-116">Poniższy przykład powoduje utworzenie niestandardowego powiązania federacyjnego bez bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="3a26c-116">This following example creates a custom federated binding without secure session.</span></span>

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="3a26c-117">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3a26c-117">Compiling the Code</span></span>

- <span data-ttu-id="3a26c-118">Aby skompilować przykład kodu, Utwórz projekt, który odwołuje się do zestawu System. ServiceModel. dll.</span><span class="sxs-lookup"><span data-stu-id="3a26c-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a26c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a26c-119">See also</span></span>

- [<span data-ttu-id="3a26c-120">Wiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="3a26c-120">Bindings and Security</span></span>](bindings-and-security.md)
