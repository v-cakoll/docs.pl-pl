---
title: "Transakcje i współbieżność"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4e06f54ed27a555daa30f16f452cd03c8e188a0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="transactions-and-concurrency"></a>Transakcje i współbieżność
Transakcja składa się z jednego polecenia lub grupy poleceń, które są wykonywane w pakiecie. Transakcje pozwalają połączyć wiele operacji w pojedynczą jednostkę pracy. Jeśli wystąpi błąd w jednym punkcie w transakcji, wszystkie aktualizacje można go z powrotem obniżyć do stanu przed transakcji.  
  
 Transakcja musi być zgodna z właściwości ACID — niepodzielność, spójności, izolacji i odporność — w celu zagwarantowania spójności danych. Większość systemów relacyjnej bazy danych, takich jak Microsoft SQL Server, Obsługa transakcji podając, blokowanie, rejestrowanie i transakcji zarządzania urządzeń zawsze, gdy aplikacja kliencka przeprowadzi aktualizację, Wstaw lub operacji usuwania.  
  
> [!NOTE]
>  Transakcje, które obejmują wiele zasobów można obniżyć współbieżności, jeśli blokady są przechowywane zbyt długa. W związku z tym należy możliwie krótki transakcji.  
  
 Jeśli transakcja obejmuje wiele tabel w tej samej bazy danych lub serwerze, następnie jawnych transakcji w procedurach składowanych często działać lepiej. Można utworzyć transakcji w procedurach składowanych serwera SQL przy użyciu języka Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, i `ROLLBACK TRANSACTION` instrukcje. Aby uzyskać więcej informacji zobacz dokumentację SQL Server — książki Online.  
  
 Transakcje dotyczące menedżerów różnych zasobów, takich jak transakcji między [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] i Oracle, wymagają transakcji rozproszonej.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Lokalne transakcje](../../../../docs/framework/data/adonet/local-transactions.md)  
 Pokazuje, jak wykonywać transakcje w bazie danych.  
  
 [Transakcje rozproszone](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 Opisuje sposób wykonywania transakcji rozproszonych w ADO.NET.  
  
 [System.Transactions integracji z programem SQL Server](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 W tym artykule opisano <xref:System.Transactions> integracji z [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] do pracy z transakcji rozproszonych.  
  
 [Optymistycznej współbieżności](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 Opisuje optymistycznej i pesymistyczne współbieżności i jak można sprawdzić naruszenia współbieżności.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje dotyczące transakcji](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 [Połączenie ze źródłem danych](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [Poleceń i parametrów](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Obiektów DataAdapter i DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
