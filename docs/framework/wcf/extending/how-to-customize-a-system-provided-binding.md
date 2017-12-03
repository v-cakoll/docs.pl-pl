---
title: "Porady: dostosowywanie powiązania dostarczane przez System"
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
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c46886879d19d612827b94821e0105c68c437c56
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-customize-a-system-provided-binding"></a><span data-ttu-id="846d2-102">Porady: dostosowywanie powiązania dostarczane przez System</span><span class="sxs-lookup"><span data-stu-id="846d2-102">How to: Customize a System-Provided Binding</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="846d2-103">zawiera kilka powiązania dostarczane przez system, które umożliwiają konfigurowanie niektórych właściwości podstawowych elementów powiązania, ale nie wszystkie właściwości.</span><span class="sxs-lookup"><span data-stu-id="846d2-103"> includes several system-provided bindings that allow you to configure some of the properties of the underlying binding elements, but not all of the properties.</span></span> <span data-ttu-id="846d2-104">W tym temacie przedstawiono sposób ustawiania właściwości do powiązania elementów do tworzenia niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="846d2-104">This topic demonstrates how to set properties on the binding elements to create a custom binding.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="846d2-105">jak bezpośrednio utworzyć i skonfigurować elementy powiązania bez korzystania z wiązania dostarczane przez system, zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="846d2-105"> how to directly create and configure binding elements without using the system-provided bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="846d2-106">Tworzenie i rozszerzanie wiązań niestandardowych, zobacz [rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="846d2-106"> creating and extending custom bindings, see [Extending Bindings](../../../../docs/framework/wcf/extending/extending-bindings.md).</span></span>  
  
 <span data-ttu-id="846d2-107">W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składają się wszystkie powiązania z *elementów wiązania*.</span><span class="sxs-lookup"><span data-stu-id="846d2-107">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] all bindings are made up of *binding elements*.</span></span> <span data-ttu-id="846d2-108">Każdy element powiązania jest pochodną <xref:System.ServiceModel.Channels.BindingElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="846d2-108">Each binding element derives from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="846d2-109">Powiązania dostarczane przez system, takich jak <xref:System.ServiceModel.BasicHttpBinding> utworzyć i skonfigurować własne elementy wiązania.</span><span class="sxs-lookup"><span data-stu-id="846d2-109">System-provided bindings such as <xref:System.ServiceModel.BasicHttpBinding> create and configure their own binding elements.</span></span> <span data-ttu-id="846d2-110">W tym temacie przedstawiono sposób dostępu i zmiana właściwości tych elementów powiązania, które nie są bezpośrednio widoczne dla powiązania; w szczególności <xref:System.ServiceModel.BasicHttpBinding> klasy.</span><span class="sxs-lookup"><span data-stu-id="846d2-110">This topic shows you how to access and change the properties of these binding elements, which are not directly exposed on the binding; specifically, the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="846d2-111">Poszczególne elementy znajdują się w kolekcji reprezentowany przez <xref:System.ServiceModel.Channels.BindingElementCollection> klasy i są dodawane w następującej kolejności: przepływu transakcji, niezawodnej sesji zabezpieczeń, złożone dupleksowy, jednokierunkowe zabezpieczenia strumienia, kodowanie komunikatu i transportu.</span><span class="sxs-lookup"><span data-stu-id="846d2-111">The individual binding elements are contained in a collection represented by the <xref:System.ServiceModel.Channels.BindingElementCollection> class and are added in this order: Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding, and Transport.</span></span> <span data-ttu-id="846d2-112">Należy pamiętać, że nie wszystkie elementy na liście są wymagane w każdym powiązania.</span><span class="sxs-lookup"><span data-stu-id="846d2-112">Note that not all the binding elements listed are required in every binding.</span></span> <span data-ttu-id="846d2-113">Elementy wiązania zdefiniowane przez użytkownika może również zostać wyświetlony w tej kolekcji element powiązania i musi występować w tej samej kolejności, w sposób opisany wcześniej.</span><span class="sxs-lookup"><span data-stu-id="846d2-113">User-defined binding elements can also appear in this binding element collection and must appear in the same order as previously described.</span></span> <span data-ttu-id="846d2-114">Na przykład transportu zdefiniowane przez użytkownika musi być ostatnim elementem kolekcji element powiązania.</span><span class="sxs-lookup"><span data-stu-id="846d2-114">For example, a user-defined transport must be the last element of the binding element collection.</span></span>  
  
 <span data-ttu-id="846d2-115"><xref:System.ServiceModel.BasicHttpBinding> Klasa zawiera trzy elementy powiązania:</span><span class="sxs-lookup"><span data-stu-id="846d2-115">The <xref:System.ServiceModel.BasicHttpBinding> class contains three binding elements:</span></span>  
  
