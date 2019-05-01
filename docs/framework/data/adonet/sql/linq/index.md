---
title: LINQ do SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 532813f68c0996337ce3bed8172a826425db1ec0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902606"
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
 [Zapytanie o języku zintegrowanym (LINQ) —C#](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 Zawiera omówienie technologii LINQ C#.
 
 [Zapytanie o języku zintegrowanym (LINQ) - Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Zawiera omówienie technologii LINQ w Visual Basic.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 W tym artykule opisano [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologii dla użytkowników programu Visual Basic.  
  
 [LINQ i ADO.NET](../../../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 Linki do [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] portalu.  
  
 [LINQ to SQL — wskazówki](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 Przedstawiono wskazówki dostępne dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 W tym artykule opisano sposób pobierania przykładowej bazy danych używane w dokumentacji.  
  
 [Omówienie kontrolki serwera sieci Web kontrolka LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 W tym artykule opisano sposób, w jaki <xref:System.Web.UI.WebControls.LinqDataSource> kontrolować ujawnia [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] deweloperom sieci Web za pośrednictwem [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] architektura kontroli źródła danych.
