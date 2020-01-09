---
title: LINQ do SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 4553be9eeab8792197503d0b1de872f4494277b6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634628"
---
# <a name="linq-to-sql"></a>LINQ do SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] jest składnikiem .NET Framework w wersji 3,5, który udostępnia infrastrukturę czasu wykonywania do zarządzania danymi relacyjnymi jako obiekty.  
  
> [!NOTE]
> Dane relacyjne są wyświetlane jako kolekcja dwuwymiarowych tabel (*relacji* lub *plików prostych*), w których wspólne kolumny wiążą tabele ze sobą. Aby efektywnie korzystać z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], musisz mieć pewną znajomość podstawowych zasad relacyjnych baz danych.  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]model danych relacyjnej bazy danych jest mapowany na model obiektów wyrażony w języku programowania dewelopera. Gdy aplikacja jest uruchomiona, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przetłumaczy do języka SQL zapytania zintegrowane z językiem w modelu obiektów i wysyła je do bazy danych w celu wykonania. Gdy baza danych zwróci wyniki, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przetłumaczy je z powrotem na obiekty, z których możesz korzystać we własnym języku programowania.  
  
 Deweloperzy korzystający z programu Visual Studio zwykle używają Object Relational Designer, który udostępnia interfejs użytkownika do implementowania wielu funkcji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Dokumentacja dołączona do tej wersji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zawiera opis podstawowych bloków konstrukcyjnych, procesów i technik potrzebnych do kompilowania aplikacji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Możesz również wyszukać Microsoft Docs pod kątem określonych problemów i można wziąć udział na [forum LINQ](https://go.microsoft.com/fwlink/?LinkId=76488), gdzie można omówić bardziej złożone tematy szczegółowo z ekspertami. Na koniec [LINQ to SQL: zapytanie zintegrowane z językiem .NET na potrzeby szczegółowych informacji na temat danych międzyfirmowych](https://go.microsoft.com/fwlink/?LinkId=93205) , [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologii C# , kompletne z Visual Basic i przykładami kodu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](getting-started.md)  
 Zawiera skrócone Omówienie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wraz z informacjami dotyczącymi sposobu rozpoczęcia korzystania z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Przewodnik programowania](programming-guide.md)  
 Zawiera kroki związane z mapowaniem, wykonywaniem zapytań, aktualizowaniem, debugowaniem i podobnymi zadaniami.  
  
 [Tematy pomocy](reference.md)  
 Zawiera informacje referencyjne na temat kilku aspektów [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Tematy zawierają mapowanie typu SQL-CLR, tłumaczenie standardowego operatora zapytań i nie tylko.  
  
 [Przykłady](samples.md)  
 Zawiera łącza do Visual Basic i C# przykładów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zapytanie zintegrowane z językiem (LINQ) C# —](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 Zapewnia przegląd technologii LINQ w programie C#.
 
 [Zapytanie zintegrowane z językiem (LINQ) — Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Zapewnia przegląd technologii LINQ w Visual Basic.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Opisuje technologie LINQ dla Visual Basic użytkowników.  
  
 [LINQ i ADO.NET](../../linq-and-ado-net.md)  
 Linki do portalu ADO.NET.  
  
 [Instruktaże LINQ to SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 Wyświetla listę instruktaży dostępnych dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Pobieranie przykładowych baz danych](downloading-sample-databases.md)  
 Opisuje sposób pobierania przykładowych baz danych używanych w dokumentacji programu.  
  
 [Formant LinqDataSource serwera sieci Web — Omówienie](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 Opisuje sposób, w jaki formant <xref:System.Web.UI.WebControls.LinqDataSource> udostępnia oparte na języku Language-Integrated Query (LINQ) do deweloperów sieci Web za pomocą architektury kontroli źródła danych ASP.NET.
