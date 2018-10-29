---
title: LINQ do SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 141505eed8e76bb5f9811b5d2bdc166885905cde
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50196833"
---
# <a name="linq-to-sql"></a>LINQ do SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest składnikiem [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] wersji 3.5, która zapewnia infrastrukturę czasu wykonywania dla zarządzania relacyjnymi bazami danych jako obiektami.  
  
> [!NOTE]
>  Dane relacyjne pojawia się jako kolekcja dwuwymiarowych tabel (*relacji* lub *plików prostych*), gdzie wspólnych kolumn powiązane tabele są ze sobą. Aby użyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] efektywnie, musi mieć pewną znajomość podstawowych zasad relacyjnych baz danych.  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], model danych relacyjnej bazy danych jest zamapowana na model obiektów wyrażony w języku programowania dewelopera. Gdy aplikacja zostanie uruchomiona, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przekłada się na SQL języku zintegrowanym zapytania w modelu obiektów, a następnie wysyła je do bazy danych do wykonania. Gdy baza danych zwraca wyniki, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy je ponownie do obiektów, które może pracować w języku programowania.  
  
 Deweloperzy zazwyczaj przy użyciu programu Visual Studio [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], który zapewnia interfejs użytkownika wykonywania wielu funkcji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Dokumentacji, który jest dołączony do tej wersji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] w tym artykule opisano podstawowe bloki konstrukcyjne, procesów i technik, potrzebujesz do tworzenia [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji. Możesz również wyszukać Microsoft Docs konkretnych problemów i można uczestniczyć w [LINQ Forum](https://go.microsoft.com/fwlink/?LinkId=76488), gdzie można omawiać bardziej złożonych tematów szczegółowo z ekspertami. Na koniec [LINQ to SQL: .NET Language-Integrated zapytania dla danych relacyjnych](https://go.microsoft.com/fwlink/?LinkId=93205) szczegóły oficjalny dokument dotyczący [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologii, wraz z przykładami kodu Visual Basic i C#.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 Zawiera omówienie skróconego [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wraz z informacjami o tym, jak rozpocząć pracę z usługą [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Przewodnik programowania](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 Zawiera instrukcje mapowania zapytań, aktualizowania, debugowania i podobne zadania.  
  
 [Dokumentacja](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 Oferuje informacje odwołań dotyczące kilka aspektów [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Tematy obejmują mapowanie typu SQL CLR, standardowe translacji operatora zapytania i nie tylko.  
  
 [Przykłady](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 Zawiera łącza do przykładów Visual Basic i C#.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 Zawiera omówienie [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologii.  
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 W tym artykule opisano [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologii dla użytkowników programu Visual Basic.  
  
 [LINQ i ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 Linki do [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] portalu.  
  
 [LINQ to SQL — wskazówki](https://msdn.microsoft.com/library/308e66ac-f704-4e00-9b4e-7af0045a2374)  
 Przedstawiono wskazówki dostępne dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 W tym artykule opisano sposób pobierania przykładowej bazy danych używane w dokumentacji.  
  
 [LinqDataSource Technology Overview](https://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136)  
 W tym artykule opisano sposób, w jaki <xref:System.Web.UI.WebControls.LinqDataSource> kontrolować ujawnia [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] deweloperom sieci Web za pośrednictwem [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] architektura kontroli źródła danych.
