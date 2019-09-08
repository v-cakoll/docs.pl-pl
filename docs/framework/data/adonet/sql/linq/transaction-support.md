---
title: Obsługa transakcji
ms.date: 03/30/2017
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
ms.openlocfilehash: 9c7128ef432fa609b8d628bc74caebe790058ede
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792278"
---
# <a name="transaction-support"></a>Obsługa transakcji
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje trzy różne modele transakcji. Poniżej wymieniono te modele w kolejności przeprowadzanych kontroli.  
  
## <a name="explicit-local-transaction"></a>Jawna transakcja lokalna  
 Gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana, <xref:System.Data.Linq.DataContext.Transaction%2A> Jeśli właściwość jest ustawiona na <xref:System.Data.Linq.DataContext.SubmitChanges%2A> (`IDbTransaction`) transakcja, wywołanie jest wykonywane w kontekście tej samej transakcji.  
  
 Ponosisz odpowiedzialność za zatwierdzenie lub wycofanie transakcji po pomyślnym wykonaniu transakcji. Połączenie odpowiadające transakcji musi być zgodne z połączeniem używanym do konstruowania <xref:System.Data.Linq.DataContext>. Wyjątek jest generowany, jeśli używane jest inne połączenie.  
  
## <a name="explicit-distributable-transaction"></a>Jawna transakcja dystrybucyjna  
 Można wywołać [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] interfejsy API (w tym, ale nie <xref:System.Data.Linq.DataContext.SubmitChanges%2A>ograniczone do) w zakresie aktywnego. <xref:System.Transactions.Transaction> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]wykrywa, czy wywołanie znajduje się w zakresie transakcji i nie tworzy nowej transakcji. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]w takim przypadku unika się również zamykania połączenia. Można wykonywać zapytania i <xref:System.Data.Linq.DataContext.SubmitChanges%2A> wykonania w kontekście takich transakcji.  
  
## <a name="implicit-transaction"></a>Niejawna transakcja  
 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>Po wywołaniu, sprawdza [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , czy wywołanie znajduje się <xref:System.Transactions.Transaction> w zakresie lub `Transaction` czy właściwość (`IDbTransaction`) jest ustawiona na lokalną transakcję uruchomioną przez użytkownika. Jeśli nie znajdzie żadnej transakcji, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] program uruchamia transakcję lokalną`IDbTransaction`() i używa jej do wykonywania wygenerowanych poleceń SQL. Po pomyślnym zakończeniu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wszystkich poleceń SQL zostanie zatwierdzona lokalna transakcja i zwrócone.  
  
## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](background-information.md)
- [Instrukcje: Przeprzesyłanie danych w nawiasach przy użyciu transakcji](how-to-bracket-data-submissions-by-using-transactions.md)
