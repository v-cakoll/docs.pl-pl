---
title: "Porady: użycie globalnych aliasów przestrzeni nazw (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- aliases [C#]
- namespaces [C#], global namespace qualifier
- global namespace [C#]
ms.assetid: 98a1d89b-3c5a-44f7-8400-c4a3c0ec22a9
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f2a854d2f963578cb8b89da445af660f3c029fae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-global-namespace-alias-c-programming-guide"></a><span data-ttu-id="24b75-102">Porady: użycie globalnych aliasów przestrzeni nazw (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="24b75-102">How to: Use the Global Namespace Alias (C# Programming Guide)</span></span>
<span data-ttu-id="24b75-103">Umożliwia uzyskiwanie dostępu do członka w globalnej [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md) jest przydatne, gdy element członkowski może być ukryty przez inną jednostkę o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="24b75-103">The ability to access a member in the global [namespace](../../../csharp/language-reference/keywords/namespace.md) is useful when the member might be hidden by another entity of the same name.</span></span>  
  
 <span data-ttu-id="24b75-104">Na przykład w poniższym kodzie `Console` jest rozpoznawana jako `TestApp.Console` zamiast do `Console` wpisz <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="24b75-104">For example, in the following code, `Console` resolves to `TestApp.Console` instead of to the `Console` type in the <xref:System> namespace.</span></span>  
  
 [!code-csharp[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-use-the-global-namespace-alias_1.cs)]  
  
 [!code-csharp[csProgGuideNamespaces#1](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_2.cs)]  
  
 <span data-ttu-id="24b75-105">Przy użyciu `System.Console` nadal powoduje błąd, ponieważ `System` przestrzeni nazw jest ukryty przez klasę `TestApp.System`:</span><span class="sxs-lookup"><span data-stu-id="24b75-105">Using `System.Console` still results in an error because the `System` namespace is hidden by the class `TestApp.System`:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#2](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_3.cs)]  
  
 <span data-ttu-id="24b75-106">Jednak można obejść ten błąd przy użyciu `global::System.Console`, podobnie do następującej:</span><span class="sxs-lookup"><span data-stu-id="24b75-106">However, you can work around this error by using `global::System.Console`, like this:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#3](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_4.cs)]  
  
 <span data-ttu-id="24b75-107">Po lewej identyfikator `global`, wyszukaj identyfikator prawo rozpoczyna się w globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="24b75-107">When the left identifier is `global`, the search for the right identifier starts at the global namespace.</span></span> <span data-ttu-id="24b75-108">Na przykład następujące oświadczenie odwołuje się do `TestApp` jako członek globalnej przestrzeni.</span><span class="sxs-lookup"><span data-stu-id="24b75-108">For example, the following declaration is referencing `TestApp` as a member of the global space.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#4](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_5.cs)]  
  
 <span data-ttu-id="24b75-109">Oczywiście, tworzenie własnych przestrzeni nazw o nazwie `System` nie jest zalecane, i jest mało prawdopodobne, wystąpi żadnego kodu, w którym miało to miejsce.</span><span class="sxs-lookup"><span data-stu-id="24b75-109">Obviously, creating your own namespaces called `System` is not recommended, and it is unlikely you will encounter any code in which this has happened.</span></span> <span data-ttu-id="24b75-110">Jednak w większych projektów jest bardzo prawdziwy możliwość, że duplikatów nazw może wystąpić w czy innej formie.</span><span class="sxs-lookup"><span data-stu-id="24b75-110">However, in larger projects, it is a very real possibility that namespace duplication may occur in one form or another.</span></span> <span data-ttu-id="24b75-111">W takich przypadkach kwalifikator globalnej przestrzeni nazw jest Twoje gwarancji, że można określić głównej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="24b75-111">In these situations, the global namespace qualifier is your guarantee that you can specify the root namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24b75-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="24b75-112">Example</span></span>  
 <span data-ttu-id="24b75-113">W tym przykładzie obszar nazw `System` jest używana do włączenia klasy `TestClass` w związku z tym `global::System.Console` musi być używany do odwołania `System.Console` klasy, która jest ukryty przez `System` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="24b75-113">In this example, the namespace `System` is used to include the class `TestClass` therefore, `global::System.Console` must be used to reference the `System.Console` class, which is hidden by the `System` namespace.</span></span> <span data-ttu-id="24b75-114">Ponadto alias `colAlias` służy do odwoływania się do przestrzeni nazw `System.Collections`; w związku z tym wystąpienie <xref:System.Collections.Hashtable?displayProperty=nameWithType> został utworzony za pomocą tego aliasu zamiast przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="24b75-114">Also, the alias `colAlias` is used to refer to the namespace `System.Collections`; therefore, the instance of a <xref:System.Collections.Hashtable?displayProperty=nameWithType> was created using this alias instead of the namespace.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#5](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-global-namespace-alias_6.cs)]  
  
 <span data-ttu-id="24b75-115">**1**</span><span class="sxs-lookup"><span data-stu-id="24b75-115">**A 1**</span></span>  
<span data-ttu-id="24b75-116">**B 2**</span><span class="sxs-lookup"><span data-stu-id="24b75-116">**B 2**</span></span>  
<span data-ttu-id="24b75-117">**C 3**</span><span class="sxs-lookup"><span data-stu-id="24b75-117">**C 3**</span></span>   
## <a name="see-also"></a><span data-ttu-id="24b75-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24b75-118">See Also</span></span>  
 [<span data-ttu-id="24b75-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="24b75-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="24b75-120">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="24b75-120">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="24b75-121">. Operator</span><span class="sxs-lookup"><span data-stu-id="24b75-121">. Operator</span></span>](../../../csharp/language-reference/operators/member-access-operator.md)  
 [<span data-ttu-id="24b75-122">:: — Operator</span><span class="sxs-lookup"><span data-stu-id="24b75-122">:: Operator</span></span>](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)  
 [<span data-ttu-id="24b75-123">extern</span><span class="sxs-lookup"><span data-stu-id="24b75-123">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)
