---
title: using — Dyrektywa (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 180c038987e7de6b39a8eae0e86871eea41a40bb
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960043"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="1b76b-102">using — Dyrektywa (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1b76b-102">using Directive (C# Reference)</span></span>
<span data-ttu-id="1b76b-103">`using` Dyrektywy ma trzy zastosowań:</span><span class="sxs-lookup"><span data-stu-id="1b76b-103">The `using` directive has three uses:</span></span>  
  
-   <span data-ttu-id="1b76b-104">Aby zezwolić na używanie typów w przestrzeni nazw, tak, aby nie trzeba Zakwalifikuj użycie typu w tej przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="1b76b-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>  
  
    ```csharp  
    using System.Text;  
    ```  
  
-   <span data-ttu-id="1b76b-105">Aby zezwolić na dostęp do statycznych elementów członkowskich typu bez konieczności kwalifikuj dostęp do nazwą typu.</span><span class="sxs-lookup"><span data-stu-id="1b76b-105">To allow you to access static members of a type without having to qualify the access with the type name.</span></span> 
  
    ```csharp  
    using static System.Math;  
    ```  
     
    <span data-ttu-id="1b76b-106">Aby uzyskać więcej informacji, zobacz [using static, dyrektywa](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="1b76b-106">For more information, see the [using static directive](using-static.md).</span></span>

-   <span data-ttu-id="1b76b-107">Aby utworzyć alias dla przestrzeni nazw lub typu.</span><span class="sxs-lookup"><span data-stu-id="1b76b-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="1b76b-108">Jest to nazywane *użycie dyrektywy alias*.</span><span class="sxs-lookup"><span data-stu-id="1b76b-108">This is called a *using alias directive*.</span></span>  
  
    ```csharp  
    using Project = PC.MyCompany.Project;  
    ```  
  
 <span data-ttu-id="1b76b-109">`using` Słowo kluczowe jest również używane do tworzenia *za pomocą instrukcji*, co pomóc, upewnij się, że <xref:System.IDisposable> obiektów, takich jak pliki i czcionki są obsługiwane poprawnie.</span><span class="sxs-lookup"><span data-stu-id="1b76b-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="1b76b-110">Zobacz [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="1b76b-110">See [using Statement](../../../csharp/language-reference/keywords/using-statement.md) for more information.</span></span>  
  
## <a name="using-static-type"></a><span data-ttu-id="1b76b-111">Za pomocą typu statycznego</span><span class="sxs-lookup"><span data-stu-id="1b76b-111">Using Static Type</span></span>  
 <span data-ttu-id="1b76b-112">Statyczne elementy członkowskie typu dostęp bez konieczności kwalifikuj dostęp do nazwą typu:</span><span class="sxs-lookup"><span data-stu-id="1b76b-112">You can access static members of a type without having to qualify the access with the type name:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="1b76b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b76b-113">Remarks</span></span>  
 <span data-ttu-id="1b76b-114">Zakres `using` dyrektywa jest ograniczona do pliku, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="1b76b-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>  
  
 <span data-ttu-id="1b76b-115">Utwórz `using` aliasu, aby ułatwić kwalifikują się do przestrzeni nazw lub typ identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="1b76b-115">Create a `using` alias to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="1b76b-116">Prawego boku za pomocą aliasu dyrektywy zawsze musi być w pełni kwalifikowanego typu niezależnie od tego używając dyrektyw, które pochodzą przed nią.</span><span class="sxs-lookup"><span data-stu-id="1b76b-116">The right side of a using alias directive must always be a fully-qualified type regardless of the using directives that come before it.</span></span>  
  
 <span data-ttu-id="1b76b-117">Utwórz `using` dyrektywy na używanie typów w przestrzeni nazw bez konieczności określania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1b76b-117">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="1b76b-118">A `using` dyrektywy nie umożliwiają dostęp do wszelkich przestrzenie nazw, które są zagnieżdżone w przestrzeni nazw, należy określić.</span><span class="sxs-lookup"><span data-stu-id="1b76b-118">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>  
  
 <span data-ttu-id="1b76b-119">Przestrzenie nazw są dostępne w dwóch kategorii: zdefiniowane przez użytkownika i zdefiniowane przez system.</span><span class="sxs-lookup"><span data-stu-id="1b76b-119">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="1b76b-120">Zdefiniowane przez użytkownika przestrzenie nazw są przestrzenie nazw zdefiniowane w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1b76b-120">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="1b76b-121">Aby uzyskać listę nazw zdefiniowaną przez system, zobacz [Przegląd biblioteki klas programu .NET Framework](../../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1b76b-121">For a list of the system-defined namespaces, see [.NET Framework Class Library Overview](../../../standard/class-library-overview.md).</span></span>  
  
 <span data-ttu-id="1b76b-122">Przykłady dotyczące odwoływania się do metody w innych zestawach, zobacz [tworzenie i użyj zestawów przy użyciu wiersza polecenia](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="1b76b-122">For examples on referencing methods in other assemblies, see [Create and Use Assemblies Using the Command Line](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="1b76b-123">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="1b76b-123">Example 1</span></span>  
  
 <span data-ttu-id="1b76b-124">Poniższy przykład pokazuje, jak zdefiniować i zastosować `using` alias dla przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="1b76b-124">The following example shows how to define and use a `using` alias for a namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
 <span data-ttu-id="1b76b-125">Using — dyrektywa alias nie może mieć to otwarty typ ogólny po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="1b76b-125">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="1b76b-126">Na przykład nie można utworzyć za pomocą aliasu dla listy\<T >, ale można utworzyć listę\<int >.</span><span class="sxs-lookup"><span data-stu-id="1b76b-126">For example, you cannot create a using alias for a List\<T>, but you can create one for a List\<int>.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="1b76b-127">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="1b76b-127">Example 2</span></span>  
  
 <span data-ttu-id="1b76b-128">Poniższy przykład pokazuje jak zdefiniować `using` dyrektywy i `using` alias dla klasy:</span><span class="sxs-lookup"><span data-stu-id="1b76b-128">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1b76b-129">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1b76b-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1b76b-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b76b-130">See Also</span></span>  
 [<span data-ttu-id="1b76b-131">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1b76b-131">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1b76b-132">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1b76b-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1b76b-133">Używanie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="1b76b-133">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)  
 [<span data-ttu-id="1b76b-134">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1b76b-134">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1b76b-135">Słowa kluczowe przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="1b76b-135">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)  
 [<span data-ttu-id="1b76b-136">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="1b76b-136">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="1b76b-137">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1b76b-137">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
