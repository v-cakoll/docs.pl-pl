---
title: Pisanie aplikacji transakcyjnych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c988f5ab5a342ad3282414634ca3bfc21f481ea5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="writing-a-transactional-application"></a>Pisanie aplikacji transakcyjnych
Dla programisty transakcyjnych aplikacji, możesz korzystać udostępniane przez modele programowania <xref:System.Transactions> przestrzeni nazw, aby utworzyć transakcji. Może korzystać z jawnym modelu programowania przy użyciu <xref:System.Transactions.Transaction> klasy lub niejawne modelu programowania, w którym transakcje są automatycznie zarządzane przez infrastrukturę, za pomocą <xref:System.Transactions.TransactionScope> klasy. Zalecane jest użycie transakcji niejawnej modelu do tworzenia aplikacji. Można znaleźć więcej informacji na temat sposobu użycia w zakresie transakcji [wykonania transakcji niejawnej przy użyciu zakresu transakcji](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) tematu.  
  
 Oba modele obsługuje zatwierdzania transakcji, gdy program dociera spójnego stanu. Jeśli zatwierdzanie zakończy się powodzeniem, transakcja została ona niezawodnie dokonana. W przypadku niepowodzenia Zatwierdzanie transakcji przerywa. Jeśli program aplikacji nie można pomyślnie ukończyć transakcji, podejmie próbę przerwania i Cofnij skutków transakcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
### <a name="creating-a-transaction"></a>Tworzenie transakcji  
 <xref:System.Transactions> Nazw zawiera dwa modele do tworzenia transakcji. Modele te zostały uwzględnione w następujących tematach.  
  
 [Implementowanie transakcji niejawnej przy użyciu zakresu transakcji](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Opisuje sposób <xref:System.Transactions> przestrzeń nazw obsługuje tworzenie niejawne transakcji za pomocą <xref:System.Transactions.TransactionScope> klasy.  
  
 [Implementowanie jawnych transakcji przy użyciu obiekcie CommittableTransaction](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 Opisuje sposób <xref:System.Transactions> przestrzeń nazw obsługuje tworzenie jawnych transakcji przy użyciu <xref:System.Transactions.CommittableTransaction> klasy.  
  
### <a name="escalating-transaction-management"></a>Eskalowania zarządzania transakcji  
 Gdy transakcji musi mieć dostęp do zasobu w innej domenie aplikacji lub jeśli chcesz zarejestrować w innej Menedżera zasobów trwałe, transakcja jest automatycznie przekazany do zarządza MSDTC. Eskalacja transakcji jest objęte [eskalacji zarządzania transakcji](../../../../docs/framework/data/transactions/transaction-management-escalation.md) tematu.  
  
### <a name="concurrency"></a>Współbieżność  
 Temat [Zarządzanie współbieżności z DependentTransaction](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md) pokazano, jak można osiągnąć współbieżności między zadań asynchronicznych za pomocą <xref:System.Transactions.DependentTransaction> klasy.  
  
### <a name="com-interop"></a>Usługę Międzyoperacyjną modelu COM +  
 Temat [współdziałanie z usługami przedsiębiorstwa i transakcje COM +](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md) przedstawiono, jak można realizowania transakcji rozproszonej interakcji z transakcji modelu COM +.  
  
### <a name="diagnostics"></a>Diagnostyka  
 [Dane śledzenia diagnostycznego](../../../../docs/framework/data/transactions/diagnostic-traces.md) w tym artykule opisano, jak używasz kody śledzenia, które są generowane przez <xref:System.Transactions> infrastruktury Rozwiązywanie problemów w aplikacji.  
  
### <a name="working-within-aspnet"></a>Praca w ramach programu ASP.NET  
 [Przy użyciu System.Transactions w programie ASP.NET](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md) temacie opisano, jak pomyślnie służy <xref:System.Transactions> wewnątrz aplikacji ASP.NET.
