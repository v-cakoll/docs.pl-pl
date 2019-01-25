---
title: Debugowanie zapytań LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
ms.openlocfilehash: 6c7b8c6cec39adfd5b7456d94cfae5622649e5a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680510"
---
# <a name="debugging-linq-to-dataset-queries"></a>Debugowanie zapytań LINQ to DataSet

Program Visual Studio obsługuje debugowanie [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu. Istnieją jednak pewne różnice między debugowania [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu i innych niż-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu zarządzanego. Większość debugujące funkcje współpracują z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instrukcji w tym przechodzenie krok po kroku, ustawiania punktów przerwania i wyświetlania wyników, które są wyświetlane w oknach debugera. Jednak odroczone zapytanie wykonywanie w programie ma pewne skutki uboczne, które należy wziąć pod uwagę podczas debugowania [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu i podlegają pewnym ograniczeniom za pomocą Edytuj i Kontynuuj. W tym temacie omówiono aspektów debugowania, które są unikatowe dla [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] w porównaniu do non -[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu zarządzanego.  
  
## <a name="viewing-results"></a>Wyświetlanie wyników  
 Możesz wyświetlić wynik [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instrukcję, używając DataTips, okna czujki i okna dialogowego QuickWatch. Korzystając z okna źródła, możesz wstrzymać wskaźnik na zapytaniu w oknie źródła i wyświetli się datatip. Możesz skopiować [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zmiennej i wklej go w oknie czujki lub okna dialogowego QuickWatch. W [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], kwerenda nie jest uwzględniana podczas tworzenia lub deklarowania, ale tylko wtedy, gdy zapytanie jest wykonywane. Jest to nazywane *wykonanie odroczone*. W związku z tym zmienna zapytania nie ma wartości dopóki jest ocenione. Aby uzyskać więcej informacji, zobacz [zapytania w LINQ to DataSet](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md).  
  
 Debuger musi zwrócić zapytanie w celu wyświetlenia wyników zapytania. Bezwarunkowa ocena występuje kiedy Twój widok [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] wynik kwerendy w debugerze, a ma jakieś konsekwencje, które należy wziąć pod uwagę. Każdej oceny kwerendy jest czasochłonne. Rozwinięcie węzła wyników zajmuje trochę czasu. Dla niektórych zapytań powtarzające się oceny mogą spowodować zmniejszyć wydajność. Ocena zapytania może spowodować efekty uboczne, które są zmianami wartości danych lub stanu programu. Nie wszystkie kwerendy mają skutki uboczne. Aby ustalić, czy zapytanie może być bezpiecznie ocenione bez efektów ubocznych, musisz zrozumieć kod, który implementuje zapytanie. Aby uzyskać więcej informacji, zobacz [efekty uboczne i wyrażenia](https://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).  
  
## <a name="edit-and-continue"></a>Edytuj i kontynuuj  
 Edytuj i Kontynuuj nie obsługuje zmiany [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania. Jeśli dodać, usunąć lub zmienić [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instrukcji podczas sesji debugowania, pojawi się okno dialogowe informujące o tym, zmiany nie jest obsługiwana przez Edytuj i Kontynuuj. W tym momencie można albo cofnąć zmiany lub zatrzymać sesję debugowania i ponownie uruchomić nową sesję edycji kodu.  
  
 Ponadto, Edytuj i Kontynuuj nie obsługuje zmiany typu lub wartości zmiennej, która jest używana w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instrukcji. Ponownie można albo cofnąć zmiany lub zatrzymać i ponownie uruchomić sesję debugowania.  
  
 W języku Visual C# w programie Visual Studio nie można użyć Edytuj i Kontynuuj na dowolnym kodzie w metodzie, która zawiera [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania.  
  
 W języku Visual Basic w programie Visual Studio, można użyć Edytuj i Kontynuuj na non -[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu, nawet w metodzie, która zawiera [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania. Można dodawać i usuwać kod przed [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instrukcji, nawet jeśli zmiany mają wpływ na numer wiersza [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania. Obsługi debugowania dla języka Visual Basic non -[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kod pozostanie niezmieniony sprzed [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] została wprowadzona. Nie można zmienić, dodawanie lub usuwanie [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania, o ile nie zatrzymasz debugowanie, aby zastosować zmiany.  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie kodu zarządzanego](/visualstudio/debugger/debugging-managed-code)
- [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
