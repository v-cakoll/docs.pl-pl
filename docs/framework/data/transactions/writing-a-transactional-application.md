---
title: Zapisywanie aplikacji transakcyjnej
ms.date: 03/30/2017
ms.assetid: a4d891f2-6fc8-4395-93c6-6819492406e0
ms.openlocfilehash: 318771c83a5b7ebc0f3fb2bb8c59240269a2dea9
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205826"
---
# <a name="writing-a-transactional-application"></a>Zapisywanie aplikacji transakcyjnej
Jako programista aplikacji transakcyjnej możesz skorzystać z dwóch modeli programowania dostarczonych przez <xref:System.Transactions> przestrzeń nazw, aby utworzyć transakcję. Można użyć jawnego modelu programowania przy użyciu <xref:System.Transactions.Transaction> klasy lub niejawnego modelu programowania, w którym transakcje są automatycznie zarządzane przez infrastrukturę, <xref:System.Transactions.TransactionScope> przy użyciu klasy. Zalecamy użycie niejawnego modelu transakcji na potrzeby programowania. Więcej informacji na temat używania zakresu transakcji można znaleźć w temacie implementowanie niejawnej [transakcji przy użyciu zakresu transakcji](implementing-an-implicit-transaction-using-transaction-scope.md) .  
  
 Oba modele obsługuje zatwierdzania transakcji, gdy program dociera spójnego stanu. Jeśli zatwierdzanie zakończy się powodzeniem, transakcja została ona niezawodnie dokonana. W przypadku niepowodzenia Zatwierdzanie transakcji przerywa. Jeśli program aplikacji nie może pomyślnie ukończyć transakcji, próbuje przerwać i cofnąć skutki transakcji.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
### <a name="creating-a-transaction"></a>Tworzenie transakcji  
 <xref:System.Transactions> Nazw zawiera dwa modele do tworzenia transakcji. Modele te zostały uwzględnione w następujących tematach.  
  
 [Implementowanie transakcji niejawnej przy użyciu zakresu transakcji](implementing-an-implicit-transaction-using-transaction-scope.md)  
  
 Opisuje sposób, <xref:System.Transactions> w jaki przestrzeń nazw obsługuje tworzenie niejawnych transakcji <xref:System.Transactions.TransactionScope> przy użyciu klasy.  
  
 [Implementowanie transakcji jawnej przy użyciu CommitableTransakction](implementing-an-explicit-transaction-using-committabletransaction.md)  
  
 Opisuje sposób, <xref:System.Transactions> w jaki przestrzeń nazw obsługuje tworzenie jawnych transakcji <xref:System.Transactions.CommittableTransaction> przy użyciu klasy.  
  
### <a name="escalating-transaction-management"></a>Eskalowania zarządzania transakcji  
 Gdy transakcja musi uzyskać dostęp do zasobu w innej domenie aplikacji lub jeśli chcesz zarejestrować się w innym trwałym Menedżerze zasobów, transakcja zostanie automatycznie przekierowane, aby była zarządzana przez usługę MSDTC. Eskalacja transakcji znajduje się w temacie [Eskalacja zarządzania](transaction-management-escalation.md) transakcjami.  
  
### <a name="concurrency"></a>Współbieżność  
 Temat [Zarządzanie współbieżnością z DependentTransaction](managing-concurrency-with-dependenttransaction.md) pokazuje, jak współbieżność można osiągnąć między zadaniami asynchronicznymi <xref:System.Transactions.DependentTransaction> przy użyciu klasy.  
  
### <a name="com-interop"></a>Usługę Międzyoperacyjną modelu COM +  
 Temat współdziałania [z usługami przedsiębiorstwa i transakcji modelu COM+](interoperability-with-enterprise-services-and-com-transactions.md) ilustruje sposób, w jaki transakcje rozproszone mogą współdziałać z transakcjami modelu com+.  
  
### <a name="diagnostics"></a>Diagnostyka  
 [Ślady diagnostyczne](diagnostic-traces.md) opisują sposób użycia kodów śledzenia generowanych przez <xref:System.Transactions> infrastrukturę w celu rozwiązywania problemów z błędami w aplikacjach.  
  
### <a name="working-within-aspnet"></a>Praca w ramach programu ASP.NET  
 [W temacie using System. Transactions w ASP.NET](using-system-transactions-in-aspnet.md) opisano, jak można <xref:System.Transactions> pomyślnie użyć wewnątrz aplikacji ASP.NET.
