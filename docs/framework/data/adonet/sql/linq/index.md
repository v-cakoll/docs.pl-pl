---
title: LINQ do SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 15a6585e0653fd87730abd1aef08ffd392cf8c87
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="linq-to-sql"></a>LINQ do SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]wchodzi w skład [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] wersji 3.5, która zapewnia infrastrukturę środowiska wykonawczego do zarządzania jako obiekty relacyjnej bazie danych.  
  
> [!NOTE]
>  Danych relacyjnych pojawia się jako kolekcja tabel dwuwymiarowa (*relacji* lub *płaskim pliki*), gdzie wspólnych kolumn są tabele powiązane ze sobą. Aby użyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] efektywnie musi posiadać pewną znajomość podstawowych zasad relacyjnych baz danych.  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], modelu danych relacyjnej bazy danych jest mapowany na model obiektowy wyrażone w języku programowania dewelopera. Po uruchomieniu aplikacji, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przekłada się na SQL języku zintegrowanym zapytania w modelu obiektów i wysyła je do bazy danych do wykonania. Gdy baza danych zwraca wyniki, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy je do obiektów, które można pracować w języku programowania.  
  
 Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] jest zwykle używany [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)], który udostępnia interfejs użytkownika wykonywania wielu funkcji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Dokumentacji, która jest zawarta w tej wersji programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] opisano podstawowe bloki konstrukcyjne, procesów i techniki potrzebne do tworzenia [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji. Możesz również wyszukać Microsoft Docs określonych problemów i mogą uczestniczyć w [LINQ Forum](http://go.microsoft.com/fwlink/?LinkId=76488), gdzie można omawiać bardziej złożonych tematów szczegółowo z ekspertami. Na koniec [LINQ do SQL: .NET Language-Integrated zapytania dla danych relacyjnych](http://go.microsoft.com/fwlink/?LinkId=93205) oficjalny dokument zawierający szczegóły [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologii, wraz z [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] i przykładów kodu w języku C#.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)  
 Zawiera omówienie skrócone [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wraz z informacjami o tym, jak rozpocząć pracę przy użyciu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Przewodnik programowania](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 Zawiera opis czynności mapowania, zapytanie, aktualizowanie, debugowanie i podobne zadania.  
  
 [Dokumentacja](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 Udostępnia informacje na temat kilka aspektów [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Tematy zawierają mapowanie typu środowiska CLR SQL, standardowe Translacja Operator zapytania i inne.  
  
 [Przykłady](../../../../../../docs/framework/data/adonet/sql/linq/samples.md)  
 Zawiera łącza do [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] i przykłady dotyczące języka C#.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [LINQ (zapytania o języku zintegrowanym)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 Zawiera omówienie [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologii.  
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 W tym artykule opisano [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologii [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] użytkowników.  
  
 [LINQ do ADO.NET](http://msdn.microsoft.com/en-us/be3297b9-1b54-4d4c-82a8-add0d79c2006)  
 Łączy się [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] portalu.  
  
 [LINQ do SQL — wskazówki](http://msdn.microsoft.com/en-us/308e66ac-f704-4e00-9b4e-7af0045a2374)  
 Przedstawiono wskazówki dostępne dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 Opisuje sposób pobierania przykładowe bazy danych używane w dokumentacji.  
  
 [LinqDataSource Technology Overview](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136)  
 Opisuje sposób <xref:System.Web.UI.WebControls.LinqDataSource> kontrolować ujawnia [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] dla deweloperów sieci Web za pośrednictwem [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] architektura formantu źródła danych.
