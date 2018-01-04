---
title: "Porady: używanie klasy ogólnej (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 168e5c7f7d144d5c20513d62f4e3458bc6f87235
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-a-generic-class-visual-basic"></a><span data-ttu-id="74ea4-102">Porady: używanie klasy ogólnej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74ea4-102">How to: Use a Generic Class (Visual Basic)</span></span>
<span data-ttu-id="74ea4-103">Klasa, która przyjmuje *parametry typu* jest nazywany *klasy ogólnej*.</span><span class="sxs-lookup"><span data-stu-id="74ea4-103">A class that takes *type parameters* is called a *generic class*.</span></span> <span data-ttu-id="74ea4-104">Jeśli korzystasz z klasy ogólnej, można wygenerować *skonstruowany klasy* z niego podając *argument typu* dla każdego z tych parametrów.</span><span class="sxs-lookup"><span data-stu-id="74ea4-104">If you are using a generic class, you can generate a *constructed class* from it by supplying a *type argument* for each of these parameters.</span></span> <span data-ttu-id="74ea4-105">Następnie można zadeklarować zmiennej typu klasy utworzone i może utworzyć wystąpienia klasy skonstruowane i przypisz je do tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="74ea4-105">You can then declare a variable of the constructed class type, and you can create an instance of the constructed class and assign it to that variable.</span></span>  
  
 <span data-ttu-id="74ea4-106">Oprócz klas można również zdefiniować i używać struktury ogólne, interfejsów, procedury i delegatów.</span><span class="sxs-lookup"><span data-stu-id="74ea4-106">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
 <span data-ttu-id="74ea4-107">Poniższa procedura ma klasy ogólnej zdefiniowane w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] i tworzy wystąpienie z niego.</span><span class="sxs-lookup"><span data-stu-id="74ea4-107">The following procedure takes a generic class defined in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and creates an instance from it.</span></span>  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a><span data-ttu-id="74ea4-108">Aby użyć klasy, która przyjmuje parametr typu</span><span class="sxs-lookup"><span data-stu-id="74ea4-108">To use a class that takes a type parameter</span></span>  
  
1.  <span data-ttu-id="74ea4-109">Na początku pliku źródłowego, obejmują [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do zaimportowania <xref:System.Collections.Generic?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="74ea4-109">At the beginning of your source file, include an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import the <xref:System.Collections.Generic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="74ea4-110">Dzięki temu można odwoływać się do <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> klasy bez konieczności pełnej kwalifikacji go w odróżnieniu od innych klas kolejki takich jak <xref:System.Collections.Queue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="74ea4-110">This allows you to refer to the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class without having to fully qualify it to differentiate it from other queue classes such as <xref:System.Collections.Queue?displayProperty=nameWithType>.</span></span>  
  
2.  <span data-ttu-id="74ea4-111">Utwórz obiekt w zwykły sposób, ale Dodaj `(Of` `type``)` natychmiast po nazwie klasy.</span><span class="sxs-lookup"><span data-stu-id="74ea4-111">Create the object in the normal way, but add `(Of` `type``)` immediately after the class name.</span></span>  
  
     <span data-ttu-id="74ea4-112">W poniższym przykładzie użyto tej samej klasy (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) można utworzyć dwa obiekty kolejki zawierających elementy różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="74ea4-112">The following example uses the same class (<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>) to create two queue objects that hold items of different data types.</span></span> <span data-ttu-id="74ea4-113">Dodaje elementy na końcu każdej kolejki, a następnie usuwa i wyświetla elementy z na początku każdej kolejki.</span><span class="sxs-lookup"><span data-stu-id="74ea4-113">It adds items to the end of each queue and then removes and displays items from the front of each queue.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="74ea4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74ea4-114">See Also</span></span>  
 [<span data-ttu-id="74ea4-115">Typy danych</span><span class="sxs-lookup"><span data-stu-id="74ea4-115">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="74ea4-116">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="74ea4-116">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="74ea4-117">Niezależność od języka i składniki niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="74ea4-117">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="74ea4-118">Z</span><span class="sxs-lookup"><span data-stu-id="74ea4-118">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [<span data-ttu-id="74ea4-119">Imports, instrukcja (przestrzeń nazw i typ .NET)</span><span class="sxs-lookup"><span data-stu-id="74ea4-119">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="74ea4-120">Instrukcje: definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych</span><span class="sxs-lookup"><span data-stu-id="74ea4-120">How to: Define a Class That Can Provide Identical Functionality on Different Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)  
 [<span data-ttu-id="74ea4-121">Iteratory</span><span class="sxs-lookup"><span data-stu-id="74ea4-121">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
