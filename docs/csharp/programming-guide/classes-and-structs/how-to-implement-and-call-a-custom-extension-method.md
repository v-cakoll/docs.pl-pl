---
title: Jak zaimplementować i wywołać metodę rozszerzenia niestandardowego — Przewodnik programowania w języku C#
description: Dowiedz się, jak zaimplementować metody rozszerzenia dla dowolnego typu .NET. Kod klienta może korzystać z metod przez dodanie odwołania do biblioteki DLL i dodanie dyrektywy using.
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 7856e78713648a42d1c961f50f7e83f2f7ef05b7
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865063"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="4941c-104">Implementowanie i wywoływanie niestandardowej metody rozszerzenia (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="4941c-104">How to implement and call a custom extension method (C# Programming Guide)</span></span>
<span data-ttu-id="4941c-105">W tym temacie przedstawiono sposób implementacji własnych metod rozszerzenia dla dowolnego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="4941c-105">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="4941c-106">Kod klienta może korzystać z metod rozszerzenia przez dodanie odwołania do biblioteki DLL, która zawiera te metody, i dodanie dyrektywy [using](../../language-reference/keywords/using-directive.md) , która określa przestrzeń nazw, w której są zdefiniowane metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="4941c-106">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="4941c-107">Aby zdefiniować i wywołać metodę rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="4941c-107">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="4941c-108">Zdefiniuj [klasę](./static-classes-and-static-class-members.md) statyczną, aby zawierała metodę rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="4941c-108">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="4941c-109">Klasa musi być widoczna dla kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="4941c-109">The class must be visible to client code.</span></span> <span data-ttu-id="4941c-110">Aby uzyskać więcej informacji na temat reguł ułatwień dostępu, zobacz [Modyfikatory dostępu](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="4941c-110">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="4941c-111">Zaimplementuj metodę rozszerzenia jako metodę statyczną z co najmniej taką samą widocznością jak zawierająca klasy.</span><span class="sxs-lookup"><span data-stu-id="4941c-111">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="4941c-112">Pierwszy parametr metody Określa typ, na którym działa Metoda; musi być poprzedzony [tym](../../language-reference/keywords/this.md) modyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="4941c-112">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="4941c-113">W kodzie wywołującym Dodaj dyrektywę, `using` Aby określić [przestrzeń nazw](../../language-reference/keywords/namespace.md) , która zawiera klasę metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="4941c-113">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="4941c-114">Wywołaj metody tak, jakby były metodami wystąpień w typie.</span><span class="sxs-lookup"><span data-stu-id="4941c-114">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="4941c-115">Należy zauważyć, że pierwszy parametr nie jest określony przez wywołanie kodu, ponieważ reprezentuje typ, na którym jest stosowany operator, a kompilator już zna typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="4941c-115">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="4941c-116">Musisz podać argumenty dla parametrów 2 przez `n` .</span><span class="sxs-lookup"><span data-stu-id="4941c-116">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4941c-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="4941c-117">Example</span></span>  
 <span data-ttu-id="4941c-118">Poniższy przykład implementuje metodę rozszerzającą o nazwie `WordCount` w `CustomExtensions.StringExtension` klasie.</span><span class="sxs-lookup"><span data-stu-id="4941c-118">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="4941c-119">Metoda działa na <xref:System.String> klasie, która jest określona jako pierwszy parametr metody.</span><span class="sxs-lookup"><span data-stu-id="4941c-119">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="4941c-120">`CustomExtensions`Przestrzeń nazw jest importowana do przestrzeni nazw aplikacji, a metoda jest wywoływana wewnątrz `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="4941c-120">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-security"></a><span data-ttu-id="4941c-121">Zabezpieczenia platformy .NET</span><span class="sxs-lookup"><span data-stu-id="4941c-121">.NET Security</span></span>  
 <span data-ttu-id="4941c-122">Metody rozszerzające nie stwarzają określonych luk w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="4941c-122">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="4941c-123">Nigdy nie mogą być używane do personifikacji istniejących metod dla typu, ponieważ wszystkie kolizje nazw są rozwiązywane na korzyść wystąpienia lub statycznej metody zdefiniowanej przez sam typ.</span><span class="sxs-lookup"><span data-stu-id="4941c-123">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="4941c-124">Metody rozszerzające nie mogą uzyskać dostępu do żadnych prywatnych danych w klasie rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="4941c-124">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4941c-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4941c-125">See also</span></span>

- [<span data-ttu-id="4941c-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4941c-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4941c-127">Metody rozszerzające</span><span class="sxs-lookup"><span data-stu-id="4941c-127">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="4941c-128">LINQ (zapytanie zintegrowane z językiem)</span><span class="sxs-lookup"><span data-stu-id="4941c-128">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="4941c-129">Klasy statyczne i statyczni członkowie klas</span><span class="sxs-lookup"><span data-stu-id="4941c-129">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="4941c-130">protected</span><span class="sxs-lookup"><span data-stu-id="4941c-130">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="4941c-131">internal</span><span class="sxs-lookup"><span data-stu-id="4941c-131">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="4941c-132">public</span><span class="sxs-lookup"><span data-stu-id="4941c-132">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="4941c-133">this</span><span class="sxs-lookup"><span data-stu-id="4941c-133">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="4941c-134">obszaru</span><span class="sxs-lookup"><span data-stu-id="4941c-134">namespace</span></span>](../../language-reference/keywords/namespace.md)
