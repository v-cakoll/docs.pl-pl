---
title: Transakcje i współbieżność
ms.date: 03/30/2017
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
ms.openlocfilehash: ba857031a54374ee295c2bfd724e7fb8651b7c1f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174697"
---
# <a name="transactions-and-concurrency"></a>Transakcje i współbieżność
Transakcja składa się z jednego polecenia lub grupy poleceń, które są wykonywane w pakiecie. Transakcje pozwala połączyć wiele operacji w pojedynczą jednostkę pracy. Jeśli wystąpi awaria w jednym punkcie w transakcji, wszystkie aktualizacje można wycofać do stanu wstępnego transakcji.  
  
 Transakcji musi odpowiadać właściwości ACID — niepodzielności, spójności, izolacji i trwałości — w celu zagwarantowania spójności danych. Większość systemy relacyjnych baz danych, takich jak Microsoft SQL Server, transakcje pomocy technicznej, podając, blokowanie, rejestrowanie i transakcji Zarządzanie usługą zawsze wtedy, gdy aplikacja kliencka przeprowadzi aktualizację, wstawiania lub usuwania operacji.  
  
> [!NOTE]
>  Transakcje obejmujące wiele zasobów można zmniejszyć współbieżność, jeśli blokady są przechowywane za długa. W związku z tym Zachowaj możliwie krótkie transakcji.  
  
 Jeśli transakcja wiąże się z wielu tabel w tej samej bazy danych lub serwerze, następnie jawnego transakcji w procedurach składowanych często działać lepiej. Można utworzyć transakcji w procedurach składowanych serwera SQL Server przy użyciu języka Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, i `ROLLBACK TRANSACTION` instrukcji. Aby uzyskać więcej informacji zobacz dokumentację SQL Server — książki Online.  
  
 Transakcje dotyczące inny zasób menedżerów, takich jak transakcji między programu SQL Server i Oracle, wymagają transakcji rozproszonej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Transakcje lokalne](../../../../docs/framework/data/adonet/local-transactions.md)  
 Pokazuje, jak wykonywać transakcje w bazie danych.  
  
 [Transakcje rozproszone](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 W tym artykule opisano, jak wykonywać transakcje rozproszone w ADO.NET.  
  
 [Integracja System.Transactions z programem SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 W tym artykule opisano <xref:System.Transactions> integracji z programem SQL Server do pracy z transakcje rozproszone.  
  
 [Optymistyczna współbieżność](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 W tym artykule opisano optymistyczne i pesymistycznej współbieżności i jak można sprawdzić, naruszenia współbieżności.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawowe informacje dotyczące transakcji](../../../../docs/framework/data/transactions/transaction-fundamentals.md)
- [Nawiązywanie połączenia ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Elementy DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
