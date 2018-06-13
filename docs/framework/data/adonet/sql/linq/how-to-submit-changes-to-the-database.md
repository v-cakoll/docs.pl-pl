---
title: 'Porady: przesyłanie zmian w bazie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
ms.openlocfilehash: fef41cd1bcb9d1c4b98f96975c56bfa19c675608
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362889"
---
# <a name="how-to-submit-changes-to-the-database"></a>Porady: przesyłanie zmian w bazie danych
Niezależnie od tego, ile zmiany wprowadzane do obiektów zmiany są wprowadzane tylko replik w pamięci. Zostały wprowadzone żadne zmiany do danych rzeczywistych w bazie danych. Zmiany nie są przesyłane do serwera, dopóki nie zostanie jawnie wywołać <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext>.  
  
 Po wprowadzeniu tego wywołania <xref:System.Data.Linq.DataContext> próbuje tłumaczenie zmiany na równoważne polecenia SQL. Można używać niestandardowej logiki do przesłonięcia te akcje, ale kolejność przesyłanie jest zorkiestrowana przez usługę <xref:System.Data.Linq.DataContext> znany jako *zmienić procesora*. Kolejność zdarzeń wygląda następująco:  
  
1.  Podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sprawdza, czy zestaw znanymi obiektami, aby określić, czy nowe wystąpienia zostały dołączone do nich. Jeśli są dostępne, te nowe wystąpienia są dodawane do zestawu obiektów śledzonych.  
  
2.  Wszystkie obiekty, które mają oczekujące zmiany są uporządkowane w sekwencji obiektów na podstawie zależności między nimi. Obiekty, której zmiany są zależne od innych obiektów są ustawione w kolejności po ich zależności.  
  
3.  Bezpośrednio przed rzeczywiste zmiany są przesyłane, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uruchamia transakcja hermetyzują serię poszczególnych poleceń.  
  
4.  Zmiany do obiektów są tłumaczone kolejno polecenia SQL i wysłane do serwera.  
  
 W tym momencie procesu przesyłania zatrzymać spowodować błędy wykryte przez bazę danych i zgłoszony wyjątek. Wszystkie zmiany do bazy danych są wycofane tak, jakby nie przesłanych kiedykolwiek wystąpił. <xref:System.Data.Linq.DataContext> Nadal ma pełne rejestrowanie wszystkich wprowadzonych zmian. W związku z tym można spróbować rozwiązać problem i wywołanie <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ponownie, jak w następującym przykładzie kodu.  
  
## <a name="example"></a>Przykład  
 Gdy transakcji wokół przesyłania zakończyło się powodzeniem, <xref:System.Data.Linq.DataContext> akceptuje zmian do obiektów przez ignorowanie informacji śledzenia zmian.  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
