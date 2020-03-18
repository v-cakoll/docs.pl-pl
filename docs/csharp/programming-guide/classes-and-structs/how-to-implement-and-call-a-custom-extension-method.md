---
title: Jak zaimplementować i wywołać niestandardową metodę rozszerzenia - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 7e2092a37c1f042a087e03f4a272139b585156c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705603"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="902aa-102">Jak zaimplementować i wywołać niestandardową metodę rozszerzenia (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="902aa-102">How to implement and call a custom extension method (C# Programming Guide)</span></span>
<span data-ttu-id="902aa-103">W tym temacie pokazano, jak zaimplementować własne metody rozszerzenia dla dowolnego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="902aa-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="902aa-104">Kod klienta można użyć metod rozszerzenia, dodając odwołanie do dll, który je zawiera i dodanie [using](../../language-reference/keywords/using-directive.md) dyrektywy, która określa obszar nazw, w którym metody rozszerzenia są zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="902aa-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="902aa-105">Aby zdefiniować i wywołać metodę rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="902aa-105">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="902aa-106">Zdefiniuj [klasę](./static-classes-and-static-class-members.md) statyczną, która zawiera metodę rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="902aa-106">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="902aa-107">Klasa musi być widoczna dla kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="902aa-107">The class must be visible to client code.</span></span> <span data-ttu-id="902aa-108">Aby uzyskać więcej informacji na temat reguł ułatwień dostępu, zobacz [Modyfikatory dostępu](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="902aa-108">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="902aa-109">Zaimplementuj metodę rozszerzenia jako metodę statyczną o co najmniej takiej samej widoczności jak klasa zawierająca.</span><span class="sxs-lookup"><span data-stu-id="902aa-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="902aa-110">Pierwszy parametr metody określa typ, na który działa metoda; musi być poprzedzony [tym](../../language-reference/keywords/this.md) modyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="902aa-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="902aa-111">W kodzie wywołującym dodaj dyrektywę, `using` aby określić obszar [nazw,](../../language-reference/keywords/namespace.md) który zawiera klasę metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="902aa-111">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="902aa-112">Wywołaj metody tak, jakby były metody wystąpienia na typ.</span><span class="sxs-lookup"><span data-stu-id="902aa-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="902aa-113">Należy zauważyć, że pierwszy parametr nie jest określony przez kod wywołujący, ponieważ reprezentuje typ, na którym operator jest stosowany, a kompilator już zna typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="902aa-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="902aa-114">Musisz podać tylko argumenty dla `n`parametrów od 2 do .</span><span class="sxs-lookup"><span data-stu-id="902aa-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="902aa-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="902aa-115">Example</span></span>  
 <span data-ttu-id="902aa-116">Poniższy przykład implementuje metodę `WordCount` rozszerzenia `CustomExtensions.StringExtension` o nazwie w klasie.</span><span class="sxs-lookup"><span data-stu-id="902aa-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="902aa-117">Metoda działa na <xref:System.String> klasie, która jest określona jako pierwszy parametr metody.</span><span class="sxs-lookup"><span data-stu-id="902aa-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="902aa-118">Obszar `CustomExtensions` nazw jest importowany do obszaru nazw aplikacji, `Main` a metoda jest wywoływana wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="902aa-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="902aa-119">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="902aa-119">.NET Framework Security</span></span>  
 <span data-ttu-id="902aa-120">Metody rozszerzenia nie zawierają żadnych konkretnych luk w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="902aa-120">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="902aa-121">Nigdy nie można użyć do personifikacji istniejących metod typu, ponieważ wszystkie kolizje nazw są rozpoznawane na korzyść wystąpienia lub metody statycznej zdefiniowanej przez sam typ.</span><span class="sxs-lookup"><span data-stu-id="902aa-121">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="902aa-122">Metody rozszerzenia nie mogą uzyskać dostępu do żadnych prywatnych danych w klasie rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="902aa-122">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="902aa-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="902aa-123">See also</span></span>

- [<span data-ttu-id="902aa-124">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="902aa-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="902aa-125">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="902aa-125">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="902aa-126">LINQ (zapytanie zintegrowane z językiem)</span><span class="sxs-lookup"><span data-stu-id="902aa-126">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="902aa-127">Klasy statyczne i statyczni członkowie klas</span><span class="sxs-lookup"><span data-stu-id="902aa-127">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="902aa-128">protected</span><span class="sxs-lookup"><span data-stu-id="902aa-128">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="902aa-129">Wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="902aa-129">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="902aa-130">Publicznego</span><span class="sxs-lookup"><span data-stu-id="902aa-130">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="902aa-131">względem tego ruchu</span><span class="sxs-lookup"><span data-stu-id="902aa-131">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="902aa-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="902aa-132">namespace</span></span>](../../language-reference/keywords/namespace.md)
