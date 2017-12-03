---
title: "Eskalacja zarządzania transakcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e96331e-31b6-4272-bbbd-29ed1e110460
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ff0eb124d2593ce16de58ca5df2f14f57d2c4c6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-management-escalation"></a>Eskalacja zarządzania transakcji
System Windows obsługuje zestaw usług i moduły, które razem stanowią Menedżera transakcji. Eskalacja zarządzania transakcji opisano proces migrację transakcji z jeden ze składników Menedżera transakcji na inny.  
  
 <xref:System.Transactions>zawiera składnik menedżera transakcji, która koordynuje transakcji związanej z co najwyżej jednego zasobu trwałe lub wiele zasobów volatile. Ponieważ menedżera transakcji używa tylko wywołania domeny należącymi do tej aplikacji, zapewni najlepszą wydajność. Deweloperzy muszą nie komunikują się z menedżerem transakcji bezpośrednio. Zamiast tego wspólnej infrastruktury, definiujący interfejsów, wspólnego zachowania i klasy pomocy są dostarczane przez <xref:System.Transactions> przestrzeni nazw.  
  
 Jeśli chcesz podać transakcji do obiektu w innej domenie aplikacji (w tym w granicach procesu i komputera) na tym samym komputerze <xref:System.Transactions> infrastruktury automatycznie Eskalowanie transakcji, które mają być zarządzane przez firmę Microsoft Koordynator transakcji rozproszonych (MSDTC). Eskalacji ma miejsce, gdy zarejestrować innego menedżera zasobów trwałe. Gdy przekazany, transakcja pozostaje zarządzanych w stanie z podwyższonym poziomem uprawnień do momentu jego zakończenia.  
  
 Między <xref:System.Transactions> transakcji i transakcji MSDTC nie pośredniczące typu transakcji, które są udostępniane za pośrednictwem awansowanie jednego etapu rejestracji (PSPE). PSPE jest inny mechanizm ważne w <xref:System.Transactions> dla optymalizacji wydajności. Umożliwia trwałe zasób zdalny, znajduje się w domenie innej aplikacji, proces lub komputera, aby uczestniczyć w <xref:System.Transactions> transakcji bez powodowania, która ma zostać przekazany do transakcji usługi MSDTC. Aby uzyskać więcej informacji o PSPE, zobacz [rejestrowanie zasobów jako uczestnicy transakcji](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md).  
  
## <a name="how-escalation-is-initiated"></a>Jak jest inicjowane eskalacji  
 Ponieważ MSDTC znajduje się w osobnym procesie i zamocowaniem transakcji MSDTC wyniki w wiadomości przesyłanych przez proces eskalacji transakcji powoduje zmniejszenie wydajności. Aby zwiększyć wydajność, należy opóźnienie lub zapobiec eskalacji do usługi MSDTC; w związku z tym musisz wiedzieć, jak i kiedy eskalacji jest inicjowana.  
  
 Tak długo, jak <xref:System.Transactions> infrastruktury obsługi lotnych zasobów i co najwyżej jeden trwały zasób, który obsługuje jednofazowy powiadomień, pozostanie transakcji w prawo własności <xref:System.Transactions> infrastruktury. Menedżer transakcji korzysta tylko do tych zasobów, że na żywo, w tej samej domenie aplikacji i dla których rejestrowania (zapisywania wyniku transakcji na dysku) nie jest wymagane. Eskalację, które spowodowało, że <xref:System.Transactions> infrastruktury transferowania własność transakcji na MSDTC się stanie po:  
  
-   Co najmniej jeden trwały zasobem, który nie obsługuje jednofazowy powiadomień jest zarejestrowany w transakcji.  
  
-   Co najmniej dwa trwałe zasobów, które obsługują jednofazowy powiadomienia biorących udział w transakcji. Na przykład rejestrowanie pojedynczego połączenia z [!INCLUDE[sqprsqlong](../../../../includes/sqprsqlong-md.md)] powoduje, że nie można podwyższyć poziomu transakcji. Jednak zawsze przy otwieraniu drugie połączenie z [!INCLUDE[sqprsqlong](../../../../includes/sqprsqlong-md.md)] bazy danych, co powoduje bazy danych zarejestrować, <xref:System.Transactions> infrastruktury wykrywa on jest drugi trwałe zasobów w transakcji, a Eskalowanie go do transakcji MSDTC.  
  
-   Żądanie do transakcji do domeny innej aplikacji lub inny proces "organizowania" jest wywoływana. Na przykład serializacji obiektu transakcji granicy domeny aplikacji. Obiekt transakcji jest przekazywane przez wartość, co oznacza, że każda próba przekazania go granicy domeny aplikacji (nawet w tym samym procesie) powoduje serializacji obiektu transakcji. Można przekazać obiektów transakcji przez wywołania zdalnej metody pobierającej <xref:System.Transactions.Transaction> jako parametr lub możesz wykonać następujące czynności dostępu zdalnego składników transakcyjnych obsługiwany. Serializuje obiekt transakcji i powoduje eskalacji jako podczas transakcji jest serializowany w domenie aplikacji. Jest dystrybuowany i lokalny Menedżer transakcji nie jest już odpowiednie.  
  
 Poniższa tabela zawiera listę wszystkich możliwych wyjątków, które mogą być generowane podczas eskalacji.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Podjęto próbę eskalować transakcji z poziomu izolacji jest taki sam, <xref:System.Transactions.IsolationLevel.Snapshot>.|  
|<xref:System.Transactions.TransactionAbortedException>|Menedżer transakcji nie działa.|  
|<xref:System.Transactions.TransactionException>|Eskalacji kończy się niepowodzeniem i aplikacji zostało przerwane.|
