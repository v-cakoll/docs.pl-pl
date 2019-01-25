---
title: 'Przewodnik: Wykonywanie zapytań w relacjach (C#)'
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: a24d96c9d138f0dcd2f162dad474da01f49e45d2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563668"
---
# <a name="walkthrough-querying-across-relationships-c"></a>Przewodnik: Wykonywanie zapytań w relacjach (C#)
W tym instruktażu pokazano użycie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *skojarzenia* do reprezentowania relacji klucza obcego w bazie danych.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 W tym przewodniku została napisana przy użyciu Visual C# ustawieniami środowiska deweloperskiego.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Konieczne jest ukończenie [instruktażu: Prosty Model obiektu i zapytanie (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md). W tym przewodniku opiera się na tym, co w tym pliku northwnd.mdf w c:\linqtest5.  
  
## <a name="overview"></a>Omówienie  
 Ten przewodnik składa się z trzech głównych zadań:  
  
-   Dodawanie klasy jednostki do reprezentowania tabeli Orders z przykładowej bazy danych Northwind.  
  
-   Uzupełniające adnotacje do `Customer` klasy w celu zwiększenia relacji między `Customer` i `Order` klasy.  
  
-   Tworzenie i uruchamianie zapytań, aby przetestować uzyskiwanie `Order` informacji przy użyciu `Customer` klasy.  
  
## <a name="mapping-relationships-across-tables"></a>Mapowanie relacji między tabelami  
 Po `Customer` definicji klasy, należy utworzyć `Order` jednostki definicji klasy, która zawiera następujący kod, który wskazuje, że `Order.Customer` odnosi się jako klucz obcy, aby `Customer.CustomerID`.  
  
#### <a name="to-add-the-order-entity-class"></a>Aby dodać klasę jednostki zamówienia  
  
-   Wpisz lub wklej następujący kod po `Customer` klasy:  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a>Dodawanie adnotacji do klasy odbiorcy  
 W tym kroku możesz dodawać adnotacje do `Customer` klasy, aby wskazać jej relacji z `Order` klasy. (To dodawanie nie jest bezwzględnie konieczne, ponieważ zdefiniowaniem relacji w dowolnym kierunku jest wystarczające, aby utworzyć łącze. Ale dodanie tej adnotacji umożliwiają łatwe nawigowanie obiektów w dowolnym kierunku).  
  
#### <a name="to-annotate-the-customer-class"></a>Dodawać adnotacje do klasy odbiorcy  
  
-   Wpisz lub wklej następujący kod do `Customer` klasy:  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Tworzenie i uruchamianie zapytań w relacji zamówienia klienta  
 Teraz uzyskiwać dostęp do `Order` obiektów bezpośrednio z `Customer` obiektów, lub w kolejności przeciwnej. Nie trzeba jawnie *sprzężenia* między klienci i zamówienia.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Dostęp do obiektów kolejności przy użyciu obiektów klienta  
  
1.  Modyfikowanie `Main` metody, wpisując lub wklejając następujący kod do metody:  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2.  Naciśnij klawisz F5, aby debugować aplikację.  
  
    > [!NOTE]
    >  Kod SQL w oknie konsoli można wyeliminować, zakomentowując `db.Log = Console.Out;`.  
  
3.  Naciśnij klawisz Enter w oknie konsoli, aby zatrzymać debugowanie.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Tworzenie silnie Typizowanego widoku bazy danych  
 Jest znacznie łatwiejsze do uruchamiania w silnie typizowanym widoku bazy danych. Zdecydowanie wpisując <xref:System.Data.Linq.DataContext> obiektu, nie trzeba wywołania <xref:System.Data.Linq.DataContext.GetTable%2A>. Silnie typizowane tabel można używać wszystkie zapytania, korzystając z silnie typizowaną <xref:System.Data.Linq.DataContext> obiektu.  
  
 W poniższych krokach utworzysz `Customers` jako silnie typizowaną tabelę, która mapuje dane do tabeli Klienci w bazie danych.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>Do silnie typu obiektu DataContext  
  
1.  Dodaj następujący kod powyżej `Customer` deklaracji klasy.  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2.  Modyfikowanie `Main` metoda do użycia w silnie typizowany <xref:System.Data.Linq.DataContext> w następujący sposób:  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3.  Naciśnij klawisz F5, aby debugować aplikację.  
  
     Dane wyjściowe z okna konsoli jest:  
  
     `ID=WHITC`  
  
4.  Naciśnij klawisz Enter w oknie konsoli, aby zatrzymać debugowanie.  
  
## <a name="next-steps"></a>Następne kroki  
 Następnym instruktażu ([instruktażu: Manipulowanie danych (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) pokazuje, jak wykonywać operacje na danych. Ten przewodnik nie wymaga zapisania dwa przewodniki w tej serii, które zostały już wykonane.  
  
## <a name="see-also"></a>Zobacz także
- [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