1.  <span data-ttu-id="846d2-116">Opcjonalne zabezpieczeń powiązania elementu, albo <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> klasy używane z transportu HTTP (zabezpieczeniami na poziomie wiadomości) lub <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> klasy, która jest używana podczas warstwy transportowej zawiera zabezpieczeń, w tym przypadku transportu HTTPS jest używany.</span><span class="sxs-lookup"><span data-stu-id="846d2-116">An optional security binding element, either the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> class used with the HTTP transport (message level security) or the <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> class, which is used when the transport layer provides security, in which case the HTTPS transport is used.</span></span>  
  
2.  <span data-ttu-id="846d2-117">Kodera komunikatów wymagane powiązanie elementu, albo <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> lub <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="846d2-117">A required message encoder binding element, either <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> or <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span></span>  
  
3.  <span data-ttu-id="846d2-118">Transport wymagane powiązanie elementu, albo <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, lub <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="846d2-118">A required transport binding element, either <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, or <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span></span>  
  
 <span data-ttu-id="846d2-119">W tym przykładzie mamy utworzyć wystąpienia powiązania, generowanie *niestandardowego powiązania* z niej informacji, sprawdź elementy niestandardowego powiązania, a gdy okaże się element powiązania protokołu HTTP, możemy jego `KeepAliveEnabled` właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="846d2-119">In this example we create an instance of the binding, generate a *custom binding* from it, examine the binding elements in the custom binding, and when we find the HTTP binding element, we set its `KeepAliveEnabled` property to `false`.</span></span> <span data-ttu-id="846d2-120">`KeepAliveEnabled` Właściwość nie jest uwidaczniana bezpośrednio na `BasicHttpBinding`, więc musi utworzyć niestandardowego powiązania, przejdź do elementu powiązania i ustaw dla tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="846d2-120">The `KeepAliveEnabled` property is not exposed directly on the `BasicHttpBinding`, so we must create a custom binding to navigate down to the binding element and set this property.</span></span>  
  
### <a name="to-modify-a-system-provided-binding"></a><span data-ttu-id="846d2-121">Aby zmodyfikować powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="846d2-121">To modify a system-provided binding</span></span>  
  
1.  <span data-ttu-id="846d2-122">Utwórz wystąpienie <xref:System.ServiceModel.BasicHttpBinding> klasy, a jego tryb zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="846d2-122">Create an instance of the <xref:System.ServiceModel.BasicHttpBinding> class and set its security mode to message-level.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  <span data-ttu-id="846d2-123">Tworzenie niestandardowego powiązania z wiązania i Utwórz <xref:System.ServiceModel.Channels.BindingElementCollection> klasy z jednej z właściwości niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="846d2-123">Create a custom binding from the binding and create a <xref:System.ServiceModel.Channels.BindingElementCollection> class from one of the custom binding's properties.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  <span data-ttu-id="846d2-124">Pętli <xref:System.ServiceModel.Channels.BindingElementCollection> klasy, i do wyszukania <xref:System.ServiceModel.Channels.HttpTransportBindingElement> klasy, ustaw jej <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="846d2-124">Loop through the <xref:System.ServiceModel.Channels.BindingElementCollection> class, and when you find the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> class, set its <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property to `false`.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="846d2-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="846d2-125">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="846d2-126">Powiązania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="846d2-126">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)
