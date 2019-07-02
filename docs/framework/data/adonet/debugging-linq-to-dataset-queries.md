---
title: Debugowanie zapytań LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: 38eda9f352c4a8d8590e5e57b48c694eadd0397b
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67503986"
---
# <a name="debugging-linq-to-dataset-queries"></a>Debugowanie zapytań LINQ to DataSet

Program Visual Studio obsługuje debugowanie LINQ do kodu zestawu danych. Istnieją jednak pewne różnice między debugowania LINQ do kodu zestawu danych i non-LINQ do kodu zarządzanego zestawu danych. Najbardziej debugujące funkcje współpracują z LINQ do instrukcji zestawu danych, w tym przechodzenie krok po kroku, ustawiania punktów przerwania i wyświetlania wyników, które są wyświetlane w oknach debugera. Jednak wykonanie odroczone zapytanie w ma pewne skutki uboczne, które należy wziąć pod uwagę podczas debugowania LINQ do kodu zestawu danych i podlegają pewnym ograniczeniom za pomocą Edytuj i Kontynuuj. W tym temacie omówiono aspektów debugowania, które są unikatowe dla programu LINQ to DataSet w porównaniu do non-LINQ do kodu zarządzanego zestawu danych.  
  
## <a name="viewing-results"></a>Wyświetlanie wyników  
 Wynik składnika LINQ to DataSet instrukcji można wyświetlić, używając DataTips, okna czujki i okna dialogowego QuickWatch. Korzystając z okna źródła, możesz wstrzymać wskaźnik na zapytaniu w oknie źródła i wyświetli się datatip. Można skopiować LINQ do zestawu danych zmiennej i wklej go w oknie czujki lub okna dialogowego QuickWatch. W składniku LINQ to DataSet kwerenda nie jest uwzględniana podczas tworzenia lub deklarowania, ale tylko wtedy, gdy zapytanie jest wykonywane. Jest to nazywane *wykonanie odroczone*. W związku z tym zmienna zapytania nie ma wartości dopóki jest ocenione. Aby uzyskać więcej informacji, zobacz [zapytania w LINQ to DataSet](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md).  
  
 Debuger musi zwrócić zapytanie w celu wyświetlenia wyników zapytania. Bezwarunkowa ocena występuje, gdy wyświetlania składnika LINQ to DataSet wyników zapytania w debugerze ma jakieś konsekwencje, które należy wziąć pod uwagę. Każdej oceny kwerendy jest czasochłonne. Rozwinięcie węzła wyników zajmuje trochę czasu. Dla niektórych zapytań powtarzające się oceny mogą spowodować zmniejszyć wydajność. Ocena zapytania może spowodować efekty uboczne, które są zmianami wartości danych lub stanu programu. Nie wszystkie kwerendy mają skutki uboczne. Aby ustalić, czy zapytanie może być bezpiecznie ocenione bez efektów ubocznych, musisz zrozumieć kod, który implementuje zapytanie. Aby uzyskać więcej informacji, zobacz [efekty uboczne i wyrażenia](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120)).  
  
## <a name="edit-and-continue"></a>Edytuj i kontynuuj  
 Edytuj i Kontynuuj nie obsługuje zmiany zapytań LINQ do zapytań zestawu danych. Jeśli dodać, usunąć lub zmienić LINQ do DataSet instrukcji podczas sesji debugowania pojawia się okno dialogowe informujące, że zmiana nie jest obsługiwana przez Edytuj i Kontynuuj. W tym momencie można albo cofnąć zmiany lub zatrzymać sesję debugowania i ponownie uruchomić nową sesję edycji kodu.  
  
 Ponadto, Edytuj i Kontynuuj nie obsługuje zmiany typu lub wartości zmiennej używanej w składniku LINQ to DataSet instrukcji. Ponownie można albo cofnąć zmiany lub zatrzymać i ponownie uruchomić sesję debugowania.  
  
 W elemencie wizualnym C# w programie Visual Studio, nie można użyć Edytuj i Kontynuuj na dowolnym kodzie w metodzie, która zawiera zapytaniu składnika LINQ to DataSet.  
  
 W języku Visual Basic w programie Visual Studio można użyć Edytuj i Kontynuuj na non-LINQ do kodu zestawu danych, nawet w metodzie, która zawiera zapytaniu składnika LINQ to DataSet. Można dodać lub usunąć kod przed LINQ to DataSet instrukcji, nawet w przypadku zmiany wpływają na liczbę wierszy w zapytaniu składnika LINQ to DataSet. Obsługi debugowania dla non-LINQ do zestawu danych kodu języka Visual Basic pozostaje taka sama jak przed wprowadzeniem LINQ to DataSet. Nie można zmienić, Dodaj lub jednak usunąć zapytaniu składnika LINQ to DataSet, o ile nie zatrzymasz debugowanie, aby zastosować zmiany.  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie kodu zarządzanego](/visualstudio/debugger/debugging-managed-code)
- [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
