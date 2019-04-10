---
title: 'Przewodnik: Wykonywanie zapytań w relacjach (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
ms.openlocfilehash: abd4941697639ec7bdda545b1ead8d57091e9e7f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314662"
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a>Przewodnik: Wykonywanie zapytań w relacjach (Visual Basic)
W tym instruktażu pokazano użycie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *skojarzenia* do reprezentowania relacji klucza obcego w bazie danych.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 W tym przewodniku została napisana przy użyciu ustawień środowiska deweloperskiego Visual Basic.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Konieczne jest ukończenie [instruktażu: Prosty Model obiektu i zapytanie (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md). W tym przewodniku opiera się na tym, co w tym pliku northwnd.mdf w c:\linqtest.  
  
## <a name="overview"></a>Omówienie  
 Ten przewodnik składa się z trzech głównych zadań:  
  
-   Dodawanie klasy jednostki do reprezentowania tabeli Orders z przykładowej bazy danych Northwind.  
  
-   Uzupełniające adnotacje do `Customer` klasy w celu zwiększenia relacji między `Customer` i `Order` klasy.  
  
-   Tworzenie i uruchamianie zapytań, aby przetestować proces uzyskiwania `Order` informacji przy użyciu `Customer` klasy.  
  
## <a name="mapping-relationships-across-tables"></a>Mapowanie relacji między tabelami  
 Po `Customer` definicji klasy, należy utworzyć `Order` jednostki definicji klasy, która zawiera następujący kod, który wskazuje, że `Orders.Customer` odnosi się jako klucz obcy, aby `Customers.CustomerID`.  
  
#### <a name="to-add-the-order-entity-class"></a>Aby dodać klasę jednostki zamówienia  
  
-   Wpisz lub wklej następujący kod po `Customer` klasy:  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a>Dodawanie adnotacji do klasy odbiorcy  
 W tym kroku możesz dodawać adnotacje do `Customer` klasy, aby wskazać jej relacji z `Order` klasy. (To dodawanie nie jest bezwzględnie konieczne, ponieważ zdefiniowaniem relacji w dowolnym kierunku jest wystarczające, aby utworzyć łącze. Ale dodanie tej adnotacji umożliwiają łatwe nawigowanie obiektów w dowolnym kierunku).  
  
#### <a name="to-annotate-the-customer-class"></a>Dodawać adnotacje do klasy odbiorcy  
  
-   Wpisz lub wklej następujący kod do `Customer` klasy:  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Tworzenie i uruchamianie zapytań w relacji zamówienia klienta  
 Teraz uzyskiwać dostęp do `Order` obiektów bezpośrednio z `Customer` obiektów, lub w kolejności przeciwnej. Nie trzeba jawnie *sprzężenia* między klienci i zamówienia.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Dostęp do obiektów kolejności przy użyciu obiektów klienta  
  
1. Modyfikowanie `Sub Main` metody, wpisując lub wklejając następujący kod do metody:  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2. Naciśnij klawisz F5, aby debugować aplikację.  
  
     Dwie nazwy wyświetlane w oknie komunikatu, a w oknie konsoli wyświetlane wygenerowanego kodu SQL.  
  
3. Zamknij okno komunikatu, aby zatrzymać debugowanie.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Tworzenie silnie Typizowanego widoku bazy danych  
 Jest znacznie łatwiejsze do uruchamiania w silnie typizowanym widoku bazy danych. Zdecydowanie wpisując <xref:System.Data.Linq.DataContext> obiektu, nie trzeba wywołania <xref:System.Data.Linq.DataContext.GetTable%2A>. Silnie typizowane tabel można używać wszystkie zapytania, korzystając z silnie typizowaną <xref:System.Data.Linq.DataContext> obiektu.  
  
 W poniższych krokach utworzysz `Customers` jako silnie typizowaną tabelę, która mapuje dane do tabeli Klienci w bazie danych.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>Do silnie typu obiektu DataContext  
  
1. Dodaj następujący kod powyżej `Customer` deklaracji klasy.  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2. Modyfikowanie `Sub Main` do użycia w silnie typizowany <xref:System.Data.Linq.DataContext> w następujący sposób:  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3. Naciśnij klawisz F5, aby debugować aplikację.  
  
     Dane wyjściowe z okna konsoli jest:  
  
     `ID=WHITC`  
  
4. Naciśnij klawisz Enter w oknie konsoli, aby zamknąć aplikację.  
  
5. Na **pliku** menu, kliknij przycisk **Zapisz wszystko** Jeśli chcesz zapisać tę aplikację.  
  
## <a name="next-steps"></a>Następne kroki  
 Następnym instruktażu ([instruktażu: Manipulowanie danych (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) pokazuje, jak wykonywać operacje na danych. Ten przewodnik nie wymaga zapisania dwa przewodniki w tej serii, które zostały już wykonane.  
  
## <a name="see-also"></a>Zobacz także

- [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
