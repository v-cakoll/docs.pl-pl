---
title: "Wskazówki: Wykonywanie zapytań w relacjach (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 552abeb1-18f2-4e93-a9c6-ef7b2db30c32
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c294b888d95c4d6a77d96198f885c2363fda4e36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-querying-across-relationships-c"></a>Wskazówki: Wykonywanie zapytań w relacjach (C#)
W tym przewodniku zademonstrowano użycie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *skojarzenia* do reprezentowania relacji klucza obcego w bazie danych.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 W tym przewodniku została napisana przy użyciu programu Visual C# programowanie ustawienia.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Należy wykonać [wskazówki: proste modelu obiektów i kwerendy (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-csharp.md). W tym przewodniku opiera się na tym z nich w tym pliku northwnd.mdf w c:\linqtest5.  
  
## <a name="overview"></a>Omówienie  
 Ten przewodnik składa się z trzech głównych zadań:  
  
-   Dodawanie klasy jednostki do reprezentowania tabeli zamówienia w bazie danych Northwind.  
  
-   Uzupełniające adnotacje do `Customer` klasy do rozszerzania relacji między `Customer` i `Order` klasy.  
  
-   Tworzenie i uruchamianie zapytań, aby przetestować uzyskiwanie `Order` informacji za pomocą `Customer` klasy.  
  
## <a name="mapping-relationships-across-tables"></a>Mapowanie relacji między tabelami  
 Po `Customer` definicji klasy, należy utworzyć `Order` definicji klasy jednostki, która zawiera następujący kod, który wskazuje, że `Order.Customer` odnosi się jako klucz obcy do `Customer.CustomerID`.  
  
#### <a name="to-add-the-order-entity-class"></a>Aby dodać klasę jednostki kolejności  
  
-   Wpisz lub wklej następujący kod po `Customer` klasy:  
  
     [!code-csharp[DLinqWalk2CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#1)]  
  
## <a name="annotating-the-customer-class"></a>Dodawanie adnotacji do klasy odbiorcy  
 W tym kroku adnotacji `Customer` klasy, aby wskazać jej relacji `Order` klasy. (To dodawanie nie jest niezbędne, ponieważ Definiowanie relacji w żadnym kierunku jest wystarczające, aby utworzyć łącze. Ale dodawanie Ta adnotacja umożliwiają łatwe przejście obiekty w obu kierunkach).  
  
#### <a name="to-annotate-the-customer-class"></a>Dla adnotacji klasy klienta  
  
-   Wpisz lub wklej następujący kod do `Customer` klasy:  
  
     [!code-csharp[DLinqWalk2CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Tworzenie i uruchamianie zapytania w relacji zamówienie klienta  
 Teraz uzyskiwać dostęp do `Order` obiektów bezpośrednio z `Customer` obiektów, lub w przeciwną kolejności. Nie trzeba jawnie *sprzężenia* między klientami a zleceń.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Dostęp do obiektów kolejności przy użyciu obiektów klienta  
  
1.  Modyfikowanie `Main` metody, wpisując lub wklejając następujący kod do metody:  
  
     [!code-csharp[DLinqWalk2CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#3)]  
  
2.  Naciśnij klawisz F5, aby debugować aplikację.  
  
    > [!NOTE]
    >  Kod SQL w oknie konsoli można wyeliminować przez komentowania limit `db.Log = Console.Out;`.  
  
3.  Naciśnij klawisz Enter w oknie konsoli, aby zatrzymać debugowanie.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Tworzenie silnie Typizowanego widoku bazy danych  
 Znacznie łatwiej rozpoczynać silnie typizowanego widoku bazy danych. Zdecydowanie wpisując <xref:System.Data.Linq.DataContext> obiektu, nie trzeba wywołania <xref:System.Data.Linq.DataContext.GetTable%2A>. Można użyć jednoznacznie tabel wszystkie zapytania, korzystając z silnie typizowaną <xref:System.Data.Linq.DataContext> obiektu.  
  
 W poniższych krokach utworzysz `Customers` jako tabelę jednoznacznie, który jest mapowany na tabeli Klienci w bazie danych.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>Do silnie typu DataContext obiektu  
  
1.  Dodaj następujący kod powyżej `Customer` deklaracji klasy.  
  
     [!code-csharp[DLinqWalk2CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#4)]  
  
2.  Modyfikowanie `Main` metoda do użycia w silnie typizowaną <xref:System.Data.Linq.DataContext> w następujący sposób:  
  
     [!code-csharp[DLinqWalk2CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk2CS/cs/Program.cs#5)]  
  
3.  Naciśnij klawisz F5, aby debugować aplikację.  
  
     Dane wyjściowe z okna konsoli jest:  
  
     `ID=WHITC`  
  
4.  Naciśnij klawisz Enter w oknie konsoli, aby zatrzymać debugowanie.  
  
## <a name="next-steps"></a>Następne kroki  
 Wskazówki dalej ([wskazówki: manipulowanie danych (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-csharp.md)) pokazuje, jak można manipulować danymi. Ten przewodnik nie wymaga zapisać dwóch wskazówki w tej serii, która została już ukończona.  
  
## <a name="see-also"></a>Zobacz też  
 [Learning przez — wskazówki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
