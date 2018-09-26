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
author: BrucePerlerMS
ms.openlocfilehash: e81469f5ac55b1c698dc99af0782dbdedab33339
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205128"
---
# <a name="how-to-disable-secure-sessions-on-a-wsfederationhttpbinding"></a><span data-ttu-id="f4fd1-102">Instrukcje: Wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f4fd1-102">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>
<span data-ttu-id="f4fd1-103">Niektóre usługi może wymagać poświadczeń federacyjnych, ale nie obsługują bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="f4fd1-103">Some services may require federated credentials but not support secure sessions.</span></span> <span data-ttu-id="f4fd1-104">W takiej sytuacji należy wyłączyć funkcję bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="f4fd1-104">In that case, you must disable the secure session feature.</span></span> <span data-ttu-id="f4fd1-105">W odróżnieniu od <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, <xref:System.ServiceModel.WSFederationHttpBinding> klasa nie umożliwia wyłączanie bezpiecznej sesji podczas komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="f4fd1-105">Unlike the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>, the <xref:System.ServiceModel.WSFederationHttpBinding> class does not provide a way to disable secure sessions when communicating with a service.</span></span> <span data-ttu-id="f4fd1-106">Zamiast tego należy utworzyć niestandardowego powiązania, który zastępuje ustawienia bezpiecznej sesji za pomocą narzędzi bootstrap.</span><span class="sxs-lookup"><span data-stu-id="f4fd1-106">Instead, you must create a custom binding that replaces the secure session settings with a bootstrap.</span></span>  
  
 <span data-ttu-id="f4fd1-107">W tym temacie przedstawiono sposób modyfikowania elementów wiązania zawartych w <xref:System.ServiceModel.WSFederationHttpBinding> do tworzenia niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="f4fd1-107">This topic demonstrates how to modify the binding elements contained within a <xref:System.ServiceModel.WSFederationHttpBinding> to create a custom binding.</span></span> <span data-ttu-id="f4fd1-108">Wynik jest taka sama jak <xref:System.ServiceModel.WSFederationHttpBinding> z tą różnicą, że nie używa bezpiecznych sesji.</span><span class="sxs-lookup"><span data-stu-id="f4fd1-108">The result is identical to the <xref:System.ServiceModel.WSFederationHttpBinding> except that it does not use secure sessions.</span></span>  
  
### <a name="to-create-a-custom-federated-binding-without-secure-session"></a><span data-ttu-id="f4fd1-109">Aby utworzyć niestandardową federacyjnego powiązania bez bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="f4fd1-109">To create a custom federated binding without secure session</span></span>  
  
1.  <span data-ttu-id="f4fd1-110">Utwórz wystąpienie obiektu <xref:System.ServiceModel.WSFederationHttpBinding> klasy obowiązkowo w kodzie lub przez załadowanie go z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f4fd1-110">Create an instance of the <xref:System.ServiceModel.WSFederationHttpBinding> class either imperatively in code or by loading one from the configuration file.</span></span>  
  
2.  <span data-ttu-id="f4fd1-111">Klonuj <xref:System.ServiceModel.WSFederationHttpBinding> do <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="f4fd1-111">Clone the <xref:System.ServiceModel.WSFederationHttpBinding> into a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
3.  <span data-ttu-id="f4fd1-112">Znajdź <xref:System.ServiceModel.Channels.SecurityBindingElement> w <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="f4fd1-112">Find the <xref:System.ServiceModel.Channels.SecurityBindingElement> in the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
4.  <span data-ttu-id="f4fd1-113">Znajdź <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> w <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="f4fd1-113">Find the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters> in the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
5.  <span data-ttu-id="f4fd1-114">Zastąp oryginalny <xref:System.ServiceModel.Channels.SecurityBindingElement> przy użyciu elementu powiązania zabezpieczeń dla uruchamiania z <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="f4fd1-114">Replace the original <xref:System.ServiceModel.Channels.SecurityBindingElement> with the bootstrap security binding element from the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4fd1-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="f4fd1-115">Example</span></span>  
 <span data-ttu-id="f4fd1-116">Ten poniższy przykład obejmuje tworzenie niestandardowego powiązania federacyjnego bez bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="f4fd1-116">This following example creates a custom federated binding without secure session.</span></span>  
  
 [!code-csharp[c_CustomFederationBinding#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customfederationbinding/cs/c_customfederationbinding.cs#0)]
 [!code-vb[c_CustomFederationBinding#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customfederationbinding/vb/c_customfederationbinding.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f4fd1-117">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f4fd1-117">Compiling the Code</span></span>  
  
-   <span data-ttu-id="f4fd1-118">Aby skompilować przykład kodu, Utwórz projekt, który odwołuje się do zestawu System.ServiceModel.dll.</span><span class="sxs-lookup"><span data-stu-id="f4fd1-118">To compile the code example, create a project that references the System.ServiceModel.dll assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4fd1-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4fd1-119">See Also</span></span>  
 [<span data-ttu-id="f4fd1-120">Powiązania i zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="f4fd1-120">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)
