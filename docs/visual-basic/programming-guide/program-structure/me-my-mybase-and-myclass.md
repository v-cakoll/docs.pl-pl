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
ms.openlocfilehash: 3eca756429c5fec8f324a17350844b59baf9ccf7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586252"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="1aeb6-102">Me, My, MyBase i MyClass w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1aeb6-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="1aeb6-103">`Me`, `My`, `MyBase` i `MyClass` w języku Visual Basic mają podobne nazwy, ale różne cele.</span><span class="sxs-lookup"><span data-stu-id="1aeb6-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="1aeb6-104">W tym temacie opisano każdy z tych obiektów w celu ich rozróżnienia.</span><span class="sxs-lookup"><span data-stu-id="1aeb6-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="1aeb6-105">Me</span><span class="sxs-lookup"><span data-stu-id="1aeb6-105">Me</span></span>  
 <span data-ttu-id="1aeb6-106">Słowo kluczowe `Me` umożliwia odwołanie się do konkretnego wystąpienia klasy lub struktury, w którym aktualnie wykonywany jest kod.</span><span class="sxs-lookup"><span data-stu-id="1aeb6-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="1aeb6-107">`Me` zachowuje się jak zmienna obiektu lub struktury, odwołując się do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1aeb6-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="1aeb6-108">Używanie słowa kluczowego `Me` jest szczególnie przydatne do przekazywania informacji o aktualnie wykonywanej instancji klasy lub struktury do procedury w innej klasie, strukturze lub module.</span><span class="sxs-lookup"><span data-stu-id="1aeb6-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="1aeb6-109">Załóżmy na przykład, że masz w module następującą procedurę.</span><span class="sxs-lookup"><span data-stu-id="1aeb6-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="1aeb6-110">Możesz wywołać tę procedurę i przekazać bieżące wystąpienie klasy <xref:System.Windows.Forms.Form> jako argument, używając następującej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1aeb6-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="1aeb6-111">My</span><span class="sxs-lookup"><span data-stu-id="1aeb6-111">My</span></span>  
 <span data-ttu-id="1aeb6-112">`My` Funkcja udostępnia proste i intuicyjne szereg klas .NET Framework, umożliwiając użytkownikowi języka Visual Basic do interakcji z komputera, aplikacji, ustawień, zasobów i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="1aeb6-112">The `My` feature provides easy and intuitive access to a number of .NET Framework classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="1aeb6-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="1aeb6-113">MyBase</span></span>  
 <span data-ttu-id="1aeb6-114">Słowo kluczowe `MyBase` zachowuje się jak zmienna obiektu odwołująca się do klasy bazowej bieżącego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="1aeb6-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="1aeb6-115">Słowo kluczowe `MyBase` jest najczęściej używane do dostępu do składowych klasy bazowej, które zostały zastąpione lub przesłonięte w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="1aeb6-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="1aeb6-116">`MyBase.New` służy do jawnego wywołania konstruktora klasy bazowej w konstruktorze klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="1aeb6-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="1aeb6-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="1aeb6-117">MyClass</span></span>  
 <span data-ttu-id="1aeb6-118">Słowo kluczowe `MyClass` zachowuje się jak odwołanie do bieżącego wystąpienia klasy zgodnie z pierwotną implementacją.</span><span class="sxs-lookup"><span data-stu-id="1aeb6-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="1aeb6-119">`MyClass` przypomina `Me`, ale wszystkie wywołania metod na tym słowie kluczowym są traktowane tak, jakby były `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="1aeb6-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aeb6-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1aeb6-120">See also</span></span>

- [<span data-ttu-id="1aeb6-121">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="1aeb6-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
