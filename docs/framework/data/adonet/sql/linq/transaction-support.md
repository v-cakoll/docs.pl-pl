---
title: "Obsługa transakcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 543ea3d1a0f767a10b36e040155e7e9304aca5a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="transaction-support"></a>Obsługa transakcji
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje trzy modele transakcji distinct. Poniższa lista zawiera te modele kolejności wykonać kontroli.  
  
## <a name="explicit-local-transaction"></a>Jawne transakcji lokalnej  
 Gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana, jeśli <xref:System.Data.Linq.DataContext.Transaction%2A> ma ustawioną wartość właściwości (`IDbTransaction`) transakcji, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> wywołanie jest wykonywany w kontekście tej samej transakcji.  
  
 Odpowiada Twojej zatwierdzania lub wycofywania transakcji po pomyślnym wykonaniu transakcji. Połączenie odpowiadające transakcji musi być zgodna połączenia używany do tworzenia <xref:System.Data.Linq.DataContext>. Jeśli jest używany przez inne połączenie, jest zgłaszany wyjątek.  
  
## <a name="explicit-distributable-transaction"></a>Jawne dystrybucyjnego transakcji  
 Możesz wywołać [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] interfejsów API (w tym między innymi <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) w zakresie aktywnego <xref:System.Transactions.Transaction>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]wykrywa, że wywołanie znajduje się w zakresie transakcji i nie tworzy nową transakcję. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]unika się również w takim przypadku zamknięcie połączenia. Można wykonywać zapytania i <xref:System.Data.Linq.DataContext.SubmitChanges%2A> wykonaniami w ramach takich transakcji.  
  
## <a name="implicit-transaction"></a>Niejawne transakcji  
 Podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sprawdza, czy połączenie jest w zakresie <xref:System.Transactions.Transaction> lub, jeśli `Transaction` właściwości (`IDbTransaction`) ma ustawioną wartość użytkownik rozpoczął transakcji lokalnej. W przypadku odnalezienia ani transakcji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uruchamia transakcji lokalnej (`IDbTransaction`) i używa go do wykonania polecenia SQL wygenerowany. Gdy wszystkie polecenia SQL została pomyślnie ukończona, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zatwierdza transakcji lokalnej i zwraca.  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Instrukcje: Przesyłanie danych nawiasów za pomocą transakcji](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
