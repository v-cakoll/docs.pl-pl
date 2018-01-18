---
title: "Debugowanie LINQ do DataSet zapytań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4c54015-8ce2-4c5c-8d18-7038144cc66d
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1c8a518dd3f8bc4c1123099522ad4a4f452c78f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="debugging-linq-to-dataset-queries"></a>Debugowanie LINQ do DataSet zapytań
[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]obsługuje debugowanie [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu. Istnieją pewne różnice między debugowania [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu i nie-[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu zarządzanego. Większość funkcji debugowania pracować z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instrukcje w tym wykonywanie krok po kroku, ustawianie punktów przerwania i wyświetlania wyników, które przedstawiono w oknach debugera. Jednak odroczone zapytania wykonywania w ma niektóre efekty uboczne, które należy wziąć pod uwagę podczas debugowania [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu i istnieją pewne ograniczenia przy użyciu Edytuj i Kontynuuj. W tym temacie omówiono aspektów debugowania, które są unikatowe dla [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] porównaniu z systemem innym niż[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu zarządzanego.  
  
## <a name="viewing-results"></a>Wyświetlanie wyników  
 Można wyświetlić wyniki [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instrukcji przy użyciu etykietek danych, okno czujki i QuickWatch — okno dialogowe. Przy użyciu okna źródła, w przypadku wstrzymania wskaźnik myszy na zapytania w oknie źródła i pojawi się etykietki danych. Możesz skopiować [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zmiennej i wklej go do okna czujki lub QuickWatch — okno dialogowe. W [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], zapytania nie jest oceniany, podczas tworzenia lub zadeklarowana, ale tylko wtedy, gdy zapytanie jest wykonywane. Ta metoda jest wywoływana *odroczonego wykonania*. Do zmiennej zapytania nie ma w związku z tym wartość, dopóki nie będzie oceniana. Aby uzyskać więcej informacji, zobacz [kwerend LINQ do DataSet](../../../../docs/framework/data/adonet/queries-in-linq-to-dataset.md).  
  
 Debuger musi ocenić zapytanie w celu wyświetlenia wyników zapytania. Ocena niejawne występuje podczas wyświetlania [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] wynik kwerendy w debugerze, a ma niektóre efekty, należy rozważyć. Każdej oceny zapytania jest czasochłonne. Rozwinięcie węzła wyników jest czasochłonne. Dla niektórych kwerend powtarzane oceny może spowodować zmniejszenie wydajności zauważalne. Ocena zapytania mogą powodować efekty uboczne, które zmian do wartości danych lub stan programu. Nie wszystkie zapytania ma efekty uboczne. Aby ustalić, czy można bezpiecznie obliczyć zapytania, bez efekty uboczne, trzeba poznać kod, który implementuje zapytania. Aby uzyskać więcej informacji, zobacz [efekty uboczne i wyrażenia](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e).  
  
## <a name="edit-and-continue"></a>Edytuj i kontynuuj  
 Edytuj i Kontynuuj nie obsługuje zmiany [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania. Jeśli dodać, usunąć lub zmienić [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instrukcji podczas sesji debugowania, zostanie wyświetlone okno dialogowe informujące o tym, zmiany nie jest obsługiwany przez Edytuj i Kontynuuj. W tym momencie można cofnąć zmiany lub zatrzymać sesję debugowania i ponownie uruchomić nową sesję edycji kodu.  
  
 Ponadto, Edytuj i Kontynuuj nie obsługuje zmiany typu lub wartości zmiennej używanej w [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instrukcji. Ponownie można cofnąć zmiany lub Zatrzymaj i uruchom ponownie sesję debugowania.  
  
 W środowisku Visual C# w programie Visual Studio, nie można użyć Edytuj i Kontynuuj na dowolny kod w metodzie, która zawiera [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania.  
  
 W języku Visual Basic w programie Visual Studio, możesz użyć Edytuj i Kontynuuj w inną niż[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kodu, nawet w metodę, która zawiera [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania. Można dodać lub usunąć kod przed [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] instrukcji, nawet jeśli zmiany wpływają na numer wiersza [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania. Debugowanie dla języka Visual Basic z systemem innym niż[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] kod pozostanie niezmieniony sprzed [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] została wprowadzona. Nie można zmienić, dodać lub usunąć [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapytania, chyba że zostanie zatrzymana, debugowanie, aby zastosować zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zarządzanego kodu](/visualstudio/debugger/debugging-managed-code)  
 [Przewodnik programowania](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
