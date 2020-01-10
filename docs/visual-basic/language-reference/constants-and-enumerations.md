---
title: Stałe i wyliczenia
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: 5109bf42c9caa7528c5405bb1a5cff0cfb62a5ac
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705759"
---
# <a name="constants-and-enumerations-visual-basic"></a>Stałe i wyliczenia (Visual Basic)

Visual Basic dostarcza wiele wstępnie zdefiniowanych stałych i wyliczeń dla deweloperów. Stałe wartości magazynu, które pozostają stałe przez cały czas wykonywania aplikacji. Wyliczenia zapewniają wygodny sposób pracy z zestawami powiązanych stałych i kojarzenia wartości stałych z nazwami.  
  
## <a name="constants"></a>{1&gt;Stałe&lt;1}  
  
### <a name="conditional-compilation-constants"></a>Stałe kompilacji warunkowej  

 W poniższej tabeli wymieniono wstępnie zdefiniowane stałe dostępne dla kompilacji warunkowej.  
  
|**Stałego**|**Opis**|  
|---|---|  
|`CONFIG`|Ciąg, który odpowiada bieżącemu ustawieniu **aktywnej konfiguracji rozwiązania** w **Configuration Manager**.|  
|`DEBUG`|Wartość `Boolean`, którą można ustawić w oknie dialogowym **właściwości projektu** . Domyślnie Konfiguracja debugowania dla projektu definiuje `DEBUG`. Gdy `DEBUG` jest zdefiniowany, <xref:System.Diagnostics.Debug> metody klasy generują dane wyjściowe do okna **danych wyjściowych** . Gdy nie jest zdefiniowany, metody klasy <xref:System.Diagnostics.Debug> nie są kompilowane i nie są generowane żadne dane wyjściowe debugowania.|  
|`TARGET`|Ciąg reprezentujący typ danych wyjściowych dla projektu lub ustawienie opcji wiersza polecenia **-Target** . Możliwe wartości `TARGET` są następujące:<br /><br /> -"winexe" dla aplikacji systemu Windows.<br />-"exe" dla aplikacji konsolowej.<br />-"Biblioteka" dla biblioteki klas.<br />-"module" dla modułu.<br />-Opcja **-Target** może być ustawiona w zintegrowanym środowisku programistycznym programu Visual Studio. Aby uzyskać więcej informacji, zobacz [-Target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|Wartość `Boolean`, którą można ustawić w oknie dialogowym **właściwości projektu** . Domyślnie wszystkie konfiguracje dla projektu definiują `TRACE`. Gdy `TRACE` jest zdefiniowany, <xref:System.Diagnostics.Trace> metody klasy generują dane wyjściowe do okna **danych wyjściowych** . Gdy nie jest on zdefiniowany, metody klasy <xref:System.Diagnostics.Trace> nie są kompilowane i nie są generowane żadne `Trace` dane wyjściowe.|  
|`VBC_VER`|Liczba reprezentująca wersję Visual Basic w języku *głównym*. Format *pomocniczy* .|  
  
### <a name="print-and-display-constants"></a>Drukowanie i wyświetlanie stałych  

 Po wywołaniu funkcji drukowania i wyświetlania, można użyć następujących stałych w kodzie zamiast rzeczywistych wartości.  
  
|**Stałego**|**Opis**|  
|---|---|  
|`vbCrLf`|Kombinacja znaków powrotu karetki/wysuwu wiersza.|  
|`vbCr`|Znak powrotu karetki.|  
|`vbLf`|Znak wysuwu wiersza.|  
|`vbNewLine`|Znak nowego wiersza.|  
|`vbNullChar`|Znak null.|  
|`vbNullString`|Nie taka sama jak ciąg o zerowej długości (""); używane do wywoływania procedur zewnętrznych.|  
|`vbObjectError`|Numer błędu. Liczba błędów zdefiniowana przez użytkownika powinna być większa niż ta wartość. Na przykład:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Znak tabulacji.|  
|`vbBack`|Znak Backspace.|  
|`vbFormFeed`|Nieużywane w systemie Microsoft Windows.|  
|`vbVerticalTab`|Nieprzydatne w systemie Microsoft Windows.|  
  
## <a name="enumerations"></a>Wyliczenia  

 W poniższej tabeli wymieniono i opisano wyliczenia dostarczone przez Visual Basic.  
  
|Wyliczenie|Opis|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Określa styl okna, który ma być używany dla wywoływanego programu podczas wywoływania funkcji <xref:Microsoft.VisualBasic.Interaction.Shell%2A>.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Wskazuje sposób odtwarzania dźwięków podczas wywoływania metod audio.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Wskazuje typ roli do sprawdzenia podczas wywoływania metody <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>.|  
|<xref:Microsoft.VisualBasic.CallType>|Wskazuje typ procedury wywoływanej podczas wywoływania funkcji <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Wskazuje sposób porównywania ciągów podczas wywoływania funkcji porównywania.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Wskazuje sposób wyświetlania dat podczas wywoływania funkcji <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Wskazuje, jak określić i sformatować interwały dat podczas wywoływania funkcji związanych z datą.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Określa, co należy zrobić, gdy katalog, który ma zostać usunięty, zawiera pliki lub katalogi.|  
|<xref:Microsoft.VisualBasic.DueDate>|Wskazuje, kiedy płatności są należne przy wywoływaniu metod finansowych.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Wskazuje, czy pola tekstowe są rozdzielane, czy o stałej szerokości.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Wskazuje atrybuty pliku do użycia podczas wywoływania funkcji dostępu do plików.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Wskazuje pierwszy dzień tygodnia, który ma być używany podczas wywoływania funkcji związanych z datą.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Wskazuje pierwszy tydzień roku, który ma być używany podczas wywoływania funkcji związanych z datą.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Wskazuje, który przycisk został naciśnięty w oknie komunikatu zwracanym przez funkcję <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Wskazuje, które przyciski mają być wyświetlane podczas wywoływania funkcji <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Wskazuje, jak otworzyć plik podczas wywoływania funkcji dostępu do plików.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Wskazuje, jak otworzyć plik podczas wywoływania funkcji dostępu do plików.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Wskazuje, jak otworzyć plik podczas wywoływania funkcji dostępu do plików.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Określa, czy plik powinien być trwale usunięty lub umieszczony w koszu.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Określa, czy mają być przeszukiwane wszystkie, czy tylko katalogi najwyższego poziomu.|  
|<xref:Microsoft.VisualBasic.TriState>|Wskazuje wartość `Boolean` lub, czy należy użyć wartości domyślnej podczas wywoływania funkcji formatowania liczb.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Określa, co należy zrobić, jeśli użytkownik kliknie **przycisk Anuluj** podczas operacji.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Określa, czy wyświetlać okno dialogowe postępu podczas kopiowania, usuwania lub przeniesienia plików lub katalogów.|  
|<xref:Microsoft.VisualBasic.VariantType>|Wskazuje typ obiektu Variant zwracanego przez funkcję <xref:Microsoft.VisualBasic.Information.VarType%2A>.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Wskazuje typ konwersji do wykonania podczas wywoływania funkcji <xref:Microsoft.VisualBasic.Strings.StrConv%2A>.|  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka Visual Basic](../../visual-basic/language-reference/index.md)
- [Stałe — przegląd](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Wyliczenia — przegląd](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
