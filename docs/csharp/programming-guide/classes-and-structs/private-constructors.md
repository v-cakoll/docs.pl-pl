---
title: Konstruktory prywatne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 1338a6efbe03522093899009178b6f31e558d8dd
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802706"
---
# <a name="private-constructors-c-programming-guide"></a>Konstruktory prywatne (Przewodnik programowania w języku C#)
Konstruktor prywatny jest konstruktorem wystąpienia specjalnego. Zazwyczaj jest używany w klasach, które zawierają tylko statyczne elementy członkowskie. Jeśli klasa ma co najmniej jeden prywatny konstruktorów i konstruktorów publicznych, inne klasy (z wyjątkiem klas zagnieżdżonych) nie można utworzyć wystąpienia tej klasy. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]  
  
 Deklaracja pustego konstruktora uniemożliwia automatyczne generowanie konstruktora domyślnego. Należy pamiętać, że jeśli nie używasz modyfikatora dostępu za pomocą konstruktora nadal będzie domyślnie prywatny. Jednak [prywatnej](../../../csharp/language-reference/keywords/private.md) modyfikator jest zwykle używany w sposób jawny do ułatwiają Wyczyść, że nie można utworzyć wystąpienia klasy.  
  
 Konstruktory prywatne są używane, aby uniknąć tworzenia wystąpienia klasy, gdy nie ma żadnych pól wystąpień lub metod, takich jak <xref:System.Math> klasy, lub gdy metoda jest wywoływana w celu uzyskania wystąpienie klasy. Jeśli wszystkie metody w klasie statycznej, należy wziąć pod uwagę pełną klasy jako możliwej statyczne. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statyczne elementy członkowskie klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Przykład  
 Oto przykład klasy przy użyciu prywatnego konstruktora.  
  
 [!code-csharp[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]  
  
 Zwróć uwagę, że jeśli usuniesz komentarz Poniższa instrukcja z przykładu, zostanie wygenerowany błąd ponieważ Konstruktor jest niedostępny z powodu swojego poziomu ochrony:  
  
 [!code-csharp[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
- [private](../../../csharp/language-reference/keywords/private.md)  
- [public](../../../csharp/language-reference/keywords/public.md)
