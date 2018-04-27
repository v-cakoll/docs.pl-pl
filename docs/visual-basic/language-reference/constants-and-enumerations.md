---
title: Stałe i wyliczenia (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bffbb8dabdd2463633c9d2ca8de3ef120850be3f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="constants-and-enumerations-visual-basic"></a>Stałe i wyliczenia (Visual Basic)
Visual Basic dostarcza szereg wstępnie zdefiniowanych stałe i wyliczenia dla deweloperów. Stałe przechowywać wartości, które pozostają stałe w trakcie wykonywania aplikacji. Wyliczenia oferują wygodny do pracy z zestawów powiązanych stałych i do skojarzenia z nazwami wartości stałych.  
  
## <a name="constants"></a>Stałe  
  
### <a name="conditional-compilation-constants"></a>Stałe kompilacja warunkowa  
 W poniższej tabeli wymieniono dostępne dla kompilacji warunkowej na stałe wstępnie zdefiniowane.  
  
|**Stała**|**Opis**|  
|---|---|  
|`CONFIG`|Ciąg, który odpowiada bieżącej ustawienia **aktywną konfigurację rozwiązania** polu **programu Configuration Manager**.|  
|`DEBUG`|A `Boolean` wartość, która może być ustawiona w **właściwości projektu** okno dialogowe. Domyślnie definiuje z konfiguracji debugowania dla projektu `DEBUG`. Gdy `DEBUG` jest zdefiniowany, <xref:System.Diagnostics.Debug> metod klasy Generowanie danych wyjściowych do **dane wyjściowe** okna. Jeśli nie jest zdefiniowana, <xref:System.Diagnostics.Debug> metod klasy nie są kompilowane i są generowane nie dane wyjściowe debugowania.|  
|`TARGET`|Ciąg reprezentujący typ danych wyjściowych dla projektu lub ustawienia wiersza polecenia **/target** opcji. Możliwe wartości `TARGET` są:<br /><br /> -"winexe" dla aplikacji systemu Windows.<br />-"exe" dla aplikacji konsoli.<br />-"library" potrzeby biblioteki klas.<br />-"module" dla modułu.<br />- **/Target** opcja może być ustawiona w Visual Studio zintegrowane środowisko programistyczne. Aby uzyskać więcej informacji, zobacz [/TARGET (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|A `Boolean` wartość, która może być ustawiona w **właściwości projektu** okno dialogowe. Domyślnie wszystkie konfiguracje dla projektu Zdefiniuj `TRACE`. Gdy `TRACE` jest zdefiniowany, <xref:System.Diagnostics.Trace> metod klasy Generowanie danych wyjściowych do **dane wyjściowe** okna. Jeśli nie jest zdefiniowana, <xref:System.Diagnostics.Trace> klasy metody nie jest skompilowany i nie `Trace` generowane dane wyjściowe.|  
|`VBC_VER`|Liczba reprezentująca wersji Visual Basic w *głównych*. *drobne* format. Numer wersji [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)] jest 8.0.|  
  
### <a name="print-and-display-constants"></a>Drukowanie i stałe wyświetlania  
 Podczas wywołania wydruku i funkcji wyświetlania, można użyć następujących stałych w kodzie zamiast wartości rzeczywistych.  
  
|**Stała**|**Opis**|  
|---|---|  
|`vbCrLf`|Kombinacja znak powrotu/wysuw wiersza karetki.|  
|`vbCr`|Znak powrotu karetki.|  
|`vbLf`|Znak wysuwu wiersza.|  
|`vbNewLine`|Znak nowego wiersza.|  
|`vbNullChar`|Znak null.|  
|`vbNullString`|Nie taka sama, jak ciąg o zerowej długości (""); używane do wywoływania procedur zewnętrznych.|  
|`vbObjectError`|Numer błędu. Numery błąd użytkownika powinna być większa niż wartość. Na przykład:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Znak tabulacji.|  
|`vbBack`|Znak Backspace.|  
|`vbFormFeed`|Nie są używane w systemie Microsoft Windows.|  
|`vbVerticalTab`|Nie jest przydatne w systemie Microsoft Windows.|  
  
## <a name="enumerations"></a>Wyliczenia  
 Poniższej tabeli wymieniono i opisano wyliczenia pochodzącymi z języka Visual Basic.  
  
|Wyliczenie|Opis|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Wskazuje styl okna do używania z programem wywołana podczas wywoływania metody <xref:Microsoft.VisualBasic.Interaction.Shell%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Wskazuje, jak można odtwarzać dźwięki podczas wywoływania metody audio.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Wskazuje typ roli, aby sprawdzić podczas wywoływania metody <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> metody.|  
|<xref:Microsoft.VisualBasic.CallType>|Wskazuje typ wywoływaną podczas wywoływania procedury <xref:Microsoft.VisualBasic.Interaction.CallByName%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Wskazuje sposób porównywania ciągów podczas wywoływania funkcji porównania.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Wskazuje sposób wyświetlania dat podczas wywoływania metody <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Wskazuje, jak określać i formatu dat podczas wywoływania funkcji związanych z datą.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Określa, co należy zrobić, jeśli katalog, który ma zostać usunięty zawiera pliki lub katalogi.|  
|<xref:Microsoft.VisualBasic.DueDate>|Wskazuje termin płatności podczas wywoływania metod finansowych.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Wskazuje, czy tekst pola są rozdzielone lub stałej szerokości.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Określa atrybuty pliku do użycia podczas wywoływania funkcji dostępu do plików.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Określa pierwszy dzień tygodnia, aby użyć podczas wywoływania funkcji związanych z datą.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Wskazuje, w pierwszym tygodniu roku używany podczas wywoływania funkcji związanych z datą.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Wskazuje, które przycisku na komunikat zwrócony przez <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Wskazuje przycisków wyświetlanych podczas wywoływania metody <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Wskazuje sposób otwierania pliku podczas wywoływania funkcji dostępu do plików.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Wskazuje sposób otwierania pliku podczas wywoływania funkcji dostępu do plików.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Wskazuje sposób otwierania pliku podczas wywoływania funkcji dostępu do plików.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Określa, czy trwale usunięte lub umieszczone w Koszu pliku.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Określa, czy Wyszukaj wszystkie lub tylko katalogi najwyższego poziomu.|  
|<xref:Microsoft.VisualBasic.TriState>|Wskazuje `Boolean` wartość lub czy powinny być używane domyślne podczas wywoływania funkcji formatowania numeru.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Określa, co należy zrobić, jeśli użytkownik klika polecenie **anulować** podczas operacji.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Określa, czy należy wyświetlić okna dialogowego postępu, gdy kopiowanie, usuwanie i przenoszenie plików i katalogów.|  
|<xref:Microsoft.VisualBasic.VariantType>|Wskazuje typ obiektu typu Wariant zwrócona przez <xref:Microsoft.VisualBasic.Information.VarType%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Wskazuje, jaki rodzaj konwersji do wykonania podczas wywoływania metody <xref:Microsoft.VisualBasic.Strings.StrConv%2A> funkcji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka Visual Basic](../../visual-basic/language-reference/index.md)  
 [Visual Basic](../../visual-basic/index.md)  
 [Stałe — przegląd](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Wyliczenia — przegląd](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
