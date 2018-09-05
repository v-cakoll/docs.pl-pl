---
title: 'Instrukcje: Używanie wielu tokenów zabezpieczeń tego samego typu'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 25afbb268a0ef7772585a0f3829b56f135758b61
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43672323"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="ab803-102">Instrukcje: Używanie wielu tokenów zabezpieczeń tego samego typu</span><span class="sxs-lookup"><span data-stu-id="ab803-102">How to: Use Multiple Security Tokens of the Same Type</span></span>
-   <span data-ttu-id="ab803-103">W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, token wiadomość tylko jeden zawartej klienta dla dowolnego typu.</span><span class="sxs-lookup"><span data-stu-id="ab803-103">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="ab803-104">Teraz komunikatów klienta może zawierać wiele tokenów typu.</span><span class="sxs-lookup"><span data-stu-id="ab803-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="ab803-105">W tym temacie pokazano jak dołączyć wielu tokenów tego samego typu w komunikacie klienta.</span><span class="sxs-lookup"><span data-stu-id="ab803-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
-   <span data-ttu-id="ab803-106">Należy pamiętać, że nie można skonfigurować usługi w ten sposób: usługa może zawierać tylko jeden token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="ab803-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="ab803-107">Aby użyć wielu tokenów zabezpieczeń tego samego typu</span><span class="sxs-lookup"><span data-stu-id="ab803-107">To use multiple security tokens of the same type</span></span>  
  
1.  <span data-ttu-id="ab803-108">Tworzenie powiązania pusta Kolekcja elementów do wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="ab803-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  <span data-ttu-id="ab803-109">Tworzenie <xref:System.ServiceModel.Channels.SecurityBindingElement> przez wywołanie metody <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="ab803-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  <span data-ttu-id="ab803-110">Utwórz <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ab803-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  <span data-ttu-id="ab803-111">Dodaj tokeny SAML do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ab803-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  <span data-ttu-id="ab803-112">Dodaj kolekcję do <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="ab803-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  <span data-ttu-id="ab803-113">Dodaj elementy powiązania do kolekcji element powiązania.</span><span class="sxs-lookup"><span data-stu-id="ab803-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  <span data-ttu-id="ab803-114">Zwraca nowe powiązanie niestandardowych utworzone na podstawie kolekcji elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="ab803-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="ab803-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab803-115">Example</span></span>  
 <span data-ttu-id="ab803-116">Poniżej przedstawiono całą metodę opisane w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="ab803-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="ab803-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab803-117">See Also</span></span>  
 [<span data-ttu-id="ab803-118">Architektura zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="ab803-118">Security Architecture</span></span>](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
