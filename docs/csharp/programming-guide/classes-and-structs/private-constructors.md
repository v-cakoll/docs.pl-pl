---
title: Konstruktory prywatne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: e8f1f097a62f022d305987800e89353b038f42ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315792"
---
# <a name="private-constructors-c-programming-guide"></a>Konstruktory prywatne (Przewodnik programowania w języku C#)
Konstruktor prywatny jest konstruktor wystąpienia specjalnego. Jest zwykle używany w klasach, które zawierają tylko statyczne elementy członkowskie. Jeśli klasa ma co najmniej jeden konstruktory prywatne i nie konstruktorów publicznych, innych klas (z wyjątkiem klasy zagnieżdżone) nie można utworzyć wystąpienia tej klasy. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]  
  
 Deklaracja pustego konstruktora uniemożliwia automatyczne generowanie konstruktora domyślnego. Należy pamiętać, że jeśli nie używasz modyfikatora dostępu z konstruktora nadal będzie domyślnie prywatne. Jednak [prywatnej](../../../csharp/language-reference/keywords/private.md) modyfikator zwykle używane jest jawnie go wyczyścić, że nie można utworzyć wystąpienia klasy.  
  
 Konstruktory prywatne są używane, aby uniknąć tworzenia wystąpień klasy, gdy nie ma żadnych pól wystąpień lub metod, takich jak <xref:System.Math> klas, lub gdy jest wywoływana metoda uzyskać wystąpienia klasy. Jeśli wszystkie metody w klasie statycznej, należy rozważyć zmianę pełnej klasy statycznej. Aby uzyskać więcej informacji, zobacz [klasy statyczne i statycznych elementów członkowskich klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Przykład  
 Oto przykład klasy przy użyciu konstruktora prywatnego.  
  
 [!code-csharp[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]  
  
 Zwróć uwagę, że jeśli usuń znaczniki komentarza z przykładu następującą instrukcję, go spowodują wygenerowanie błędu, ponieważ Konstruktor jest niedostępny z powodu swojego poziomu ochrony:  
  
 [!code-csharp[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [public](../../../csharp/language-reference/keywords/public.md)
