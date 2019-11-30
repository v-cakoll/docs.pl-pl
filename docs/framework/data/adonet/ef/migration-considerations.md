---
title: Zagadnienia dotyczące migracji (Entity Framework)
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: 168aec6ef369f446cfac22ee5c4361fa06aaf16d
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569437"
---
# <a name="migration-considerations-entity-framework"></a>Zagadnienia dotyczące migracji (Entity Framework)
ADO.NET Entity Framework zapewnia kilka korzyści dla istniejącej aplikacji. Jedną z najważniejszych korzyści jest możliwość użycia modelu koncepcyjnego do oddzielenia struktur danych używanych przez aplikację ze schematu w źródle danych. Dzięki temu można łatwo wprowadzać przyszłe zmiany w modelu magazynu lub do samego źródła danych bez konieczności kompensowania zmian w aplikacji. Aby uzyskać więcej informacji na temat korzyści z używania Entity Framework, zobacz [Entity Framework Omówienie](overview.md) i [Entity Data Model](../entity-data-model.md).  
  
 Aby skorzystać z zalet Entity Framework, można migrować istniejącą aplikację do Entity Framework. Niektóre zadania są wspólne dla wszystkich zmigrowanych aplikacji. Te typowe zadania obejmują Uaktualnianie aplikacji w taki sposób, aby korzystały z .NET Framework począwszy od wersji 3,5 Service Pack 1 (SP1), definiowania modeli i mapowania oraz konfigurowania Entity Framework. W przypadku migrowania aplikacji do Entity Framework istnieją dodatkowe zagadnienia, które mają zastosowanie. Te zagadnienia zależą od typu migrowanej aplikacji i określonych funkcji aplikacji. Ten temat zawiera informacje ułatwiające wybór najlepszego podejścia do użycia podczas uaktualniania istniejącej aplikacji.  
  
## <a name="general-migration-considerations"></a>Ogólne zagadnienia dotyczące migracji  
 Podczas migrowania dowolnej aplikacji do Entity Framework należy wziąć pod uwagę następujące zagadnienia:  
  
- Wszystkie aplikacje, które używają .NET Framework począwszy od wersji 3,5 SP1, można migrować do Entity Framework, o ile dostawca danych dla źródła danych używany przez aplikację obsługuje Entity Framework.  
  
- Entity Framework może nie obsługiwać wszystkich funkcji dostawcy źródła danych, nawet jeśli ten dostawca obsługuje Entity Framework.  
  
- W przypadku dużej lub złożonej aplikacji nie jest wymagane Migrowanie całej aplikacji do Entity Framework jednocześnie. Jednak jakakolwiek część aplikacji, która nie używa Entity Framework, musi zostać zmieniona w przypadku zmiany źródła danych.  
  
- Połączenie dostawcy danych używane przez Entity Framework może być współużytkowane z innymi częściami aplikacji, ponieważ Entity Framework używa dostawców danych ADO.NET w celu uzyskania dostępu do źródła danych. Na przykład dostawca SqlClient jest używany przez Entity Framework w celu uzyskania dostępu do bazy danych SQL Server. Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Typowe zadania migracji  
 Ścieżka do migracji istniejącej aplikacji do Entity Framework zależy zarówno od typu aplikacji, jak i istniejącej strategii dostępu do danych. Jednak podczas migrowania istniejącej aplikacji do Entity Framework należy zawsze wykonać poniższe zadania.  
  
> [!NOTE]
> Wszystkie te zadania są wykonywane automatycznie przy użyciu narzędzi Entity Data Model, które są uruchamiane w programie Visual Studio 2008. Aby uzyskać więcej informacji, zobacz [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
1. Uaktualnij aplikację.  
  
     Projekt utworzony przy użyciu wcześniejszej wersji programu Visual Studio i .NET Framework musi zostać uaktualniony do korzystania z programu Visual Studio 2008 z dodatkiem SP1 i .NET Framework, począwszy od wersji 3,5 SP1.  
  
2. Zdefiniuj modele i mapowania.  
  
     Model i pliki mapowania definiują jednostki w modelu koncepcyjnym; struktury w źródle danych, takie jak tabele, procedury składowane i widoki; i mapowanie między jednostkami i strukturami źródła danych. Aby uzyskać więcej informacji, zobacz [jak: ręcznie zdefiniować model i pliki mapowania](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).  
  
     Typy, które są zdefiniowane w modelu magazynu, muszą być zgodne z nazwą obiektów w źródle danych. Jeśli istniejąca aplikacja uwidacznia dane jako obiekty, należy się upewnić, że jednostki i właściwości zdefiniowane w modelu koncepcyjnym pasują do nazw istniejących klas danych i właściwości. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie modelowania i plików mapowania do pracy z obiektami niestandardowymi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738625(v=vs.100)).  
  
    > [!NOTE]
    > Projektant Entity Data Model może służyć do zmiany nazw jednostek w modelu koncepcyjnym w celu dopasowania do istniejących obiektów. Aby uzyskać więcej informacji, zobacz [Entity Data Model Designer](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)).  
  
