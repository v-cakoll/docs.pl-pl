---
title: LINQ i ADO.NET
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: be91650c7c06a3bdb5410166cc560ffc9a65d542
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="linq-and-adonet"></a>LINQ i ADO.NET
Dzisiaj, użyć wielu firm deweloperów języków programowania (co najmniej dwa): języka wysokiego poziomu dla warstwy logiki i prezentacji firm (na przykład Visual C# lub Visual Basic), a język kwerendy do interakcji z bazy danych (takich jak [!INCLUDE[tsql](../../../../includes/tsql-md.md)]). Wymaga deweloperowi można wykorzystać w wielu językach zadziałało i powoduje także, że język niezgodności w środowisku programistycznym. Na przykład aplikację, która używa interfejsu API dostępu do danych można wykonać kwerendy w bazie danych określa zapytanie jako literału ciągu przy użyciu znaków cudzysłowu. Ten ciąg zapytania nie można odczytać w kompilatorze i nie jest sprawdzany pod kątem błędów, takich jak Błędna składnia lub czy kolumn lub wierszy, do których się odwołuje faktycznie istnieją. Nie ma typu Sprawdzanie parametrów zapytania i nie `IntelliSense` obsługuje albo.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Umożliwia deweloperom tworzą zapytań na podstawie zestawu w ich kodu aplikacji bez konieczności używania języka osobne zapytania. Można napisać [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytań dotyczących różnych źródeł danych wyliczenia (czyli źródła danych, które implementuje <xref:System.Collections.IEnumerable> interfejsu), na przykład struktury danych w pamięci, dokumentów XML, baz danych, i <xref:System.Data.DataSet> obiektów. Mimo że te źródła danych wyliczenia są implementowane na różne sposoby, wszystkie udostępnianie tego samego konstrukcje składni i języka. Ponieważ zapytania mogą powstawać samego języka programowania, nie masz język zapytania osadzonego jako literały ciągu, których nie zrozumiał ani zweryfikowany przez kompilator. Integrowanie zapytania języka programowania umożliwia również [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] programistom są bardziej wydajni, zapewniając typu kompilacji i sprawdzanie składni, i `IntelliSense`. Te funkcje zmniejszenia konieczności debugowania zapytania i naprawienie błędów.  
  
 Transfer danych z tabel SQL do obiektów w pamięci jest często żmudnego i podatne na błędy. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] Dostawcy implementowane przez [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] i [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] konwertuje dane źródłowe do <xref:System.Collections.IEnumerable>— na podstawie kolekcji obiektów. Programistę zawsze widoków danych jako <xref:System.Collections.IEnumerable> kolekcji, zarówno podczas wykonywania zapytań i kiedy aktualizować. Pełna `IntelliSense` pomoc techniczna jest świadczona w pisaniu zapytań dotyczących tych kolekcji.  
  
 Istnieją trzy oddzielne ADO.NET [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] technologii: [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], i [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] zapewnia bogaty i zoptymalizowane obsługę zapytań <xref:System.Data.DataSet> i [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] umożliwia bezpośrednie kwerendy schematów bazy danych programu SQL Server, i [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)] umożliwia zapytania [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].  
  
 Następujący diagram zawiera omówienie technologii ADO.NET LINQ wzajemne relacje poszczególnych wysokiego poziomu języków programowania i źródeł danych z obsługą LINQ.  
  
 ![LINQ do omówienia ADO.NET](../../../../docs/framework/data/adonet/media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 Aby uzyskać ogólne informacje na temat funkcji języka LINQ, zobacz [wprowadzenie do LINQ](http://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e). Aby dowiedzieć się, jak za pomocą LINQ w aplikacji, zobacz [NOT IN kompilacji: Przewodnik programowania w języku LINQ ogólne](http://msdn.microsoft.com/library/609c7a6b-cbdd-429d-99f3-78d13d3bc049), zawiera szczegółowe informacje o sposobie używania technologii LINQ.  
  
 Poniższe sekcje zawierają więcej informacji na temat [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], i [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)].  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 <xref:System.Data.DataSet> Jest kluczowym elementem odłączonego programowania modelu [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] jest zbudowany na i jest powszechnie używany. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] Umożliwia deweloperom tworzenie bardziej rozbudowane możliwości zapytania <xref:System.Data.DataSet> przez ten sam mechanizm formułowanie zapytania, która jest dostępna dla innych źródeł danych. Aby uzyskać więcej informacji, zobacz [LINQ do DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] to narzędzie przydatne dla deweloperów, którzy nie wymagają mapowania do modelu koncepcyjnego. Za pomocą [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], można użyć [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] model programowania bezpośrednio przez istniejący schemat bazy danych. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] Umożliwia deweloperom Generowanie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] klasy reprezentujące dane. Zamiast mapowania do modelu koncepcyjnego danych, te wygenerowane klasy mapy bezpośrednio do tabel bazy danych, widoki, procedury składowane i funkcje zdefiniowane przez użytkownika.  
  
 Z [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], programiści mogą pisać kod bezpośrednio przed korzystającej z tego samego schematu magazynu [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] programowania wzorca jako kolekcje w pamięci i <xref:System.Data.DataSet>, oprócz innych źródeł danych, takich jak XML. Aby uzyskać więcej informacji, zobacz [LINQ do SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ do Jednostek  
 Większość aplikacji aktualnie są zapisywane na górze relacyjnych baz danych. W pewnym momencie te aplikacje będą muszą wchodzić w interakcje z danymi reprezentowane w formularzu relacyjnych. Schematy bazy danych nie są zawsze idealne rozwiązanie w przypadku tworzenia aplikacji i modelach koncepcyjnych aplikacji nie są takie same logicznego Modele baz danych. [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Model koncepcyjny danych, który może służyć do modelu danych konkretnej domeny, dzięki czemu aplikacje mogą współdziałać ze danych jako obiekty. Zobacz [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) Aby uzyskać więcej informacji.  
  
 Za pomocą [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)], relacyjnej bazie danych jest ujawniona jako obiekty w środowisku .NET. Dzięki temu warstwy obiektu docelowego nadaje się doskonale dla obiekt [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] pomocy technicznej, co umożliwia deweloperom do formułowania zapytań dotyczących bazy danych z język używany do tworzenia logiki biznesowej. Ta funkcja jest nazywany [!INCLUDE[linq_entities](../../../../includes/linq-entities-md.md)]. Zobacz [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)  
 [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)  
 [LINQ (zapytania o języku zintegrowanym)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
