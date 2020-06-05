---
title: Stałe i wyliczenia
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: 60cd1ddac9bca685ddc5778e7d289710245a183e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374489"
---
# <a name="constants-and-enumerations-visual-basic"></a>Stałe i wyliczenia (Visual Basic)

Visual Basic dostarcza wiele wstępnie zdefiniowanych stałych i wyliczeń dla deweloperów. Stałe wartości magazynu, które pozostają stałe przez cały czas wykonywania aplikacji. Wyliczenia zapewniają wygodny sposób pracy z zestawami powiązanych stałych i kojarzenia wartości stałych z nazwami.  
  
## <a name="constants"></a>Stałe  
  
### <a name="conditional-compilation-constants"></a>Stałe kompilacji warunkowej  

 W poniższej tabeli wymieniono wstępnie zdefiniowane stałe dostępne dla kompilacji warunkowej.  
  
|**Stały**|**Opis**|  
|---|---|  
|`CONFIG`|Ciąg, który odpowiada bieżącemu ustawieniu **aktywnej konfiguracji rozwiązania** w **Configuration Manager**.|  
|`DEBUG`|`Boolean`Wartość, którą można ustawić w oknie dialogowym **właściwości projektu** . Domyślnie Konfiguracja debugowania dla projektu jest zdefiniowana `DEBUG` . Gdy `DEBUG` jest zdefiniowany, <xref:System.Diagnostics.Debug> metody klasy generują dane wyjściowe w oknie **danych wyjściowych** . Gdy nie jest zdefiniowany, <xref:System.Diagnostics.Debug> metody klasy nie są kompilowane i nie są generowane żadne dane wyjściowe debugowania.|  
|`TARGET`|Ciąg reprezentujący typ danych wyjściowych dla projektu lub ustawienie opcji wiersza polecenia **-Target** . Możliwe wartości `TARGET` to:<br /><br /> -"winexe" dla aplikacji systemu Windows.<br />-"exe" dla aplikacji konsolowej.<br />-"Biblioteka" dla biblioteki klas.<br />-"module" dla modułu.<br />-Opcja **-Target** może być ustawiona w zintegrowanym środowisku programistycznym programu Visual Studio. Aby uzyskać więcej informacji, zobacz [-Target (Visual Basic)](../reference/command-line-compiler/target.md).|  
|`TRACE`|`Boolean`Wartość, którą można ustawić w oknie dialogowym **właściwości projektu** . Domyślnie wszystkie konfiguracje projektu są definiowane `TRACE` . Gdy `TRACE` jest zdefiniowany, <xref:System.Diagnostics.Trace> metody klasy generują dane wyjściowe w oknie **danych wyjściowych** . Gdy nie jest zdefiniowany, <xref:System.Diagnostics.Trace> metody klasy nie są kompilowane i nie `Trace` są generowane żadne dane wyjściowe.|  
|`VBC_VER`|Liczba reprezentująca wersję Visual Basic w języku *głównym*. Format *pomocniczy* .|  
  
### <a name="print-and-display-constants"></a>Drukowanie i wyświetlanie stałych  

 Po wywołaniu funkcji drukowania i wyświetlania, można użyć następujących stałych w kodzie zamiast rzeczywistych wartości.  
  
|**Stały**|**Opis**|  
|---|---|  
|`vbCrLf`|Kombinacja znaków powrotu karetki/wysuwu wiersza.|  
|`vbCr`|Znak powrotu karetki.|  
|`vbLf`|Znak wysuwu wiersza.|  
|`vbNewLine`|Znak nowego wiersza.|  
|`vbNullChar`|Znak null.|  
|`vbNullString`|Nie taka sama jak ciąg o zerowej długości (""); używane do wywoływania procedur zewnętrznych.|  
|`vbObjectError`|Numer błędu. Liczba błędów zdefiniowana przez użytkownika powinna być większa niż ta wartość. Przykład:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Znak tabulacji.|  
|`vbBack`|Znak Backspace.|  
|`vbFormFeed`|Nieużywane w systemie Microsoft Windows.|  
|`vbVerticalTab`|Nieprzydatne w systemie Microsoft Windows.|  
  
## <a name="enumerations"></a>Wyliczenia  

 W poniższej tabeli wymieniono i opisano wyliczenia dostarczone przez Visual Basic.  
  
|Wyliczenie|Opis|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Określa styl okna, który ma być używany dla wywoływanego programu podczas wywoływania <xref:Microsoft.VisualBasic.Interaction.Shell%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Wskazuje sposób odtwarzania dźwięków podczas wywoływania metod audio.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Wskazuje typ roli do sprawdzenia podczas wywoływania <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> metody.|  
|<xref:Microsoft.VisualBasic.CallType>|Wskazuje typ procedury wywoływanej podczas wywoływania <xref:Microsoft.VisualBasic.Interaction.CallByName%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Wskazuje sposób porównywania ciągów podczas wywoływania funkcji porównywania.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Wskazuje sposób wyświetlania dat podczas wywoływania <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Wskazuje, jak określić i sformatować interwały dat podczas wywoływania funkcji związanych z datą.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Określa, co należy zrobić, gdy katalog, który ma zostać usunięty, zawiera pliki lub katalogi.|  
|<xref:Microsoft.VisualBasic.DueDate>|Wskazuje, kiedy płatności są należne przy wywoływaniu metod finansowych.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Wskazuje, czy pola tekstowe są rozdzielane, czy o stałej szerokości.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Wskazuje atrybuty pliku do użycia podczas wywoływania funkcji dostępu do plików.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Wskazuje pierwszy dzień tygodnia, który ma być używany podczas wywoływania funkcji związanych z datą.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Wskazuje pierwszy tydzień roku, który ma być używany podczas wywoływania funkcji związanych z datą.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Wskazuje, który przycisk został naciśnięty w oknie komunikatu zwracanym przez <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkcję.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Wskazuje, które przyciski mają być wyświetlane podczas wywoływania <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Wskazuje, jak otworzyć plik podczas wywoływania funkcji dostępu do plików.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Wskazuje, jak otworzyć plik podczas wywoływania funkcji dostępu do plików.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Wskazuje, jak otworzyć plik podczas wywoływania funkcji dostępu do plików.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Określa, czy plik powinien być trwale usunięty lub umieszczony w koszu.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Określa, czy mają być przeszukiwane wszystkie, czy tylko katalogi najwyższego poziomu.|  
|<xref:Microsoft.VisualBasic.TriState>|Wskazuje `Boolean` wartość lub, czy należy użyć wartości domyślnej podczas wywoływania funkcji formatowania liczb.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Określa, co należy zrobić, jeśli użytkownik kliknie **przycisk Anuluj** podczas operacji.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Określa, czy wyświetlać okno dialogowe postępu podczas kopiowania, usuwania lub przeniesienia plików lub katalogów.|  
|<xref:Microsoft.VisualBasic.VariantType>|Wskazuje typ obiektu Variant zwracanego przez <xref:Microsoft.VisualBasic.Information.VarType%2A> funkcję.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Wskazuje typ konwersji do wykonania podczas wywoływania <xref:Microsoft.VisualBasic.Strings.StrConv%2A> funkcji.|  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka Visual Basic](index.md)
- [Stałe — Przegląd](../programming-guide/language-features/constants-enums/constants-overview.md)
- [Enumerations — Przegląd](../programming-guide/language-features/constants-enums/enumerations-overview.md)
