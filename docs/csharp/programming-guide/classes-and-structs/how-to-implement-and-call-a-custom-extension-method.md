---
title: 'Porady: implementowanie i wywołanie niestandardowej metody rozszerzenia (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e73ccee84c35678a4923347ab04619bb6017aca5
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="bc4df-102">Porady: implementowanie i wywołanie niestandardowej metody rozszerzenia (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="bc4df-102">How to: Implement and Call a Custom Extension Method (C# Programming Guide)</span></span>
<span data-ttu-id="bc4df-103">W tym temacie pokazano, jak wdrożyć własne metody rozszerzenia dla dowolnego typu .NET.</span><span class="sxs-lookup"><span data-stu-id="bc4df-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="bc4df-104">Kod klienta można użyć metody rozszerzenia Dodawanie odwołania do pliku DLL zawierającego je i dodawanie [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywy, który określa przestrzeń nazw, w którym zdefiniowano metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="bc4df-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../../csharp/language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="bc4df-105">Aby zdefiniować i wywołanie metody rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="bc4df-105">To define and call the extension method</span></span>  
  
1.  <span data-ttu-id="bc4df-106">Definiowanie statycznego [klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) zawiera metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="bc4df-106">Define a static [class](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="bc4df-107">Klasa musi być widoczny dla kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="bc4df-107">The class must be visible to client code.</span></span> <span data-ttu-id="bc4df-108">Aby uzyskać więcej informacji o regułach ułatwień dostępu, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="bc4df-108">For more information about accessibility rules, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
2.  <span data-ttu-id="bc4df-109">Zaimplementuj metodę rozszerzenie jako metoda statyczna z co najmniej taką samą widoczność jak klasa zawierająca.</span><span class="sxs-lookup"><span data-stu-id="bc4df-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3.  <span data-ttu-id="bc4df-110">Pierwszy parametr metody Określa typ, metoda operuje na; musi być poprzedzony literą [to](../../../csharp/language-reference/keywords/this.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="bc4df-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../../csharp/language-reference/keywords/this.md) modifier.</span></span>  
  
4.  <span data-ttu-id="bc4df-111">W kodu wywołującego dodać `using` dyrektywy do określenia [przestrzeń nazw](../../../csharp/language-reference/keywords/namespace.md) zawiera klasę — metoda rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="bc4df-111">In the calling code, add a `using` directive to specify the [namespace](../../../csharp/language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5.  <span data-ttu-id="bc4df-112">Wywołanie metody, tak jakby były to wystąpienie metody w typie.</span><span class="sxs-lookup"><span data-stu-id="bc4df-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="bc4df-113">Należy zauważyć, że pierwszy parametr nie zostanie określony przez wywołanie kodu, ponieważ reprezentuje ona typu, dla którego stosowana jest operator i kompilator zna już typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="bc4df-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="bc4df-114">Musisz podać argumenty parametrów 2 za pośrednictwem `n`.</span><span class="sxs-lookup"><span data-stu-id="bc4df-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc4df-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc4df-115">Example</span></span>  
 <span data-ttu-id="bc4df-116">Poniższy przykład implementuje metodę rozszerzenia o nazwie `WordCount` w `CustomExtensions.StringExtension` klasy.</span><span class="sxs-lookup"><span data-stu-id="bc4df-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="bc4df-117">Metoda działa na <xref:System.String> klasy, która jest określony jako pierwszego parametru metody.</span><span class="sxs-lookup"><span data-stu-id="bc4df-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="bc4df-118">`CustomExtensions` Przestrzeni nazw jest importowany do przestrzeni nazw aplikacji, a metoda jest wywoływana wewnątrz `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="bc4df-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-implement-and-call-a-custom-extension-method_1.cs)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bc4df-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="bc4df-119">Compiling the Code</span></span>  
 <span data-ttu-id="bc4df-120">Aby uruchomić ten kod, skopiuj i wklej go do języka Visual C# projektu aplikacji konsolowej utworzony w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bc4df-120">To run this code, copy and paste it into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="bc4df-121">Domyślnie ten projekt jest przeznaczony dla wersji 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], i zawiera odwołania do System.Core.dll i `using` dyrektywy dla System.Linq.</span><span class="sxs-lookup"><span data-stu-id="bc4df-121">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="bc4df-122">Jeśli co najmniej jeden z tych wymagań brakuje z projektu, należy je dodać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="bc4df-122">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="bc4df-123">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="bc4df-123">.NET Framework Security</span></span>  
 <span data-ttu-id="bc4df-124">Metody rozszerzenia udostępniają nie luk.</span><span class="sxs-lookup"><span data-stu-id="bc4df-124">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="bc4df-125">One nigdy nie można personifikować istniejących metod typu, ponieważ wszystkie konflikty nazw są rozpoznawane na rzecz wystąpienia lub statycznej metody zdefiniowane przez samego typu.</span><span class="sxs-lookup"><span data-stu-id="bc4df-125">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="bc4df-126">Metody rozszerzenia nie dostęp do danych prywatnych rozszerzoną klasy.</span><span class="sxs-lookup"><span data-stu-id="bc4df-126">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc4df-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc4df-127">See Also</span></span>  
 [<span data-ttu-id="bc4df-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bc4df-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bc4df-129">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="bc4df-129">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [<span data-ttu-id="bc4df-130">LINQ (zapytania o języku zintegrowanym)</span><span class="sxs-lookup"><span data-stu-id="bc4df-130">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="bc4df-131">Klasy statyczne i statyczne elementy członkowskie klas</span><span class="sxs-lookup"><span data-stu-id="bc4df-131">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [<span data-ttu-id="bc4df-132">protected</span><span class="sxs-lookup"><span data-stu-id="bc4df-132">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="bc4df-133">internal</span><span class="sxs-lookup"><span data-stu-id="bc4df-133">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 [<span data-ttu-id="bc4df-134">public</span><span class="sxs-lookup"><span data-stu-id="bc4df-134">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="bc4df-135">this</span><span class="sxs-lookup"><span data-stu-id="bc4df-135">this</span></span>](../../../csharp/language-reference/keywords/this.md)  
 [<span data-ttu-id="bc4df-136">namespace</span><span class="sxs-lookup"><span data-stu-id="bc4df-136">namespace</span></span>](../../../csharp/language-reference/keywords/namespace.md)
