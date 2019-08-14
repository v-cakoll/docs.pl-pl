---
title: 'Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
ms.openlocfilehash: 810c5b127a34fb0a35e8fd2d83ff59e00aca0ba1
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972046"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="0d96b-102">Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0d96b-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>

<span data-ttu-id="0d96b-103">Niektóre usługi mogą wymagać poświadczeń federacyjnych, ale nie obsługują bezpiecznych sesji.</span><span class="sxs-lookup"><span data-stu-id="0d96b-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="0d96b-104">W takim przypadku należy wyłączyć funkcję bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="0d96b-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="0d96b-105">W przeciwieństwie <xref:System.ServiceModel.WSHttpBinding>do <xref:System.ServiceModel.WSFederationHttpBinding> klasy, Klasa nie pozwala na wyłączenie bezpiecznych sesji podczas komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="0d96b-105">Unlike the <xref:System.ServiceModel.WSHttpBinding>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="0d96b-106">Zamiast tego należy utworzyć niestandardowe powiązanie, które zastępuje ustawienia bezpiecznej sesji przy użyciu Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="0d96b-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>

<span data-ttu-id="0d96b-107">W tym temacie pokazano, jak modyfikować elementy powiązania zawarte w elemencie <xref:System.ServiceModel.WSFederationHttpBinding> w celu utworzenia niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="0d96b-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="0d96b-108">Wynik jest identyczny <xref:System.ServiceModel.WSFederationHttpBinding> z tą różnicą, że nie używa bezpiecznych sesji.</span><span class="sxs-lookup"><span data-stu-id="0d96b-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>

## <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="0d96b-109">Aby utworzyć niestandardowe powiązanie federacyjne bez bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="0d96b-109">To create a custom federated binding without secure session</span></span>

1. <span data-ttu-id="0d96b-110">Utwórz wystąpienie <xref:System.ServiceModel.WSFederationHttpBinding> klasy jako bezwzględnie w kodzie lub przez załadowanie jednego z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0d96b-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>

2. <span data-ttu-id="0d96b-111">Klonowanie<xref:System.ServiceModel.Channels.CustomBinding>do <xref:System.ServiceModel.WSFederationHttpBinding> .</span><span class="sxs-lookup"><span data-stu-id="0d96b-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

3. <span data-ttu-id="0d96b-112"><xref:System.ServiceModel.Channels.SecurityBindingElement> Znajdź<xref:System.ServiceModel.Channels.CustomBinding>w.</span><span class="sxs-lookup"><span data-stu-id="0d96b-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>

4. <span data-ttu-id="0d96b-113"><xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> Znajdź<xref:System.ServiceModel.Channels.SecurityBindingElement>w.</span><span class="sxs-lookup"><span data-stu-id="0d96b-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>

5. <span data-ttu-id="0d96b-114">Zastąp oryginał <xref:System.ServiceModel.Channels.SecurityBindingElement> elementem powiązania zabezpieczeń Bootstrap <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>z.</span><span class="sxs-lookup"><span data-stu-id="0d96b-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>

## <a name="example"></a><span data-ttu-id="0d96b-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d96b-115">Example</span></span>

<span data-ttu-id="0d96b-116">Poniższy przykład powoduje utworzenie niestandardowego powiązania federacyjnego bez bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="0d96b-116">This following example creates a custom federated binding without secure session.</span></span>

[!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
[!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]

## <a name="compiling-the-code"></a><span data-ttu-id="0d96b-117">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0d96b-117">Compiling the Code</span></span>

- <span data-ttu-id="0d96b-118">Aby skompilować przykład kodu, Utwórz projekt, który odwołuje się do zestawu System. ServiceModel. dll.</span><span class="sxs-lookup"><span data-stu-id="0d96b-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d96b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d96b-119">See also</span></span>

- [<span data-ttu-id="0d96b-120">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="0d96b-120">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
