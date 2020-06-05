---
title: 'Instrukcje: Używanie klasy ogólnej'
ms.date: 07/20/2015
helpviewer_keywords:
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- generic parameters
- data type parameters
- generics [Visual Basic], about generics
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], creating generic types
- data type arguments
- parameters [Visual Basic], data type
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
ms.openlocfilehash: 01f1f7ef5963feeb3fe2b5390244e4e516773bad
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393847"
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="c8f66-102">Porady: używanie klasy ogólnej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c8f66-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="c8f66-103">Klasa, która pobiera *parametry typu* , jest nazywana *klasą rodzajową*.</span><span class="sxs-lookup"><span data-stu-id="c8f66-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="c8f66-104">Jeśli używasz klasy generycznej, możesz wygenerować utworzoną *klasę* z niej, dostarczając *argument typu* dla każdego z tych parametrów.</span><span class="sxs-lookup"><span data-stu-id="c8f66-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="c8f66-105">Następnie można zadeklarować zmienną typu konstruowanej klasy i można utworzyć wystąpienie klasy skonstruowanej i przypisać ją do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c8f66-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="c8f66-106">Oprócz klas można także definiować struktury ogólne, interfejsy, procedury i Delegaty oraz korzystać z nich.</span><span class="sxs-lookup"><span data-stu-id="c8f66-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="c8f66-107">Poniższa procedura przyjmuje klasę generyczną zdefiniowaną w .NET Framework i tworzy dla niej wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="c8f66-107">The following procedure takes a generic class defined in the .NET Framework and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="c8f66-108">Aby użyć klasy, która przyjmuje parametr typu</span><span class="sxs-lookup"><span data-stu-id="c8f66-108">To use a class that takes a type parameter</span></span>  
  
1. <span data-ttu-id="c8f66-109">Na początku pliku źródłowego Dołącz [instrukcję Imports (przestrzeń nazw i typ platformy .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) , aby zaimportować <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="c8f66-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c8f66-110">Pozwala to na odwoływanie się do <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> klasy bez konieczności pełnego kwalifikowania go do odróżnienia od innych klas kolejek, takich jak <xref:System.Collections.Queue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c8f66-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="c8f66-111">Utwórz obiekt w normalny sposób, ale Dodaj `(Of type)` natychmiast po nazwie klasy.</span><span class="sxs-lookup"><span data-stu-id="c8f66-111">Create the object in the normal way, but add `(Of type)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="c8f66-112">Poniższy przykład używa tej samej klasy ( <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> ) do tworzenia dwóch obiektów kolejki, które zawierają elementy o różnych typach danych.</span><span class="sxs-lookup"><span data-stu-id="c8f66-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="c8f66-113">Dodaje elementy do końca każdej kolejki, a następnie usuwa i wyświetla elementy z przodu każdej kolejki.</span><span class="sxs-lookup"><span data-stu-id="c8f66-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="c8f66-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8f66-114">See also</span></span>

- [<span data-ttu-id="c8f66-115">Typy danych</span><span class="sxs-lookup"><span data-stu-id="c8f66-115">Data Types</span></span>](index.md)
- [<span data-ttu-id="c8f66-116">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c8f66-116">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="c8f66-117">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="c8f66-117">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="c8f66-118">Z</span><span class="sxs-lookup"><span data-stu-id="c8f66-118">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="c8f66-119">Imports — Instrukcja (.NET Namespace i Type)</span><span class="sxs-lookup"><span data-stu-id="c8f66-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="c8f66-120">Instrukcje: Definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych</span><span class="sxs-lookup"><span data-stu-id="c8f66-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](how-to-define-a-class-that-can-provide-identical-functionality.md)
- [<span data-ttu-id="c8f66-121">Iteratory</span><span class="sxs-lookup"><span data-stu-id="c8f66-121">Iterators</span></span>](../../concepts/iterators.md)
