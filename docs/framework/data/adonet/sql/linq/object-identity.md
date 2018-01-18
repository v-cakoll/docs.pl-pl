---
title: "Tożsamość obiektu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c788f2f9-65cc-4455-9907-e8388a268e00
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 21b8dbb934b778d792ff55d54f60fca92cac8e88
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="object-identity"></a>Tożsamość obiektu
Obiekty w środowisku uruchomieniowym mają unikatowych tożsamości. Dwie zmienne odwołujące się do tego samego obiektu faktycznie odwoływać się do tego samego wystąpienia obiektu. Ze względu na fakt ten zmiany wprowadzone na ścieżkę za pośrednictwem jednej zmiennej są od razu widoczne przez innych.  
  
 Wiersze w tabeli relacyjnej bazy danych nie mają unikatowych tożsamości. Ponieważ każdy wiersz ma unikatowy klucz podstawowy, żadne dwa wiersze udostępnić tę samą wartość klucza. Jednak ten fakt ogranicza tylko zawartość tabeli bazy danych.  
  
 W rzeczywistości najczęściej przekazywane dane z bazy danych z do innej warstwy, gdy aplikacja działa z nim. Jest to model który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje. Przekazywane dane z bazy danych jako wiersze, ma nie oczekuje, że odpowiadają faktycznie dwa wiersze, które reprezentują te same dane do tego samego wystąpienia wiersza. Po wykonaniu zapytania określonego klienta dwa razy, otrzymasz dwa wiersze danych. Każdy wiersz zawiera te same informacje.  
  
 Z obiektami spodziewasz się bardzo inny. Przypuszczasz, że jeśli zadajesz <xref:System.Data.Linq.DataContext> dla tych samych informacji, w rzeczywistości podaje tego samego wystąpienia obiektu. To zachowanie jest oczekiwane, ponieważ obiekty mają specjalne znaczenie dla aplikacji i dzieleniu zachowywać się jak w przypadku obiektów. Zaprojektowany je jako hierarchii lub wykresy. Spodziewasz się pobrać je jako takie, a nie otrzymywać multitudes zreplikowanych wystąpień wyłącznie z powodu zostanie wyświetlony monit o podanie samo więcej niż jeden raz.  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.DataContext> zarządza tożsamość obiektu. Zawsze, gdy nowy wiersz można pobrać z bazy danych, wiersz jest zalogowany za pomocą klucza podstawowego tabeli tożsamości i jest tworzony nowy obiekt. Przy każdym pobraniu samego wiersza oryginalnego wystąpienia obiektu jest przekazywany powrót do aplikacji. W ten sposób <xref:System.Data.Linq.DataContext> wykonuje translację pojęcie tożsamości widziany przez bazę danych (klucze podstawowe) na pojęcie tożsamości widziana przez język (to znaczy wystąpień). Aplikacja widoczny jest tylko obiekt w stanie, aby najpierw został pobrany. Nowe dane, jeśli jest inny, zostaną odrzucone. Aby uzyskać więcej informacji, zobacz [podczas pobierania obiektów z pamięci podręcznej tożsamości](../../../../../../docs/framework/data/adonet/sql/linq/retrieving-objects-from-the-identity-cache.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]korzysta z tej metody do zarządzania integralność lokalnej obiektów w celu obsługi optymistycznej aktualizacji. Ponieważ tylko zmiany, które są wykonywane po obiekt jest początkowo utworzony przez aplikację, celem aplikacji jest wyczyszczone. Jeśli zmiany przez firmę zewnętrzną wystąpiły w międzyczasie, są identyfikowane w czasie `SubmitChanges()` jest wywoływana.  
  
> [!NOTE]
>  Jeśli żądanego przez zapytanie obiektu identyfikację wśród już pobrane, kwerenda nie została wykonana. W tabeli tożsamości działa jako pamięci podręcznej wszystkich wcześniej pobrane obiektów.  
  
## <a name="examples"></a>Przykłady  
  
### <a name="object-caching-example-1"></a>Obiekt buforowania przykład 1  
 W tym przykładzie Jeśli wykonanie tej samej kwerendy dwa razy, pojawi się odwołanie do tego samego obiektu w pamięci zawsze.  
  
 [!code-csharp[DLinqObjectIdentity#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#1)]
 [!code-vb[DLinqObjectIdentity#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#1)]  
  
### <a name="object-caching-example-2"></a>Obiekt buforowania przykład 2  
 W tym przykładzie Jeśli można wykonywać różne zapytań, które zwracają tego samego wiersza z bazy danych, pojawi się odwołanie do tego samego obiektu w pamięci zawsze.  
  
 [!code-csharp[DLinqObjectIdentity#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectIdentity/cs/Program.cs#2)]
 [!code-vb[DLinqObjectIdentity#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectIdentity/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
