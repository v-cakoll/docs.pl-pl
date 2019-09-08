---
title: Tożsamość obiektu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c788f2f9-65cc-4455-9907-e8388a268e00
ms.openlocfilehash: 053c861bae951f044d30d048951aa072b3d85a42
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792943"
---
# <a name="object-identity"></a>Tożsamość obiektu
Obiekty w środowisku uruchomieniowym mają unikatowe tożsamości. Dwie zmienne, które odwołują się do tego samego obiektu, faktycznie odwołują się do tego samego wystąpienia obiektu. Ze względu na ten fakt zmiany wprowadzane w drodze ścieżki za pomocą jednej zmiennej są natychmiast widoczne w innym.  
  
 Wiersze w tabeli relacyjnej bazy danych nie mają unikatowych tożsamości. Ponieważ każdy wiersz ma unikatowy klucz podstawowy, żadne dwa wiersze nie mają tej samej wartości klucza. Jednak ten fakt ogranicza tylko zawartość tabeli bazy danych.  
  
 W rzeczywistości dane są najczęściej przenoszone z bazy danych programu i do innej warstwy, w której działa aplikacja. Jest to model, który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje. Gdy dane są wyłączane z bazy danych jako wiersze, nie oczekuje się, że dwa wiersze reprezentujące te same dane odpowiadają tym samym wystąpieniem wiersza. Jeśli kwerenda dotyczy określonego klienta dwa razy, otrzymujesz dwa wiersze danych. Każdy wiersz zawiera te same informacje.  
  
 Z obiektami, których oczekuje coś bardzo się różni. Należy się spodziewać, że jeśli <xref:System.Data.Linq.DataContext> podasz te same informacje wielokrotnie, spowoduje to nadanie tego samego wystąpienia obiektu. To zachowanie jest oczekiwane, ponieważ obiekty mają specjalne znaczenie dla aplikacji i oczekiwano ich zachowania, jak obiekty. Zaprojektowano je jako hierarchie lub wykresy. Należy się spodziewać, że zostaną one pobrane jako takie i nie będą otrzymywać wielu zreplikowanych wystąpień tylko dlatego, że zażądano tego samego elementu co więcej niż jeden raz.  
  
 W programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]zarządzatożsamościąobiektu <xref:System.Data.Linq.DataContext> . Za każdym razem, gdy pobierasz nowy wiersz z bazy danych, wiersz jest rejestrowany w tabeli tożsamości według jego klucza podstawowego i tworzony jest nowy obiekt. Po każdym pobraniu tego samego wiersza wystąpienie oryginalnego obiektu zostanie przekazane do aplikacji. W ten sposób <xref:System.Data.Linq.DataContext> tłumaczy koncepcję tożsamości widzianą przez bazę danych (czyli klucze podstawowe) do koncepcji tożsamości widocznej dla języka (czyli wystąpień). Aplikacja widzi tylko obiekt w stanie, w którym został po raz pierwszy pobrany. Nowe dane, jeśli są inne, są odrzucane. Aby uzyskać więcej informacji, zobacz [pobieranie obiektów z pamięci podręcznej tożsamości](retrieving-objects-from-the-identity-cache.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]używa tego podejścia do zarządzania integralnością obiektów lokalnych w celu obsługi aktualizacji optymistycznych. Ze względu na to, że jedyne zmiany, które wystąpiły po utworzeniu obiektu po raz pierwszy, są wykonywane przez aplikację, zamiar aplikacji jest wyczyszczone. Jeśli zmiany dokonane przez stronę zewnętrzną wystąpiły w tymczasowym czasie, są one identyfikowane w momencie `SubmitChanges()` wywołania.  
  
> [!NOTE]
> Jeśli obiekt żądany przez zapytanie jest łatwo do zidentyfikowania, ponieważ został już pobrany, żadne zapytanie nie jest wykonywane. Tabela tożsamości działa jako pamięć podręczna wszystkich wcześniej pobranych obiektów.  
  
## <a name="examples"></a>Przykłady  
  
### <a name="object-caching-example-1"></a>Przykład buforowania obiektu 1  
 W tym przykładzie, jeśli wykonujesz to samo zapytanie dwa razy, otrzymujesz odwołanie do tego samego obiektu w pamięci za każdym razem.  
  
 [!code-csharp[DLinqObjectIdentity#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#1)]
 [!code-vb[DLinqObjectIdentity#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#1)]  
  
### <a name="object-caching-example-2"></a>Przykład buforowania obiektów 2  
 W tym przykładzie, jeśli wykonujesz inne zapytania, które zwracają ten sam wiersz z bazy danych, w każdym momencie otrzymujesz odwołanie do tego samego obiektu w pamięci.  
  
 [!code-csharp[DLinqObjectIdentity#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#2)]
 [!code-vb[DLinqObjectIdentity#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Informacje uzupełniające](background-information.md)
