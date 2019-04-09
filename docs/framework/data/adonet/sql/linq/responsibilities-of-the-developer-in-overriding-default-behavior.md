---
title: Obowiązki dewelopera podczas zastępowania domyślnego zachowania
ms.date: 03/30/2017
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
ms.openlocfilehash: 12ea526d71946cdc7ab821f5e38948fcbb57d158
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184772"
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a>Obowiązki dewelopera podczas zastępowania domyślnego zachowania
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie wymusza następujące wymagania, ale zachowanie jest niezdefiniowane, jeśli te wymagania nie zostały spełnione.  
  
-   Metoda przesłaniania nie mogą wywoływać <xref:System.Data.Linq.DataContext.SubmitChanges%2A> lub <xref:System.Data.Linq.Table%601.Attach%2A>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zgłasza wyjątek, jeśli te metody są wywoływane w to metoda przesłonięcia.  
  
-   Zastąpienie metody nie można uruchomić, zatwierdzania lub zatrzymać transakcji. <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Operacja jest wykonywana w ramach transakcji. Wewnętrzny transakcji zagnieżdżonej może zakłócać zewnętrzne transakcji. Obciążenia zastąpienie metody można rozpocząć transakcji, tylko wtedy, gdy ustalają one, że operacja nie jest akurat wykonywane w <xref:System.Transactions.Transaction>.  
  
-   Zastąpienie metody powinny Wykonaj mapowanie dotyczy optymistycznej współbieżności. Metoda przesłaniająca powinien zgłosić <xref:System.Data.Linq.ChangeConflictException> gdy wystąpi konflikt optymistycznej współbieżności. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Przechwytuje ten wyjątek, dzięki czemu można poprawnie przetworzyć <xref:System.Data.Linq.DataContext.SubmitChanges%2A> opcji na <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
-   Tworzenie (`Insert`) i `Update` zastąpienie metody przewidywań powrotem wartości dla wygenerowanych w bazie danych kolumn do odpowiednich elementach członkowskich obiektu po pomyślnym zakończeniu operacji.  
  
     Na przykład jeśli `Order.OrderID` jest mapowany na kolumnę tożsamości (*autoincrement* klucza podstawowego), a następnie `InsertOrder()` metodę przesłaniającą należy pobrać identyfikator wygenerowanych w bazie danych i ustaw `Order.OrderID` elementu członkowskiego do tego identyfikatora. Podobnie znacznik czasu: elementy Członkowskie musi zostać zaktualizowany do wartości timestamp wygenerowanych w bazie danych, aby upewnić się, że zaktualizowanych obiektów są spójne. Błąd do propagowania wartości wygenerowanych w bazie danych może spowodować niespójność między bazy danych i obiektów śledzonych przez <xref:System.Data.Linq.DataContext>.  
  
-   Odpowiada za użytkownika wywołania poprawne dynamicznego interfejsu API. Na przykład w aktualizacji metoda musi zostać zastąpiona, tylko <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> może zostać wywołana. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie wykrywa ani nie Sprawdź, czy wywołana metoda dynamiczna pasuje do odpowiednich operacji. Jeśli zostanie wywołana metoda nie ma zastosowania (na przykład <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> dla obiektu do zaktualizowania), wyniki są niezdefiniowane.  
  
-   Na koniec metoda przesłaniania powinien wykonać określonej operacji. Semantyka [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] operacje, takie jak wczesne ładowanie, odroczone ładowanie, a <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) wymaga zastąpienia do zapewnienia określonej usługi. Na przykład obciążenia musi zostać zastąpiona, po prostu zwraca pustą kolekcję bez sprawdzania, czy zawartość w bazie danych prawdopodobnie spowoduje niespójność danych.  
  
## <a name="see-also"></a>Zobacz także

- [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
