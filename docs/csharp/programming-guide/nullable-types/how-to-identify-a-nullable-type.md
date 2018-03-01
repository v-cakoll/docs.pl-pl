---
title: "Porady: identyfikowanie typu dopuszczającego wartość zerową (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 610ed18308df02c5632361cd09ef94330dea598b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="cddd3-102">Porady: identyfikowanie typu dopuszczającego wartość zerową (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="cddd3-102">How to: Identify a Nullable Type (C# Programming Guide)</span></span>
<span data-ttu-id="cddd3-103">Można użyć języka C# [typeof](../../../csharp/language-reference/keywords/typeof.md) operatora do utworzenia <xref:System.Type> obiekt, który reprezentuje typ dopuszczający wartość null:</span><span class="sxs-lookup"><span data-stu-id="cddd3-103">You can use the C# [typeof](../../../csharp/language-reference/keywords/typeof.md) operator to create a <xref:System.Type> object that represents a Nullable type:</span></span>  
  
```  
System.Type type = typeof(int?);  
```  
  
 <span data-ttu-id="cddd3-104">Można również użyć klasy i metody <xref:System.Reflection> przestrzeni nazw, aby wygenerować <xref:System.Type> obiektów, które reprezentują typy dopuszczające wartości zerowe.</span><span class="sxs-lookup"><span data-stu-id="cddd3-104">You can also use the classes and methods of the <xref:System.Reflection> namespace to generate <xref:System.Type> objects that represent Nullable types.</span></span> <span data-ttu-id="cddd3-105">Jednak Jeśli spróbujesz uzyskać informacji o typie z wartości null zmienne w czasie wykonywania za pomocą <xref:System.Object.GetType%2A> — metoda lub `is` operatora, wynikiem jest <xref:System.Type> obiekt, który reprezentuje typ podstawowy nie Nullable wpisz samej siebie.</span><span class="sxs-lookup"><span data-stu-id="cddd3-105">However, if you try to obtain type information from Nullable variables at runtime by using the <xref:System.Object.GetType%2A> method or the `is` operator, the result is a <xref:System.Type> object that represents the underlying type, not the Nullable type itself.</span></span>  
  
 <span data-ttu-id="cddd3-106">Wywoływanie `GetType` na typu Nullable typu powoduje, że na opakowanie operacji można wykonać, gdy typ jest niejawnie przekonwertowana na <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="cddd3-106">Calling `GetType` on a Nullable type causes a boxing operation to be performed when the type is implicitly converted to <xref:System.Object>.</span></span> <span data-ttu-id="cddd3-107">W związku z tym <xref:System.Object.GetType%2A> zawsze zwraca <xref:System.Type> obiekt, który reprezentuje typ podstawowy typ dopuszczający wartość null.</span><span class="sxs-lookup"><span data-stu-id="cddd3-107">Therefore <xref:System.Object.GetType%2A> always returns a <xref:System.Type> object that represents the underlying type, not the Nullable type.</span></span>  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 <span data-ttu-id="cddd3-108">C# [jest](../../../csharp/language-reference/keywords/is.md) operator również działa na typ podstawowy typu Nullable.</span><span class="sxs-lookup"><span data-stu-id="cddd3-108">The C# [is](../../../csharp/language-reference/keywords/is.md) operator also operates on a Nullable's underlying type.</span></span> <span data-ttu-id="cddd3-109">W związku z tym nie można użyć `is` do ustalenia, czy zmienna jest typu dopuszczającego wartość null.</span><span class="sxs-lookup"><span data-stu-id="cddd3-109">Therefore you cannot use `is` to determine whether a variable is a Nullable type.</span></span> <span data-ttu-id="cddd3-110">W poniższym przykładzie pokazano, że `is` operator traktuje typu Nullable\<int > zmiennej jako int.</span><span class="sxs-lookup"><span data-stu-id="cddd3-110">The following example shows that the `is` operator treats a Nullable\<int> variable as an int.</span></span>  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## <a name="example"></a><span data-ttu-id="cddd3-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="cddd3-111">Example</span></span>  
 <span data-ttu-id="cddd3-112">Poniższy kod umożliwia określenie, czy <xref:System.Type> obiekt reprezentuje typ dopuszczający wartość null.</span><span class="sxs-lookup"><span data-stu-id="cddd3-112">Use the following code to determine whether a <xref:System.Type> object represents a Nullable type.</span></span> <span data-ttu-id="cddd3-113">Należy pamiętać, że ten kod zawsze zwraca wartość false, jeśli `Type` obiektu zwróconego przez wywołanie <xref:System.Object.GetType%2A>, jak opisano wcześniej w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="cddd3-113">Remember that this code always returns false if the `Type` object was returned from a call to <xref:System.Object.GetType%2A>, as explained earlier in this topic.</span></span>  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cddd3-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cddd3-114">See Also</span></span>  
 [<span data-ttu-id="cddd3-115">Typy dopuszczające wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="cddd3-115">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="cddd3-116">Konwersja boxing typów dopuszczających wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="cddd3-116">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)
