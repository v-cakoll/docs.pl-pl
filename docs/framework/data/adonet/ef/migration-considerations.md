---
title: Zagadnienia dotyczące migracji (Entity Framework)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: c31d7d481d5016b8f2d440f8a727e5bfcf66717c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="migration-considerations-entity-framework"></a>Zagadnienia dotyczące migracji (Entity Framework)
[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Entity Framework zapewnia kilka korzyści z istniejącą aplikacją. Jednym z najbardziej ważne z tych zalet jest możliwość używania modelu koncepcyjnego do oddzielania struktur danych używany przez aplikację ze schematu źródła danych. Dzięki temu można łatwo utworzyć przyszłe zmiany w modelu magazynu lub do źródła danych bez wprowadzania zmian kompensacyjnych do aplikacji. Aby uzyskać więcej informacji o zaletach korzystania [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], zobacz [Omówienie struktury jednostek](../../../../../docs/framework/data/adonet/ef/overview.md) i [modelu Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 Aby skorzystać z zalet [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], można przeprowadzić migrację istniejącej aplikacji do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Niektóre zadania są wspólne dla wszystkich aplikacji zmigrowane. Tych zadań obejmują uaktualniania aplikacji na używanie [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] począwszy od wersji 3.5 z dodatkiem Service Pack 1 (SP1), definiowania modeli i mapowania i konfigurowania programu Entity Framework. Podczas migracji aplikacji [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], istnieją dodatkowe zagadnienia, które są stosowane. Te zagadnienia zależą od typu migrowanych aplikacji i określonych funkcji aplikacji. Ten temat zawiera informacje ułatwiające wybór najlepszym podejściem do użycia podczas uaktualniania istniejącej aplikacji.  
  
## <a name="general-migration-considerations"></a>Zagadnienia dotyczące migracji ogólne  
 Następujące kwestie podczas migracji każdej aplikacji [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]:  
  
-   Dowolnej aplikacji, która używa [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] począwszy od wersji 3.5 z dodatkiem SP1 można poddać migracji do programu Entity Framework, tak długo, jak dostawca danych dla źródła danych, która jest używana przez aplikację obsługuje programu Entity Framework.  
  
-   Entity Framework mogą nie obsługiwać wszystkich funkcji dostawcy źródła danych, nawet wtedy, gdy ten dostawca obsługuje programu Entity Framework.  
  
-   Dla dużych lub złożonych aplikacji nie należy przeprowadzić migrację całej aplikacji do narzędzia Entity Framework w tym samym czasie. Jednak dowolną część aplikacji, która nie korzysta z programu Entity Framework nadal musi można zmieniać w przypadku zmiany źródła danych.  
  
-   Połączenie dostawcy danych, które są używane przez program Entity Framework może być współużytkowany przez innych części aplikacji, ponieważ [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] używa [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] dostawcy danych do uzyskiwania dostępu do źródła danych. Na przykład dostawca SqlClient jest używany przez program Entity Framework dostępu do bazy danych programu SQL Server. Aby uzyskać więcej informacji, zobacz [dostawcy EntityClient Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Typowe zadania migracji  
 Ścieżka do migracji istniejącej aplikacji do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zależy od zarówno typ aplikacji oraz istniejąca strategia dostępu do danych. Jednak należy zawsze wykonać następujące zadania podczas migracji istniejącej aplikacji do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
> [!NOTE]
>  Wszystkie te zadania są wykonywane automatycznie za pomocą narzędzi modelu danych jednostki, począwszy od [!INCLUDE[vsOrcas](../../../../../includes/vsorcas-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: Użyj Kreatora modelu danych jednostki](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
1.  Uaktualnienie aplikacji.  
  
     Projekt utworzony przy użyciu starszej wersji programu Visual Studio i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] muszą zostać uaktualnione do użycia [!INCLUDE[vsOrcas](../../../../../includes/vsorcas-md.md)] z dodatkiem SP1 i [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] począwszy od wersji 3.5 z dodatkiem SP1.  
  
2.  Zdefiniuj modeli i mapowania.  
  
     Model i mapowania plików Definiowanie jednostek w modelu koncepcyjnym; struktury w źródle danych, takich jak tabele, procedury składowane i widoków; i mapowanie między struktury źródłowej jednostki i dane. Aby uzyskać więcej informacji, zobacz [porady: ręczne definiowanie modelu i mapowania plików](http://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a).  
  
     Typy, które są zdefiniowane w modelu magazynu musi odpowiadać nazwie obiektów w źródle danych. Jeśli istniejącej aplikacji udostępnia dane jako obiekty, należy się upewnić, że nazwy tych istniejących klas danych i właściwości są zgodne jednostki i właściwości, które są zdefiniowane w modelu koncepcyjnym. Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie modelowania i mapowania plików do pracy z obiektami niestandardowe](http://msdn.microsoft.com/library/bb40c4db-0121-4e45-a167-8fb06707a708).  
  
    > [!NOTE]
    >  Projektant modelu danych jednostki można zmienić nazwy jednostek w modelu koncepcyjnym odpowiadające istniejących obiektów. Aby uzyskać więcej informacji, zobacz [Projektant modelu danych jednostki](http://msdn.microsoft.com/library/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf).  
  
3.  Zdefiniowanie ciągu połączenia.  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Używa ciągu połączenia specjalnie sformatowana podczas wykonywania zapytań dotyczących modelu koncepcyjnego. Ten ciąg połączenia hermetyzuje informacje o modelu i mapowania plików i połączenia ze źródłem danych. Aby uzyskać więcej informacji, zobacz [porady: definiowanie ciągu połączenia](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md).  
  
4.  Konfigurowanie projektu programu Visual Studio.  
  
     Odwołuje się do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zestawów i modelu i mapowania plików musi zostać dodany do projektu programu Visual Studio. Możesz dodać pliki te mapowania do projektu, aby upewnić się, że są wdrożone w aplikacji w lokalizacji określonej w parametrach połączenia. Aby uzyskać więcej informacji, zobacz [porady: ręczne konfigurowanie projektu programu Entity Framework](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Zagadnienia dotyczące aplikacji za pomocą istniejących obiektów  
 Począwszy od [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] obsługuje "zwykły stary" obiektów CLR (POCO), nazywany również ignorujących trwałość obiektów. W większości przypadków istniejących obiektów może współpracować z [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] drobne zmiany. Aby uzyskać więcej informacji, zobacz [Praca z obiektów POCO jednostek](http://msdn.microsoft.com/library/5e0fb82a-b6d1-41a1-b37b-c12db61629d3). Można również migrację aplikacji [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i używać klas danych, które są generowane przez narzędzia Entity Framework. Aby uzyskać więcej informacji, zobacz [porady: Użyj Kreatora modelu danych jednostki](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>Zagadnienia dotyczące aplikacji, które korzystają z dostawcy ADO.NET  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] dostawcy, na przykład SqlClient, umożliwiają zapytanie zwracające dane tabelaryczne źródła danych. Dane mogą również zostać załadowane do [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] zestawu danych. Na poniższej liście opisano zagadnienia dotyczące uaktualniania aplikacji, która wykorzystuje istniejące [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] dostawcy:  
  
 Wyświetlanie danych tabelarycznych przy użyciu czytnik danych.  
 Można rozważyć wykonywania [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytania przy użyciu dostawcy EntityClient i wyliczania zwróconego <xref:System.Data.EntityClient.EntityDataReader> obiektu. Tylko, jeśli aplikacja wyświetla dane tabelaryczne przy użyciu czytnika danych i nie wymaga urządzenia dostarczonych przez [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dla materializowania danych na obiekty, śledzenie zmian i wprowadzanie aktualizacji. Można kontynuować używanie istniejącego kodu dostępu do danych powoduje, że aktualizacje się ze źródłem danych, ale można użyć istniejącego połączenia użytkowcy <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> właściwość <xref:System.Data.EntityClient.EntityConnection>. Aby uzyskać więcej informacji, zobacz [dostawcy EntityClient Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
 Praca z zestawami danych.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Zawiera wiele z tym samym funkcje udostępniane przez zestaw danych, w tym trwałości w pamięci, śledzenia zmian, powiązania danych oraz serializacji obiektów w postaci danych XML. Aby uzyskać więcej informacji, zobacz [Praca z obiektami](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Jeśli [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] nie zapewnia funkcjonalności zestawu danych jest wymagane przez aplikację, możesz nadal można korzystać z zalet zapytań LINQ za pomocą [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]. Aby uzyskać więcej informacji, zobacz [LINQ do DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Zagadnienia dotyczące aplikacji, które wiązanie danych do formantów  
 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] Umożliwia Hermetyzowanie danych w źródle danych, takich jak zestaw danych lub jako [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] danych kontroli źródła, a następnie powiązać elementy interfejsu użytkownika do tych kontrolek danych. Na poniższej liście opisano zagadnienia dotyczące powiązywanie kontrolek z danymi programu Entity Framework.  
  
 Wiązanie danych do kontrolek.  
 Podczas wykonywania zapytań w modelu koncepcyjnym [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] zwraca dane jako obiekty, które są wystąpień typów jednostek. Te obiekty można powiązać bezpośrednio z formantów, a to powiązanie obsługuje aktualizacje. Oznacza to, że zmiany danych w formancie, takie jak wiersz w <xref:System.Windows.Forms.DataGridView>, automatycznie są zapisywane w bazie danych podczas <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metoda jest wywoływana.  
  
 Wylicza wyników zapytania do wyświetlania danych w aplikacji <xref:System.Windows.Forms.DataGridView> lub innego typu formantu, który obsługuje powiązanie danych, można zmodyfikować aplikację do powiązania kontrolki do wyniku <xref:System.Data.Objects.ObjectQuery%601>.  
  
 Aby uzyskać więcej informacji, zobacz [powiązanie obiektów z formantami](http://msdn.microsoft.com/library/2fd34855-929b-4303-a91e-4bb69d958f2b).  
  
 [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] kontrolki źródła danych.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obejmuje formantu źródła danych ma na celu uproszczenie powiązanie danych w [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] aplikacji sieci Web. Aby uzyskać więcej informacji, zobacz [formantu źródła danych programu Entity Framework](http://msdn.microsoft.com/library/1f09af00-9578-4744-a029-765710a3c83f).  
  
## <a name="other-considerations"></a>Inne zagadnienia  
 Poniżej przedstawiono informacje, które mogą być zastosowane podczas migracji określonych typów aplikacji do narzędzia Entity Framework.  
  
 Aplikacje, które udostępniają usługi danych.  
 Usługi sieci Web i aplikacje, które są oparte na systemie Windows Communication Foundation (WCF) ujawniać dane ze źródła danych przy użyciu formatu komunikatów żądań i odpowiedzi XML. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Obsługuje serializacji obiektów jednostek przy użyciu pliku binarnego, XML, lub kontraktu usługi WCF danych serializacji. Dane binarne i serializacji WCF obsługuje pełne serializacja wykresów obiektów. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji warstwowych](http://msdn.microsoft.com/library/9439d2ba-6b5f-44e8-be65-8a442d922cbb).  
  
 Aplikacje, które używają danych XML.  
 Serializacja obiektu umożliwia utworzenie [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] usług danych. Tych usług dostarczają dane do aplikacji, które wykorzystują dane XML, takie jak aplikacji internetowych opartych na technologii AJAX. W takich sytuacjach należy rozważyć użycie [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)]. Usługi te dane są oparte na modelu danych jednostki i podaj dynamiczne dostęp do danych entity przy użyciu standardowych działań transferu REST (Representational State) HTTP, takich jak GET PUT i POST. Aby uzyskać więcej informacji, zobacz [4.5 usługi danych WCF](../../../../../docs/framework/data/wcf/index.md).  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] Nie obsługuje typu danych native XML. Oznacza to, że gdy jednostka jest zamapowana do tabeli zawierającej kolumny XML, właściwość równoważne jednostki dla kolumny XML ma ciąg. Obiekty można rozłączona i zserializowanym w formacie XML. Aby uzyskać więcej informacji, zobacz [serializacji obiektów](http://msdn.microsoft.com/library/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99).  
  
 Jeśli aplikacja wymaga możliwość wykonywania kwerend w danych XML, można nadal będzie korzystać z zalet zapytań LINQ za pomocą LINQ do XML. Aby uzyskać więcej informacji, zobacz [LINQ do XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).  
  
 Aplikacje, które zarządzania stanem.  
 [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] Aplikacje sieci Web często muszą zachować stan strony sieci Web lub sesja użytkownika. Obiekty w <xref:System.Data.Objects.ObjectContext> wystąpienia można przechowywanych w widoku stanu klienta lub stanu sesji na serwerze i później pobrane i ponownie nałożona nowy kontekst obiektu. Aby uzyskać więcej informacji, zobacz [Dołączanie i odłączanie obiektów](http://msdn.microsoft.com/library/41d5c1ef-1b78-4502-aa10-7e1438d62d23).  
  
## <a name="see-also"></a>Zobacz też  
 [Zagadnienia dotyczące wdrażania](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)  
 [Terminologia programu Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md)
