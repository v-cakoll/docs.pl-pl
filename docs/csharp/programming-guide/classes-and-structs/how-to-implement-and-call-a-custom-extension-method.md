---
title: Jak zaimplementować i wywołać metodę rozszerzenia niestandardowego — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: f3d96c033380698ade37c49ecbfeed14f05d3e11
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970892"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="201c1-102">Implementowanie i wywoływanie niestandardowej metody rozszerzenia (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="201c1-102">How to implement and call a custom extension method (C# Programming Guide)</span></span>
<span data-ttu-id="201c1-103">W tym temacie przedstawiono sposób implementacji własnych metod rozszerzenia dla dowolnego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="201c1-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="201c1-104">Kod klienta może korzystać z metod rozszerzenia przez dodanie odwołania do biblioteki DLL, która zawiera te metody, i dodanie dyrektywy [using](../../language-reference/keywords/using-directive.md) , która określa przestrzeń nazw, w której są zdefiniowane metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="201c1-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="201c1-105">Aby zdefiniować i wywołać metodę rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="201c1-105">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="201c1-106">Zdefiniuj [klasę](./static-classes-and-static-class-members.md) statyczną, aby zawierała metodę rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="201c1-106">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="201c1-107">Klasa musi być widoczna dla kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="201c1-107">The class must be visible to client code.</span></span> <span data-ttu-id="201c1-108">Aby uzyskać więcej informacji na temat reguł ułatwień dostępu, zobacz [Modyfikatory dostępu](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="201c1-108">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="201c1-109">Zaimplementuj metodę rozszerzenia jako metodę statyczną z co najmniej taką samą widocznością jak zawierająca klasy.</span><span class="sxs-lookup"><span data-stu-id="201c1-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="201c1-110">Pierwszy parametr metody Określa typ, na którym działa Metoda; musi być poprzedzony [tym](../../language-reference/keywords/this.md) modyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="201c1-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="201c1-111">W kodzie wywołującym Dodaj dyrektywę `using`, aby określić [przestrzeń nazw](../../language-reference/keywords/namespace.md) , która zawiera klasę metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="201c1-111">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="201c1-112">Wywołaj metody tak, jakby były metodami wystąpień w typie.</span><span class="sxs-lookup"><span data-stu-id="201c1-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="201c1-113">Należy zauważyć, że pierwszy parametr nie jest określony przez wywołanie kodu, ponieważ reprezentuje typ, na którym jest stosowany operator, a kompilator już zna typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="201c1-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="201c1-114">Musisz podać argumenty dla parametrów 2 do `n`.</span><span class="sxs-lookup"><span data-stu-id="201c1-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="201c1-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="201c1-115">Example</span></span>  
 <span data-ttu-id="201c1-116">Poniższy przykład implementuje metodę rozszerzającą o nazwie `WordCount` w klasie `CustomExtensions.StringExtension`.</span><span class="sxs-lookup"><span data-stu-id="201c1-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="201c1-117">Metoda działa na klasie <xref:System.String>, która jest określona jako pierwszy parametr metody.</span><span class="sxs-lookup"><span data-stu-id="201c1-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="201c1-118">Przestrzeń nazw `CustomExtensions` jest zaimportowana do przestrzeni nazw aplikacji, a metoda jest wywoływana wewnątrz metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="201c1-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="201c1-119">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="201c1-119">.NET Framework Security</span></span>  
 <span data-ttu-id="201c1-120">Metody rozszerzające nie stwarzają określonych luk w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="201c1-120">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="201c1-121">Nigdy nie mogą być używane do personifikacji istniejących metod dla typu, ponieważ wszystkie kolizje nazw są rozwiązywane na korzyść wystąpienia lub statycznej metody zdefiniowanej przez sam typ.</span><span class="sxs-lookup"><span data-stu-id="201c1-121">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="201c1-122">Metody rozszerzające nie mogą uzyskać dostępu do żadnych prywatnych danych w klasie rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="201c1-122">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="201c1-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="201c1-123">See also</span></span>

- [<span data-ttu-id="201c1-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="201c1-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="201c1-125">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="201c1-125">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="201c1-126">LINQ (zapytanie zintegrowane z językiem)</span><span class="sxs-lookup"><span data-stu-id="201c1-126">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="201c1-127">Klasy statyczne i statyczne elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="201c1-127">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="201c1-128">protected</span><span class="sxs-lookup"><span data-stu-id="201c1-128">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="201c1-129">internal</span><span class="sxs-lookup"><span data-stu-id="201c1-129">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="201c1-130">public</span><span class="sxs-lookup"><span data-stu-id="201c1-130">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="201c1-131">this</span><span class="sxs-lookup"><span data-stu-id="201c1-131">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="201c1-132">namespace</span><span class="sxs-lookup"><span data-stu-id="201c1-132">namespace</span></span>](../../language-reference/keywords/namespace.md)
