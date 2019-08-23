---
title: Zagadnienia dotyczące migracji (Entity Framework)
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: 8370156d2bd0f3858d7fa0936fa967a658e6e910
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929308"
---
# <a name="migration-considerations-entity-framework"></a>Zagadnienia dotyczące migracji (Entity Framework)
ADO.NET Entity Framework zapewnia kilka korzyści dla istniejącej aplikacji. Jedną z najważniejszych korzyści jest możliwość użycia modelu koncepcyjnego do oddzielenia struktur danych używanych przez aplikację ze schematu w źródle danych. Dzięki temu można łatwo wprowadzać przyszłe zmiany w modelu magazynu lub do samego źródła danych bez konieczności kompensowania zmian w aplikacji. Aby uzyskać więcej informacji na temat korzyści z używania [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]usługi, zobacz [Entity Framework Omówienie](../../../../../docs/framework/data/adonet/ef/overview.md) i [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 Aby skorzystać z zalet programu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ,możnaprzeprowadzićmigracjęistniejącejaplikacjidoprogramu.[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Niektóre zadania są wspólne dla wszystkich zmigrowanych aplikacji. Te typowe zadania obejmują Uaktualnianie aplikacji w taki sposób, aby korzystały z .NET Framework począwszy od wersji 3,5 Service Pack 1 (SP1), definiowania modeli i mapowania oraz konfigurowania Entity Framework. W przypadku migrowania aplikacji do programu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]istnieją dodatkowe zagadnienia, które mają zastosowanie. Te zagadnienia zależą od typu migrowanej aplikacji i określonych funkcji aplikacji. Ten temat zawiera informacje ułatwiające wybór najlepszego podejścia do użycia podczas uaktualniania istniejącej aplikacji.  
  
## <a name="general-migration-considerations"></a>Ogólne zagadnienia dotyczące migracji  
 Podczas migrowania dowolnej aplikacji do programu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]można zastosować następujące zagadnienia:  
  
- Wszystkie aplikacje, które używają .NET Framework począwszy od wersji 3,5 SP1, można migrować do Entity Framework, o ile dostawca danych dla źródła danych używany przez aplikację obsługuje Entity Framework.  
  
- Entity Framework może nie obsługiwać wszystkich funkcji dostawcy źródła danych, nawet jeśli ten dostawca obsługuje Entity Framework.  
  
- W przypadku dużej lub złożonej aplikacji nie jest wymagane Migrowanie całej aplikacji do Entity Framework jednocześnie. Jednak jakakolwiek część aplikacji, która nie używa Entity Framework, musi zostać zmieniona w przypadku zmiany źródła danych.  
  
- Połączenie dostawcy danych używane przez Entity Framework może być współużytkowane z innymi częściami aplikacji, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ponieważ używa dostawców danych ADO.NET do uzyskiwania dostępu do źródła danych. Na przykład dostawca SqlClient jest używany przez Entity Framework w celu uzyskania dostępu do bazy danych SQL Server. Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Typowe zadania migracji  
 Ścieżka do migracji istniejącej aplikacji do programu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zależy zarówno od typu aplikacji, jak i istniejącej strategii dostępu do danych. Jednak podczas migrowania istniejącej aplikacji do programu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]należy zawsze wykonać poniższe zadania.  
  
> [!NOTE]
> Wszystkie te zadania są wykonywane automatycznie przy użyciu narzędzi Entity Data Model, które są uruchamiane w programie Visual Studio 2008. Aby uzyskać więcej informacji, zobacz [jak: Użyj kreatora](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.  
  
1. Uaktualnij aplikację.  
  
     Projekt utworzony przy użyciu wcześniejszej wersji programu Visual Studio i .NET Framework musi zostać uaktualniony do korzystania z programu Visual Studio 2008 z dodatkiem SP1 i .NET Framework, począwszy od wersji 3,5 SP1.  
  
2. Zdefiniuj modele i mapowania.  
  
     Model i pliki mapowania definiują jednostki w modelu koncepcyjnym; struktury w źródle danych, takie jak tabele, procedury składowane i widoki; i mapowanie między jednostkami i strukturami źródła danych. Aby uzyskać więcej informacji, zobacz [jak: Ręcznie zdefiniuj model i pliki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100))mapowania.  
  
     Typy, które są zdefiniowane w modelu magazynu, muszą być zgodne z nazwą obiektów w źródle danych. Jeśli istniejąca aplikacja uwidacznia dane jako obiekty, należy się upewnić, że jednostki i właściwości zdefiniowane w modelu koncepcyjnym pasują do nazw istniejących klas danych i właściwości. Aby uzyskać więcej informacji, zobacz [jak: Dostosuj modelowanie i mapowanie plików do pracy z obiektami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738625(v=vs.100))niestandardowymi.  
  
    > [!NOTE]
    > Projektant Entity Data Model może służyć do zmiany nazw jednostek w modelu koncepcyjnym w celu dopasowania do istniejących obiektów. Aby uzyskać więcej informacji, zobacz [Entity Data Model Designer](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)).  
  
