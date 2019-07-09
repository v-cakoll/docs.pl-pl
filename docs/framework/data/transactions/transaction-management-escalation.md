---
title: Eskalacja zarządzania transakcjami
ms.date: 03/30/2017
ms.assetid: 1e96331e-31b6-4272-bbbd-29ed1e110460
ms.openlocfilehash: df2597d6fcce7fbd51f6f17bd42469cb7fcf3fdf
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662464"
---
# <a name="transaction-management-escalation"></a>Eskalacja zarządzania transakcjami
System Windows obsługuje zestaw usług i moduły, które razem stanowią Menedżera transakcji. Eskalacja zarządzania transakcji opisano proces migrację transakcji z jeden ze składników Menedżera transakcji na inny.  
  
 <xref:System.Transactions> obejmuje to składnik Menedżer transakcji koordynujący transakcję co najwyżej pojedynczy zasób trwałego lub wiele zasobów lotnych. Ponieważ Menedżer transakcji używa tylko wywołania domeny należącymi do tej aplikacji, daje najlepszą wydajność. Deweloperzy muszą nie komunikują się z menedżerem transakcji bezpośrednio. Zamiast tego wspólnej infrastruktury, definiujący interfejsów, wspólnego zachowania i klasy pomocy są dostarczane przez <xref:System.Transactions> przestrzeni nazw.  
  
 Jeśli chcesz zapewnić transakcji na obiekt w innej domenie aplikacji (w tym granic procesu i maszynowo) na tym samym komputerze <xref:System.Transactions> infrastruktury automatycznie Eskalowanie transakcji, które mają być zarządzane przez firmę Microsoft Distributed Transaction Coordinator (MSDTC). Eskalacji ma miejsce, gdy zarejestrować innego menedżera zasobów trwałe. Przy eskalacji, transakcji pozostaje zarządzanych w stanie z podwyższonym poziomem uprawnień do jej zakończenia.  
  
 Między <xref:System.Transactions> transakcji i transakcji MSDTC nie pośredniczące typu transakcji, które są udostępniane za pośrednictwem awansowanie jednego etapu rejestracji (PSPE). PSPE jest inny mechanizm ważne w <xref:System.Transactions> dla optymalizacji wydajności. Umożliwia trwałe zasób zdalny, znajduje się w domenie innej aplikacji, proces lub komputer, aby uczestniczyć w <xref:System.Transactions> transakcji bez powodowania zostać przekazany do transakcji MSDTC. Aby uzyskać więcej informacji o PSPE, zobacz [rejestrowanie zasobów jako uczestników transakcji](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md).  
  
## <a name="how-escalation-is-initiated"></a>Jak jest inicjowane eskalacji  
 Ponieważ MSDTC znajduje się w osobnym procesie i zamocowaniem transakcji MSDTC wyniki w wiadomości przesyłanych przez proces eskalacji transakcji powoduje zmniejszenie wydajności. Aby zwiększyć wydajność, należy opóźnić lub uniknąć kontaktu z MSDTC; w związku z tym musisz wiedzieć, jak i kiedy jest inicjowane eskalacji.  
  
 Tak długo, jak <xref:System.Transactions> infrastruktury obsługi lotnych zasobów i co najwyżej jeden trwały zasób, który obsługuje jednofazowy powiadomień, pozostanie transakcji w prawo własności <xref:System.Transactions> infrastruktury. Menedżer transakcji skorzysta tylko do tych zasobów, że na żywo, w tej samej domenie aplikacji i które logowania (zapisywanie wyniku transakcji na dysku) nie jest wymagane. Eskalację, które spowodowało, że <xref:System.Transactions> infrastruktury transferowania własność transakcji na MSDTC się stanie po:  
  
- Co najmniej jeden trwały zasobem, który nie obsługuje jednofazowy powiadomień jest zarejestrowany w transakcji.  
  
- Co najmniej dwa trwałe zasobów, które obsługują jednofazowy powiadomienia biorących udział w transakcji. Na przykład rejestrowanie jednego połączenia z SQL Server 2005 nie powoduje transakcji podwyższenie poziomu. Jednak zawsze przy otwieraniu drugie połączenie z bazą danych programu SQL Server 2005, bazy danych zarejestrować, powodując <xref:System.Transactions> infrastruktury wykrywa on jest drugi trwałe zasobów w transakcji, a Eskalowanie go do transakcji MSDTC.  
  
- Żądania transakcji w domenie innej aplikacji lub innego procesu "organizowania" jest wywoływana. Na przykład serializacji obiektu transakcji między granic domeny aplikacji. Obiekt transakcji jest przekazywane przez wartość, co oznacza, że każda próba krzyż granic domeny aplikacji (nawet w tym samym procesie) powoduje serializacji obiektu transakcji. Można przekazać obiektów transakcji przez wywołania zdalnej metody pobierającej <xref:System.Transactions.Transaction> jako parametr lub możesz wykonać następujące czynności dostępu zdalnego składników transakcyjnych obsługiwany. Serializuje obiekt transakcji i powoduje eskalację jako podczas transakcji jest serializowana na domenę aplikacji. Jest dystrybuowany i lokalny Menedżer transakcji nie jest już odpowiednie.  
  
 Poniższa tabela zawiera listę wszystkich możliwych wyjątków, które mogą być generowane podczas eskalacji.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Podjęto próbę eskalować transakcji z poziomu izolacji jest taki sam, <xref:System.Transactions.IsolationLevel.Snapshot>.|  
|<xref:System.Transactions.TransactionAbortedException>|Menedżer transakcji nie działa.|  
|<xref:System.Transactions.TransactionException>|Eskalacji nie powiedzie się, a aplikacja jest przerwana.|