3. Zdefiniuj parametry połączenia.  
  
     Entity Framework używa specjalnie sformatowanego ciągu połączenia podczas wykonywania zapytań względem modelu koncepcyjnego. Te parametry połączenia hermetyzują informacje o modelu i plikach mapowania oraz o połączeniu ze źródłem danych. Aby uzyskać więcej informacji, zobacz [jak: Definiowanie parametrów połączenia](how-to-define-the-connection-string.md).  
  
4. Skonfiguruj projekt programu Visual Studio.  
  
     Odwołania do zestawów Entity Framework i modelu i plików mapowania należy dodać do projektu programu Visual Studio. Można dodać te pliki mapowania do projektu, aby upewnić się, że są one wdrażane z aplikacją w lokalizacji określonej w parametrach połączenia. Aby uzyskać więcej informacji, zobacz [jak: ręcznie skonfigurować projekt Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Zagadnienia dotyczące aplikacji z istniejącymi obiektami  
 Począwszy od .NET Framework 4, Entity Framework obsługuje "zwykłe stare" obiekty CLR (POCO), nazywane również obiektami trwałości-ignorujących. W większości przypadków istniejące obiekty mogą współdziałać z Entity Framework przez wprowadzanie drobnych zmian. Aby uzyskać więcej informacji, zobacz [Praca z jednostkami poco](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100)). Można również migrować aplikację do Entity Framework i używać klas danych, które są generowane przez narzędzia Entity Framework. Aby uzyskać więcej informacji, zobacz [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>Zagadnienia dotyczące aplikacji korzystających z dostawców ADO.NET  
 Dostawcy ADO.NET, na przykład klient SqlClient, mogą wysyłać zapytania do źródła danych, aby zwracały dane tabelaryczne. Dane można również ładować do zestawu danych ADO.NET. Na poniższej liście opisano zagadnienia dotyczące uaktualniania aplikacji, która korzysta z istniejącego dostawcy ADO.NET:  
  
- Wyświetlanie danych tabelarycznych za pomocą czytnika danych.  

  Można rozważyć wykonanie zapytania [!INCLUDE[esql](../../../../../includes/esql-md.md)] przy użyciu dostawcy EntityClient i Wyliczenie przez zwrócony obiekt <xref:System.Data.EntityClient.EntityDataReader>. Zrób to tylko wtedy, gdy aplikacja wyświetla dane tabelaryczne przy użyciu czytnika danych i nie wymaga możliwości zapewnianych przez Entity Framework do obiektów, śledzenia zmian i wprowadzania aktualizacji. Można nadal używać istniejącego kodu dostępu do danych, który wprowadza aktualizacje do źródła danych, ale można użyć istniejącego połączenia z właściwością <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> <xref:System.Data.EntityClient.EntityConnection>. Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](entityclient-provider-for-the-entity-framework.md).  
  
- Praca z zestawami danych.  

  Entity Framework zapewnia wiele funkcji zapewnianych przez zestaw danych, w tym trwałość w pamięci, śledzenie zmian, powiązanie danych i Serializowanie obiektów jako dane XML. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](working-with-objects.md).  
  
  Jeśli Entity Framework nie zapewnia funkcjonalności zestawu danych wymaganego przez aplikację, można nadal korzystać z zalet zapytań LINQ przy użyciu LINQ to DataSet. Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Zagadnienia dotyczące aplikacji, które wiążą dane z kontrolkami  
 .NET Framework pozwala hermetyzować dane w źródle danych, takim jak zestaw danych lub kontrolka źródła danych ASP.NET, a następnie powiązać elementy interfejsu użytkownika z tymi kontrolkami danych. Na poniższej liście opisano zagadnienia dotyczące kontroli powiązań w celu Entity Framework danych.  
  
