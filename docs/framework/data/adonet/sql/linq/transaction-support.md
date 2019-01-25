---
title: Obsługa transakcji
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: f53a6081102991c73543b4cd76365f7e2c0faf89
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517204"
---
# <a name="transaction-support"></a>Obsługa transakcji
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje trzy modele distinct transakcji. Poniższa lista zawiera te modele, zgodnie z kolejnością kontrole wykonywane.  
  
## <a name="explicit-local-transaction"></a>Jawnych transakcji lokalnej  
 Gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> zostanie wywołana, jeśli <xref:System.Data.Linq.DataContext.Transaction%2A> właściwość jest ustawiona na (`IDbTransaction`) transakcji <xref:System.Data.Linq.DataContext.SubmitChanges%2A> wywołanie jest wykonywane w ramach tej samej transakcji.  
  
 Jest odpowiedzialny za zatwierdzenia lub wycofania transakcji po pomyślnym wykonaniu transakcji. Połączenie odpowiadające transakcji musi odpowiadać połączenie używane do konstruowania <xref:System.Data.Linq.DataContext>. Wyjątek jest generowany, jeśli jest używany przez inne połączenie.  
  
## <a name="explicit-distributable-transaction"></a>Transakcji jawnej dystrybucyjny  
 Możesz wywołać [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] interfejsy API (w tym między innymi <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) w zakresie aktywnego <xref:System.Transactions.Transaction>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wykrywa, że wywołanie znajduje się w zakresie transakcji i nie tworzy nową transakcję. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] unika również w tym przypadku zamknięcie połączenia. Można wykonać zapytania i <xref:System.Data.Linq.DataContext.SubmitChanges%2A> wykonania w ramach takich transakcji.  
  
## <a name="implicit-transaction"></a>Transakcji niejawnej  
 Gdy wywołujesz <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sprawdza, czy wywołanie znajduje się w zakresie <xref:System.Transactions.Transaction> lub jeśli `Transaction` właściwości (`IDbTransaction`) jest ustawiona na pracę użytkownika transakcji lokalnej. Jeśli znajdzie ani transakcji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozpoczyna się transakcji lokalnej (`IDbTransaction`) i używa go do wykonywania wygenerowany poleceń SQL. Po pomyślnym zakończeniu wszystkich poleceń SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zatwierdzeń transakcji lokalnej i zwraca.  
  
## <a name="see-also"></a>Zobacz także
- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [Instrukcje: Przesyłanie danych nawiasów za pomocą transakcji](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
