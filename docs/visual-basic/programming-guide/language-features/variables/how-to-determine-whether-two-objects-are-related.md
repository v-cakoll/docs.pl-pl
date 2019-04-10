---
title: 'Instrukcje: Określanie, czy dwa obiekty są powiązane (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: f59e00d80d28fc4bf24874d25b5c12643649c834
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342105"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="513f7-102">Instrukcje: Określanie, czy dwa obiekty są powiązane (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="513f7-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>
<span data-ttu-id="513f7-103">Możesz porównać dwa obiekty przeznaczone do określenia relacji między klasami, z których są tworzone.</span><span class="sxs-lookup"><span data-stu-id="513f7-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="513f7-104"><xref:System.Type.IsInstanceOfType%2A> Metody <xref:System.Type?displayProperty=nameWithType> klasy zwraca `True` czy określona klasa dziedziczy z klasy, czy bieżący typ jest interfejsem obsługiwanych przez określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="513f7-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="513f7-105">Aby określić, jeśli jeden obiekt dziedziczy z klasy lub interfejsu innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="513f7-105">To determine if one object inherits from another object's class or interface</span></span>  
  
1. <span data-ttu-id="513f7-106">W obiekcie Twoim zdaniem może być typu podstawowego, wywoływanie <xref:System.Object.GetType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="513f7-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>  
  
2. <span data-ttu-id="513f7-107">Na <xref:System.Type?displayProperty=nameWithType> obiektu zwróconego przez <xref:System.Object.GetType%2A>, wywołaj <xref:System.Type.IsInstanceOfType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="513f7-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
3. <span data-ttu-id="513f7-108">Na liście argumentów dla <xref:System.Type.IsInstanceOfType%2A>, określ obiekt Twoim zdaniem mogą być typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="513f7-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>  
  
     <xref:System.Type.IsInstanceOfType%2A> <span data-ttu-id="513f7-109">Zwraca `True` jeśli jego typ argumentu dziedziczy z <xref:System.Type?displayProperty=nameWithType> typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="513f7-109">returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="513f7-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="513f7-110">Example</span></span>  
 <span data-ttu-id="513f7-111">Poniższy przykład określa, czy jeden obiekt reprezentuje klasy pochodzącej od klasy innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="513f7-111">The following example determines whether one object represents a class derived from another object's class.</span></span>  
  
```  
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
  
 <span data-ttu-id="513f7-112">Należy pamiętać, nieoczekiwany umieszczania zmiennych dwóch obiektów w wywołaniu <xref:System.Type.IsInstanceOfType%2A>.</span><span class="sxs-lookup"><span data-stu-id="513f7-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="513f7-113">Umożliwia generowanie tymczasowego obiektu typu podstawowego <xref:System.Type?displayProperty=nameWithType> klasy i tymczasowego obiektu typu pochodnego jest przekazywany jako argument do <xref:System.Type.IsInstanceOfType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="513f7-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="513f7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="513f7-114">See also</span></span>

- <xref:System.Object.GetType%2A>
- <xref:System.Type?displayProperty=nameWithType>
- <xref:System.Type.IsInstanceOfType%2A>
- [<span data-ttu-id="513f7-115">Object — typ danych</span><span class="sxs-lookup"><span data-stu-id="513f7-115">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="513f7-116">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="513f7-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="513f7-117">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="513f7-117">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="513f7-118">Instrukcje: Określanie, czy dwa obiekty są jednakowe</span><span class="sxs-lookup"><span data-stu-id="513f7-118">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
