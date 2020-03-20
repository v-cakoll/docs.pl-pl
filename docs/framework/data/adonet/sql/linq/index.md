---
title: LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 73d13345-eece-471a-af40-4cc7a2f11655
ms.openlocfilehash: b0660312f540a69911905edd08541ed70cf39bb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174319"
---
# <a name="linq-to-sql"></a>LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]jest składnikiem programu .NET Framework w wersji 3.5, który zapewnia infrastrukturę w czasie wykonywania do zarządzania danymi relacyjnych jako obiekty.  
  
> [!NOTE]
> Dane relacyjne są wyświetlane jako zbiór tabel dwuwymiarowych *(relacji* lub *plików płaskich),* w których wspólne kolumny odnoszą się do siebie. Aby [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] skutecznie korzystać, musisz mieć pewną znajomość podstawowych zasad relacyjnych baz danych.  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programie model danych relacyjnej bazy danych jest mapowany na model obiektu wyrażony w języku programowania dewelopera. Po uruchomieniu aplikacji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy na sql zapytania zintegrowane z językiem w modelu obiektu i wysyła je do bazy danych do wykonania. Gdy baza danych zwraca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wyniki, tłumaczy je z powrotem do obiektów, które można pracować z w języku programowania.  
  
 Deweloperzy korzystający z programu Visual Studio zazwyczaj używają projektanta relacyjnego [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]obiektu, który udostępnia interfejs użytkownika do implementowania wielu funkcji .  
  
 Dokumentacja dołączona do tej [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wersji opisuje podstawowe bloki konstrukcyjne, procesy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] i techniki potrzebne do tworzenia aplikacji. Można również wyszukać Microsoft Docs dla konkretnych problemów, a także uczestniczyć w [LINQ Forum](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), gdzie można omówić bardziej złożone tematy szczegółowo z ekspertami. Na koniec [LINQ do SQL: .NET Language-Integrated Query for Relational Data](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, wraz z przykładami kodu języka Visual Basic i C#.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Wprowadzenie](getting-started.md)  
 Zawiera skrócony przegląd [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] wraz z informacjami o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tym, jak rozpocząć korzystanie .  
  
 [Przewodnik po programowaniu](programming-guide.md)  
 Zawiera kroki mapowania, wykonywania zapytań, aktualizowania, debugowania i podobnych zadań.  
  
 [Dokumentacja](reference.md)  
 Zawiera informacje referencyjne [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]dotyczące kilku aspektów . Tematy obejmują mapowanie typów SQL-CLR, tłumaczenie standardowego operatora zapytań i inne.  
  
 [Próbki](samples.md)  
 Zawiera łącza do przykładów języka Visual Basic i C#.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Zapytanie zintegrowane z językiem (LINQ) - C #](../../../../../csharp/programming-guide/concepts/linq/index.md)\
 Zawiera przeglądy technologii LINQ w języku C#.

 [Zapytanie zintegrowane z językiem (LINQ) — Visual Basic](../../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 Zawiera przeglądy technologii LINQ w języku Visual Basic.
  
 [Linq](../../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 Zawiera opis technologii LINQ dla użytkowników języka Visual Basic.  
  
 [LINQ i ADO.NET](../../linq-and-ado-net.md)  
 Linki do portalu ADO.NET.  
  
 [Wskazówki dotyczące języka LINQ do SQL](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb386295(v=vs.90))  
 Wyświetla listę instruktajni dostępnych dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 [Pobieranie przykładowych baz danych](downloading-sample-databases.md)  
 W tym artykule opisano sposób pobierania przykładowych baz danych używanych w dokumentacji.  
  
 [Omówienie kontroli serwera sieci Web LinqDataSource](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))  
 W tym <xref:System.Web.UI.WebControls.LinqDataSource> artykule opisano, jak formant udostępnia programom sieci Web (Language-Integrated Query) programiści sieci Web za pośrednictwem ASP.NET architektura kontroli źródła danych.
