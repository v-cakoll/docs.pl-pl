---
title: LINQ to SQL
description: LINQ to SQL jest składnikiem .NET Framework, który zapewnia infrastrukturę czasu wykonywania do zarządzania danymi relacyjnymi jako obiekty.
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: 13502bfee3ee24764d190dace1512bc958343973
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286316"
---
# <a name="linq-to-sql"></a>LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]jest składnikiem .NET Framework w wersji 3,5, który udostępnia infrastrukturę czasu wykonywania do zarządzania danymi relacyjnymi jako obiekty.  
  
> [!NOTE]
> Dane relacyjne są wyświetlane jako kolekcja dwuwymiarowych tabel (*relacji* lub *plików prostych*), w których wspólne kolumny wiążą tabele ze sobą. Aby efektywnie korzystać z programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , musisz mieć pewną znajomość podstawowych zasad relacyjnych baz danych.  
  
 W programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] model danych relacyjnej bazy danych jest mapowany na model obiektów wyrażony w języku programowania dewelopera. Po uruchomieniu aplikacji program [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy do języka SQL zapytania zintegrowane z językiem w modelu obiektów i wysyła je do bazy danych w celu wykonania. Gdy baza danych zwróci wyniki, program [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy je z powrotem na obiekty, z których możesz korzystać w własnym języku programowania.  
  
 Deweloperzy korzystający z programu Visual Studio zwykle używają Object Relational Designer, który udostępnia interfejs użytkownika do implementowania wielu funkcji programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
 Dokumentacja, która jest dostępna w tej wersji programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , zawiera opis podstawowych bloków konstrukcyjnych, procesów i technik potrzebnych do kompilowania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji. Możesz również wyszukać Microsoft Docs pod kątem określonych problemów i można wziąć udział na [forum LINQ](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), gdzie można omówić bardziej złożone tematy szczegółowo z ekspertami. Na koniec [LINQ to SQL: zapytanie zintegrowane z językiem .NET na potrzeby](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) Detailed Data Paper — [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technologia, kompletna z Visual Basic i kodu C# przykłady.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](getting-started.md)  
 Zawiera skrócone Omówienie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wraz z informacjami dotyczącymi sposobu rozpoczęcia korzystania z programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
 [Przewodnik programowania](programming-guide.md)  
 Zawiera kroki związane z mapowaniem, wykonywaniem zapytań, aktualizowaniem, debugowaniem i podobnymi zadaniami.  
  
 [Dokumentacja](reference.md)  
 Zawiera informacje referencyjne o kilku aspektach [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Tematy zawierają mapowanie typu SQL-CLR, tłumaczenie standardowego operatora zapytań i nie tylko.  
  
 [Samples](samples.md)  
 Zawiera łącza do przykładów Visual Basic i C#.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zapytanie zintegrowane z językiem (LINQ)-C #](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 Oferuje przegląd technologii LINQ w języku C#.

 [Zapytanie zintegrowane z językiem (LINQ) — Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Zapewnia przegląd technologii LINQ w Visual Basic.
  
 [LINQ](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Opisuje technologie LINQ dla Visual Basic użytkowników.  
  
 [LINQ i ADO.NET](../../linq-and-ado-net.md)  
 Linki do portalu ADO.NET.  
  
 [Instruktaże LINQ to SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 Wyświetla listę przewodników dostępnych dla programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .  
  
 [Pobieranie przykładowych baz danych](downloading-sample-databases.md)  
 Opisuje sposób pobierania przykładowych baz danych używanych w dokumentacji programu.  
  
 [Formant LinqDataSource serwera sieci Web — Omówienie](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 Opisuje, w jaki sposób <xref:System.Web.UI.WebControls.LinqDataSource> formant uwidacznia oparte na języku Language-Integrated Query (LINQ) do deweloperów sieci Web za pomocą architektury kontroli źródła danych ASP.NET.
