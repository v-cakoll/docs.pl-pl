---
title: 'Instrukcje: Użyj globalnego aliasu przestrzeni nazw C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: b163981d3cf6d56ab953757931b0b386a47263ff
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796287"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="c544d-102">Instrukcje: Użyj globalnego aliasu przestrzeni nazwC# (Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="c544d-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="c544d-103">Możliwość uzyskania dostępu do elementu członkowskiego w globalnej [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md) jest przydatna, gdy członek może być ukryty przez inną jednostkę o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="c544d-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="c544d-104">Na przykład, `Console` w poniższym kodzie, jest rozpoznawana jako `TestApp.Console` zamiast <xref:System> do `Console` typu w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c544d-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuide/CS/using.cs#1)]  
  
 [!code-csharp[csProgGuideNamespaces#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#1)]  
  
 <span data-ttu-id="c544d-105">Użycie `System.Console` nadal powoduje błąd, `System` ponieważ przestrzeń nazw jest ukryta przez klasę `TestApp.System`:</span><span class="sxs-lookup"><span data-stu-id="c544d-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#2)]  
  
 <span data-ttu-id="c544d-106">Można jednak obejść ten błąd przy użyciu `global::System.Console`, jak to:</span><span class="sxs-lookup"><span data-stu-id="c544d-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#3)]  
  
 <span data-ttu-id="c544d-107">Gdy lewy identyfikator to `global`, wyszukiwanie właściwego identyfikatora zaczyna się od globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c544d-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="c544d-108">Na przykład następująca deklaracja jest odwołująca `TestApp` się jako składowa obszaru globalnego.</span><span class="sxs-lookup"><span data-stu-id="c544d-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces.cs#4)]  
  
 <span data-ttu-id="c544d-109">Oczywiście utworzenie własnych nazw o nazwie `System` nie jest zalecane i jest mało prawdopodobne, że zostanie napotkany kod, w którym wystąpił ten plik.</span><span class="sxs-lookup"><span data-stu-id="c544d-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="c544d-110">Jednak w większych projektach jest to bardzo prawdziwa możliwość duplikowania przestrzeni nazw może wystąpić w jednej postaci lub w innym.</span><span class="sxs-lookup"><span data-stu-id="c544d-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="c544d-111">W takich sytuacjach kwalifikator globalnej przestrzeni nazw jest gwarancją, że można określić główną przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="c544d-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c544d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c544d-112">See also</span></span>

- [<span data-ttu-id="c544d-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c544d-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c544d-114">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="c544d-114">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
- [<span data-ttu-id="c544d-115">:: operator</span><span class="sxs-lookup"><span data-stu-id="c544d-115">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="c544d-116">extern</span><span class="sxs-lookup"><span data-stu-id="c544d-116">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
