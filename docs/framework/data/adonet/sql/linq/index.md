---
title: LINQ do SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: fbb2f8cf37bd05864dc93b8ebbd33466a9a2c55e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793077"
---
# <a name="linq-to-sql"></a>LINQ do SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]jest składnikiem .NET Framework w wersji 3,5, który udostępnia infrastrukturę czasu wykonywania do zarządzania danymi relacyjnymi jako obiekty.  
  
> [!NOTE]
> Dane relacyjne są wyświetlane jako kolekcja dwuwymiarowych tabel (*relacji* lub *plików prostych*), w których wspólne kolumny wiążą tabele ze sobą. Aby efektywnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] korzystać z programu, musisz mieć pewną znajomość podstawowych zasad relacyjnych baz danych.  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie model danych relacyjnej bazy danych jest mapowany na model obiektów wyrażony w języku programowania dewelopera. Po uruchomieniu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji program tłumaczy do języka SQL zapytania zintegrowane z językiem w modelu obiektów i wysyła je do bazy danych w celu wykonania. Gdy baza danych zwróci wyniki, program [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy je z powrotem na obiekty, z których możesz korzystać w własnym języku programowania.  
  
 Deweloperzy korzystający z programu Visual Studio zwykle używają Object Relational Designer, który udostępnia interfejs użytkownika do implementowania wielu funkcji programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Dokumentacja, która jest dostępna w tej wersji programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , zawiera opis podstawowych bloków konstrukcyjnych, procesów i technik potrzebnych do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kompilowania aplikacji. Możesz również wyszukać Microsoft Docs pod kątem określonych problemów i można wziąć udział na [forum LINQ](https://go.microsoft.com/fwlink/?LinkId=76488), gdzie można omówić bardziej złożone tematy szczegółowo z ekspertami. Na koniec LINQ to SQL: zastosowana w [języku .NET zapytanie zintegrowane z założeniami](https://go.microsoft.com/fwlink/?LinkId=93205) informacji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] o relacyjnej ilości danych, C# kompletne z Visual Basic i przykładami kodu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](getting-started.md)  
 Zawiera skrócone Omówienie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wraz z informacjami dotyczącymi sposobu rozpoczęcia korzystania z programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Przewodnik programowania](programming-guide.md)  
 Zawiera kroki związane z mapowaniem, wykonywaniem zapytań, aktualizowaniem, debugowaniem i podobnymi zadaniami.  
  
 [Dokumentacja](reference.md)  
 Zawiera informacje referencyjne o kilku aspektach [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Tematy zawierają mapowanie typu SQL-CLR, tłumaczenie standardowego operatora zapytań i nie tylko.  
  
 [Przykłady](samples.md)  
 Zawiera łącza do Visual Basic i C# przykładów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Language-Integrated Query (LINQ) —C#](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 Zapewnia przegląd technologii LINQ w programie C#.
 
 [Zapytanie zintegrowane z językiem (LINQ) — Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Zapewnia przegląd technologii LINQ w Visual Basic.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Opisuje [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologie dla Visual Basic użytkowników.  
  
 [LINQ i ADO.NET](../../linq-and-ado-net.md)  
 Linki do portalu ADO.NET.  
  
 [Instruktaże LINQ to SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 Wyświetla listę przewodników dostępnych [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]dla programu.  
  
 [Pobieranie przykładowych baz danych](downloading-sample-databases.md)  
 Opisuje sposób pobierania przykładowych baz danych używanych w dokumentacji programu.  
  
 [Formant LinqDataSource serwera sieci Web — Omówienie](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 Opisuje, w <xref:System.Web.UI.WebControls.LinqDataSource> jaki sposób [!INCLUDE[vbteclinqext](../../../../../../includes/vbteclinqext-md.md)] formant ujawnia deweloperom sieci Web za pomocą architektury kontroli źródła danych ASP.NET.
