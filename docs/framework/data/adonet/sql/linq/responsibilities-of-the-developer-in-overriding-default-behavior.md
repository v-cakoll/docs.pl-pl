---
title: Obowiązki dewelopera podczas zastępowania domyślnego zachowania
ms.date: 03/30/2017
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
ms.openlocfilehash: 4bfb108e81f64ea368c6bcc846553eb1af5c23b1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792726"
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a>Obowiązki dewelopera podczas zastępowania domyślnego zachowania
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie wymusza następujących wymagań, ale zachowanie jest niezdefiniowane, jeśli te wymagania nie są spełnione.  
  
- Metoda przesłaniania nie może wywołać <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metody <xref:System.Data.Linq.Table%601.Attach%2A>lub. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]zgłasza wyjątek, jeśli te metody są wywoływane w metodzie przesłaniania.  
  
- Metody override nie mogą być używane do uruchamiania, zatwierdzania ani zatrzymywania transakcji. <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Operacja jest wykonywana w ramach transakcji. Wewnętrzna transakcja zagnieżdżona może zakłócać zewnętrzną transakcję. Metody przesłaniania obciążenia mogą rozpoczynać transakcję dopiero po ustaleniu, że operacja nie jest wykonywana w <xref:System.Transactions.Transaction>.  
  
- Metody przesłaniania powinny być zgodne z odpowiednimi optymistycznymi mapowania współbieżności. Metoda przesłaniania powinna zgłosić, <xref:System.Data.Linq.ChangeConflictException> gdy występuje konflikt optymistyczny współbieżności. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]przechwytuje ten wyjątek, dzięki czemu można prawidłowo przetwarzać <xref:System.Data.Linq.DataContext.SubmitChanges%2A> tę opcję. <xref:System.Data.Linq.DataContext.SubmitChanges%2A>  
  
- Metody Create`Insert`() `Update` i override powinny przepływać z powrotem wartości kolumn generowanych przez bazę danych do odpowiednich członków obiektów po pomyślnym zakończeniu operacji.  
  
     Na przykład jeśli `Order.OrderID` jest mapowany do kolumny tożsamości (klucz podstawowy*AutoIncrement* `InsertOrder()` ), Metoda override musi pobrać identyfikator wygenerowany przez `Order.OrderID` bazę danych i ustawić element członkowski na ten identyfikator. Podobnie elementy członkowskie znacznika czasu muszą zostać zaktualizowane do wartości sygnatur czasowych generowanych przez bazę danych, aby upewnić się, że zaktualizowane obiekty są spójne. Niepowodzenie propagowania wartości generowanych przez bazę danych może spowodować niespójność bazy danych i obiektów śledzonych przez <xref:System.Data.Linq.DataContext>.  
  
- Użytkownik jest odpowiedzialny za wywoływanie prawidłowego dynamicznego interfejsu API. Na przykład, w metodzie przesłaniania aktualizacji <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> można wywołać tylko metodę. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie wykrywa ani nie sprawdza, czy wywołana metoda dynamiczna pasuje do odpowiedniej operacji. W przypadku wywołania metody niestosowanej (na przykład <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> w przypadku obiektu, który ma zostać zaktualizowany) wyniki są niezdefiniowane.  
  
- Na koniec Metoda przesłaniania jest oczekiwana do wykonania określonej operacji. Semantyka [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] operacji, takich jak ładowanie eager, odroczone ładowanie i <xref:System.Data.Linq.DataContext.SubmitChanges%2A>), wymaga zastąpień w celu zapewnienia określonej usługi. Na przykład przesłonięcie obciążenia, które po prostu zwraca pustą kolekcję bez sprawdzania zawartości w bazie danych, prawdopodobnie spowoduje niespójne dane.  
  
## <a name="see-also"></a>Zobacz także

- [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](customizing-insert-update-and-delete-operations.md)
