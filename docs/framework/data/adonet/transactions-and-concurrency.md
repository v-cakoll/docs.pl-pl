---
title: Transakcje i współbieżność
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: c78031150d9b1209372dece49813dfcf0a03b9d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965212"
---
# <a name="transactions-and-concurrency"></a>Transakcje i współbieżność
Transakcja składa się z jednego polecenia lub grupy poleceń, które są wykonywane jako pakiet. Transakcje umożliwiają łączenie wielu operacji w pojedynczą jednostkę pracy. Jeśli wystąpi awaria w jednym punkcie transakcji, wszystkie aktualizacje można przywrócić do stanu sprzed transakcji.  
  
 Transakcja musi być zgodna z właściwościami KWASu — niepodzielności, spójności, izolacji i trwałości — w celu zagwarantowania spójności danych. Większość systemów relacyjnej bazy danych, takich jak Microsoft SQL Server, obsługa transakcji przez zapewnienie blokowania, rejestrowania i zarządzania transakcjami za każdym razem, gdy aplikacja kliencka wykonuje operację Update, INSERT lub DELETE.  
  
> [!NOTE]
> Transakcje obejmujące wiele zasobów mogą obniżać współbieżność, jeśli blokady są zbyt długie. W związku z tym Zachowaj transakcje tak krótkie, jak to możliwe.  
  
 Jeśli transakcja obejmuje wiele tabel w tej samej bazie danych lub serwerze, to jawne transakcje w procedurach składowanych często działają lepiej. Można tworzyć transakcje w SQL Server procedury składowane przy użyciu instrukcji Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`i `ROLLBACK TRANSACTION` . Aby uzyskać więcej informacji, zobacz SQL Server Books Online.  
  
 Transakcje dotyczące różnych menedżerów zasobów, takich jak transakcja między SQL Server i Oracle, wymagają transakcji rozproszonej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Transakcje lokalne](../../../../docs/framework/data/adonet/local-transactions.md)  
 Pokazuje, jak wykonywać transakcje względem bazy danych.  
  
 [Transakcje rozproszone](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 Opisuje sposób wykonywania transakcji rozproszonych w programie ADO.NET.  
  
 [Integracja System.Transactions z programem SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 Opisuje <xref:System.Transactions> integrację z SQL Server do pracy z transakcjami rozproszonymi.  
  
 [Optymistyczna współbieżność](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 Opisuje optymistyczne i pesymistyczne współbieżność oraz sposób testowania naruszeń współbieżności.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe informacje dotyczące transakcji](../../../../docs/framework/data/transactions/transaction-fundamentals.md)
- [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
