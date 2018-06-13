---
title: Poziomy zaufania zabezpieczeń podczas uzyskiwania dostępu do zasobów
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: 8e7d632c361ea73cb65668e43506d9e1128d31ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357598"
---
# <a name="security-trust-levels-in-accessing-resources"></a>Poziomy zaufania zabezpieczeń podczas uzyskiwania dostępu do zasobów
W tym temacie opisano, jak dostęp jest ograniczony do typów zasobów, które <xref:System.Transactions> przedstawia.  
  
 Istnieją trzy główne poziomy zaufania <xref:System.Transactions>. Poziomy zaufania są definiowane w oparciu o typy zasobów który <xref:System.Transactions> ujawnia i poziom zaufania, który powinien uzyskać dostęp do tych zasobów. Zasoby który <xref:System.Transactions> zapewnia dostęp do pamięci systemowej, zasoby całego procesu współużytkowanego i międzynarodowe zasoby systemowe. Dostępne są następujące poziomy:  
  
-   **AllowPartiallyTrustedCallers** (APTCA) dla aplikacji za pomocą transakcji w obrębie domeny pojedynczej aplikacji.  
  
-   **DistributedTransactionPermission** (DTP) dla aplikacji za pomocą transakcji rozproszonych.  
  
-   Pełne zaufanie trwałe zasobów, konfiguracji aplikacji do zarządzania i starsze aplikacje międzyoperacyjne.  
  
> [!NOTE]
>  Nie należy wywołać wszystkich interfejsów rejestracja przy użyciu personifikowanej kontekstów.  
  
## <a name="trust-levels"></a>Poziomy zaufania  
  
### <a name="aptca-partial-trust"></a>APTCA (częściowej relacji zaufania)  
 <xref:System.Transactions> Zestawu może być wywoływany przez kod częściowo zaufany, ponieważ została ona oznaczona z **AllowPartiallyTrustedCallers** atrybutu (APTCA). Ten atrybut zasadniczo usuwa niejawne <xref:System.Security.Permissions.SecurityAction.LinkDemand> dla **FullTrust** oznacza to zestaw uprawnień w przeciwnym razie automatycznie umieszczane w każdej metody publicznie dostępne w poszczególnych typów. Niektóre typy i elementy członkowskie nadal wymaga jednak lepsze gwarancje uprawnień.  
  
 Atrybut APTCA umożliwia aplikacjom używanie transakcji w częściowej relacji zaufania w domenie pojedynczej aplikacji. Umożliwia to-eskalowany transakcji i nietrwałe, które mogą być używane do obsługi błędów. Przykładem tego jest tablicy skrótów transakcyjne i aplikacja, która korzysta z niego. Dane mogą być dodawane do lub usunięte z tabeli skrótu w pojedynczą transakcję. Jeśli transakcja jest później wycofana, wszystkie zmiany wprowadzone w tabeli wyznaczania wartości skrótu, w tym transakcji można cofnąć.  
  
### <a name="distributedtransactionpermission-dtp"></a>DistributedTransactionPermission (DTP)  
 Gdy <xref:System.Transactions> eskalacji transakcji, aby były zarządzane przez MSDTC, <xref:System.Transactions> wymagań <xref:System.Transactions.DistributedTransactionPermission> (DTP), aby utworzyć transakcji rozproszonych. Oznacza to, że transakcje mogą być przekazany kod (takie jak za pomocą serializacji lub dodatkowe trwałych rejestracji) musi otrzymać DTP. Kod, który pierwotnie został utworzony <xref:System.Transactions> transakcji nie trzeba mieć to uprawnienie.  
  
### <a name="fulltrust-link-demands"></a>Wymaga FullTrust łącza  
 Ten poziom uprawnień jest przeznaczony do ograniczenia aplikacji, które zapisują trwałe zasobów. W przypadku awarii aplikacji musi istnieć możliwość odzyskania z menedżerem transakcji, aby określić ostateczny wynik transakcji, tak aby można było uaktualnić trwałych danych. Ten typ aplikacji nosi nazwę menedżera trwałe źródła. Klasycznym przykładem tego typu aplikacji jest SQL.  
  
 Aby włączyć odzyskiwanie, ten typ aplikacji może stale zużywanie zasobów systemowych. Jest to spowodowane Menedżer transakcji do odzyskania musi zapamiętać transakcje, które mają wykonywane, dopóki nie można potwierdzić, że otrzymane wyniki wszystkich menedżerów trwałe zasobów, które uczestniczą w transakcji. Dlatego ten typ aplikacji wymaga pełnego zaufania i nie powinna być uruchamiana, chyba że któremu przyznano poziom zaufania.  
  
 Aby uzyskać więcej informacji o trwałych rejestracji i odzyskiwania, zobacz [rejestrowanie zasobów jako uczestnicy transakcji](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md) i [wykonywania odzyskiwania](../../../../docs/framework/data/transactions/performing-recovery.md) tematów.  
  
 Aplikacje wykonujące starszych międzyoperacyjnego korzystają z modelu COM + również muszą mieć pełne zaufanie.  
  
 Poniżej przedstawiono listę typów i członków, których nie można wywołać przez częściowo zaufanego kodu, ponieważ są one oznaczone **FullTrust** zabezpieczenia deklaratywne atrybutu:  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
-   <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
-   <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
-   <xref:System.Transactions.TransactionInterop>  
  
-   <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
-   <xref:System.Transactions.HostCurrentTransactionCallback>  
  
-   <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
-   <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
-   <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 Tylko do bezpośredniego obiektu wywołującego jest wymagany do posiadał **FullTrust** zestawu uprawnień do użycia powyżej typach lub metodach.
