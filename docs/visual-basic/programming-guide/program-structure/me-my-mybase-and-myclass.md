---
title: Me, My, MyBase, i MyClass w Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bebf404cd65d1b3a2c4059d3a7c986f0157dfe2d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="794ff-102">Me, My, MyBase, i MyClass w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="794ff-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="794ff-103">`Me`, `My`, `MyBase`, i `MyClass` w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] mają podobne nazwy, ale różnych celów.</span><span class="sxs-lookup"><span data-stu-id="794ff-103">`Me`, `My`, `MyBase`, and `MyClass` in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] have similar names, but different purposes.</span></span> <span data-ttu-id="794ff-104">W tym temacie opisano każdy z tych obiektów, aby odróżnić je.</span><span class="sxs-lookup"><span data-stu-id="794ff-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="794ff-105">Mnie</span><span class="sxs-lookup"><span data-stu-id="794ff-105">Me</span></span>  
 <span data-ttu-id="794ff-106">`Me` — Słowo kluczowe zapewnia sposób odwołania do konkretnego wystąpienia klasy lub struktury, w którym kod jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="794ff-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="794ff-107">`Me`zachowuje się jak zmienna obiektu lub zmienna struktury odwołanie do bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="794ff-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="794ff-108">Przy użyciu `Me` jest szczególnie przydatne podczas przekazywania informacji o obecnie wykonywanym wystąpienia klasy lub struktury do procedury w innej klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="794ff-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="794ff-109">Na przykład załóżmy, że masz następujące procedury w module.</span><span class="sxs-lookup"><span data-stu-id="794ff-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="794ff-110">Możesz nazwać tę procedurę i przekazać bieżące wystąpienie klasy <xref:System.Windows.Forms.Form> klasy jako argument przy użyciu następujących instrukcji.</span><span class="sxs-lookup"><span data-stu-id="794ff-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="794ff-111">Moje</span><span class="sxs-lookup"><span data-stu-id="794ff-111">My</span></span>  
 <span data-ttu-id="794ff-112">`My` Funkcji umożliwia proste i intuicyjne dostęp do wielu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] klas, włączanie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] użytkownika do interakcji z komputera, aplikacji, ustawień, zasobów i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="794ff-112">The `My` feature provides easy and intuitive access to a number of [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes, enabling the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="794ff-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="794ff-113">MyBase</span></span>  
 <span data-ttu-id="794ff-114">`MyBase` — Słowo kluczowe zachowuje się jak zmienna obiektu odwołujące się do klasy bazowej bieżącego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="794ff-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="794ff-115">`MyBase`jest najczęściej używany do dostęp do elementów członkowskich klasy podstawowej, które są zastępowane lub cieniowanie w klasie pochodnej.</span><span class="sxs-lookup"><span data-stu-id="794ff-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="794ff-116">`MyBase.New`Służy do jawnie wywołać konstruktora klasy podstawowej z konstruktora klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="794ff-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="794ff-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="794ff-117">MyClass</span></span>  
 <span data-ttu-id="794ff-118">`MyClass` — Słowo kluczowe zachowuje się jak zmienna obiektu odwołanie do bieżącego wystąpienia klasy pierwotnie zaimplementowanych.</span><span class="sxs-lookup"><span data-stu-id="794ff-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="794ff-119">`MyClass`przypomina `Me`, ale wszystkie wywołania metody na nim są traktowane jak gdyby metoda `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="794ff-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="794ff-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="794ff-120">See Also</span></span>  
 [<span data-ttu-id="794ff-121">Podstawowe informacje o dziedziczeniu</span><span class="sxs-lookup"><span data-stu-id="794ff-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
