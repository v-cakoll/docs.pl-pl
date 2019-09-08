---
title: Debugowanie zapytań LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: a82fd3e99a556daf40e5c65a16cf20278f38ea26
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785213"
---
# <a name="debugging-linq-to-dataset-queries"></a>Debugowanie zapytań LINQ to DataSet

Program Visual Studio obsługuje debugowanie kodu LINQ to DataSet. Istnieją jednak pewne różnice między debugowaniem LINQ to DataSet kodu i nieLINQ to DataSet kod zarządzany. Większość funkcji debugowania współpracuje z instrukcjami LINQ to DataSet, w tym krokowe, ustawianie punktów przerwania i wyświetlanie wyników, które są wyświetlane w oknach debugera. Jednak opóźnione wykonywanie zapytań w programie ma pewne efekty uboczne, które należy wziąć pod uwagę podczas debugowania kodu LINQ to DataSet i istnieją pewne ograniczenia dotyczące używania funkcji Edytuj i Kontynuuj. W tym temacie omówiono aspekty debugowania, które są unikatowe dla LINQ to DataSet w porównaniu do kodu zarządzanego nieLINQ to DataSetowego.  
  
## <a name="viewing-results"></a>Wyświetlanie wyników  
 Można wyświetlić wynik instrukcji LINQ to DataSet przy użyciu etykietek danych, okno wyrażeń kontrolnych i okna dialogowego QuickWatch. Za pomocą okna źródłowego można wstrzymać wskaźnik zapytania w oknie źródło i pojawi się etykietki danych. Można skopiować zmienną LINQ to DataSet i wkleić ją do okna dialogowego okno wyrażeń kontrolnych lub QuickWatch. W LINQ to DataSet zapytanie nie jest oceniane podczas tworzenia lub deklarowania, ale tylko wtedy, gdy zapytanie jest wykonywane. Jest to tzw. *wykonywanie odroczone*. W związku z tym zmienna zapytania nie ma wartości, dopóki nie zostanie ona oceniona. Aby uzyskać więcej informacji, zobacz [zapytania w LINQ to DataSet](queries-in-linq-to-dataset.md).  
  
 Debuger musi oszacować zapytanie, aby wyświetlić wyniki zapytania. Ta niejawna Ocena występuje po wyświetleniu LINQ to DataSet wyniku zapytania w debugerze i ma pewne skutki, które należy wziąć pod uwagę. Każda Ocena zapytania trwa. Rozszerzanie węzła wyników zajmuje trochę czasu. W przypadku niektórych zapytań powtórzona Ocena może spowodować zauważalną spadek wydajności. Obliczenie zapytania może również spowodować skutki uboczne, które są zmieniane na wartość danych lub stan programu. Nie wszystkie zapytania mają efekty uboczne. Aby określić, czy zapytanie może być bezpiecznie ocenione bez efektów ubocznych, należy zrozumieć kod implementujący zapytanie. Aby uzyskać więcej informacji, zobacz [efekty uboczne i wyrażenia](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/a7a250bs(v=vs.120)).  
  
## <a name="edit-and-continue"></a>Edytuj i kontynuuj  
 Edytuj i Kontynuuj nie obsługuje zmian w zapytaniach LINQ to DataSet. W przypadku dodania, usunięcia lub zmiany instrukcji LINQ to DataSet podczas sesji debugowania zostanie wyświetlone okno dialogowe z informacją, że zmiana nie jest obsługiwana przez polecenie Edytuj i Kontynuuj. W tym momencie można albo cofnąć zmiany lub zatrzymać sesję debugowania i ponownie uruchomić nową sesję z edytowanym kodem.  
  
 Ponadto polecenie Edytuj i Kontynuuj nie obsługuje zmiany typu ani wartości zmiennej, która jest używana w instrukcji LINQ to DataSet. Ponownie można cofnąć zmiany lub zatrzymać i ponownie uruchomić sesję debugowania.  
  
 W wizualizacji C# w programie Visual Studio nie można używać żadnych kodu w metodzie, która zawiera kwerendę LINQ to DataSet, nie jest możliwe używanie żadnych kodów.  
  
 W Visual Basic w programie Visual Studio można użyć funkcji Edytuj i Kontynuuj w przypadku kodu nieLINQ to DataSet, nawet w metodzie zawierającej zapytanie LINQ to DataSet. Możesz dodać lub usunąć kod przed instrukcją LINQ to DataSet, nawet jeśli zmiany wpłyną na numer wiersza zapytania LINQ to DataSetowego. Visual Basic środowisko debugowania dla kodu nieLINQ to DataSet pozostaje taki sam, jak poprzednio LINQ to DataSet został wprowadzony. Nie można zmienić, dodać ani usunąć zapytania LINQ to DataSet, jednak o ile nie zatrzymasz debugowania w celu zastosowania zmian.  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie kodu zarządzanego](/visualstudio/debugger/debugging-managed-code)
- [Przewodnik programowania](programming-guide-linq-to-dataset.md)
