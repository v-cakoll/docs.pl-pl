---
title: N-warstwowa LINQ to SQL z użyciem usług internetowych
ms.date: 03/30/2017
ms.assetid: 9cb10eb8-957f-4beb-a271-5f682016fed2
ms.openlocfilehash: 279907aeaaa83d6901621c03231068d61045ec5c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781330"
---
# <a name="linq-to-sql-n-tier-with-web-services"></a>N-warstwowa LINQ to SQL z użyciem usług internetowych
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Program został zaprojektowany szczególnie do użycia w warstwie środkowej w luźno sprzężonej warstwie dostępu do danych (DAL), takiej jak usługa sieci Web. Jeśli warstwa prezentacji jest stroną sieci Web ASP.NET, użyj <xref:System.Web.UI.WebControls.LinqDataSource> kontrolki serwer sieci Web do zarządzania transferem danych między interfejsem użytkownika a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] warstwą środkową. Jeśli warstwa prezentacji nie jest stroną ASP.NET, wówczas zarówno warstwa warstwy środkowej, jak i warstwy prezentacji muszą wykonać kilka dodatkowych czynności w celu zarządzania serializacji i deserializacji danych.  
  
## <a name="setting-up-linq-to-sql-on-the-middle-tier"></a>Konfigurowanie LINQ to SQL w warstwie środkowej  
 W przypadku usługi sieci Web lub aplikacji n-warstwowej warstwa środkowa zawiera kontekst danych i klasy jednostek. Te klasy można utworzyć ręcznie lub za pomocą SQLMetal. exe lub Object Relational Designer, jak opisano w innych miejscach w dokumentacji. W czasie projektowania masz możliwość serializacji klas jednostek. Aby uzyskać więcej informacji, zobacz [jak: Utwórz obiekty do](how-to-make-entities-serializable.md)serializacji. Innym rozwiązaniem jest utworzenie oddzielnego zestawu klas, które hermetyzują dane, które mają być serializowane, a następnie projektu do tych możliwych do serializacji typów podczas zwracania danych [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] w zapytaniach.  
  
 Następnie należy zdefiniować interfejs przy użyciu metod, które klienci będą wywoływać, aby pobierać, wstawiać i aktualizować dane. Metody interfejsu zawijają [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytania. Można użyć dowolnego rodzaju mechanizmu serializacji do obsługi wywołań metod zdalnych i serializacji danych. Jedynym wymaganiem jest to, że jeśli masz cykliczne lub dwukierunkowe relacje w modelu obiektów, takie jak między klientami i zamówieniami w standardowym modelu obiektów Northwind, należy użyć serializatora, który go obsługuje. Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.DataContractSerializer> obsługuje relacje dwukierunkowe, ale XmlSerializer, który jest używany z usługami sieci Web spoza programu WCF. W przypadku wybrania opcji używania elementu XmlSerializer należy upewnić się, że model obiektów nie ma relacji cyklicznych.  
  
 Aby uzyskać więcej informacji na temat Windows Communication Foundation, zobacz [Windows Communication Foundation Services i usługi danych programu WCF w programie Visual Studio](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio).  
  
 Zaimplementuj reguły biznesowe lub inną logikę specyficzną dla domeny, używając częściowych klas i metod <xref:System.Data.Linq.DataContext> dla i klas jednostek do podłączania do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zdarzeń środowiska uruchomieniowego. Aby uzyskać więcej informacji, zobacz [implementacja wielowarstwowej logiki biznesowej](implementing-business-logic-linq-to-sql.md).  
  
## <a name="defining-the-serializable-types"></a>Definiowanie typów możliwych do serializacji  
 Klient lub warstwa prezentacji muszą mieć definicje typów dla klas, które będą otrzymywać z warstwy środkowej. Te typy mogą być klasami jednostek lub klasami specjalnymi, które zawijają tylko niektóre pola z klas jednostek na potrzeby komunikacji zdalnej. W każdym przypadku jest [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] całkowicie Niezainteresowani, w jaki sposób warstwa prezentacji uzyskuje te definicje typów. Na przykład warstwa prezentacji może użyć funkcji WCF do automatycznego wygenerowania typów lub może mieć kopię biblioteki DLL, w której te typy są zdefiniowane lub po prostu mogą definiować własne wersje typów.  
  
## <a name="retrieving-and-inserting-data"></a>Pobieranie i wstawianie danych  
 Warstwa środkowa definiuje interfejs, który określa sposób, w jaki warstwa prezentacji uzyskuje dostęp do danych. Na przykład `GetProductByID(int productID)`lub `GetCustomers()`. W warstwie środkowej treść metody zwykle tworzy nowe wystąpienie <xref:System.Data.Linq.DataContext>, wykonuje zapytanie względem jednej lub kilku jej tabeli. Warstwa środkowa zwraca wynik jako <xref:System.Collections.Generic.IEnumerable%601>, gdzie `T` jest klasą jednostki lub innym typem, który jest używany do serializacji. Warstwa prezentacji nigdy nie wysyła ani nie odbiera zmiennych zapytania bezpośrednio do lub z warstwy środkowej. Dwie warstwy wymieniają wartości, obiekty i kolekcje konkretnych danych. Po odebraniu kolekcji warstwa prezentacji może używać [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] obiektów do wykonywania zapytań w razie potrzeby.  
  
 Podczas wstawiania danych warstwa prezentacji może utworzyć nowy obiekt i przesłać go do warstwy środkowej lub można utworzyć obiekt warstwy środkowej na podstawie wartości, które zapewnia. Ogólnie rzecz biorąc, pobieranie i wstawianie danych w aplikacjach n-warstwowych nie różni się od procesu w aplikacjach dwuwarstwowych. Aby uzyskać więcej informacji, zobacz [wykonywanie zapytań dotyczących bazy danych](querying-the-database.md) i [wprowadzanie i przesyłanie zmian danych](making-and-submitting-data-changes.md).  
  
## <a name="tracking-changes-for-updates-and-deletes"></a>Śledzenie zmian dotyczących aktualizacji i usunięć  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obsługuje optymistyczne współbieżność na podstawie sygnatur czasowych (o nazwie RowVersions) i oryginalnych wartości. Jeśli tabele bazy danych mają sygnatury czasowe, aktualizacje i usunięcia wymagają nieco dodatkowej pracy w warstwie środkowej lub warstwowej prezentacji. Jeśli jednak musisz użyć oryginalnych wartości dla optymistycznych kontroli współbieżności, warstwa prezentacji jest odpowiedzialna za śledzenie tych wartości i wysyłanie ich z powrotem podczas aktualizacji. Wynika to z faktu, że zmiany wprowadzone w jednostkach w warstwie prezentacji nie są śledzone w warstwie środkowej. W rzeczywistości oryginalne pobieranie jednostki i ostateczne aktualizacje są zwykle wykonywane przez dwa całkowicie oddzielone wystąpienia <xref:System.Data.Linq.DataContext>.  
  
 Im większa liczba zmian dokonanych przez warstwę prezentacji, tym bardziej skomplikowana staje się śledzenie tych zmian i pakowanie ich z powrotem do warstwy środkowej. Implementacja mechanizmu przekazywania zmian jest całkowicie do aplikacji. Jedynym wymaganiem jest, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] że należy podać te oryginalne wartości, które są wymagane do optymistycznych kontroli współbieżności.  
  
 Aby uzyskać więcej informacji, zobacz [operacje pobierania i cud danych w aplikacjach N-warstwowych (LINQ to SQL)](data-retrieval-and-cud-operations-in-n-tier-applications.md).  
  
## <a name="see-also"></a>Zobacz także

- [N-warstwowe i zdalne aplikacje z użyciem LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md)
- [Formant LinqDataSource serwera sieci Web — Omówienie](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))
