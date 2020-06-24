---
title: Poziomy zaufania zabezpieczeń podczas uzyskiwania dostępu do zasobów
description: Informacje o poziomach zaufania zabezpieczeń w przypadku uzyskiwania dostępu do zasobów w programie .NET. Istnieją trzy główne poziomy zaufania dla elementu System. Transactions.
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: 64f298460bde99181ab8dc8be13ae95aaa846299
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141955"
---
# <a name="security-trust-levels-in-accessing-resources"></a>Poziomy zaufania zabezpieczeń podczas uzyskiwania dostępu do zasobów
W tym temacie opisano, jak dostęp jest ograniczony do typów zasobów, które <xref:System.Transactions> przedstawia.  
  
 Istnieją trzy główne poziomy zaufania <xref:System.Transactions>. Poziomy zaufania są definiowane w oparciu o typy zasobów który <xref:System.Transactions> ujawnia i poziom zaufania, który powinien uzyskać dostęp do tych zasobów. Zasoby który <xref:System.Transactions> zapewnia dostęp do pamięci systemowej, zasoby całego procesu współużytkowanego i międzynarodowe zasoby systemowe. Dostępne są następujące poziomy:  
  
- **AllowPartiallyTrustedCallers** (APTCA) dla aplikacji korzystających z transakcji w ramach jednej domeny aplikacji.  
  
- **DistributedTransactionPermission** (DTP) dla aplikacji korzystających z transakcji rozproszonych.  
  
- Pełne zaufanie do trwałych zasobów, aplikacji do zarządzania konfiguracją i starszych aplikacji międzyoperacyjnych.  
  
> [!NOTE]
> Nie należy wywołać wszystkich interfejsów rejestracja przy użyciu personifikowanej kontekstów.  
  
## <a name="trust-levels"></a>Poziomy zaufania  
  
### <a name="aptca-partial-trust"></a>APTCA (częściowej relacji zaufania)  
 <xref:System.Transactions>Zestaw może być wywoływany przez częściowo zaufany kod, ponieważ został oznaczony przy użyciu atrybutu **ALLOWPARTIALLYTRUSTEDCALLERS** (APTCA). Ten atrybut zasadniczo usuwa niejawny <xref:System.Security.Permissions.SecurityAction.LinkDemand> dla zestawu uprawnień **FullTrust** , który jest w inny sposób automatycznie umieszczany w każdej publicznie dostępnej metodzie w każdym typie. Niektóre typy i elementy członkowskie nadal wymaga jednak lepsze gwarancje uprawnień.  
  
 Atrybut APTCA umożliwia aplikacjom używanie transakcji w częściowej relacji zaufania w ramach jednej domeny aplikacji. Umożliwia to-eskalowany transakcji i nietrwałe, które mogą być używane do obsługi błędów. Przykładem jest tabela skrótów transakcyjnych i aplikacja, która go używa. Dane mogą być dodawane do lub usunięte z tabeli skrótu w pojedynczą transakcję. Jeśli transakcja jest później wycofana, wszystkie zmiany wprowadzone w tabeli wyznaczania wartości skrótu, w tym transakcji można cofnąć.  
  
### <a name="distributedtransactionpermission-dtp"></a>DistributedTransactionPermission (DTP)  
 Gdy <xref:System.Transactions> eskalacji transakcji, aby były zarządzane przez MSDTC, <xref:System.Transactions> wymagań <xref:System.Transactions.DistributedTransactionPermission> (DTP), aby utworzyć transakcji rozproszonych. Oznacza to, że transakcje mogą być przekazany kod (takie jak za pomocą serializacji lub dodatkowe trwałych rejestracji) musi otrzymać DTP. Kod, który pierwotnie został utworzony <xref:System.Transactions> transakcji nie trzeba mieć to uprawnienie.  
  
### <a name="fulltrust-link-demands"></a>Wymaga FullTrust łącza  
 Ten poziom uprawnień jest przeznaczony do ograniczania aplikacji, które są zapisywane w trwałych zasobach. W przypadku niepowodzenia aplikacja musi mieć możliwość odzyskania przy użyciu Menedżera transakcji, aby określić końcowy wynik transakcji, dzięki czemu może ona zaktualizować stałe dane. Ten typ aplikacji jest znany jako Menedżer trwałego źródła. Klasycznym przykładem tego typu aplikacji jest SQL.  
  
 Aby włączyć odzyskiwanie, ten typ aplikacji umożliwia trwałe korzystanie z zasobów systemowych. Jest to spowodowane Menedżer transakcji do odzyskania musi zapamiętać transakcje, które mają wykonywane, dopóki nie można potwierdzić, że otrzymane wyniki wszystkich menedżerów trwałe zasobów, które uczestniczą w transakcji. W związku z tym ten typ aplikacji wymaga pełnego zaufania i nie należy go uruchamiać, chyba że zostanie udzielony ten poziom zaufania.  
  
 Aby uzyskać więcej informacji na temat trwałych rejestracji i odzyskiwania, zobacz temat [Rejestrowanie zasobów jako uczestników transakcji](enlisting-resources-as-participants-in-a-transaction.md) i [wykonywanie odzyskiwania](performing-recovery.md) .  
  
 Aplikacje korzystające ze starszej współdziałania z modelem COM+ również muszą mieć pełne zaufanie.  
  
 Poniżej znajduje się lista typów i elementów członkowskich, które nie są wywoływane przez częściowo zaufany kod, ponieważ są one uzupełnione atrybutem zabezpieczeń deklaratywnych **FullTrust** :  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
- <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
- <xref:System.Transactions.TransactionInterop>  
  
- <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
- <xref:System.Transactions.HostCurrentTransactionCallback>  
  
- <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
- <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
- <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 Tylko bezpośredni obiekt wywołujący jest wymagany do posiadania zestawu uprawnień **FullTrust** , aby używać powyższych typów lub metod.