- Powiązywanie danych z kontrolkami.  

  Podczas wykonywania zapytania względem modelu koncepcyjnego Entity Framework zwraca dane jako obiekty, które są wystąpieniami typów jednostek. Te obiekty mogą być powiązane bezpośrednio z kontrolkami, a to powiązanie obsługuje aktualizacje. Oznacza to, że zmiany danych w kontrolce, takie jak wiersz w <xref:System.Windows.Forms.DataGridView>, są automatycznie zapisywane w bazie danych po wywołaniu metody <xref:System.Data.Objects.ObjectContext.SaveChanges%2A>.  
  
  Jeśli aplikacja wylicza wyniki zapytania w celu wyświetlenia danych w <xref:System.Windows.Forms.DataGridView> lub innego typu formantu, który obsługuje powiązanie danych, można zmodyfikować aplikację, aby powiązać kontrolę z wynikiem <xref:System.Data.Objects.ObjectQuery%601>.  
  
  Aby uzyskać więcej informacji, zobacz [Powiązywanie obiektów z kontrolkami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738469(v=vs.100)).  
  
- ASP.NET kontrolki źródła danych.  

  Entity Framework obejmuje kontrolkę źródła danych zaprojektowaną do uproszczenia wiązania danych w aplikacjach sieci Web ASP.NET. Aby uzyskać więcej informacji, zobacz temat [formant serwera sieci Web EntityDataSource — Omówienie](https://docs.microsoft.com/previous-versions/aspnet/cc488502(v=vs.100)).  
  
## <a name="other-considerations"></a>Inne zagadnienia  
 Poniżej przedstawiono zagadnienia, które mogą być stosowane podczas migrowania określonych typów aplikacji do Entity Framework.  
  
- Aplikacje, które uwidaczniają usługi danych.  

  Usługi sieci Web i aplikacje, które są oparte na Windows Communication Foundation (WCF) uwidaczniają dane z bazowego źródła danych przy użyciu formatu wiadomości żądania/odpowiedzi XML. Entity Framework obsługuje serializację obiektów jednostki przy użyciu danych binarnych, XML lub serializacji kontraktu. Serializacja binarna i WCF obsługują pełną serializację grafów obiektów. Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji N-warstwowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896304(v=vs.100)).  
  
- Aplikacje korzystające z danych XML.  

  Serializacja obiektu umożliwia tworzenie usług danych Entity Framework. Te usługi zapewniają dane aplikacjom korzystającym z danych XML, takich jak aplikacje internetowe oparte na technologii AJAX. W takich przypadkach należy rozważyć użycie Usługi danych programu WCF. Te usługi danych są oparte na Entity Data Model i zapewniają dynamiczny dostęp do danych jednostki przy użyciu standardowych akcji protokołu HTTP do przenoszenia stanu (REST), takich jak GET, PUT i POST. Aby uzyskać więcej informacji, zobacz [Usługi danych programu WCF 4,5](../../wcf/index.md).  
  
  Entity Framework nie obsługuje natywnego typu danych XML. Oznacza to, że gdy jednostka jest zamapowana na tabelę z kolumną XML, właściwość jednostki równoważnej kolumny XML jest ciągiem. Obiekty mogą być rozłączone i serializowane jako XML. Aby uzyskać więcej informacji, zobacz [Serializowanie obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
  Jeśli aplikacja wymaga możliwości wykonywania zapytań dotyczących danych XML, można nadal korzystać z zalet zapytań LINQ przy użyciu LINQ to XML. Aby uzyskać więcej informacji, zobacz [LINQ to XMLC#()](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) lub [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
- Aplikacje, które utrzymują stan.  

  ASP.NET aplikacje sieci Web muszą często zachować stan strony sieci Web lub sesji użytkownika. Obiekty w wystąpieniu <xref:System.Data.Objects.ObjectContext> mogą być przechowywane w stanie widoku klienta lub w stanie sesji na serwerze, a następnie pobierane i ponownie dołączane do nowego kontekstu obiektu. Aby uzyskać więcej informacji, zobacz [dołączanie i odłączanie obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896271(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące wdrażania](deployment-considerations.md)
- [Terminologia programu Entity Framework](terminology.md)
