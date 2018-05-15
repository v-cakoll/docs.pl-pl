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
ms.openlocfilehash: 9df2bc9257c3f697f30cbe8c679ffc88ec34517b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="method-implementation-in-custom-controls"></a><span data-ttu-id="18ee8-102">Implementacja metody w formantach niestandardowych</span><span class="sxs-lookup"><span data-stu-id="18ee8-102">Method Implementation in Custom Controls</span></span>
<span data-ttu-id="18ee8-103">Metoda jest zaimplementowana w formancie w taki sam sposób, które metody są realizowane w innych składników.</span><span class="sxs-lookup"><span data-stu-id="18ee8-103">A method is implemented in a control in the same manner a method would be implemented in any other component.</span></span>  
  
 <span data-ttu-id="18ee8-104">W języku Visual Basic, jeśli metoda jest wymagane w celu zwrócenia wartości, są one zaimplementowane jako `Public Function`.</span><span class="sxs-lookup"><span data-stu-id="18ee8-104">In Visual Basic, if a method is required to return a value, it is implemented as a `Public Function`.</span></span> <span data-ttu-id="18ee8-105">Jeśli wartość nie zostanie zwrócone, jest zaimplementowany jako `Public Sub`.</span><span class="sxs-lookup"><span data-stu-id="18ee8-105">If no value is returned, it is implemented as a `Public Sub`.</span></span> <span data-ttu-id="18ee8-106">Metody zadeklarowane za pomocą następującej składni:</span><span class="sxs-lookup"><span data-stu-id="18ee8-106">Methods are declared using the following syntax:</span></span>  
  
```vb  
Public Function ConvertMatterToEnergy(Matter as Integer) As Integer  
   ' Conversion code goes here.  
End Function  
```  
  
 <span data-ttu-id="18ee8-107">Ponieważ funkcje zwracają wartość, musi określić typ zwracany, takie jak liczba całkowita, ciąg, obiekt i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="18ee8-107">Because functions return a value, they must specify a return type, such as integer, string, object, and so on.</span></span> <span data-ttu-id="18ee8-108">Argumenty `Function` lub `Sub` wykonać procedury, jeśli istnieje, należy także określić.</span><span class="sxs-lookup"><span data-stu-id="18ee8-108">The arguments `Function` or `Sub` procedures take, if any, must also be specified.</span></span>  
  
 <span data-ttu-id="18ee8-109">C# nie rozróżnia między funkcje i procedury, tak jak w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="18ee8-109">C# makes no distinction between functions and procedures, as Visual Basic does.</span></span> <span data-ttu-id="18ee8-110">Metoda zwraca wartość lub zwraca `void`.</span><span class="sxs-lookup"><span data-stu-id="18ee8-110">A method either returns a value or returns `void`.</span></span> <span data-ttu-id="18ee8-111">Składnia deklaracji publiczną metodę C# jest:</span><span class="sxs-lookup"><span data-stu-id="18ee8-111">The syntax for declaring a C# public method is:</span></span>  
  
```csharp  
public int ConvertMatterToEnergy(int matter)  
{  
   // Conversion code goes here.  
}  
```  
  
 <span data-ttu-id="18ee8-112">W deklaracji metody, należy zadeklarować wszystkie argumenty jako typy danych jawne, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="18ee8-112">When you declare a method, declare all of its arguments as explicit data types whenever possible.</span></span> <span data-ttu-id="18ee8-113">Argumenty, które przyjmują odwołania do obiektów powinien być zadeklarowany jako klasa określonych typów — na przykład `As Widget` zamiast `As Object`.</span><span class="sxs-lookup"><span data-stu-id="18ee8-113">Arguments that take object references should be declared as specific class types — for example, `As Widget` instead of `As Object`.</span></span> <span data-ttu-id="18ee8-114">W języku Visual Basic, domyślne ustawienie `Option Strict` automatycznie wymusza tej reguły.</span><span class="sxs-lookup"><span data-stu-id="18ee8-114">In Visual Basic, the default setting `Option Strict` automatically enforces this rule.</span></span>  
  
 <span data-ttu-id="18ee8-115">Argumenty typu Zezwalaj na wiele błędów developer wychwycony przez kompilator, a nie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="18ee8-115">Typed arguments allow many developer errors to be caught by the compiler, rather than at run time.</span></span> <span data-ttu-id="18ee8-116">Kompilator zawsze połowy błędów, natomiast czasu wykonywania testów jest tylko zestaw testów.</span><span class="sxs-lookup"><span data-stu-id="18ee8-116">The compiler always catches errors, whereas run-time testing is only as good as the test suite.</span></span>  
  
## <a name="overloaded-methods"></a><span data-ttu-id="18ee8-117">Metody przeciążane</span><span class="sxs-lookup"><span data-stu-id="18ee8-117">Overloaded Methods</span></span>  
 <span data-ttu-id="18ee8-118">Jeśli chcesz umożliwić użytkownikom formantu umożliwiają określanie kombinacji parametrów do metody, zawierają wiele przeciążenia metody, przy użyciu jawnych typów.</span><span class="sxs-lookup"><span data-stu-id="18ee8-118">If you want to allow users of your control to supply different combinations of parameters to a method, provide multiple overloads of the method, using explicit data types.</span></span> <span data-ttu-id="18ee8-119">Unikaj tworzenia parametrami zadeklarowanymi jako `As Object` który może zawierać dowolny typ danych, ponieważ może to prowadzić do błędów, które nie mogą być przechwycono testowania.</span><span class="sxs-lookup"><span data-stu-id="18ee8-119">Avoid creating parameters declared `As Object` that can contain any data type, as this can lead to errors that might not be caught in testing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18ee8-120">Typ danych uniwersalnych w środowisku uruchomieniowym języka jest `Object` zamiast `Variant`.</span><span class="sxs-lookup"><span data-stu-id="18ee8-120">The universal data type in the common language runtime is `Object` rather than `Variant`.</span></span> <span data-ttu-id="18ee8-121">`Variant` została usunięta z języka.</span><span class="sxs-lookup"><span data-stu-id="18ee8-121">`Variant` has been removed from the language.</span></span>  
  
 <span data-ttu-id="18ee8-122">Na przykład `Spin` metody hipotetyczny `Widget` formant może zezwala na bezpośrednie specyfikacji pokrętła kierunek i szybkość lub specyfikacji innego `Widget` obiektu, z którym pędu jest pochłanianej:</span><span class="sxs-lookup"><span data-stu-id="18ee8-122">For example, the `Spin` method of a hypothetical `Widget` control might allow either direct specification of spin direction and speed, or specification of another `Widget` object from which angular momentum is to be absorbed:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="18ee8-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18ee8-123">See Also</span></span>  
 [<span data-ttu-id="18ee8-124">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="18ee8-124">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="18ee8-125">Właściwości kontrolek formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18ee8-125">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
