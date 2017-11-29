---
title: "Konwersja boxing typów dopuszczających wartości zerowe (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 29fccba56f6758fdfd407fa1879baa9260b69187
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="boxing-nullable-types-c-programming-guide"></a><span data-ttu-id="c50fd-102">Konwersja boxing typów dopuszczających wartości zerowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c50fd-102">Boxing Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="c50fd-103">Obiekty na podstawie typów wartości null są opakowany tylko, jeśli obiekt jest inne niż null.</span><span class="sxs-lookup"><span data-stu-id="c50fd-103">Objects based on nullable types are only boxed if the object is non-null.</span></span> <span data-ttu-id="c50fd-104">Jeśli <xref:System.Nullable%601.HasValue%2A> jest `false`, odwołanie do obiektu jest przypisany do `null` zamiast boxing.</span><span class="sxs-lookup"><span data-stu-id="c50fd-104">If <xref:System.Nullable%601.HasValue%2A> is `false`, the object reference is assigned to `null` instead of boxing.</span></span> <span data-ttu-id="c50fd-105">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c50fd-105">For example:</span></span>  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 <span data-ttu-id="c50fd-106">Jeśli obiekt jest różna od null — Jeśli <xref:System.Nullable%601.HasValue%2A> jest `true` — następnie konwersja boxing występuje, ale tylko na podstawie wartości null obiekt podstawowy typ jest opakowany.</span><span class="sxs-lookup"><span data-stu-id="c50fd-106">If the object is non-null -- if <xref:System.Nullable%601.HasValue%2A> is `true` -- then boxing occurs, but only the underlying type that the nullable object is based on is boxed.</span></span> <span data-ttu-id="c50fd-107">Konwersja boxing typ innych niż null wartości null wartości pola typu wartości, nie <xref:System.Nullable%601?displayProperty=nameWithType> zawija się typ wartości.</span><span class="sxs-lookup"><span data-stu-id="c50fd-107">Boxing a non-null nullable value type boxes the value type itself, not the <xref:System.Nullable%601?displayProperty=nameWithType> that wraps the value type.</span></span> <span data-ttu-id="c50fd-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c50fd-108">For example:</span></span>  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 <span data-ttu-id="c50fd-109">Dwa obiekty opakowanego są takie same jak te utworzone przez boxing typów wartości null.</span><span class="sxs-lookup"><span data-stu-id="c50fd-109">The two boxed objects are identical to those created by boxing non-nullable types.</span></span> <span data-ttu-id="c50fd-110">I tak samo jak typy opakowanego wartości null, mogą być rozpakowany do typów dopuszczających wartości zerowe, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c50fd-110">And, just like non-nullable boxed types, they can be unboxed into nullable types, as in the following example:</span></span>  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a><span data-ttu-id="c50fd-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c50fd-111">Remarks</span></span>  
 <span data-ttu-id="c50fd-112">Zachowanie typy dopuszczające wartości null, gdy opakowany dwie zalety:</span><span class="sxs-lookup"><span data-stu-id="c50fd-112">The behavior of nullable types when boxed provides two advantages:</span></span>  
  
1.  <span data-ttu-id="c50fd-113">Dopuszczające wartości zerowe obiektów i ich odpowiednika ramce można sprawdzane pod kątem wartości null:</span><span class="sxs-lookup"><span data-stu-id="c50fd-113">Nullable objects and their boxed counterpart can be tested for null:</span></span>  
  
    ```csharp  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  <span data-ttu-id="c50fd-114">Opakowany typy dopuszczające wartości zerowe obsługują w pełni funkcje typ bazowy:</span><span class="sxs-lookup"><span data-stu-id="c50fd-114">Boxed nullable types fully support the functionality of the underlying type:</span></span>  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c50fd-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c50fd-115">See Also</span></span>  
 [<span data-ttu-id="c50fd-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c50fd-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c50fd-117">Typy dopuszczające wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="c50fd-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="c50fd-118">Porady: Identyfikowanie typu dopuszczającego wartość null</span><span class="sxs-lookup"><span data-stu-id="c50fd-118">How to: Identify a Nullable Type</span></span>](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
