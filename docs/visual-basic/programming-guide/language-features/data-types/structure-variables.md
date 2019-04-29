---
title: Zmienne struktur (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 9a6e542e297a17f44d929235530ae6058cf13a36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663391"
---
# <a name="structure-variables-visual-basic"></a><span data-ttu-id="e2a44-102">Zmienne struktur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2a44-102">Structure Variables (Visual Basic)</span></span>
<span data-ttu-id="e2a44-103">Po utworzeniu struktury można zadeklarować zmienne poziom procedury i poziom modułu jako tego typu.</span><span class="sxs-lookup"><span data-stu-id="e2a44-103">Once you have created a structure, you can declare procedure-level and module-level variables as that type.</span></span> <span data-ttu-id="e2a44-104">Na przykład można utworzyć struktury rejestrującą informacje o systemie komputerowym.</span><span class="sxs-lookup"><span data-stu-id="e2a44-104">For example, you can create a structure that records information about a computer system.</span></span> <span data-ttu-id="e2a44-105">Poniższy przykład przedstawia to.</span><span class="sxs-lookup"><span data-stu-id="e2a44-105">The following example demonstrates this.</span></span>  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 <span data-ttu-id="e2a44-106">Możesz teraz zadeklarować zmienne tego typu.</span><span class="sxs-lookup"><span data-stu-id="e2a44-106">You can now declare variables of that type.</span></span> <span data-ttu-id="e2a44-107">Następująca deklaracja przedstawia to.</span><span class="sxs-lookup"><span data-stu-id="e2a44-107">The following declaration illustrates this.</span></span>  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  <span data-ttu-id="e2a44-108">W klasach i moduły struktury zadeklarowane za pomocą [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) domyślnie dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="e2a44-108">In classes and modules, structures declared using the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) default to public access.</span></span> <span data-ttu-id="e2a44-109">Jeśli planujesz struktury jako prywatny, upewnij się, można zadeklarować za pomocą [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="e2a44-109">If you intend a structure to be private, make sure you declare it using the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword.</span></span>  
  
## <a name="access-to-structure-values"></a><span data-ttu-id="e2a44-110">Dostęp do wartości struktury</span><span class="sxs-lookup"><span data-stu-id="e2a44-110">Access to Structure Values</span></span>  
 <span data-ttu-id="e2a44-111">Aby przypisać i pobieranie wartości z elementów tworzonej tablicy zmiennej struktury, należy użyć tej samej składni jak umożliwia ustawianie i pobieranie właściwości w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="e2a44-111">To assign and retrieve values from the elements of a structure variable, you use the same syntax as you use to set and get properties on an object.</span></span> <span data-ttu-id="e2a44-112">Umieść operator dostępu do elementu członkowskiego (`.`) między nazwą zmiennej struktury i nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="e2a44-112">You place the member access operator (`.`) between the structure variable name and the element name.</span></span> <span data-ttu-id="e2a44-113">Poniższy przykład uzyskuje dostęp do elementów zmiennych wcześniej zadeklarowany jako typ `systemInfo`.</span><span class="sxs-lookup"><span data-stu-id="e2a44-113">The following example accesses elements of the variables previously declared as type `systemInfo`.</span></span>  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a><span data-ttu-id="e2a44-114">Przypisywanie zmienne struktur</span><span class="sxs-lookup"><span data-stu-id="e2a44-114">Assigning Structure Variables</span></span>  
 <span data-ttu-id="e2a44-115">Można także przypisać jedną zmienną do innego, jeśli obie są tego samego typu struktury.</span><span class="sxs-lookup"><span data-stu-id="e2a44-115">You can also assign one variable to another if both are of the same structure type.</span></span> <span data-ttu-id="e2a44-116">Wszystkie elementy jedną strukturę to skopiowanie na odpowiednie elementy w innym.</span><span class="sxs-lookup"><span data-stu-id="e2a44-116">This copies all the elements of one structure to the corresponding elements in the other.</span></span> <span data-ttu-id="e2a44-117">Następująca deklaracja przedstawia to.</span><span class="sxs-lookup"><span data-stu-id="e2a44-117">The following declaration illustrates this.</span></span>  
  
```  
yourSystem = mySystem  
```  
  
 <span data-ttu-id="e2a44-118">Jeśli element struktury jest typu odwołania, takich jak `String`, `Object`, lub tablicy, wskaźnik do danych jest kopiowany.</span><span class="sxs-lookup"><span data-stu-id="e2a44-118">If a structure element is a reference type, such as a `String`, `Object`, or array, the pointer to the data is copied.</span></span> <span data-ttu-id="e2a44-119">W poprzednim przykładzie Jeśli `systemInfo` zawiera zmienną obiektu, a następnie w poprzednim przykładzie będą kopiowane wskaźnika z `mySystem` do `yourSystem`, a zmiany do obiektu danych za pomocą jedną strukturę będzie obowiązywać podczas uzyskiwania dostępu do za pomocą innych struktury.</span><span class="sxs-lookup"><span data-stu-id="e2a44-119">In the previous example, if `systemInfo` had included an object variable, then the preceding example would have copied the pointer from `mySystem` to `yourSystem`, and a change to the object's data through one structure would be in effect when accessed through the other structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2a44-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2a44-120">See also</span></span>

- [<span data-ttu-id="e2a44-121">Typy danych</span><span class="sxs-lookup"><span data-stu-id="e2a44-121">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="e2a44-122">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="e2a44-122">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="e2a44-123">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="e2a44-123">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="e2a44-124">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="e2a44-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="e2a44-125">Struktury</span><span class="sxs-lookup"><span data-stu-id="e2a44-125">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="e2a44-126">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="e2a44-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="e2a44-127">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="e2a44-127">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="e2a44-128">Struktury oraz inne elementy programowania</span><span class="sxs-lookup"><span data-stu-id="e2a44-128">Structures and Other Programming Elements</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [<span data-ttu-id="e2a44-129">Struktury i klasy</span><span class="sxs-lookup"><span data-stu-id="e2a44-129">Structures and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [<span data-ttu-id="e2a44-130">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e2a44-130">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
