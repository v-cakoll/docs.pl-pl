---
title: 'Porady: określanie, czy dwa obiekty są powiązane (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], Visual Basic objects
- objects [Visual Basic], inheritance
- object variables [Visual Basic], determining relation
ms.assetid: da002e3f-6616-4bad-a229-f842d06652bb
ms.openlocfilehash: 2041f89ffd954e479046eb85c6dd82de1f8793ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649828"
---
# <a name="how-to-determine-whether-two-objects-are-related-visual-basic"></a><span data-ttu-id="5c5ba-102">Porady: określanie, czy dwa obiekty są powiązane (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c5ba-102">How to: Determine Whether Two Objects Are Related (Visual Basic)</span></span>
<span data-ttu-id="5c5ba-103">Możesz porównać dwa obiekty określenia relacji między klasami, z których są tworzone.</span><span class="sxs-lookup"><span data-stu-id="5c5ba-103">You can compare two objects to determine the relationship, if any, between the classes from which they are created.</span></span> <span data-ttu-id="5c5ba-104"><xref:System.Type.IsInstanceOfType%2A> Metody <xref:System.Type?displayProperty=nameWithType> klasy zwraca `True` czy określonej klasy dziedziczy z klasy, czy bieżący typ jest interfejsem obsługiwane przez określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="5c5ba-104">The <xref:System.Type.IsInstanceOfType%2A> method of the <xref:System.Type?displayProperty=nameWithType> class returns `True` if the specified class inherits from the current class, or if the current type is an interface supported by the specified class.</span></span>  
  
### <a name="to-determine-if-one-object-inherits-from-another-objects-class-or-interface"></a><span data-ttu-id="5c5ba-105">Aby określić, jeśli jeden obiekt dziedziczy z klasy lub interfejsu innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5c5ba-105">To determine if one object inherits from another object's class or interface</span></span>  
  
1.  <span data-ttu-id="5c5ba-106">W obiekcie uważasz, że może być typu podstawowego, wywołaj <xref:System.Object.GetType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5c5ba-106">On the object you think might be of the base type, invoke the <xref:System.Object.GetType%2A> method.</span></span>  
  
2.  <span data-ttu-id="5c5ba-107">Na <xref:System.Type?displayProperty=nameWithType> obiektu zwróconego przez <xref:System.Object.GetType%2A>, wywołaj <xref:System.Type.IsInstanceOfType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5c5ba-107">On the <xref:System.Type?displayProperty=nameWithType> object returned by <xref:System.Object.GetType%2A>, invoke the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
3.  <span data-ttu-id="5c5ba-108">Na liście argumentów dla <xref:System.Type.IsInstanceOfType%2A>, określ uważasz, że obiekt może być typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="5c5ba-108">In the argument list for <xref:System.Type.IsInstanceOfType%2A>, specify the object you think might be of the derived type.</span></span>  
  
     <span data-ttu-id="5c5ba-109"><xref:System.Type.IsInstanceOfType%2A> Zwraca `True` jeśli jego typ argumentu dziedziczy <xref:System.Type?displayProperty=nameWithType> typu obiektu.</span><span class="sxs-lookup"><span data-stu-id="5c5ba-109"><xref:System.Type.IsInstanceOfType%2A> returns `True` if its argument type inherits from the <xref:System.Type?displayProperty=nameWithType> object type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c5ba-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c5ba-110">Example</span></span>  
 <span data-ttu-id="5c5ba-111">Poniższy przykład określa, czy jeden obiekt reprezentuje klasę pochodzącą od klasy innego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5c5ba-111">The following example determines whether one object represents a class derived from another object's class.</span></span>  
  
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
  
 <span data-ttu-id="5c5ba-112">Należy pamiętać, nieoczekiwany umieszczania zmiennych dwóch obiektów w wywołaniu <xref:System.Type.IsInstanceOfType%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c5ba-112">Note the unexpected placement of the two object variables in the call to <xref:System.Type.IsInstanceOfType%2A>.</span></span> <span data-ttu-id="5c5ba-113">Domniemana typ podstawowy jest używany do generowania <xref:System.Type?displayProperty=nameWithType> klasy i właściwego typu pochodnego jest przekazywany jako argument <xref:System.Type.IsInstanceOfType%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5c5ba-113">The supposed base type is used to generate the <xref:System.Type?displayProperty=nameWithType> class, and the supposed derived type is passed as an argument to the <xref:System.Type.IsInstanceOfType%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c5ba-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c5ba-114">See Also</span></span>  
 <xref:System.Object.GetType%2A>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Type.IsInstanceOfType%2A>  
 [<span data-ttu-id="5c5ba-115">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="5c5ba-115">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="5c5ba-116">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="5c5ba-116">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="5c5ba-117">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="5c5ba-117">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="5c5ba-118">Instrukcje: określanie, czy dwa obiekty są jednakowe</span><span class="sxs-lookup"><span data-stu-id="5c5ba-118">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
