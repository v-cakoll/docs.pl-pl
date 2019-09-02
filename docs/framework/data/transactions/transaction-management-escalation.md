---
title: Eskalacja zarządzania transakcjami
ms.date: 03/30/2017
ms.assetid: 1e96331e-31b6-4272-bbbd-29ed1e110460
ms.openlocfilehash: d2f027f8a94ee8f0cd23d0f0909ecc9137873bc2
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205846"
---
# <a name="transaction-management-escalation"></a>Eskalacja zarządzania transakcjami
System Windows obsługuje zestaw usług i moduły, które razem stanowią Menedżera transakcji. Eskalacja zarządzania transakcji opisano proces migrację transakcji z jeden ze składników Menedżera transakcji na inny.  
  
 <xref:System.Transactions>zawiera składnik Menedżera transakcji, który koordynuje transakcję obejmującą co najwyżej pojedynczy zasób trwały lub wiele zasobów lotnych. Ponieważ Menedżer transakcji używa tylko wywołań domeny wewnątrz aplikacji, zapewnia najlepszą wydajność. Deweloperzy muszą nie komunikują się z menedżerem transakcji bezpośrednio. Zamiast tego wspólnej infrastruktury, definiujący interfejsów, wspólnego zachowania i klasy pomocy są dostarczane przez <xref:System.Transactions> przestrzeni nazw.  
  
 Jeśli chcesz podać transakcję do obiektu w innej domenie aplikacji (w tym między granicami procesów i maszyn) na tym samym komputerze, <xref:System.Transactions> infrastruktura automatycznie przeniesie transakcję, która ma być zarządzana przez firmę Microsoft. Distributed Transaction Coordinator (MSDTC). Eskalacji ma miejsce, gdy zarejestrować innego menedżera zasobów trwałe. W przypadku eskalacji transakcja pozostaje zarządzana w stanie podwyższonym uprawnień do momentu jego zakończenia.  
  
 Między <xref:System.Transactions> transakcji i transakcji MSDTC nie pośredniczące typu transakcji, które są udostępniane za pośrednictwem awansowanie jednego etapu rejestracji (PSPE). PSPE jest inny mechanizm ważne w <xref:System.Transactions> dla optymalizacji wydajności. Umożliwia ona zdalny trwały zasób, znajdujący się w innej domenie aplikacji, procesie lub komputerze, aby uczestniczyć w <xref:System.Transactions> transakcji bez powodowania jego eskalacji do transakcji MSDTC. Aby uzyskać więcej informacji na temat PSPE, zobacz temat [Rejestrowanie zasobów jako uczestników transakcji](enlisting-resources-as-participants-in-a-transaction.md).  
  
## <a name="how-escalation-is-initiated"></a>Jak jest inicjowane eskalacji  
 Ponieważ MSDTC znajduje się w osobnym procesie i zamocowaniem transakcji MSDTC wyniki w wiadomości przesyłanych przez proces eskalacji transakcji powoduje zmniejszenie wydajności. Aby zwiększyć wydajność, należy opóźnić lub uniknąć eskalacji do usługi MSDTC; w tym celu należy wiedzieć, jak i kiedy zostanie zainicjowane eskalacja.  
  
 Tak długo, jak <xref:System.Transactions> infrastruktury obsługi lotnych zasobów i co najwyżej jeden trwały zasób, który obsługuje jednofazowy powiadomień, pozostanie transakcji w prawo własności <xref:System.Transactions> infrastruktury. Menedżer transakcji korzysta tylko z tych zasobów, które znajdują się na żywo w tej samej domenie aplikacji i dla których rejestrowanie (zapisywanie wyniku transakcji na dysku) nie jest wymagane. Eskalację, które spowodowało, że <xref:System.Transactions> infrastruktury transferowania własność transakcji na MSDTC się stanie po:  
  
- Co najmniej jeden trwały zasobem, który nie obsługuje jednofazowy powiadomień jest zarejestrowany w transakcji.  
  
- Co najmniej dwa trwałe zasobów, które obsługują jednofazowy powiadomienia biorących udział w transakcji. Na przykład rejestrowanie pojedynczego połączenia z SQL Server 2005 nie powoduje podwyższenia poziomu transakcji. Jednak po otwarciu drugiego połączenia z bazą danych SQL Server 2005 powodującej zarejestrowanie <xref:System.Transactions> bazy danych infrastruktura wykryje, że jest to drugi trwały zasób w transakcji i przekazuje go do transakcji MSDTC.  
  
- Zostanie wywołana prośba o przekierowanie transakcji do innej domeny aplikacji lub innego procesu. Na przykład serializacja obiektu Transaction między granicami domeny aplikacji. Obiekt transakcji jest zorganizowany przez wartość, co oznacza, że każda próba przekazania go przez granicę domeny aplikacji (nawet w tym samym procesie) powoduje serializację obiektu transakcji. Można przekazać obiektów transakcji przez wywołania zdalnej metody pobierającej <xref:System.Transactions.Transaction> jako parametr lub możesz wykonać następujące czynności dostępu zdalnego składników transakcyjnych obsługiwany. Spowoduje to serializacji obiektu transakcji i skutkuje eskalacją, tak jak w przypadku serializacji transakcji w domenie aplikacji. Jest dystrybuowany i lokalny Menedżer transakcji nie jest już odpowiednie.  
  
 Poniższa tabela zawiera listę wszystkich możliwych wyjątków, które mogą być generowane podczas eskalacji.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Podjęto próbę eskalować transakcji z poziomu izolacji jest taki sam, <xref:System.Transactions.IsolationLevel.Snapshot>.|  
|<xref:System.Transactions.TransactionAbortedException>|Menedżer transakcji nie działa.|  
|<xref:System.Transactions.TransactionException>|Eskalacja nie powiedzie się, a aplikacja zostanie przerwana.|
