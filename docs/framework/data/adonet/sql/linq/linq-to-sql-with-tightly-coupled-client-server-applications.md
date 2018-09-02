---
title: LINQ to SQL ze ściśle powiązanymi aplikacjami klient serwer
ms.date: 03/30/2017
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
ms.openlocfilehash: 9c36fc1f402d3791611af47a3a6d997db4f31167
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408963"
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a>LINQ to SQL ze ściśle powiązanymi aplikacjami klient serwer
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] może służyć w warstwie środkowej za pomocą ściśle powiązane klienci Inteligentni w warstwie prezentacji. W scenariuszach, które wymagają dostępu do danych tylko do odczytu, nie kontroli optymistycznej współbieżności lub optymistycznej współbieżności z sygnaturami czasowymi nie istnieje znacznie więcej złożoności niż w przypadku ze scenariuszami zdalną. Jednak kiedy bazy danych wymaga optymistycznej współbieżności sprawdza oryginalne wartości, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie wymaga poziomu wsparcia Pełna zgodnooć wersji danych, który można znaleźć w zestawach danych. Jednak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] warstwy środkowej mogą wymieniać dane z klientami na dowolnej platformie.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] w [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] zapewnia brak infrastruktury do śledzenia stanu jednostki po ma zostały serializowany do klienta. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Umożliwia architektury zorientowanej na usługi, gdzie interakcji między warstwami danych i prezentacji są małe, jak i względnie niepodzielne, ale nie wykonuje żadnych Pełna zgodnooć wersji oryginalnej wartości. W związku z tym jeśli chcesz użyć klienta inteligentne ściśle powiązane z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]i baza danych używa optymistycznej współbieżności przy użyciu oryginalnych wartości, należy zaimplementować własny mechanizm komunikacji zmiany między warstwą prezentacji a środkowej warstwy. Zależy od projektantów systemów, aby zdecydować, czy warto to zrobić ten bit dodatkowej pracy w zamian za korzyści [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] udostępnia w warstwie środkowej. Z drugiej strony Jeśli baza danych zawiera sygnatury czasowe, następnie nie ma potrzeby niestandardowej logiki śledzenie zmian.  
  
## <a name="see-also"></a>Zobacz też  
 [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [N-warstwowa LINQ to SQL z użyciem usług internetowych](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [Praca z zestawami danych w aplikacjach n-warstwowych](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications)
