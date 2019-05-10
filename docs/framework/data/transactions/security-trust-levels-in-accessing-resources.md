---
title: Poziomy zaufania zabezpieczeń podczas uzyskiwania dostępu do zasobów
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: 847467b964e86f6d13be6ba103162512270fa684
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596757"
---
# <a name="security-trust-levels-in-accessing-resources"></a>Poziomy zaufania zabezpieczeń podczas uzyskiwania dostępu do zasobów
W tym temacie opisano, jak dostęp jest ograniczony do typów zasobów, które <xref:System.Transactions> przedstawia.  
  
 Istnieją trzy główne poziomy zaufania <xref:System.Transactions>. Poziomy zaufania są definiowane w oparciu o typy zasobów który <xref:System.Transactions> ujawnia i poziom zaufania, który powinien uzyskać dostęp do tych zasobów. Zasoby który <xref:System.Transactions> zapewnia dostęp do pamięci systemowej, zasoby całego procesu współużytkowanego i międzynarodowe zasoby systemowe. Dostępne są następujące poziomy:  
  
- **AllowPartiallyTrustedCallers** (APTCA) dla aplikacji za pomocą transakcji wewnątrz domeny pojedynczej aplikacji.  
  
- **DistributedTransactionPermission** (DTP) dla aplikacji za pomocą transakcjach rozproszonych.  
  
- Pełne zaufanie trwałe zasobów, konfiguracji zarządzania aplikacjami i starsze aplikacje współdziałania.  
  
> [!NOTE]
>  Nie należy wywołać wszystkich interfejsów rejestracja przy użyciu personifikowanej kontekstów.  
  
## <a name="trust-levels"></a>Poziomy zaufania  
  
### <a name="aptca-partial-trust"></a>APTCA (częściowej relacji zaufania)  
 <xref:System.Transactions> Zestawu może być wywoływany przez częściowo zaufany kod, ponieważ została ona oznaczona przy użyciu **AllowPartiallyTrustedCallers** atrybutu (APTCA). Ten atrybut zasadniczo usuwa niejawne <xref:System.Security.Permissions.SecurityAction.LinkDemand> dla **FullTrust** oznacza to zestaw uprawnień w przeciwnym razie automatycznie umieszczane w każdej metody publicznie w każdego typu. Niektóre typy i elementy członkowskie nadal wymaga jednak lepsze gwarancje uprawnień.  
  
 Atrybut APTCA umożliwia aplikacji, aby móc używać transakcji w częściowej relacji zaufania w ramach domeny pojedynczej aplikacji. Umożliwia to-eskalowany transakcji i nietrwałe, które mogą być używane do obsługi błędów. Przykładem jest tabela transacted skrótu i aplikacji, która korzysta z niego. Dane mogą być dodawane do lub usunięte z tabeli skrótu w pojedynczą transakcję. Jeśli transakcja jest później wycofana, wszystkie zmiany wprowadzone w tabeli wyznaczania wartości skrótu, w tym transakcji można cofnąć.  
  
### <a name="distributedtransactionpermission-dtp"></a>DistributedTransactionPermission (DTP)  
 Gdy <xref:System.Transactions> eskalacji transakcji, aby były zarządzane przez MSDTC, <xref:System.Transactions> wymagań <xref:System.Transactions.DistributedTransactionPermission> (DTP), aby utworzyć transakcji rozproszonych. Oznacza to, że transakcje mogą być przekazany kod (takie jak za pomocą serializacji lub dodatkowe trwałych rejestracji) musi otrzymać DTP. Kod, który pierwotnie został utworzony <xref:System.Transactions> transakcji nie trzeba mieć to uprawnienie.  
  
### <a name="fulltrust-link-demands"></a>Wymaga FullTrust łącza  
 Ten poziom uprawnień jest przeznaczona do ograniczenia aplikacji, które zapisują trwałe zasobów. W przypadku awarii aplikacji musi być możliwe odzyskanie z menedżerem transakcji w celu ustalenia końcowego wyniku transakcji, tak, aby zaktualizować trwała danych. Ten typ aplikacji jest znany jako Menedżer trwałe źródła. Klasyczny przykład tego typu aplikacji jest SQL.  
  
 Aby włączyć odzyskiwanie, ten typ aplikacji ma możliwość trwale użycie zasobów systemowych. Jest to spowodowane Menedżer transakcji do odzyskania musi zapamiętać transakcje, które mają wykonywane, dopóki nie można potwierdzić, że otrzymane wyniki wszystkich menedżerów trwałe zasobów, które uczestniczą w transakcji. W związku z tym ten typ aplikacji wymaga pełnego zaufania i nie powinna być uruchamiana, chyba że których przypisano poziom zaufania.  
  
 Aby uzyskać więcej informacji na trwałych rejestracji i odzyskiwania, zobacz [rejestrowanie zasobów jako uczestników transakcji](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) i [przeprowadzania odzyskiwania](../../../../docs/framework/data/transactions/performing-recovery.md) tematów.  
  
 Aplikacje, które wykonują starszego współdziałania pracę z modelu COM + wymagane są także być pełnego zaufania.  
  
 Poniżej przedstawiono listę typów i elementów członkowskich, które nie są wywoływane przez częściowo zaufanego kodu, ponieważ mają one z **FullTrust** atrybut deklaratywne zabezpieczeń:  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
- <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
- <xref:System.Transactions.TransactionInterop>  
  
- <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
- <xref:System.Transactions.HostCurrentTransactionCallback>  
  
- <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
- <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
- <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 Tylko do bezpośredniego obiektu wywołującego jest wymagana do posiadają **FullTrust** uprawnienia skonfigurowane do korzystania z powyższych typów lub metody.
