---
title: Zagadnienia dotyczące migracji (Entity Framework)
ms.date: 03/30/2017
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
ms.openlocfilehash: d783bc79585740710e663d26ecd4110f64882b44
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903908"
---
# <a name="migration-considerations-entity-framework"></a>Zagadnienia dotyczące migracji (Entity Framework)
[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Entity Framework zapewnia kilka korzyści z istniejącą aplikacją. Jednym z najbardziej istotna te korzyści jest możliwość stosowania modelu koncepcyjnego do oddzielnych struktur danych używanych przez aplikację ze schematu w źródle danych. Dzięki temu można łatwo wprowadzić przyszłe zmiany w modelu magazynu lub do źródła danych bez wprowadzania zmian wyrównującej do aplikacji. Aby uzyskać więcej informacji o zaletach korzystania z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], zobacz [Omówienie programu Entity Framework](../../../../../docs/framework/data/adonet/ef/overview.md) i [modelu Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 Aby móc korzystać z zalet [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], można migrować istniejącą aplikację [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Niektóre zadania są wspólne dla wszystkich migrowanych aplikacji. Typowe zadania obejmują uaktualniania aplikacji do korzystania z [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] począwszy od wersji 3.5 z dodatkiem Service Pack 1 (SP1) i definiowanie modeli i mapowania certyfikatu oraz konfigurowanie platformy Entity Framework. Podczas migracji aplikacji [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], istnieją dodatkowe zagadnienia, które są stosowane. Te zagadnienia są zależne od typu migrowanych aplikacji oraz o określonych funkcjach aplikacji. Ten temat zawiera informacje ułatwiające wybór najlepszym podejściem do użycia podczas uaktualniania istniejącej aplikacji.  
  
## <a name="general-migration-considerations"></a>Zagadnienia dotyczące migracji ogólne  
 Podczas migracji dowolnej aplikacji mają zastosowanie następujące kwestie [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]:  
  
-   Każda aplikacja, który używa [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] począwszy od wersji 3.5 z dodatkiem SP1 można migrować do programu Entity Framework, tak długo, jak dostawca danych dla źródła danych, który jest używany przez aplikację obsługuje platformy Entity Framework.  
  
-   Entity Framework mogą nie obsługiwać wszystkich funkcji dostawcy źródła danych, nawet wtedy, gdy ten dostawca obsługuje platformy Entity Framework.  
  
-   Dla dużych i złożonych aplikacji nie należy przeprowadzić migrację całej aplikacji w programie Entity Framework w tym samym czasie. Jednak dowolnej części aplikacji, która nie korzysta z programu Entity Framework nadal musi zostać zmieniony, gdy zmiany źródła danych.  
  
-   Połączenie dostawcy danych, które są używane przez program Entity Framework mogą być współużytkowane z innymi częściami aplikacji, ponieważ [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] używa [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] dostawcy danych można uzyskać dostępu do źródła danych. Na przykład dostawcy SqlClient jest używany przez program Entity Framework dostępu do bazy danych programu SQL Server. Aby uzyskać więcej informacji, zobacz [dostawca EntityClient dla programu Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Typowe zadania migracji  
 Ścieżka do migrowania istniejących aplikacji [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zależy od zarówno typ aplikacji i istniejąca strategia dostępu do danych. Jednak należy zawsze wykonać następujące zadania podczas migracji istniejącej aplikacji do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
> [!NOTE]
>  Wszystkie te zadania są wykonywane automatycznie, gdy jest możliwe użycie narzędzi modelu Entity Data Model, począwszy od programu Visual Studio 2008. Aby uzyskać więcej informacji, zobacz [jak: Użyj Kreatora modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
1.  Uaktualnienie aplikacji.  
  
     Projekt, który został utworzony przy użyciu wcześniejszej wersji programu Visual Studio i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] musi zostać uaktualniony, aby użyć programu Visual Studio 2008 z dodatkiem SP1 i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] począwszy od wersji 3.5 z dodatkiem SP1.  
  
2.  Zdefiniuj modeli i mapowania.  
  
     Modelu i mapowania plików definiowania jednostek w modelu koncepcyjnego; struktury w źródle danych, takich jak tabele, procedur przechowywanych i widoków; i mapowanie między struktury źródła danych i jednostek. Aby uzyskać więcej informacji, zobacz [jak: Ręcznie zdefiniować modelu i mapowania plików](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399785(v=vs.100)).  
  
     Typy, które są zdefiniowane w modelu magazynu musi odpowiadać nazwie obiektów w źródle danych. Jeśli istniejącej aplikacji udostępnia danych jako obiektami, upewnij się, że jednostki i właściwości, które są zdefiniowane w modelu koncepcyjnym odpowiadać nazwom tych istniejących klas danych i właściwości. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie modelowanie i mapowanie plików do pracy z niestandardowych obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738625(v=vs.100)).  
  
    > [!NOTE]
    >  Projektant modelu danych jednostki może służyć do zmiany nazwy jednostki w modelu koncepcyjnym, aby dopasować istniejących obiektów. Aby uzyskać więcej informacji, zobacz [projektancie Entity Data Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716685(v=vs.100)).  
  
3.  Zdefiniowanie ciągu połączenia.  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Używa parametrów połączenia specjalnie sformatowanego, podczas wykonywania zapytań względem modelu koncepcyjnego. Te parametry połączenia hermetyzuje informacje o modelu i mapowania plików oraz połączenia ze źródłem danych. Aby uzyskać więcej informacji, zobacz [jak: Zdefiniowanie ciągu połączenia](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md).  
  
4.  Konfigurowanie projektu Visual Studio.  
  
     Odwołuje się do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zestawów i modelu i mapowania plików musi zostać dodany do projektu programu Visual Studio. Możesz dodać te pliki mapowania do projektu, aby upewnić się, że są one wdrażane za pomocą aplikacji w lokalizacji, która jest wskazywany w parametrach połączenia. Aby uzyskać więcej informacji, zobacz [jak: Ręczne konfigurowanie projektu programu Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100)).  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Uwagi dotyczące aplikacji przy użyciu istniejących obiektów  
 Począwszy od [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] obsługuje "plain old" obiektów CLR (POCO), nazywany również zakresu trwałość obiektów. W większości przypadków można pracować z istniejących obiektów [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] , wprowadzając drobne zmiany. Aby uzyskać więcej informacji, zobacz [Praca z jednostkami obiektów POCO](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456853(v=vs.100)). Można również przeprowadzić migrację aplikacji [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i użyć klas danych, które są generowane przez narzędzia Entity Framework. Aby uzyskać więcej informacji, zobacz [jak: Użyj Kreatora modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>Uwagi dotyczące aplikacji korzystających z dostawców ADO.NET  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] dostawców, takich jak Klient SQL, umożliwiają zapytanie zwracające dane tabelaryczne źródła danych. Dane można również załadować do [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] zestawu danych. Na poniższej liście opisano zagadnienia dotyczące uaktualniania aplikacji korzystającej z istniejącej [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] dostawcy:  
  
- Wyświetlanie danych tabelarycznych przy użyciu czytnika danych.  

  Można rozważyć wykonania [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytania przy użyciu dostawca EntityClient i wyliczania zwracanego <xref:System.Data.EntityClient.EntityDataReader> obiektu. Tylko, jeśli aplikacja zawiera dane tabelaryczne przy użyciu czytnika danych i nie wymaga urządzenia dostarczane przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dla materializowanie danych w obiektach, śledzenie zmian i wprowadzania aktualizacji. Można kontynuować używanie istniejącego kodu dostępu do danych, dzięki której aktualizacji do źródła danych, ale można użyć istniejącego połączenia, które są dostępne z <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> właściwość <xref:System.Data.EntityClient.EntityConnection>. Aby uzyskać więcej informacji, zobacz [dostawca EntityClient dla programu Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
- Praca z zestawami danych.  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Udostępnia wiele z tych samych funkcje udostępniane przez zestaw danych, łącznie z trwałości w pamięci do śledzenia zmian, powiązań danych i serializacji obiektów w postaci danych XML. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
  Jeśli [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] nie udostępnia funkcji zestawu wymagane przez aplikację przy użyciu nadal może korzystać z zalet zapytań LINQ [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]. Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Uwagi dotyczące aplikacji, które wiązanie danych z kontrolkami  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Umożliwia hermetyzację danych w źródle danych, takich jak zestaw danych lub moduł [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] danych kontroli źródła, a następnie powiązać elementy interfejsu użytkownika formantów tych danych. Na poniższej liście opisano zagadnienia dotyczące powiązywanie kontrolek z danymi programu Entity Framework.  
  
- Powiązywanie danych z kontrolkami.  

  Kiedy wykonujesz zapytanie o modelu koncepcyjnego [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zwraca dane jako obiekty, które są wystąpieniami typów jednostek. Te obiekty można powiązać bezpośrednio do kontrolek, a to powiązanie obsługuje aktualizacje. Oznacza to, że zmiany danych w kontrolce wiersza w <xref:System.Windows.Forms.DataGridView>, automatycznie są zapisywane w bazie danych podczas <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metoda jest wywoływana.  
  
  Wylicza wyników kwerendy, aby wyświetlić dane w aplikacji <xref:System.Windows.Forms.DataGridView> lub inny typ kontrolki obsługującej powiązanie danych, można zmodyfikować aplikację, aby powiązać formant z wynikiem <xref:System.Data.Objects.ObjectQuery%601>.  
  
  Aby uzyskać więcej informacji, zobacz [powiązanie obiektów z kontrolkami](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738469(v=vs.100)).  
  
- [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] kontrolki źródła danych.  

  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obejmuje zaprojektowane w celu uproszczenia powiązanie danych w kontroli źródła danych [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] aplikacji sieci Web. Aby uzyskać więcej informacji, zobacz [omówienie kontrolki serwera sieci Web EntityDataSource](https://docs.microsoft.com/previous-versions/aspnet/cc488502(v=vs.100)).  
  
## <a name="other-considerations"></a>Inne zagadnienia  
 Poniżej przedstawiono zagadnienia, które mogą mieć zastosowanie w przypadku migracji określonych typów aplikacji w programie Entity Framework.  
  
- Aplikacje, które udostępniają usługi danych.  

  Usługi sieci Web i aplikacje, które są oparte na Windows Communication Foundation (WCF) uwidocznić dane z bazowego źródła danych, używając formatu komunikatów żądań/odpowiedzi XML. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obsługuje serializacji obiektów jednostki przy użyciu plików binarnych, XML, lub umowy serializacji w danych programu WCF. Plik binarny i serializacji WCF obsługują pełne serializację wykresów obiektów. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji N-warstwowa](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896304(v=vs.100)).  
  
- Aplikacje, które używają danych XML.  

  Odpowiedzialność za serializację obiektu pozwala na tworzenie [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] usługi danych. Te usługi przekazywania danych do aplikacji, które wykorzystują dane XML, takie jak aplikacji internetowych opartych na technologii AJAX. W takich przypadkach należy rozważyć użycie [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)]. Usługi te dane są oparte na modelu Entity Data Model i zapewnianie dynamiczny dostęp do danych jednostki przy użyciu standardowych działań Representational State Transfer (REST) HTTP, takich jak GET PUT i publikowania. Aby uzyskać więcej informacji, zobacz [4.5 usług danych WCF](../../../../../docs/framework/data/wcf/index.md).  
  
  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nie obsługuje typu danych native XML. Oznacza to, że gdy jednostka jest zamapowana do tabeli z kolumną XML, właściwość równoważne jednostki dla kolumny XML jest ciąg. Obiekty można odłączony i zserializowanym w formacie XML. Aby uzyskać więcej informacji, zobacz [serializacji obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738446(v=vs.100)).  
  
  Jeśli aplikacja wymaga możliwości do wykonywania zapytań w danych XML, możesz nadal może z zalet zapytań LINQ za pomocą LINQ to XML. Aby uzyskać więcej informacji, zobacz [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) lub [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
- Aplikacje, które zarządzania stanem.  

  [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] Aplikacje sieci Web, często musisz utrzymywać stan strony sieci Web lub z sesji użytkownika. Obiekty w <xref:System.Data.Objects.ObjectContext> wystąpienia może być przechowywanych w stan widoku klienta lub w stanie sesji na serwerze i później mogą być pobierane i ponownie dołączyć do nowego obiektu kontekstu. Aby uzyskać więcej informacji, zobacz [Dołączanie i odłączanie obiektów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896271(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także
- [Zagadnienia dotyczące wdrażania](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)
- [Terminologia programu Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md)
