---
title: "Instrukcje: Wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding"
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
- WCF, federation
- federation
ms.assetid: 675fa143-6a4e-4be3-8afc-673334ab55ec
caps.latest.revision: "16"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: bb2970209814fbbee9f71f0263a4d3d4f02f3e20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="993e8-102">Instrukcje: Wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="993e8-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>
<span data-ttu-id="993e8-103">Niektóre usługi mogą wymagają poświadczeń federacyjnych, ale nie obsługują bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="993e8-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="993e8-104">W takim przypadku należy wyłączyć funkcję bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="993e8-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="993e8-105">W odróżnieniu od <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, <xref:System.ServiceModel.WSFederationHttpBinding> klasa nie zapewnia możliwość wyłączenia bezpiecznej sesji podczas komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="993e8-105">Unlike the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="993e8-106">Zamiast tego należy utworzyć niestandardowego powiązania, który zastępuje ładowania początkowego ustawienia bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="993e8-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>  
  
 <span data-ttu-id="993e8-107">W tym temacie przedstawiono sposób modyfikowania elementów wiązania zawartych w <xref:System.ServiceModel.WSFederationHttpBinding> do tworzenia niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="993e8-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="993e8-108">Wynik jest taki sam jak <xref:System.ServiceModel.WSFederationHttpBinding> z tą różnicą, że nie używa bezpiecznych sesji.</span><span class="sxs-lookup"><span data-stu-id="993e8-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="993e8-109">Aby utworzyć niestandardowy federacyjnych powiązania bez bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="993e8-109">To create a custom federated binding without secure session</span></span>  
  
1.  <span data-ttu-id="993e8-110">Utwórz wystąpienie <xref:System.ServiceModel.WSFederationHttpBinding> klasy imperatively w kodzie lub przez załadowanie go z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="993e8-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>  
  
2.  <span data-ttu-id="993e8-111">Klonowanie <xref:System.ServiceModel.WSFederationHttpBinding> do <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="993e8-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
3.  <span data-ttu-id="993e8-112">Znajdź <xref:System.ServiceModel.Channels.SecurityBindingElement> w <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="993e8-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
4.  <span data-ttu-id="993e8-113">Znajdź <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> w <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="993e8-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
5.  <span data-ttu-id="993e8-114">Zastąp oryginalny <xref:System.ServiceModel.Channels.SecurityBindingElement> z elementu powiązania zabezpieczeń ładowania początkowego z <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="993e8-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="993e8-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e8-115">Example</span></span>  
 <span data-ttu-id="993e8-116">Poniższy przykład tworzy niestandardowego powiązania federacyjnego bez bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="993e8-116">This following example creates a custom federated binding without secure session.</span></span>  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="993e8-117">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="993e8-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="993e8-118">Aby skompilować przykładów kodu, należy utworzyć projekt, który odwołuje się do zestawu System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="993e8-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="993e8-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="993e8-119">See Also</span></span>  
 [<span data-ttu-id="993e8-120">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="993e8-120">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
