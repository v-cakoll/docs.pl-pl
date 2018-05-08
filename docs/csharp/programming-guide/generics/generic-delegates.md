---
title: Delegaty ogólne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: a9f06dcf608a83b53e894310f20810182cf6daa4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="generic-delegates-c-programming-guide"></a>Delegaty ogólne (Przewodnik programowania w języku C#)
A [delegować](../../../csharp/language-reference/keywords/delegate.md) można zdefiniować własny parametrów typu. Kod, że odwołania Delegat ogólny można określić argumentu typu można utworzyć typu skonstruowane zamknięte, podobnie jak w przypadku tworzenia wystąpienia klasy ogólnej lub wywołanie metody ogólnej, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 C# w wersji 2.0 zawiera nową funkcję o nazwie konwersji grupy — metoda, która stosuje się do typów delegatów konkretnych, jak również ogólne i umożliwia pisanie poprzedniego wiersza przy użyciu tej składni uproszczoną:  
  
 [!code-csharp[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 Delegaty zdefiniowany w klasie ogólnej można używać parametrów typu klasy ogólnej w taki sam sposób, że metody klasy.  
  
 [!code-csharp[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 Kod, który odwołuje się do delegata należy określić argument typu zawierającego klasy, w następujący sposób:  
  
 [!code-csharp[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 Delegaty ogólne są szczególnie przydatne podczas definiowania zdarzenia oparte na wzorcu typowe, ponieważ argumentu sender mogą być silnie typizowane i nie ma już można rzutować do i z <xref:System.Object>.  
  
 [!code-csharp[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Wprowadzenie do typów ogólnych](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Metody ogólne](../../../csharp/programming-guide/generics/generic-methods.md)  
 [Klasy ogólne](../../../csharp/programming-guide/generics/generic-classes.md)  
 [Interfejsy ogólne](../../../csharp/programming-guide/generics/generic-interfaces.md)  
 [Delegaci](../../../csharp/programming-guide/delegates/index.md)  
 [Typy ogólne](~/docs/standard/generics/index.md)
