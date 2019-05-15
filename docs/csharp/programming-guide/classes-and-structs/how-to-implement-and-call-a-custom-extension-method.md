---
title: 'Instrukcje: Implementowanie i wywołanie niestandardowej metody rozszerzenia - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 2fe07f8e4311417980caccc9c286b4f94c7ea994
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585956"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="c1b16-102">Instrukcje: Implementowanie i wywołanie niestandardowej metody rozszerzenia (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="c1b16-102">How to: Implement and Call a Custom Extension Method (C# Programming Guide)</span></span>
<span data-ttu-id="c1b16-103">W tym temacie pokazano, jak można implementować własne metody rozszerzenia dla dowolnego typu platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="c1b16-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="c1b16-104">Kod klienta można użyć metody rozszerzenia przez dodanie odwołania do biblioteki DLL, która je zawiera i dodawanie [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywę, który określa obszar nazw, w którym zdefiniowano metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c1b16-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../../csharp/language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="c1b16-105">Aby zdefiniować i wywołanie metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="c1b16-105">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="c1b16-106">Definiowanie statycznego [klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) zawiera metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c1b16-106">Define a static [class](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="c1b16-107">Klasy muszą być widoczne dla kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="c1b16-107">The class must be visible to client code.</span></span> <span data-ttu-id="c1b16-108">Aby uzyskać więcej informacji o regułach ułatwień dostępu, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="c1b16-108">For more information about accessibility rules, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="c1b16-109">Implementuje metody rozszerzenia jako metody statycznej z co najmniej taką samą widoczność jak klasa zawierająca.</span><span class="sxs-lookup"><span data-stu-id="c1b16-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="c1b16-110">Pierwszy parametr metody Określa typ, który działa metody; musi być poprzedzony znakiem [to](../../../csharp/language-reference/keywords/this.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="c1b16-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../../csharp/language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="c1b16-111">W wywoływanym kodzie Dodaj `using` dyrektywy, aby określić [przestrzeni nazw](../../../csharp/language-reference/keywords/namespace.md) zawierający klasę metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c1b16-111">In the calling code, add a `using` directive to specify the [namespace](../../../csharp/language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="c1b16-112">Tak, jakby były metodami wystąpień w typie, należy wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="c1b16-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="c1b16-113">Pamiętaj, że pierwszy parametr nie jest określony przez wywołanie kodu, ponieważ reprezentuje on typ, na którym jest stosowany operator kompilator wie już typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="c1b16-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="c1b16-114">Musisz podać argumenty dla parametrów 2 za pośrednictwem `n`.</span><span class="sxs-lookup"><span data-stu-id="c1b16-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1b16-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="c1b16-115">Example</span></span>  
 <span data-ttu-id="c1b16-116">Poniższy przykład implementuje metodę rozszerzenia o nazwie `WordCount` w `CustomExtensions.StringExtension` klasy.</span><span class="sxs-lookup"><span data-stu-id="c1b16-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="c1b16-117">Metoda działa na <xref:System.String> klasy, która jest określony jako pierwszy parametr metody.</span><span class="sxs-lookup"><span data-stu-id="c1b16-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="c1b16-118">`CustomExtensions` Przestrzeni nazw jest importowany do przestrzeni nazw aplikacji, a metoda jest wywoływana wewnątrz `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="c1b16-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="c1b16-119">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="c1b16-119">.NET Framework Security</span></span>  
 <span data-ttu-id="c1b16-120">Metody rozszerzenia udostępniają nie luk w zabezpieczeniach określone.</span><span class="sxs-lookup"><span data-stu-id="c1b16-120">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="c1b16-121">One nigdy nie można dokonać personifikacji istniejących metod w danym typie ponieważ wszystkich konfliktów nazw są rozpoznawane na rzecz wystąpienia lub statycznej metody zdefiniowane przez samego typu.</span><span class="sxs-lookup"><span data-stu-id="c1b16-121">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="c1b16-122">Metody rozszerzenia nie może uzyskać dostęp do wszelkich danych prywatnych w rozszerzona klasa.</span><span class="sxs-lookup"><span data-stu-id="c1b16-122">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b16-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1b16-123">See also</span></span>

- [<span data-ttu-id="c1b16-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c1b16-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c1b16-125">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="c1b16-125">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="c1b16-126">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="c1b16-126">LINQ (Language-Integrated Query)</span></span>](../../../csharp/linq/linq-in-csharp.md)
- [<span data-ttu-id="c1b16-127">Klasy statyczne i statyczne elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="c1b16-127">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="c1b16-128">protected</span><span class="sxs-lookup"><span data-stu-id="c1b16-128">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
- [<span data-ttu-id="c1b16-129">internal</span><span class="sxs-lookup"><span data-stu-id="c1b16-129">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
- [<span data-ttu-id="c1b16-130">public</span><span class="sxs-lookup"><span data-stu-id="c1b16-130">public</span></span>](../../../csharp/language-reference/keywords/public.md)
- [<span data-ttu-id="c1b16-131">this</span><span class="sxs-lookup"><span data-stu-id="c1b16-131">this</span></span>](../../../csharp/language-reference/keywords/this.md)
- [<span data-ttu-id="c1b16-132">namespace</span><span class="sxs-lookup"><span data-stu-id="c1b16-132">namespace</span></span>](../../../csharp/language-reference/keywords/namespace.md)
