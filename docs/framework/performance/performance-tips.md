---
title: Wskazówki dotyczące wydajności .NET
ms.date: 03/30/2017
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2969551bef279e6b13d2b08ff7f0e4711a80794
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219246"
---
# <a name="net-performance-tips"></a>Wskazówki dotyczące wydajności .NET
Termin *wydajności* zazwyczaj odnosi się do szybkości wykonywania programu. Czasami możesz zwiększyć szybkość realizacji przez następujących podstawowych reguł w kodzie źródłowym. W niektórych programach jest ważne, aby dokładnie sprawdzić kod i użyć profilerów, aby upewnić się, że działa tak szybko, jak to możliwe. W innych programach nie trzeba wykonywać takiej optymalizacji, ponieważ kod działa zadowalająco szybko, jak jest pisany. W tym artykule wymieniono niektóre typowe obszary, w których może to spowodować obniżenie wydajności i wskazówki dotyczące poprawiania go, a także łącza do tematów wyższą wydajność. Aby uzyskać więcej informacji na temat planowania i dokonywania jej pomiarów wydajności, zobacz [wydajności](../../../docs/framework/performance/index.md)  
  
## <a name="boxing-and-unboxing"></a>Opakowywanie i rozpakowywanie  
 Najlepiej jest unikać stosowania wartości typów w sytuacjach, w którym musi być zapakowany dużą liczbę razy, na przykład w kolekcji nieogólnej klasy takie jak <xref:System.Collections.ArrayList?displayProperty=nameWithType>. Możesz uniknąć pakowania typów wartości używając kolekcji ogólnych, takich jak <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Opakowywanie i rozpakowywanie są obciążającymi procesami. Gdy typ wartości jest zapakowany, należy utworzyć zupełnie nowy obiekt. Może to potrwać maksymalnie 20 razy dłużej niż proste przypisywanie odwołania. Podczas rozpakowywania, proces rzutowania może zająć cztery razy przypisania. Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="strings"></a>Ciągi  
 Podczas łączenia dużej liczby zmiennych typu string, na przykład w pętli, użyj <xref:System.Text.StringBuilder?displayProperty=nameWithType> zamiast C# [+ — operator](~/docs/csharp/language-reference/operators/addition-operator.md) lub Visual Basic [Concatenation — operatory](~/docs/visual-basic/language-reference/operators/concatenation-operators.md). Aby uzyskać więcej informacji, zobacz [jak: Łączenie wielu ciągów](../../csharp/how-to/concatenate-multiple-strings.md) i [Concatenation — operatory w języku Visual Basic](~/docs/visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Destruktory  
 Nie można używać pustych destruktorów. Gdy klasa zawiera destruktor, zapis jest tworzony w kolejce Finalize. Po wywołaniu destruktora moduł odśmiecania pamięci jest wywoływana, aby przetworzyć kolejkę. Jeśli destruktor jest pusty, po prostu powoduje to spadek wydajności. Aby uzyskać więcej informacji, zobacz [destruktory](~/docs/csharp/programming-guide/classes-and-structs/destructors.md) i [okres istnienia obiektów: Jak obiekty są tworzone i niszczone](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
## <a name="other-resources"></a>Inne zasoby  
  
-   [Szybsze pisanie kodu zarządzanego: Znaj koszt](https://go.microsoft.com/fwlink/?LinkId=99294)  
  
-   [Pisanie wysokiej wydajności aplikacji zarządzanych: A Primer](https://go.microsoft.com/fwlink/?LinkId=99295)  
  
-   [Podstawy modułu odśmiecania pamięci i wskazówki dotyczące wydajności](https://go.microsoft.com/fwlink/?LinkId=99296)  
  
-   [I porady dotyczące wydajności w aplikacjach platformy .NET](https://go.microsoft.com/fwlink/?LinkId=99297)  

-   [Informacje o technologii Rico Mariani wydajności](https://go.microsoft.com/fwlink/?LinkId=115679)  

-   [Blog Morrison zaliczko](https://blogs.msdn.microsoft.com/vancem/)
  
## <a name="see-also"></a>Zobacz także
- [Wydajność](../../../docs/framework/performance/index.md)
- [Przewodnik programowania w języku Visual Basic](../../visual-basic/programming-guide/index.md)
- [Przewodnik programowania w języku C#](../../csharp/programming-guide/index.md)
