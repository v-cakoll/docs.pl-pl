---
title: out — Modyfikator ogólny (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 95ccbe3ab5bf2d326e1154af0b169972a24f7e38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="out-generic-modifier-c-reference"></a>out — Modyfikator ogólny (odwołanie w C#)
Parametry typu ogólnego `out` — słowo kluczowe Określa, że parametr typu jest kowariantny. Można użyć `out` — słowo kluczowe w interfejsach i delegatów.  
  
 Kowariancja pozwala na użycie typu bardziej pochodnego od określonej przez parametr ogólny. Dzięki temu niejawna konwersja klas implementujących interfejsów typu variant i niejawna konwersja typów delegatów. Kowariancja i kontrawariancja są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.  
  
 Interfejs, który ma parametr typu kowariantnego umożliwia sposobów niż określony przez parametr typu bardziej pochodnego typy zwracane. Na przykład ponieważ w .NET Framework 4 w <xref:System.Collections.Generic.IEnumerable%601>typu T jest kowariantny, można przypisać obiektu `IEnumerable(Of String)` typu do obiektu `IEnumerable(Of Object)` typu bez korzystania z żadnych metod konwersji specjalnych.  
  
 Kowariantnego delegata można przypisać inną delegata tego samego typu, ale także z bardziej pochodny parametr typu ogólnego.  
  
 Aby uzyskać więcej informacji, zobacz [Kowariancja i Kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zadeklarować, rozszerzać i implementacji kowariantnego interfejs generyczny. On również przedstawia użycie niejawna konwersja dla klas implementujących interfejs kowariantny.  
  
 [!code-csharp[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 W interfejsie ogólny parametru typu mogą być deklarowane jako kowariantnego, spełnia następujące warunki:  
  
-   Parametr typu jest używany tylko jako typ zwracany metody interfejsu i nie jest używany jako typ argumentów metody.  
  
    > [!NOTE]
    >  Istnieje jeden wyjątek od tej reguły. Jeśli w interfejsie kowariantnego to delegat generyczny kontrawariantnego jako parametr metody, można użyć typu kowariantnego jako parametr typu ogólnego dla tego obiektu delegowanego. Aby uzyskać więcej informacji na temat kowariantnego i kontrawariantnego delegatów, zobacz [wariancji w Delegatach](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancję Func i delegatów akcji](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
-   Parametr typu nie jest używany jako ogólne ograniczenia dla metod interfejsu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zadeklarować, wystąpienia i wywoływać kowariantnego Delegat ogólny. Widoczny jest również sposób niejawnie przekonwertować typu delegowanego.  
  
 [!code-csharp[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 Delegat ogólny typu mogą być deklarowane kowariantnego Jeśli jest używany tylko jako typ zwracany metody i nie są używane dla argumentów metody.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wariancje w interfejsach ogólnych](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [in](../../../csharp/language-reference/keywords/in-generic-modifier.md)  
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)
