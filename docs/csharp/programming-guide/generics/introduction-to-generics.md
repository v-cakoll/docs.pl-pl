---
title: Wprowadzenie do typów ogólnych — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: d09cc686e934f722193cb4671d25671f7f4ef5f7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978517"
---
# <a name="introduction-to-generics-c-programming-guide"></a>Wprowadzenie do typów ogólnych (Przewodnik programowania w języku C#)
Ogólne klasy i metody łączenia możliwość ponownego wykorzystania, bezpieczeństwa i wydajności w taki sposób, że nie można ich odpowiedniki nieogólnego. Najczęściej używanych typów ogólnych za pomocą metod, które działają na nich i kolekcje. Biblioteki klas .NET Framework w wersji 2.0 oferuje nową przestrzeń nazw <xref:System.Collections.Generic>, który zawiera kilka nowych klas kolekcji ogólnej. Zalecane jest, że wszystkie aplikacje przeznaczone na platformę .NET Framework 2.0 i późniejszego użycia nowej kolekcji ogólnej klasy zamiast starszych odpowiedniki nieogólnego, takich jak <xref:System.Collections.ArrayList>. Aby uzyskać więcej informacji, zobacz [typy ogólne w .NET](../../../standard/generics/index.md).  
  
 Oczywiście można również utworzyć niestandardowe typy ogólne i metody w celu zapewnienia własne uogólniony rozwiązań i wzorców projektowych, które są bezpieczne i wydajne. Poniższy przykład kodu pokazuje prosty klasy połączonej listy ogólnej dla celów demonstracyjnych. (W większości przypadków należy używać <xref:System.Collections.Generic.List%601> klasy biblioteki klas .NET Framework, zamiast tworzyć własne.) Parametr typu `T` jest używany w kilku lokalizacjach, gdzie konkretny typ byłyby zwykle używane do wskazać typ elementu przechowywane na liście. Jest on używany w następujący sposób:  
  
-   Jako typ parametru metody w `AddHead` metody.  
  
-   Jako typ zwracany `Data` właściwość w zagnieżdżonej `Node` klasy.  
  
-   Jako typ prywatnego elementu członkowskiego `data` w klasie zagnieżdżonej.  
  
 Należy pamiętać, że T jest dostępny do zagnieżdżonego `Node` klasy. Gdy `GenericList<T>` zostanie uruchomiony przy użyciu konkretnego typu, na przykład jako `GenericList<int>`, każde wystąpienie `T` zostanie zastąpiony `int`.  
  
 [!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]  
  
 Poniższy przykład kodu pokazuje, jak kod klienta korzysta z ogólnego `GenericList<T>` klasy, aby utworzyć listę liczb całkowitych. Po prostu zmieniając argument typu, poniższy kod można łatwo można zmodyfikować, aby utworzyć listę ciągów lub dowolny inny typ niestandardowy:  
  
 [!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Typy ogólne](../../../csharp/programming-guide/generics/index.md)
