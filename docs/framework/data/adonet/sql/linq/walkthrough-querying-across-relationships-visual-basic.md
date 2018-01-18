---
title: "Wskazówki: Wykonywanie zapytań w relacjach (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: a7da43e3-769f-4e07-bcd6-552b8bde66f4
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: fef9880d5f9fa652eab2eb0d17bbf782dc64773d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-querying-across-relationships-visual-basic"></a>Wskazówki: Wykonywanie zapytań w relacjach (Visual Basic)
W tym przewodniku zademonstrowano użycie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *skojarzenia* do reprezentowania relacji klucza obcego w bazie danych.  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 W tym przewodniku została napisana przy użyciu ustawienia środowiska deweloperskiego Visual Basic.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Należy wykonać [wskazówki: prosty Model obiektów i zapytań (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-simple-object-model-and-query-visual-basic.md). W tym przewodniku opiera się na tym z nich w tym pliku northwnd.mdf w c:\linqtest.  
  
## <a name="overview"></a>Omówienie  
 Ten przewodnik składa się z trzech głównych zadań:  
  
-   Dodawanie klasy jednostki do reprezentowania tabeli zamówienia w bazie danych Northwind.  
  
-   Uzupełniające adnotacje do `Customer` klasy do rozszerzania relacji między `Customer` i `Order` klasy.  
  
-   Tworzenie i uruchamianie zapytań, aby przetestować proces uzyskiwania `Order` informacji za pomocą `Customer` klasy.  
  
## <a name="mapping-relationships-across-tables"></a>Mapowanie relacji między tabelami  
 Po `Customer` definicji klasy, należy utworzyć `Order` definicji klasy jednostki, która zawiera następujący kod, który wskazuje, że `Orders.Customer` odnosi się jako klucz obcy do `Customers.CustomerID`.  
  
#### <a name="to-add-the-order-entity-class"></a>Aby dodać klasę jednostki kolejności  
  
-   Wpisz lub wklej następujący kod po `Customer` klasy:  
  
     [!code-vb[DLinqWalk2VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#1)]  
  
## <a name="annotating-the-customer-class"></a>Dodawanie adnotacji do klasy odbiorcy  
 W tym kroku adnotacji `Customer` klasy, aby wskazać jej relacji `Order` klasy. (To dodawanie nie jest niezbędne, ponieważ Definiowanie relacji w żadnym kierunku jest wystarczające, aby utworzyć łącze. Ale dodawanie Ta adnotacja umożliwiają łatwe przejście obiekty w obu kierunkach).  
  
#### <a name="to-annotate-the-customer-class"></a>Dla adnotacji klasy klienta  
  
-   Wpisz lub wklej następujący kod do `Customer` klasy:  
  
     [!code-vb[DLinqWalk2VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#2)]  
  
## <a name="creating-and-running-a-query-across-the-customer-order-relationship"></a>Tworzenie i uruchamianie zapytania w relacji zamówienie klienta  
 Teraz uzyskiwać dostęp do `Order` obiektów bezpośrednio z `Customer` obiektów, lub w przeciwną kolejności. Nie trzeba jawnie *sprzężenia* między klientami a zleceń.  
  
#### <a name="to-access-order-objects-by-using-customer-objects"></a>Dostęp do obiektów kolejności przy użyciu obiektów klienta  
  
1.  Modyfikowanie `Sub Main` metody, wpisując lub wklejając następujący kod do metody:  
  
     [!code-vb[DLinqWalk2VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#3)]  
  
2.  Naciśnij klawisz F5, aby debugować aplikację.  
  
     Dwie nazwy wyświetlane w oknie komunikatu i w oknie konsoli wyświetlane z wygenerowanego kodu SQL.  
  
3.  Zamknij okno komunikatu, aby zatrzymać debugowanie.  
  
## <a name="creating-a-strongly-typed-view-of-your-database"></a>Tworzenie silnie Typizowanego widoku bazy danych  
 Znacznie łatwiej rozpoczynać silnie typizowanego widoku bazy danych. Zdecydowanie wpisując <xref:System.Data.Linq.DataContext> obiektu, nie trzeba wywołania <xref:System.Data.Linq.DataContext.GetTable%2A>. Można użyć jednoznacznie tabel wszystkie zapytania, korzystając z silnie typizowaną <xref:System.Data.Linq.DataContext> obiektu.  
  
 W poniższych krokach utworzysz `Customers` jako tabelę jednoznacznie, który jest mapowany na tabeli Klienci w bazie danych.  
  
#### <a name="to-strongly-type-the-datacontext-object"></a>Do silnie typu DataContext obiektu  
  
1.  Dodaj następujący kod powyżej `Customer` deklaracji klasy.  
  
     [!code-vb[DLinqWalk2VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#4)]  
  
2.  Modyfikowanie `Sub Main` do użycia w silnie typizowaną <xref:System.Data.Linq.DataContext> w następujący sposób:  
  
     [!code-vb[DLinqWalk2VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk2VB/vb/Module1.vb#5)]  
  
3.  Naciśnij klawisz F5, aby debugować aplikację.  
  
     Dane wyjściowe z okna konsoli jest:  
  
     `ID=WHITC`  
  
4.  Naciśnij klawisz Enter w oknie konsoli, aby zamknąć aplikację.  
  
5.  Na **pliku** menu, kliknij przycisk **Zapisz wszystko** Jeśli chcesz zapisać tej aplikacji.  
  
## <a name="next-steps"></a>Następne kroki  
 Wskazówki dalej ([wskazówki: manipulowanie danych (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-manipulating-data-visual-basic.md)) pokazuje, jak można manipulować danymi. Ten przewodnik nie wymaga zapisać dwóch wskazówki w tej serii, która została już ukończona.  
  
## <a name="see-also"></a>Zobacz też  
 [Nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
