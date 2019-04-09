---
title: 'Instrukcje: Przesyłanie zmian do bazy danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
ms.openlocfilehash: 572c4427ada06701c5982770ae476bd1c6c2b13a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59082545"
---
# <a name="how-to-submit-changes-to-the-database"></a>Instrukcje: Przesyłanie zmian do bazy danych
Niezależnie od tego, ile zmiany wprowadzone do obiektów zmiany są wprowadzane tylko do repliki w pamięci. Rzeczywiste dane w bazie danych wprowadzono żadnych zmian. Zmiany nie są przekazywane do serwera, dopóki nie zostanie jawnie wywołana <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext>.  
  
 Po wprowadzeniu tego wywołania <xref:System.Data.Linq.DataContext> próbuje tłumaczenie zmiany w środowisku równoważne polecenia SQL. Można użyć własnej logiki niestandardowej do zastąpienia tych akcji, ale kolejność przesyłania jest zarządzane przez usługę <xref:System.Data.Linq.DataContext> znane jako *zmienić procesora*. Kolejność zdarzeń jest następująca:  
  
1.  Gdy wywołujesz <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sprawdza zestawu obiektów znane, aby ustalić, czy nowe wystąpienia zostały dołączone do nich. Jeśli mają one te nowe wystąpienia są dodawane do zestawu obiektów śledzonych.  
  
2.  Wszystkie obiekty, które ma oczekujące zmiany są uporządkowane w sekwencji obiektów na podstawie zależności między nimi. Obiekty, w której zmiany są zależne od innych obiektów są ustawione w kolejności po ich zależności.  
  
3.  Od razu, przed przesłaniem żadnych rzeczywistych zmian [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozpoczyna się transakcja Hermetyzuj serię pojedynczych poleceń.  
  
4.  Zmiany do obiektów są przetłumaczone pojedynczo, aby poleceń SQL i wysyłane do serwera.  
  
 W tym momencie wszelkie błędy wykryte przez bazę danych, że proces przesyłania zatrzymać i zgłaszany jest wyjątek. Wszystkie zmiany do bazy danych jest przedstawiana tak, jakby nigdy nie wystąpił brak zgłoszenia. <xref:System.Data.Linq.DataContext> Środki, nieopłacone pełne rejestrowanie wszystkich zmian. W związku z tym można spróbować rozwiązać problem i wywołania <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ponownie, tak jak w poniższym przykładzie kodu.  
  
## <a name="example"></a>Przykład  
 Gdy transakcja wokół przesyłania zakończyło się powodzeniem, <xref:System.Data.Linq.DataContext> akceptuje zmiany do obiektów, ignorując informacji śledzenia zmian.  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)
- [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
