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
ms.openlocfilehash: 48b62990abf85eac4d4ab30c9a4b891de0875cd7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444536"
---
# <a name="net-performance-tips"></a>Wskazówki dotyczące wydajności .NET
Termin *wydajność* zwykle odnosi się do szybkości wykonywania programu. Czasami można zwiększyć szybkość wykonywania, wykonując pewne podstawowe reguły w kodzie źródłowym. W niektórych programach ważne jest dokładne badanie kodu i używanie narzędzi do uruchamiania, aby upewnić się, że działa tak szybko, jak to możliwe. W innych programach nie trzeba wykonywać takich optymalizacji, ponieważ kod jest uruchamiany zadowalająco szybko, gdy zostanie zapisany. W tym artykule wymieniono niektóre typowe obszary, w których wydajność może pogorszyć się, a także linki do dodatkowych tematów dotyczących wydajności. Aby uzyskać więcej informacji na temat planowania i mierzenia wydajności, zobacz [wydajność](index.md)  
  
## <a name="boxing-and-unboxing"></a>Opakowywanie i rozpakowywanie  
 Najlepszym rozwiązaniem jest unikanie używania typów wartości w sytuacjach, gdy muszą one być opakowane dużą liczbę razy, na przykład w klasach kolekcji innych niż ogólne, takich jak <xref:System.Collections.ArrayList?displayProperty=nameWithType>. Można uniknąć pakowania typów wartości przy użyciu kolekcji ogólnych, takich jak <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Opakowanie i rozpakowywanie są w sposób obliczeniowy kosztowny. Gdy typ wartości jest opakowany, należy utworzyć zupełnie nowy obiekt. Może to potrwać do 20 razy więcej niż proste przypisanie odwołania. Podczas rozpakowywania proces rzutowania może trwać czterokrotnie tak długo, jak przypisanie. Aby uzyskać więcej informacji, zobacz [opakowanie i rozpakowywanie](../../csharp/programming-guide/types/boxing-and-unboxing.md).  
  
## <a name="strings"></a>Ciągi  
 W przypadku łączenia dużej liczby zmiennych ciągów, na przykład w ścisłej pętli, użyj <xref:System.Text.StringBuilder?displayProperty=nameWithType> zamiast C# [operatora +](../../csharp/language-reference/operators/addition-operator.md) lub Visual Basic [operatorów łączenia](../../visual-basic/language-reference/operators/concatenation-operators.md). Aby uzyskać więcej informacji, zobacz [jak połączyć wiele ciągów](../../csharp/how-to/concatenate-multiple-strings.md) i [operatorów łączenia w Visual Basic](../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md).  
  
## <a name="destructors"></a>Destruktory  
 Puste destruktory nie powinny być używane. Gdy Klasa zawiera destruktor, w kolejce Finalize zostanie utworzony wpis. Gdy destruktor jest wywoływany, Moduł wyrzucania elementów bezużytecznych jest wywoływany w celu przetworzenia kolejki. Jeśli destruktor jest pusty, to po prostu powoduje utratę wydajności. Aby uzyskać więcej informacji, zobacz [destruktory](../../csharp/programming-guide/classes-and-structs/destructors.md) i [czas istnienia obiektu: jak obiekty są tworzone i niszczone](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
## <a name="other-resources"></a>Inne zasoby  
  
- [Szybsze pisanie kodu zarządzanego: informacje o kosztach](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973852(v=msdn.10))  
  
- [Pisanie aplikacji zarządzanych o wysokiej wydajności: podstawowy](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973858(v=msdn.10))  
  
- [Podstawy modułu wyrzucania elementów bezużytecznych i wskazówki dotyczące wydajności](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973837(v=msdn.10))  
  
- [Porady i wskazówki dotyczące wydajności w aplikacjach .NET](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973839(v=msdn.10))  

- [Mariani wydajność smakowite kąski](https://blogs.msdn.microsoft.com/ricom/)  

- [Blog Vance Morrison](https://blogs.msdn.microsoft.com/vancem/)
  
## <a name="see-also"></a>Zobacz także

- [Wydajność](index.md)
- [Przewodnik programowania Visual Basic](../../visual-basic/programming-guide/index.md)
- [Przewodnik programowania w języku C#](../../csharp/programming-guide/index.md)