3. Zdefiniuj parametry połączenia.  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Używa specjalnie sformatowanego ciągu połączenia podczas wykonywania zapytań względem modelu koncepcyjnego. Te parametry połączenia hermetyzują informacje o modelu i plikach mapowania oraz o połączeniu ze źródłem danych. Aby uzyskać więcej informacji, zobacz [jak: Zdefiniuj parametry](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md)połączenia.  
  
4. Skonfiguruj projekt programu Visual Studio.  
  
     Odwołania do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zestawów i modelu i plików mapowania należy dodać do projektu programu Visual Studio. Można dodać te pliki mapowania do projektu, aby upewnić się, że są one wdrażane z aplikacją w lokalizacji określonej w parametrach połączenia. Aby uzyskać więcej informacji, zobacz [jak: Ręcznie skonfiguruj projekt](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))Entity Framework.  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Zagadnienia dotyczące aplikacji z istniejącymi obiektami  
 Począwszy od .NET Framework 4, obsługiwane są [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] "zwykłe stare" obiekty CLR (POCO), nazywane również obiektami trwałości-ignorujących. W większości przypadków istniejące obiekty mogą współdziałać z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] przez wprowadzanie drobnych zmian. Aby uzyskać więcej informacji, zobacz [Praca z jednostkami poco](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100)). Można również migrować aplikację do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i używać klas danych, które są generowane przez narzędzia Entity Framework. Aby uzyskać więcej informacji, zobacz [jak: Użyj kreatora](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>Zagadnienia dotyczące aplikacji korzystających z dostawców ADO.NET  
 Dostawcy ADO.NET, na przykład klient SqlClient, mogą wysyłać zapytania do źródła danych, aby zwracały dane tabelaryczne. Dane można również ładować do zestawu danych ADO.NET. Na poniższej liście opisano zagadnienia dotyczące uaktualniania aplikacji, która korzysta z istniejącego dostawcy ADO.NET:  
  
- Wyświetlanie danych tabelarycznych za pomocą czytnika danych.  

  Można rozważyć wykonanie [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytania przy użyciu dostawcy EntityClient i Wyliczenie za pośrednictwem zwracanego <xref:System.Data.EntityClient.EntityDataReader> obiektu. Zrób to tylko wtedy, gdy aplikacja wyświetla dane tabelaryczne przy użyciu czytnika danych i nie wymaga obiektów dostarczonych przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] program do materializacji danych do obiektów, śledzenia zmian i wprowadzania aktualizacji. Można nadal używać istniejącego kodu dostępu do danych, który wprowadza aktualizacje do źródła danych, ale można użyć istniejącego połączenia z <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> <xref:System.Data.EntityClient.EntityConnection>właściwością. Aby uzyskać więcej informacji, zobacz [EntityClient Provider for the Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
- Praca z zestawami danych.  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zapewnia wiele z tych samych funkcji zapewnianych przez zestaw danych, w tym trwałość w pamięci, śledzenie zmian, powiązanie danych i Serializowanie obiektów jako dane XML. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Jeśli program nie udostępnia funkcji zestawu danych wymaganego przez aplikację, można nadal korzystać z zalet zapytań LINQ przy użyciu LINQ to DataSet. Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Zagadnienia dotyczące aplikacji, które wiążą dane z kontrolkami  
 .NET Framework pozwala hermetyzować dane w źródle danych, takim jak zestaw danych lub kontrolka źródła danych ASP.NET, a następnie powiązać elementy interfejsu użytkownika z tymi kontrolkami danych. Na poniższej liście opisano zagadnienia dotyczące kontroli powiązań w celu Entity Framework danych.  
  
- Powiązywanie danych z kontrolkami.  

  Podczas wykonywania zapytania względem modelu [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] koncepcyjnego zwraca dane jako obiekty, które są wystąpieniami typów jednostek. Te obiekty mogą być powiązane bezpośrednio z kontrolkami, a to powiązanie obsługuje aktualizacje. Oznacza to, że zmiany danych w formancie, takie jak wiersz w <xref:System.Windows.Forms.DataGridView>, są automatycznie zapisywane w bazie danych, <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> gdy metoda jest wywoływana.  
  
  Jeśli aplikacja wylicza wyniki zapytania, aby wyświetlić dane w <xref:System.Windows.Forms.DataGridView> lub innego typu kontrolki obsługującej powiązanie danych, można zmodyfikować aplikację, aby powiązać ją z wynikiem. <xref:System.Data.Objects.ObjectQuery%601>  
  
  Aby uzyskać więcej informacji, zobacz [Powiązywanie obiektów z kontrolkami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738469(v=vs.100)).  
  
- ASP.NET kontrolki źródła danych.  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zawiera kontrolkę źródła danych zaprojektowaną do uproszczenia wiązania danych w aplikacjach sieci Web ASP.NET. Aby uzyskać więcej informacji, zobacz temat [formant serwera sieci Web EntityDataSource — Omówienie](https://docs.microsoft.com/previous-versions/aspnet/cc488502(v=vs.100)).  
  
## <a name="other-considerations"></a>Inne zagadnienia  
 Poniżej przedstawiono zagadnienia, które mogą być stosowane podczas migrowania określonych typów aplikacji do Entity Framework.  
  
- Aplikacje, które uwidaczniają usługi danych.  

  Usługi sieci Web i aplikacje, które są oparte na Windows Communication Foundation (WCF) uwidaczniają dane z bazowego źródła danych przy użyciu formatu wiadomości żądania/odpowiedzi XML. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obsługuje serializację obiektów jednostki przy użyciu danych binarnych, XML lub serializacji kontraktu. Serializacja binarna i WCF obsługują pełną serializację grafów obiektów. Aby uzyskać więcej informacji, zobacz [Tworzenie aplikacji N-warstwowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896304(v=vs.100)).  
  
- Aplikacje korzystające z danych XML.  

  Serializacja obiektu umożliwia tworzenie [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] usług danych. Te usługi zapewniają dane aplikacjom korzystającym z danych XML, takich jak aplikacje internetowe oparte na technologii AJAX. W takich przypadkach należy rozważyć użycie [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)]. Te usługi danych są oparte na Entity Data Model i zapewniają dynamiczny dostęp do danych jednostki przy użyciu standardowych akcji protokołu HTTP do przenoszenia stanu (REST), takich jak GET, PUT i POST. Aby uzyskać więcej informacji, zobacz [4.5 usług danych WCF](../../../../../docs/framework/data/wcf/index.md).  
  
  Obiekt [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] nie obsługuje natywnego typu danych XML. Oznacza to, że gdy jednostka jest zamapowana na tabelę z kolumną XML, właściwość jednostki równoważnej kolumny XML jest ciągiem. Obiekty mogą być rozłączone i serializowane jako XML. Aby uzyskać więcej informacji, zobacz [Serializowanie obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
  Jeśli aplikacja wymaga możliwości wykonywania zapytań dotyczących danych XML, można nadal korzystać z zalet zapytań LINQ przy użyciu LINQ to XML. Aby uzyskać więcej informacji, zobacz [LINQ to XMLC#()](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) lub [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
- Aplikacje, które utrzymują stan.  

  ASP.NET aplikacje sieci Web muszą często zachować stan strony sieci Web lub sesji użytkownika. Obiekty w <xref:System.Data.Objects.ObjectContext> wystąpieniu mogą być przechowywane w stanie widoku klienta lub w stanie sesji na serwerze, a później pobrane i ponownie dołączone do nowego kontekstu obiektu. Aby uzyskać więcej informacji, zobacz Dołączanie [i odłączanie obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896271(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także

- [Zagadnienia dotyczące wdrażania](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)
- [Terminologia programu Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md)
