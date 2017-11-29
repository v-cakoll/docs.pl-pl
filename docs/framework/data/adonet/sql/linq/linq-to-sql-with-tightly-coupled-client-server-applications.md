---
title: "LINQ do SQL z aplikacjami ściśle powiązane klient serwer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e3879d8eeec498f2855ee2b540f77570ee91109f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-sql-with-tightly-coupled-client-server-applications"></a>LINQ do SQL z aplikacjami ściśle powiązane klient serwer
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]można na warstwy środkowej klientom ściśle powiązane inteligentne w warstwie prezentacji. W scenariuszach, które wymagają dostępu do danych tylko do odczytu, nie sprawdzenie optymistycznej współbieżności lub optymistycznej współbieżności z sygnaturami czasowymi nie ma złożoność większą niż-remote scenariuszy. Kiedy bazy danych wymaga jednak optymistycznej współbieżności sprawdza z oryginalnych wartości [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie ma poziomu wsparcia dla dwustronną komunikację danych, który można znaleźć w zestawach danych. Jednak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] warstwy środkowej można wymieniać dane z klientów na dowolnej platformie.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]w [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] zapewnia bez infrastruktury do śledzenia stanu jednostki po ma zostały serializacji do klienta. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Umożliwia architektury zorientowane na usługę, której interakcji między warstwami danych i prezentacji są małe i względnie atomic, ale nie wykonuje żadnych dwustronną komunikację oryginalnych wartości. W związku z tym jeśli chcesz użyć klienta inteligentne ściśle powiązane z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]i bazy danych używa optymistycznej współbieżności z oryginalnych wartości, należy wdrożyć własny mechanizm komunikacji zmiany między warstwą prezentacji a drugie warstwy. Do projektanta systemu, aby zdecydować, czy warto to zrobić to bit dodatkowej pracy w zamian za korzyści [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zawiera warstwy środkowej. Z drugiej strony Jeśli baza danych ma sygnatury czasowe, to nie ma niestandardowej logiki śledzenie zmian nie jest konieczne.  
  
## <a name="see-also"></a>Zobacz też  
 [N-warstwowa oraz zdalnych aplikacji za pomocą LINQ do SQL](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)  
 [LINQ do SQL N-warstwowa z usługami sieci Web](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
 [Praca z zestawami danych w aplikacjach warstwowych](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20)
