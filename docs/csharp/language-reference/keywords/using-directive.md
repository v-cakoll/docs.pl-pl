---
title: "using — Dyrektywa (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 02c50b1e7a54d776985b60570c898e7d0739c44c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="0e2a9-102">using — Dyrektywa (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0e2a9-102">using Directive (C# Reference)</span></span>
<span data-ttu-id="0e2a9-103">`using` Dyrektywy ma trzy zastosowań:</span><span class="sxs-lookup"><span data-stu-id="0e2a9-103">The `using` directive has three uses:</span></span>  
  
-   <span data-ttu-id="0e2a9-104">Aby zezwolić na użycie typów w przestrzeni nazw, dzięki czemu nie trzeba Zakwalifikuj użycie typu w tej przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="0e2a9-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   <span data-ttu-id="0e2a9-105">Aby umożliwić dostęp do statycznych elementów członkowskich typu bez kwalifikacji dostępu o nazwie typu.</span><span class="sxs-lookup"><span data-stu-id="0e2a9-105">To allow you to access static members of a type without having to qualify the access with the type name.</span></span> 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    <span data-ttu-id="0e2a9-106">Aby uzyskać więcej informacji, zobacz [statycznych dyrektywa using](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="0e2a9-106">For more information, see the [using static directive](using-static.md).</span></span>

-   <span data-ttu-id="0e2a9-107">Aby utworzyć alias dla przestrzeni nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="0e2a9-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="0e2a9-108">Ta metoda jest wywoływana *alias dyrektywa using*.</span><span class="sxs-lookup"><span data-stu-id="0e2a9-108">This is called a *using alias directive*.</span></span>  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 <span data-ttu-id="0e2a9-109">`using` — Słowo kluczowe jest również używany do tworzenia *instrukcje using*, który pomocy, upewnij się, że <xref:System.IDisposable> obiekty, takie jak pliki i czcionki są prawidłowo obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="0e2a9-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="0e2a9-110">Zobacz [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="0e2a9-110">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) for more information.</span></span>  
  
## <a name="using-static-type"></a><span data-ttu-id="0e2a9-111">Przy użyciu typu statycznego</span><span class="sxs-lookup"><span data-stu-id="0e2a9-111">Using Static Type</span></span>  
 <span data-ttu-id="0e2a9-112">Statyczne elementy członkowskie typu dostępne bez konieczności zakwalifikować dostępu o nazwie:</span><span class="sxs-lookup"><span data-stu-id="0e2a9-112">You can access static members of a type without having to qualify the access with the type name:</span></span>  
  
```csharp  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="0e2a9-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0e2a9-113">Remarks</span></span>  
 <span data-ttu-id="0e2a9-114">Zakres `using` dyrektywa jest ograniczona do pliku, w których występuje.</span><span class="sxs-lookup"><span data-stu-id="0e2a9-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>  
  
 <span data-ttu-id="0e2a9-115">Utwórz `using` alias, aby ułatwić kwalifikują się do przestrzeni nazw lub typ identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="0e2a9-115">Create a `using` alias to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="0e2a9-116">Prawej stronie, używając aliasu dyrektywy zawsze musi być typem pełną niezależnie od tego, użycie dyrektywy znajdujące się przed nim.</span><span class="sxs-lookup"><span data-stu-id="0e2a9-116">The right side of a using alias directive must always be a fully-qualified type regardless of the using directives that come before it.</span></span>  
  
 <span data-ttu-id="0e2a9-117">Utwórz `using` dyrektywy można używać typów w przestrzeni nazw, bez konieczności określania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0e2a9-117">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="0e2a9-118">A `using` dyrektywy nie udostępnia wszystkie przestrzenie nazw, które są zagnieżdżone w przestrzeni nazw, należy określić.</span><span class="sxs-lookup"><span data-stu-id="0e2a9-118">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>  
  
 <span data-ttu-id="0e2a9-119">Przestrzenie nazw są dostępne w dwóch kategorii: zdefiniowane przez użytkownika i zdefiniowane przez system.</span><span class="sxs-lookup"><span data-stu-id="0e2a9-119">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="0e2a9-120">Zdefiniowane przez użytkownika przestrzenie nazw są nazw zdefiniowanych w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0e2a9-120">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="0e2a9-121">Aby uzyskać listę obszarów nazw zdefiniowanych w systemie, zobacz [Przegląd biblioteki klas programu .NET Framework](../../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0e2a9-121">For a list of the system-defined namespaces, see [.NET Framework Class Library Overview](../../../standard/class-library-overview.md).</span></span>  
  
 <span data-ttu-id="0e2a9-122">Przykłady dotyczące odwoływania się do metody w innych zestawów można znaleźć [tworzenie i użyj zestawów przy użyciu wiersza polecenia](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="0e2a9-122">For examples on referencing methods in other assemblies, see [Create and Use Assemblies Using the Command Line](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="0e2a9-123">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="0e2a9-123">Example 1</span></span>  
  
 <span data-ttu-id="0e2a9-124">Poniższy przykład przedstawia sposób zdefiniować i użyć `using` alias przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="0e2a9-124">The following example shows how to define and use a `using` alias for a namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 <span data-ttu-id="0e2a9-125">Za pomocą dyrektywy alias nie może być otwartym typem ogólnym po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="0e2a9-125">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="0e2a9-126">Na przykład nie można utworzyć za pomocą aliasu dla listy\<T >, ale można utworzyć listę\<int >.</span><span class="sxs-lookup"><span data-stu-id="0e2a9-126">For example, you cannot create a using alias for a List\<T>, but you can create one for a List\<int>.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="0e2a9-127">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="0e2a9-127">Example 2</span></span>  
  
 <span data-ttu-id="0e2a9-128">Poniższy przykład przedstawia sposób definiowania `using` dyrektywy i `using` alias klasy:</span><span class="sxs-lookup"><span data-stu-id="0e2a9-128">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0e2a9-129">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0e2a9-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0e2a9-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0e2a9-130">See Also</span></span>  
 [<span data-ttu-id="0e2a9-131">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="0e2a9-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0e2a9-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0e2a9-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0e2a9-133">Używanie usługi przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="0e2a9-133">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [<span data-ttu-id="0e2a9-134">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0e2a9-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0e2a9-135">Słowa kluczowe Namespace</span><span class="sxs-lookup"><span data-stu-id="0e2a9-135">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="0e2a9-136">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="0e2a9-136">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="0e2a9-137">Using — instrukcja</span><span class="sxs-lookup"><span data-stu-id="0e2a9-137">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
