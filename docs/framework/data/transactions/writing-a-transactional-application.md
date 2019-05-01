---
title: Zapisywanie aplikacji transakcyjnej
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: 048df434ff0ada2ab5f8c7473913f6c34c05d1a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793494"
---
# <a name="writing-a-transactional-application"></a>Zapisywanie aplikacji transakcyjnej
Programistą transakcyjnych aplikacji, możesz skorzystać z dwóch modelach programowania udostępnione przez <xref:System.Transactions> przestrzeni nazw, można utworzyć transakcję. Można korzystać ze jawnego modelu programowania przy użyciu <xref:System.Transactions.Transaction> klasy lub niejawnych modelu programowania, w którym transakcje są zarządzane automatycznie przez infrastrukturę, za pomocą <xref:System.Transactions.TransactionScope> klasy. Zalecamy użycie niejawnej transakcji modelu do tworzenia aplikacji. Można znaleźć więcej informacji na temat korzystania z zakresu transakcji w [implementowanie transakcji niejawnej przy użyciu zakresu transakcji](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md) tematu.  
  
 Oba modele obsługuje zatwierdzania transakcji, gdy program dociera spójnego stanu. Jeśli zatwierdzanie zakończy się powodzeniem, transakcja została ona niezawodnie dokonana. W przypadku niepowodzenia Zatwierdzanie transakcji przerywa. Jeśli program aplikacji nie można pomyślnie ukończyć transakcji, próbuje przerwania i Cofnij skutków transakcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
### <a name="creating-a-transaction"></a>Tworzenie transakcji  
 <xref:System.Transactions> Nazw zawiera dwa modele do tworzenia transakcji. Modele te zostały uwzględnione w następujących tematach.  
  
 [Implementowanie transakcji niejawnej przy użyciu zakresu transakcji](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 W tym artykule opisano sposób, w jaki <xref:System.Transactions> przestrzeń nazw obsługuje tworzenie niejawne transakcji za pomocą <xref:System.Transactions.TransactionScope> klasy.  
  
 [Implementowanie transakcji jawnej przy użyciu CommitableTransakction](../../../../docs/framework/data/transactions/implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 W tym artykule opisano sposób, w jaki <xref:System.Transactions> przestrzeń nazw obsługuje tworzenie jawnego transakcji za pomocą <xref:System.Transactions.CommittableTransaction> klasy.  
  
### <a name="escalating-transaction-management"></a>Eskalowania zarządzania transakcji  
 Gdy transakcji musi mieć dostęp do zasobów w innej domenie aplikacji lub jeśli chcesz zarejestrować innego menedżera zasobów trwałe, transakcji jest automatycznie przekazany do były zarządzane przez MSDTC. Eskalacja transakcji opisanych w [Eskalacja zarządzania transakcjami](../../../../docs/framework/data/transactions/transaction-management-escalation.md) tematu.  
  
### <a name="concurrency"></a>Współbieżność  
 Temat [Zarządzanie współbieżnością za pomocą DependentTransaction](../../../../docs/framework/data/transactions/managing-concurrency-with-dependenttransaction.md) pokazuje, jak można osiągnąć współbieżności między asynchroniczne zadania przy użyciu <xref:System.Transactions.DependentTransaction> klasy.  
  
### <a name="com-interop"></a>Usługę Międzyoperacyjną modelu COM +  
 Temat [współdziałanie z usługami przedsiębiorstwa i transakcjami COM +](../../../../docs/framework/data/transactions/interoperability-with-enterprise-services-and-com-transactions.md) ilustruje, jak można realizowania transakcji rozproszonych interakcję z transakcji modelu COM +.  
  
### <a name="diagnostics"></a>Diagnostyka  
 [Dane śledzenia diagnostycznego](../../../../docs/framework/data/transactions/diagnostic-traces.md) w tym artykule opisano, jak skorzystać z kodów śledzenia, które są generowane przez <xref:System.Transactions> infrastruktury w celu usunięcia błędów w aplikacji.  
  
### <a name="working-within-aspnet"></a>Praca w ramach programu ASP.NET  
 [Przy użyciu System.Transactions w programie ASP.NET:](../../../../docs/framework/data/transactions/using-system-transactions-in-aspnet.md) temacie opisano, jak pomyślnie użyć <xref:System.Transactions> w aplikacji ASP.NET.
