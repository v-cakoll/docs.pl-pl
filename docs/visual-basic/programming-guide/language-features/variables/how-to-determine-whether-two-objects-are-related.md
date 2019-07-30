---
title: 'Instrukcje: Określanie, czy dwa obiekty są powiązane (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2b17be4ef5a7dabfc4779ab6f5675cc2baec9c3c
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68626556"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="9a13b-102">Instrukcje: Określanie, czy dwa obiekty są powiązane (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a13b-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>

<span data-ttu-id="9a13b-103">Można porównać dwa obiekty, aby określić relację, jeśli istnieje, między klasami, z których zostały utworzone.</span><span class="sxs-lookup"><span data-stu-id="9a13b-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="9a13b-104"><xref:System.Type.IsInstanceOfType%2A> Metoda klasy<xref:System.Type?displayProperty=nameWithType> zwraca ,jeśliokreślonaklasadziedziczyzbieżącejklasylubjeślibieżącytypjest`True` interfejsem obsługiwanym przez określoną klasę.</span><span class="sxs-lookup"><span data-stu-id="9a13b-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>

### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="9a13b-105">Aby określić, czy jeden obiekt dziedziczy z klasy lub interfejsu innego obiektu</span><span class="sxs-lookup"><span data-stu-id="9a13b-105">To determine if one object inherits from another object's class or interface</span></span>

1. <span data-ttu-id="9a13b-106">Na obiekcie, który sądzisz, może być typu podstawowego, wywołaj <xref:System.Object.GetType%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="9a13b-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>

2. <span data-ttu-id="9a13b-107">Dla obiektu zwróconego przez <xref:System.Object.GetType%2A>, wywołaj <xref:System.Type.IsInstanceOfType%2A> metodę. <xref:System.Type?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9a13b-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

3. <span data-ttu-id="9a13b-108">Na liście argumentów dla <xref:System.Type.IsInstanceOfType%2A>Określ obiekt, który może być typem pochodnym.</span><span class="sxs-lookup"><span data-stu-id="9a13b-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>

    <span data-ttu-id="9a13b-109"><xref:System.Type.IsInstanceOfType%2A>zwraca `True` wartość, jeśli jej typ argumentu dziedziczy <xref:System.Type?displayProperty=nameWithType> z typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="9a13b-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>

## <a name="example"></a><span data-ttu-id="9a13b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a13b-110">Example</span></span>
 <span data-ttu-id="9a13b-111">Poniższy przykład określa, czy jeden obiekt reprezentuje klasę pochodzącą od klasy innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="9a13b-111">The following example determines whether one object represents a class derived from another object's class.</span></span>

```vb
Public Class baseClass
End Class
Public Class derivedClass : Inherits baseClass
End Class
Public Class testTheseClasses
    Public Sub seeIfRelated()
        Dim baseObj As Object = New baseClass()
        Dim derivedObj As Object = New derivedClass()
        Dim related As Boolean
        related = baseObj.GetType().IsInstanceOfType(derivedObj)
        MsgBox(CStr(related))
    End Sub
End Class
```

<span data-ttu-id="9a13b-112">Zwróć uwagę na nieoczekiwane rozmieszczenie dwóch zmiennych obiektów w wywołaniu <xref:System.Type.IsInstanceOfType%2A>.</span><span class="sxs-lookup"><span data-stu-id="9a13b-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="9a13b-113">Przypuszczalny typ podstawowy jest używany do generowania <xref:System.Type?displayProperty=nameWithType> klasy, a typ pochodny jest przenoszona jako argument <xref:System.Type.IsInstanceOfType%2A> do metody.</span><span class="sxs-lookup"><span data-stu-id="9a13b-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a13b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a13b-114">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [<span data-ttu-id="9a13b-115">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="9a13b-115">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="9a13b-116">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="9a13b-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="9a13b-117">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="9a13b-117">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="9a13b-118">Instrukcje: Określanie, czy dwa obiekty są identyczne</span><span class="sxs-lookup"><span data-stu-id="9a13b-118">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
