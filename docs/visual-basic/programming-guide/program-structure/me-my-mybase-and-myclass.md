---
title: Me, My, MyBase i MyClass w Visual Basic
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: a8df6e48fd5bce9bb28d8aef7e031f36741ad0ad
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813395"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="6651b-102">Me, My, MyBase i MyClass w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6651b-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="6651b-103">`Me`, `My`, `MyBase` i `MyClass` w języku Visual Basic mają podobne nazwy, ale różne cele.</span><span class="sxs-lookup"><span data-stu-id="6651b-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="6651b-104">W tym temacie opisano każdy z tych obiektów w celu ich rozróżnienia.</span><span class="sxs-lookup"><span data-stu-id="6651b-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="6651b-105">Me</span><span class="sxs-lookup"><span data-stu-id="6651b-105">Me</span></span>  
 <span data-ttu-id="6651b-106">Słowo kluczowe `Me` umożliwia odwołanie się do konkretnego wystąpienia klasy lub struktury, w którym aktualnie wykonywany jest kod.</span><span class="sxs-lookup"><span data-stu-id="6651b-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="6651b-107">`Me` zachowuje się jak zmienna obiektu lub struktury, odwołując się do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6651b-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="6651b-108">Używanie słowa kluczowego `Me` jest szczególnie przydatne do przekazywania informacji o aktualnie wykonywanej instancji klasy lub struktury do procedury w innej klasie, strukturze lub module.</span><span class="sxs-lookup"><span data-stu-id="6651b-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="6651b-109">Załóżmy na przykład, że masz w module następującą procedurę.</span><span class="sxs-lookup"><span data-stu-id="6651b-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="6651b-110">Możesz wywołać tę procedurę i przekazać bieżące wystąpienie klasy <xref:System.Windows.Forms.Form> jako argument, używając następującej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6651b-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="6651b-111">My</span><span class="sxs-lookup"><span data-stu-id="6651b-111">My</span></span>  
 <span data-ttu-id="6651b-112">Właściwość `My` pozwala na łatwy i intuicyjny dostęp do wielu klas [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], umożliwiając użytkownikowi języka Visual Basic interakcję z komputerem, aplikacją, ustawieniami, zasobami i innymi elementami.</span><span class="sxs-lookup"><span data-stu-id="6651b-112">The `My` feature provides easy and intuitive access to a number of [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="6651b-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="6651b-113">MyBase</span></span>  
 <span data-ttu-id="6651b-114">Słowo kluczowe `MyBase` zachowuje się jak zmienna obiektu odwołująca się do klasy bazowej bieżącego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="6651b-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="6651b-115">Słowo kluczowe `MyBase` jest najczęściej używane do dostępu do składowych klasy bazowej, które zostały zastąpione lub przesłonięte w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="6651b-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="6651b-116">`MyBase.New` służy do jawnego wywołania konstruktora klasy bazowej w konstruktorze klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="6651b-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="6651b-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="6651b-117">MyClass</span></span>  
 <span data-ttu-id="6651b-118">Słowo kluczowe `MyClass` zachowuje się jak odwołanie do bieżącego wystąpienia klasy zgodnie z pierwotną implementacją.</span><span class="sxs-lookup"><span data-stu-id="6651b-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="6651b-119">`MyClass` przypomina `Me`, ale wszystkie wywołania metod na tym słowie kluczowym są traktowane tak, jakby były `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="6651b-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6651b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6651b-120">See also</span></span>

- [<span data-ttu-id="6651b-121">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="6651b-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
