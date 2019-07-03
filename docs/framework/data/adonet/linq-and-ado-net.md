---
title: LINQ i ADO.NET
ms.date: 03/30/2017
ms.assetid: bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec
ms.openlocfilehash: 9c517b3efca8cd2b41782858ef1e18e3cba76c1b
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539405"
---
# <a name="linq-and-adonet"></a>LINQ i ADO.NET
Obecnie wielu deweloperów firmy należy za pomocą języków programowania (co najmniej dwa): języka wysokiego poziomu dla warstw logiki i prezentacji firm (np. Visual C# lub Visual Basic) i język zapytań umożliwiający korzystanie z bazy danych (na przykład Transact-SQL) . To wymaga programista ma być biegły w kilku językach zaczęła obowiązywać, a także powoduje niezgodności języka w środowisku programistycznym. Na przykład aplikację, która używa danych dostęp do interfejsu API do wykonania zapytania względem bazy danych określa zapytanie jako literał ciągu przy użyciu znaków cudzysłowu. Ten ciąg zapytania nie można odczytać w kompilatorze i nie jest sprawdzane pod kątem błędów, takich jak nieprawidłową składnię lub tego, czy kolumny lub wiersze, które odwołuje się faktycznie istnieje. Istnieje żaden typ weryfikacji parametry zapytania i nie `IntelliSense` obsługuje albo.  
  
 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] Umożliwia deweloperom formularza zapytania w oparciu o zestaw w ich kodzie aplikacji bez konieczności używania języka oddzielnego zapytania. Można napisać [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] zapytań dotyczących różnych źródeł danych wyliczalny (oznacza to, że źródła danych, które implementuje <xref:System.Collections.IEnumerable> interface), takie jak struktury danych w pamięci, dokumentów XML, baz danych SQL, i <xref:System.Data.DataSet> obiektów. Mimo że te źródła danych wyliczalny są implementowane w na różne sposoby, wszystkie one udostępnianie tego samego konstrukcje składni i języka. Ponieważ zapytania mogą powstawać w języku programowania, ma używać innego język zapytań, który jest osadzony jako literały ciągu, których nie rozumie lub zweryfikowane przez kompilator. Integrowanie zapytań języka programowania również umożliwia programistom Visual Studio mu bardziej wydajnej pracy, zapewniając typów w czasie kompilacji i sprawdzanie składni, i `IntelliSense`. Te funkcje zmniejszyć zapotrzebowanie na debugowanie zapytania i naprawianie błędów.  
  
 Transfer danych z tabelami SQL do obiektów w pamięci jest często uciążliwe i podatne na błędy. [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] Dostawcy w składniku LINQ to DataSet i [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] konwertuje dane źródłowe do <xref:System.Collections.IEnumerable>— na podstawie kolekcji obiektów. Programisty należy zawsze widoków danych jako <xref:System.Collections.IEnumerable> kolekcji, zarówno podczas wysyłania zapytania, jak i kiedy aktualizować. Pełna `IntelliSense` pomoc techniczna jest dostępna do pisania zapytań dotyczących tych kolekcjach.  
  
 Istnieją trzy osobne ADO.NET [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] technologii: LINQ to DataSet, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]i LINQ to Entities. LINQ do DataSet zawiera bardziej zaawansowane, zoptymalizowane zapytań <xref:System.Data.DataSet> i [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] pozwala na bezpośrednie wyszukiwanie schematy bazy danych programu SQL Server i składniku LINQ to Entities umożliwia zapytania modelu danych jednostki.  
  
 Poniższy diagram zawiera omówienie technologii ADO.NET LINQ wzajemne relacje poszczególnych języków programowania wysokiego poziomu i źródła danych z obsługą zapytań LINQ.  
  
 ![LINQ to ADO.NET — Przegląd](../../../../docs/framework/data/adonet/media/dpue-linqtoadonetoverview-bpuedev11.gif "DPUE_LinqToAdoNetOverview_bpuedev11")  
  
 Aby uzyskać więcej informacji na temat LINQ, zobacz [Language Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).
  
 Poniższe sekcje zawierają więcej informacji na temat programu LINQ do zestawu danych, [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)]i LINQ to Entities.  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 <xref:System.Data.DataSet> Jest kluczowym elementem odłączonego modelu programowania, ADO.NET jest oparta na, która jest powszechnie używana. LINQ to DataSet oferuje deweloperom tworzenie bogatszych możliwości kwerend <xref:System.Data.DataSet> przy użyciu tego samego zapytania formułowanie mechanizm który jest dostępny dla innych źródeł danych. Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] jest przydatne narzędzie dla deweloperów, którzy nie wymagają mapowania do modelu koncepcyjnego. Za pomocą [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], możesz użyć [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] model programowania bezpośrednio przez istniejący schemat bazy danych. [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)] Umożliwia deweloperom Generowanie klas .NET Framework, które reprezentują dane. Zamiast mapowania do modelu koncepcyjnego danych, te wygenerowane klasy mapy bezpośrednio do tabel bazy danych, widoki, procedury składowane i funkcje zdefiniowane przez użytkownika.  
  
 Za pomocą [!INCLUDE[vbtecdlinq](../../../../includes/vbtecdlinq-md.md)], programiści mogą pisać kod bezpośrednio w odniesieniu do schematu magazynu, korzystając z tych samych [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] programowania wzorca jako kolekcji w pamięci i <xref:System.Data.DataSet>, oprócz innych źródeł danych, takich jak XML. Aby uzyskać więcej informacji, zobacz [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ do Jednostek  
 Większość aplikacji obecnie są zapisywane na podstawie relacyjnych baz danych. W pewnym momencie te aplikacje należy interakcję z danymi reprezentowane w formularzu relacyjnych. Schematy bazy danych nie są zawsze idealne rozwiązanie do tworzenia aplikacji i modeli koncepcyjnych aplikacji nie są takie same jak modele logiczne baz danych. W modelu Entity Data Model jest model koncepcyjny danych, który może służyć do modelowania danych określonej domeny, aby aplikacje mogą wchodzić w interakcje z danymi w postaci obiektów. Zobacz [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) Aby uzyskać więcej informacji.  
  
 Za pomocą modelu Entity Data Model w relacyjnej bazie danych jest udostępniany jako obiekty w środowisku .NET. To sprawia, że obiekt warstwy obiektu docelowego idealne rozwiązanie dla [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] pomocy technicznej, co pozwoli deweloperom na formułowanie zapytania względem bazy danych z języka używany do tworzenia logiki biznesowej. Ta możliwość jest znana jako LINQ to Entities. Zobacz [składnik LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md)
- [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md)
- [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)
- [Language Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)
- [Omówienie ADO.NET](ado-net-overview.md)
