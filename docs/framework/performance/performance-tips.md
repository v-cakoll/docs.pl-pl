---
title: "Wskazówki dotyczące wydajności .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- C# language, performance
- performance [C#]
- Visual Basic, performance
- performance [Visual Basic]
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
caps.latest.revision: "36"
author: BillWagner
ms.author: wiwagn
manager: wpickett
ms.openlocfilehash: 93db69b67bfac3bcefbc818032aae64df0fd47b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="net-performance-tips"></a>Wskazówki dotyczące wydajności .NET
Termin *wydajności* zazwyczaj odwołuje się do szybkości wykonywania programu. Czasami może zwiększyć szybkość wykonywania, wykonując podstawowe reguły w kodzie źródłowym. W przypadku niektórych programów należy dokładnie sprawdzić kod i upewnij się, że działa tak szybko jak to możliwe przy użyciu profilowania. W innych programów nie trzeba wykonywać takie optymalizacji, ponieważ kod nie działa prawidłowo szybkie, ponieważ jest ona zapisywana. W tym artykule wymieniono niektóre typowe obszary, w którym może się pogorszyć wydajność i wskazówki dotyczące poprawiania go, a także linki do tematów wyższą wydajność. Aby uzyskać więcej informacji na temat planowania i pomiaru wydajności, zobacz [wydajności](../../../docs/framework/performance/index.md)  
  
## <a name="boxing-and-unboxing"></a>Opakowywanie i rozpakowywanie  
 Najlepiej jest, aby uniknąć przy użyciu wartości typów w sytuacjach, w którym musi zostać opakowany dużą liczbę razy, na przykład w kolekcji nieogólnej klasy takie jak <xref:System.Collections.ArrayList?displayProperty=nameWithType>. Konwersja boxing typów wartości można uniknąć, używając kolekcji ogólnych, takich jak <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Opakowywanie i rozpakowywanie to procesy praktyce kosztowne. Typ wartości jest opakowany, całkowicie nowy obiekt musi zostać utworzona. Może to zająć maksymalnie 20 razy dłuższy niż przypisania proste odwołanie. Gdy Rozpakowywanie, proces rzutowanie może zająć cztery razy tak długo, jak przypisania. Aby uzyskać więcej informacji, zobacz [opakowywanie i rozpakowywanie](~/docs/csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="strings"></a>Ciągi  
 Podczas łączenia dużej liczby zmiennych ciągu, na przykład w pętli ścisłej użyć <xref:System.Text.StringBuilder?displayProperty=nameWithType> zamiast C# [+ — operator](~/docs/csharp/language-reference/operators/addition-operator.md) lub Visual Basic [operatory łączenia](~/docs/visual-basic/language-reference/operators/concatenation-operators.md). Aby uzyskać więcej informacji, zobacz [porady: łączenie wielu ciągów](~/docs/csharp/programming-guide/strings/how-to-concatenate-multiple-strings.md) i [operatory łączenia w Visual Basic](~/docs/visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Destruktory  
 Nie należy używać destruktory puste. Jeśli klasa zawiera destruktor, wpis jest tworzony w kolejce Finalize. Po wywołaniu destruktor moduł garbage collector jest wywoływane w celu przetworzenia kolejki. Jeśli destruktor jest pusta, to po prostu powoduje spadek wydajności. Aby uzyskać więcej informacji, zobacz [destruktory](~/docs/csharp/programming-guide/classes-and-structs/destructors.md) i [okres istnienia obiektów: sposób obiekty są utworzone i Destroyed](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
## <a name="other-resources"></a>Inne zasoby  
  
-   [Szybsze pisanie kodu zarządzanego: Znać koszt rzeczy](http://go.microsoft.com/fwlink/?LinkId=99294)  
  
-   [Zapisywanie wysokiej wydajności zarządzane aplikacje: Elementarz](http://go.microsoft.com/fwlink/?LinkId=99295)  
  
-   [Moduł zbierający elementy bezużyteczne podstawy i wskazówki dotyczące wydajności](http://go.microsoft.com/fwlink/?LinkId=99296)  
  
-   [I porady dotyczące wydajności w aplikacjach .NET](http://go.microsoft.com/fwlink/?LinkId=99297)  
  
-   [Wewnątrz narzędzi diagnostycznych dla platformy .NET](http://go.microsoft.com/fwlink/?LinkId=112407)  
  
-   [Informacje o technologii Rico Mariani wydajności](http://go.microsoft.com/fwlink/?LinkId=115679)  
  
## <a name="see-also"></a>Zobacz też  
 [Wydajność](../../../docs/framework/performance/index.md)  
 [Koncepcje programowania](http://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6)  
 [Przewodnik programowania w języku Visual Basic](../../visual-basic/programming-guide/index.md)  
 [Przewodnik programowania w języku C#](http://msdn.microsoft.com/library/ac0f23a2-6bf3-4077-be99-538ae5fd3bc5)
