---
title: 'Instrukcje: używanie wielu tokenów zabezpieczeń tego samego typu'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
ms.openlocfilehash: 84009eacca113fcd83a0e4908c7d6eb0c82db7d5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928761"
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="d2d13-102">Instrukcje: używanie wielu tokenów zabezpieczeń tego samego typu</span><span class="sxs-lookup"><span data-stu-id="d2d13-102">How to: Use Multiple Security Tokens of the Same Type</span></span>

- <span data-ttu-id="d2d13-103">W .NET Framework 3,0 komunikat klienta zawiera tylko jeden token danego typu.</span><span class="sxs-lookup"><span data-stu-id="d2d13-103">In .NET Framework 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="d2d13-104">Teraz komunikaty klienta mogą zawierać wiele tokenów typu.</span><span class="sxs-lookup"><span data-stu-id="d2d13-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="d2d13-105">W tym temacie pokazano, jak uwzględnić wiele tokenów tego samego typu w komunikacie klienta.</span><span class="sxs-lookup"><span data-stu-id="d2d13-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
- <span data-ttu-id="d2d13-106">Należy pamiętać, że usługi nie można skonfigurować w ten sposób: usługa może zawierać tylko jeden token pomocniczy.</span><span class="sxs-lookup"><span data-stu-id="d2d13-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="d2d13-107">Aby użyć wielu tokenów zabezpieczających tego samego typu</span><span class="sxs-lookup"><span data-stu-id="d2d13-107">To use multiple security tokens of the same type</span></span>  
  
1. <span data-ttu-id="d2d13-108">Utwórz pustą kolekcję elementów powiązania, która ma zostać wypełniona.</span><span class="sxs-lookup"><span data-stu-id="d2d13-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2. <span data-ttu-id="d2d13-109">Utwórz przez wywołanie <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>. <xref:System.ServiceModel.Channels.SecurityBindingElement></span><span class="sxs-lookup"><span data-stu-id="d2d13-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3. <span data-ttu-id="d2d13-110"><xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> Utwórz kolekcję.</span><span class="sxs-lookup"><span data-stu-id="d2d13-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4. <span data-ttu-id="d2d13-111">Dodaj tokeny SAML do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d2d13-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5. <span data-ttu-id="d2d13-112">Dodaj kolekcję do <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="d2d13-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6. <span data-ttu-id="d2d13-113">Dodaj elementy powiązania do kolekcji elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2d13-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7. <span data-ttu-id="d2d13-114">Zwróć nowe niestandardowe powiązanie utworzone na podstawie kolekcji elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="d2d13-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="d2d13-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2d13-115">Example</span></span>  
 <span data-ttu-id="d2d13-116">Poniżej znajduje się cała Metoda opisana przez poprzednią procedurę.</span><span class="sxs-lookup"><span data-stu-id="d2d13-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
