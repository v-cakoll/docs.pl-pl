---
title: 'Przewodnik: Wykonywanie zapytań w relacjach (C#)'
ms.date: 03/30/2017
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
ms.openlocfilehash: a9e0583b14c07df2b1de23ba37fa88552a4c5c7c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946948"
---
# <a name="walkthrough-querying-across-relationships-c"></a>Przewodnik: Wykonywanie zapytań w relacjach (C#)
W tym instruktażu przedstawiono sposób [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] użycia *skojarzeń* do reprezentowania relacji FOREIGN KEY w bazie danych.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 Ten Instruktaż został zapisany przy użyciu ustawień C# deweloperskich.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Należy wykonać [następujące instrukcje: Prosty model obiektu i zapytanie (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md). Ten przewodnik jest oparty na tym instruktażu, w tym o obecności pliku northwnd. mdf w c:\linqtest5.  
  
## <a name="overview"></a>Omówienie  
 Ten przewodnik składa się z trzech głównych zadań:  
  
- Dodawanie klasy jednostki do reprezentowania tabeli Orders w przykładowej bazie danych Northwind.  
  
- Uzupełnianie adnotacji do `Customer` klasy w celu zwiększenia relacji `Customer` między klasami `Order` i.  
  
- Utworzenie i uruchomienie zapytania w celu przetestowania uzyskiwania `Order` informacji przy `Customer` użyciu klasy.  
  
## <a name="mapping-relationships-across-tables"></a>Mapowanie relacji między tabelami  
 Po zdefiniowaniu `Order` `Order.Customer` `Customer.CustomerID`klasy Utwórz definicję klasy jednostki, która zawiera następujący kod, który wskazuje, że odnosi się jako klucz obcy do. `Customer`  
  
### <a name="to-add-the-order-entity-class"></a>Aby dodać klasę Entity Order  
  
- Wpisz lub wklej następujący kod po `Customer` klasie:  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a>Dodawanie adnotacji do klasy Customer  
 W tym kroku utworzysz adnotację `Customer` klasy, aby wskazać jej relację `Order` z klasą. (To dodawanie nie jest absolutnie konieczne, ponieważ zdefiniowanie relacji w dowolnym kierunku jest wystarczające do utworzenia linku. Jednak dodanie tej adnotacji umożliwia łatwe nawigowanie po obiektach w dowolnym kierunku.  
  
### <a name="to-annotate-the-customer-class"></a>Aby dodać adnotacje do klasy Customer  
  
- Wpisz lub wklej następujący kod do `Customer` klasy:  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Tworzenie i uruchamianie zapytania w ramach relacji zamówienia klienta  
 Teraz możesz uzyskiwać dostęp `Order` do obiektów bezpośrednio `Customer` z obiektów lub w odwrotnej kolejności. Nie jest potrzebne jawne dołączenie między klientami i zamówieniami.  
  
### <a name="to-access-order-objects-by-using-customer-objects"></a>Aby uzyskać dostęp do obiektów zamówienia przy użyciu obiektów klienta  
  
1. `Main` Zmodyfikuj metodę, wpisując lub wklejając następujący kod do metody:  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2. Naciśnij klawisz F5, aby debugować aplikację.  
  
    > [!NOTE]
    > Możesz wyeliminować kod SQL w oknie konsoli, dodając do niego komentarz `db.Log = Console.Out;`.  
  
3. Naciśnij klawisz ENTER w oknie konsoli, aby zatrzymać debugowanie.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Tworzenie widoku bazy danych o jednoznacznie określonym typie  
 Znacznie łatwiej jest zacząć od jednoznacznie określonego widoku bazy danych. Silnie wpisywanie <xref:System.Data.Linq.DataContext> obiektu nie wymaga wywołania do <xref:System.Data.Linq.DataContext.GetTable%2A>. Można używać tabel z jednoznacznie określonymi typami we wszystkich zapytaniach, gdy używasz obiektu <xref:System.Data.Linq.DataContext> silnie określonego typu.  
  
 W poniższych krokach `Customers` utworzysz jako tabelę o jednoznacznie określonym typie, która jest mapowana na tabelę Customers w bazie danych.  
  
### <a name="to-strongly-type-the-datacontext-object"></a>Aby silnie wpisać obiekt DataContext  
  
1. Dodaj następujący kod powyżej `Customer` deklaracji klasy.  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2. Zmodyfikuj metodę, tak aby używała silnie wpisanej <xref:System.Data.Linq.DataContext> metody w następujący sposób: `Main`  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3. Naciśnij klawisz F5, aby debugować aplikację.  
  
     Dane wyjściowe okna konsoli są następujące:  
  
     `ID=WHITC`  
  
4. Naciśnij klawisz ENTER w oknie konsoli, aby zatrzymać debugowanie.  
  
## <a name="next-steps"></a>Następne kroki  
 Następny Przewodnik ([Przewodnik: Manipulowanie danymi (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) demonstruje sposób manipulowania danymi. Ten Instruktaż nie wymaga zapisania dwóch instruktaży w tej serii, które zostały już wykonane.  
  
## <a name="see-also"></a>Zobacz także

- [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
