---
title: Implementacja metody w formantach niestandardowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], method implementation
- custom controls [Windows Forms], overloading methods
- custom controls [Windows Forms], method implementation
- methods [Windows Forms]
- methods [Windows Forms], custom controls
ms.assetid: 35d14fca-4bb4-4a27-8211-1f7a98ea27de
ms.openlocfilehash: 867bf97ea13654de6f9c0209c64b9320824f9665
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931751"
---
# <a name="method-implementation-in-custom-controls"></a><span data-ttu-id="3713f-102">Implementacja metody w formantach niestandardowych</span><span class="sxs-lookup"><span data-stu-id="3713f-102">Method Implementation in Custom Controls</span></span>
<span data-ttu-id="3713f-103">Metoda jest implementowana w kontrolce w taki sam sposób, jak metoda zostanie zaimplementowana w innym składniku.</span><span class="sxs-lookup"><span data-stu-id="3713f-103">A method is implemented in a control in the same manner a method would be implemented in any other component.</span></span>  
  
 <span data-ttu-id="3713f-104">W Visual Basic, jeśli metoda jest wymagana do zwrócenia wartości, zostanie zaimplementowana jako `Public Function`.</span><span class="sxs-lookup"><span data-stu-id="3713f-104">In Visual Basic, if a method is required to return a value, it is implemented as a `Public Function`.</span></span> <span data-ttu-id="3713f-105">Jeśli żadna wartość nie zostanie zwrócona, zostanie zaimplementowana jako `Public Sub`.</span><span class="sxs-lookup"><span data-stu-id="3713f-105">If no value is returned, it is implemented as a `Public Sub`.</span></span> <span data-ttu-id="3713f-106">Metody są deklarowane przy użyciu następującej składni:</span><span class="sxs-lookup"><span data-stu-id="3713f-106">Methods are declared using the following syntax:</span></span>  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 <span data-ttu-id="3713f-107">Ponieważ funkcje zwracają wartość, muszą określić zwracany typ, taki jak Integer, String, Object i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="3713f-107">Because functions return a value, they must specify a return type, such as integer, string, object, and so on.</span></span> <span data-ttu-id="3713f-108">Należy również `Function` określić `Sub` argumenty lub procedury, jeśli istnieją.</span><span class="sxs-lookup"><span data-stu-id="3713f-108">The arguments `Function` or `Sub` procedures take, if any, must also be specified.</span></span>  
  
 <span data-ttu-id="3713f-109">C#nie wykonuje rozróżnienia między funkcjami i procedurami, jak Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3713f-109">C# makes no distinction between functions and procedures, as Visual Basic does.</span></span> <span data-ttu-id="3713f-110">Metoda zwraca wartość lub zwraca `void`.</span><span class="sxs-lookup"><span data-stu-id="3713f-110">A method either returns a value or returns `void`.</span></span> <span data-ttu-id="3713f-111">Składnia do deklarowania metody C# publicznej to:</span><span class="sxs-lookup"><span data-stu-id="3713f-111">The syntax for declaring a C# public method is:</span></span>  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 <span data-ttu-id="3713f-112">Podczas deklarowania metody należy zadeklarować wszystkie jej argumenty jako jawne typy danych zawsze wtedy, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="3713f-112">When you declare a method, declare all of its arguments as explicit data types whenever possible.</span></span> <span data-ttu-id="3713f-113">Argumenty, które przyjmują odwołania do obiektów, powinny być deklarowane jako określone typy `As Widget` klas — `As Object`na przykład, zamiast.</span><span class="sxs-lookup"><span data-stu-id="3713f-113">Arguments that take object references should be declared as specific class types — for example, `As Widget` instead of `As Object`.</span></span> <span data-ttu-id="3713f-114">W Visual Basic domyślne ustawienie `Option Strict` automatycznie wymusza tę regułę.</span><span class="sxs-lookup"><span data-stu-id="3713f-114">In Visual Basic, the default setting `Option Strict` automatically enforces this rule.</span></span>  
  
 <span data-ttu-id="3713f-115">Wpisane argumenty umożliwiają przechwycić wiele błędów dewelopera przez kompilator, a nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3713f-115">Typed arguments allow many developer errors to be caught by the compiler, rather than at run time.</span></span> <span data-ttu-id="3713f-116">Kompilator zawsze przechwytuje błędy, podczas gdy testowanie w czasie wykonywania jest dobrym warunkiem jako zestaw testów.</span><span class="sxs-lookup"><span data-stu-id="3713f-116">The compiler always catches errors, whereas run-time testing is only as good as the test suite.</span></span>  
  
## <a name="overloaded-methods"></a><span data-ttu-id="3713f-117">Przeciążone metody</span><span class="sxs-lookup"><span data-stu-id="3713f-117">Overloaded Methods</span></span>  
 <span data-ttu-id="3713f-118">Jeśli chcesz zezwolić użytkownikom formantu na dostarczanie różnych kombinacji parametrów do metody, podaj wiele przeciążeń metody przy użyciu jawnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="3713f-118">If you want to allow users of your control to supply different combinations of parameters to a method, provide multiple overloads of the method, using explicit data types.</span></span> <span data-ttu-id="3713f-119">Unikaj tworzenia zadeklarowanych `As Object` parametrów, które mogą zawierać dowolny typ danych, ponieważ może to prowadzić do błędów, które mogą nie zostać przechwycone podczas testowania.</span><span class="sxs-lookup"><span data-stu-id="3713f-119">Avoid creating parameters declared `As Object` that can contain any data type, as this can lead to errors that might not be caught in testing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3713f-120">Uniwersalny typ danych w środowisku uruchomieniowym języka wspólnego jest `Object` `Variant`zamiast.</span><span class="sxs-lookup"><span data-stu-id="3713f-120">The universal data type in the common language runtime is `Object` rather than `Variant`.</span></span> <span data-ttu-id="3713f-121">`Variant`został usunięty z języka.</span><span class="sxs-lookup"><span data-stu-id="3713f-121">`Variant` has been removed from the language.</span></span>  
  
 <span data-ttu-id="3713f-122">Na przykład `Spin` Metoda hipotetycznej `Widget` kontrolki może zezwalać na bezpośrednią specyfikację kierunku i szybkości pokrętła lub specyfikacją innego `Widget` obiektu, z którego ma być pochłaniana wartość kąta kątowego:</span><span class="sxs-lookup"><span data-stu-id="3713f-122">For example, the `Spin` method of a hypothetical `Widget` control might allow either direct specification of spin direction and speed, or specification of another `Widget` object from which angular momentum is to be absorbed:</span></span>  
  
```vb  
Overloads Public Sub Spin( _  
   ByVal SpinDirection As SpinDirectionsEnum, _  
   ByVal RevolutionsPerSecond As Double)  
   ' Implementation code here.  
End Sub  
Overloads Public Sub Spin(ByVal Driver As Widget) _  
   ' Implementation code here.  
End Sub  
```  
  
```csharp  
public void Spin(SpinDirectionsEnum spinDirection, double revolutionsPerSecond)  
{  
   // Implementation code here.  
}  
  
public void Spin(Widget driver)  
{  
   // Implementation code here.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3713f-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3713f-123">See also</span></span>

- [<span data-ttu-id="3713f-124">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="3713f-124">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="3713f-125">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3713f-125">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
