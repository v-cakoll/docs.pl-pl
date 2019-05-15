---
title: 'Instrukcje: używanie wielu tokenów zabezpieczeń tego samego typu'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 1b383c6ccd96d1b3d7b091b2d7c67bb166da51df
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589418"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="c1d76-102">Instrukcje: używanie wielu tokenów zabezpieczeń tego samego typu</span><span class="sxs-lookup"><span data-stu-id="c1d76-102">How to: Use Multiple Security Tokens of the Same Type</span></span>
- <span data-ttu-id="c1d76-103">W programie .NET Framework 3.0 wiadomość klienta zawierała tylko jeden token danego typu.</span><span class="sxs-lookup"><span data-stu-id="c1d76-103">In .NET Framework 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="c1d76-104">Teraz komunikatów klienta może zawierać wiele tokenów typu.</span><span class="sxs-lookup"><span data-stu-id="c1d76-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="c1d76-105">W tym temacie pokazano jak dołączyć wielu tokenów tego samego typu w komunikacie klienta.</span><span class="sxs-lookup"><span data-stu-id="c1d76-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
- <span data-ttu-id="c1d76-106">Należy pamiętać, że nie można skonfigurować usługi w ten sposób: usługa może zawierać tylko jeden token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="c1d76-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="c1d76-107">Aby użyć wielu tokenów zabezpieczeń tego samego typu</span><span class="sxs-lookup"><span data-stu-id="c1d76-107">To use multiple security tokens of the same type</span></span>  
  
1. <span data-ttu-id="c1d76-108">Tworzenie powiązania pusta Kolekcja elementów do wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="c1d76-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. <span data-ttu-id="c1d76-109">Tworzenie <xref:System.ServiceModel.Channels.SecurityBindingElement> przez wywołanie metody <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="c1d76-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. <span data-ttu-id="c1d76-110">Utwórz <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c1d76-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. <span data-ttu-id="c1d76-111">Dodaj tokeny SAML do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c1d76-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. <span data-ttu-id="c1d76-112">Dodaj kolekcję do <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="c1d76-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. <span data-ttu-id="c1d76-113">Dodaj elementy powiązania do kolekcji element powiązania.</span><span class="sxs-lookup"><span data-stu-id="c1d76-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. <span data-ttu-id="c1d76-114">Zwraca nowe powiązanie niestandardowych utworzone na podstawie kolekcji elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="c1d76-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="c1d76-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1d76-115">Example</span></span>  
 <span data-ttu-id="c1d76-116">Poniżej przedstawiono całą metodę opisane w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="c1d76-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
