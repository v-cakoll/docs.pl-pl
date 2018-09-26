---
title: 'Instrukcje: Używanie wielu tokenów zabezpieczeń tego samego typu'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
author: BrucePerlerMS
ms.openlocfilehash: 9d1dab0f4da82e4db96471f0a8cf25c32bd5eced
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47110922"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="2d20d-102">Instrukcje: Używanie wielu tokenów zabezpieczeń tego samego typu</span><span class="sxs-lookup"><span data-stu-id="2d20d-102">How to: Use Multiple Security Tokens of the Same Type</span></span>
-   <span data-ttu-id="2d20d-103">W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, token wiadomość tylko jeden zawartej klienta dla dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="2d20d-103">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="2d20d-104">Teraz komunikatów klienta może zawierać wiele tokenów typu.</span><span class="sxs-lookup"><span data-stu-id="2d20d-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="2d20d-105">W tym temacie pokazano jak dołączyć wielu tokenów tego samego typu w komunikacie klienta.</span><span class="sxs-lookup"><span data-stu-id="2d20d-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
-   <span data-ttu-id="2d20d-106">Należy pamiętać, że nie można skonfigurować usługi w ten sposób: usługa może zawierać tylko jeden token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="2d20d-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="2d20d-107">Aby użyć wielu tokenów zabezpieczeń tego samego typu</span><span class="sxs-lookup"><span data-stu-id="2d20d-107">To use multiple security tokens of the same type</span></span>  
  
1.  <span data-ttu-id="2d20d-108">Tworzenie powiązania pusta Kolekcja elementów do wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="2d20d-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  <span data-ttu-id="2d20d-109">Tworzenie <xref:System.ServiceModel.Channels.SecurityBindingElement> przez wywołanie metody <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="2d20d-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  <span data-ttu-id="2d20d-110">Utwórz <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2d20d-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  <span data-ttu-id="2d20d-111">Dodaj tokeny SAML do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2d20d-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  <span data-ttu-id="2d20d-112">Dodaj kolekcję do <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="2d20d-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  <span data-ttu-id="2d20d-113">Dodaj elementy powiązania do kolekcji element powiązania.</span><span class="sxs-lookup"><span data-stu-id="2d20d-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  <span data-ttu-id="2d20d-114">Zwraca nowe powiązanie niestandardowych utworzone na podstawie kolekcji elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="2d20d-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="2d20d-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d20d-115">Example</span></span>  
 <span data-ttu-id="2d20d-116">Poniżej przedstawiono całą metodę opisane w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="2d20d-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="2d20d-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d20d-117">See Also</span></span>  
 [<span data-ttu-id="2d20d-118">Architektura zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="2d20d-118">Security Architecture</span></span>](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
