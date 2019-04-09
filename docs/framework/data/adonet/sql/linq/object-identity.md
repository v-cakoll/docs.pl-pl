---
title: Tożsamość obiektu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c788f2f9-65cc-4455-9907-e8388a268e00
ms.openlocfilehash: 0f1b6cf27101c2a7f55757b72b56b2291198404d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200665"
---
# <a name="object-identity"></a>Tożsamość obiektu
Obiekty w środowisku uruchomieniowym mają unikatowych tożsamości. Dwie zmienne odwołujące się do tego samego obiektu faktycznie dotyczą tego samego wystąpienia obiektu. Ze względu na fakt ten zmiany wprowadzone za pomocą ścieżki za pomocą jednej zmiennej są natychmiast widoczne przez innych.  
  
 Wiersze w tabeli relacyjnej bazy danych nie mają unikatowych tożsamości. Ponieważ każdy wiersz ma unikatowy klucz podstawowy, żadne dwa wiersze udostępnić taką samą wartość klucza. Jednak ten fakt ogranicza tylko zawartość tabeli bazy danych.  
  
 W rzeczywistości w większości przypadków przekazywane dane z bazy danych, a także do innej warstwy, w której aplikacja działa z nim. Jest to model, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje. Dane zaimportowane z bazy danych jako wiersze, użytkownik nie czy dwa wiersze, które reprezentują te same dane faktycznie odnoszą się do tych samych wystąpieniach wiersza. Po wykonaniu zapytania dotyczącego określonego odbiorcy dwa razy, uzyskasz dwa wiersze danych. Każdy wiersz zawiera te same informacje.  
  
 Przy użyciu obiektów oczekujesz, że coś, co jest bardzo różnią się. Należy oczekiwać, że jeśli poprosisz <xref:System.Data.Linq.DataContext> dla tych samych informacji cyklicznie, w rzeczywistości uzyskasz tego samego wystąpienia obiektu. To zachowanie jest oczekiwane, ponieważ obiekty mają specjalne znaczenie dla twojej aplikacji, a Twoim oczekiwaniom zachowują się jak obiekty. Możesz je zaprojektowany jako hierarchie lub wykresów. Spodziewasz się, pobrać je jako takie, a nie otrzymywać liczne replikowanych wystąpień, po prostu, ponieważ zażądano samo więcej niż jeden raz.  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.DataContext> zarządza tożsamość obiektu. Przy każdym pobraniu nowy wiersz z bazy danych wiersz jest zalogowany za pomocą klucza podstawowego tabeli tożsamości, a następnie tworzony jest nowy obiekt. Przy każdym pobraniu tym samym wierszu, oryginalne wystąpienie obiektu jest przekazywane ponownie do aplikacji. W ten sposób <xref:System.Data.Linq.DataContext> wykonuje translację koncepcji tożsamości widziany przez bazę danych (klucze podstawowe) na koncepcji tożsamości widzianych przez język (czyli wystąpienia). Aplikacja widoczny jest tylko obiekt w stanie, aby najpierw został pobrany. Nowe dane, jeśli są różne, zostaną odrzucone. Aby uzyskać więcej informacji, zobacz [pobieranie obiektów z pamięci podręcznej tożsamości](../../../../../../docs/framework/data/adonet/sql/linq/retrieving-objects-from-the-identity-cache.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] używa tego podejścia do zarządzania integralności obiektów lokalnych w celu obsługi optymistycznej aktualizacji. Ponieważ tylko zmiany, które wystąpiły po na początku tworzenia obiektu tych wykonywanych przez aplikację, celem aplikacji jest wyczyszczone. Jeśli zmiany przez stronę poza miały miejsce w międzyczasie, są identyfikowane w czasie `SubmitChanges()` jest wywoływana.  
  
> [!NOTE]
>  Jeśli żądany obiekt przez zapytanie jest łatwa do zidentyfikowania jako jeden już pobrane, jest wykonywane bez określenia zapytania. Tabela tożsamości działa jako pamięć podręczną wszystkich pobrane wcześniej obiektów.  
  
## <a name="examples"></a>Przykłady  
  
### <a name="object-caching-example-1"></a>Obiekt buforowania przykład 1  
 W tym przykładzie Jeśli wykonania tego samego zapytania dwa razy, zostanie wyświetlony odwołanie do tego samego obiektu w pamięci każdym razem.  
  
 [!code-csharp[DLinqObjectIdentity#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#1)]
 [!code-vb[DLinqObjectIdentity#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#1)]  
  
### <a name="object-caching-example-2"></a>Obiekt buforowania przykład 2  
 W tym przykładzie Jeśli wykonać różne zapytania, które zwracają ten sam wiersz z bazy danych, zostanie wyświetlony odwołanie do tego samego obiektu w pamięci każdym.  
  
 [!code-csharp[DLinqObjectIdentity#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#2)]
 [!code-vb[DLinqObjectIdentity#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
