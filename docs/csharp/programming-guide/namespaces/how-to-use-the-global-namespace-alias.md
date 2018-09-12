---
title: 'Porady: użycie globalnych aliasów przestrzeni nazw (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
ms.openlocfilehash: c15271abb55cb29a200185e4b512a76a4913d848
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514621"
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="c8082-102">Porady: użycie globalnych aliasów przestrzeni nazw (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c8082-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="c8082-103">Możliwość dostępu do elementu członkowskiego w globalnym [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md) jest przydatne, gdy element członkowski może być ono ukryte przez inną jednostkę o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="c8082-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="c8082-104">Na przykład w poniższym kodzie `Console` jest rozpoznawana jako `TestApp.Console` zamiast do `Console` wpisać <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c8082-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 <span data-ttu-id="c8082-105">Za pomocą `System.Console` nadal powoduje błąd, ponieważ `System` przestrzeni nazw jest ukryty przez klasę `TestApp.System`:</span><span class="sxs-lookup"><span data-stu-id="c8082-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 <span data-ttu-id="c8082-106">Jednak możesz obejść ten błąd, za pomocą `global::System.Console`, podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="c8082-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 <span data-ttu-id="c8082-107">Gdy jest identyfikator po lewej stronie `global`, wyszukaj identyfikator prawo rozpoczyna się w globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c8082-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="c8082-108">Na przykład następująca deklaracja odwołuje się do `TestApp` jako członek globalnej przestrzeni.</span><span class="sxs-lookup"><span data-stu-id="c8082-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 <span data-ttu-id="c8082-109">Oczywiście, tworząc własne przestrzenie nazw o nazwie `System` nie jest zalecane, i jest mało prawdopodobne, będą napotykać jakiegokolwiek kodu, w którym to się stało.</span><span class="sxs-lookup"><span data-stu-id="c8082-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="c8082-110">Jednak w dużych projektach, jest bardzo prawdziwy możliwość, że duplikacji przestrzeni nazw może wystąpić w czy innej formie.</span><span class="sxs-lookup"><span data-stu-id="c8082-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="c8082-111">W takich sytuacjach kwalifikator globalnej przestrzeni nazw jest usługi gwarancji, że można określić głównej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c8082-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8082-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8082-112">Example</span></span>  
 <span data-ttu-id="c8082-113">W tym przykładzie obszar nazw `System` jest używana do włączenia klasy `TestClass` w związku z tym, `global::System.Console` musi być używana do odwołania `System.Console` klasy, która jest ukryta przez `System` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c8082-113">In this example, the namespace `System` is used to include the class `TestClass` therefore, `global::System.Console` must be used to reference the `System.Console` class, which is hidden by the `System` namespace.</span></span> <span data-ttu-id="c8082-114">Ponadto alias `colAlias` służy do odwoływania się do przestrzeni nazw `System.Collections`; w związku z tym, wystąpienie <xref:System.Collections.Hashtable?displayProperty=nameWithType> został utworzony za pomocą tego aliasu zamiast przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c8082-114">Also, the alias `colAlias` is used to refer to the namespace `System.Collections`; therefore, the instance of a <xref:System.Collections.Hashtable?displayProperty=nameWithType> was created using this alias instead of the namespace.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
<span data-ttu-id="c8082-115">**1**
**B 2**
**C 3**</span><span class="sxs-lookup"><span data-stu-id="c8082-115">**A 1**
**B 2**
**C 3**</span></span>

## <a name="see-also"></a><span data-ttu-id="c8082-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8082-116">See Also</span></span>

- [<span data-ttu-id="c8082-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c8082-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c8082-118">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="c8082-118">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
- [<span data-ttu-id="c8082-119">. operator</span><span class="sxs-lookup"><span data-stu-id="c8082-119">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
- [<span data-ttu-id="c8082-120">::, operator</span><span class="sxs-lookup"><span data-stu-id="c8082-120">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
- [<span data-ttu-id="c8082-121">extern</span><span class="sxs-lookup"><span data-stu-id="c8082-121">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
