---
title: Stałe i wyliczenia (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- constants [Visual Basic]
- constants [Visual Basic], list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
ms.openlocfilehash: 0a9c01269e12c2d84be4f30c236c439012a88153
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839593"
---
# <a name="constants-and-enumerations-visual-basic"></a>Stałe i wyliczenia (Visual Basic)
Visual Basic udostępnia wiele wstępnie zdefiniowanych stałych i wyliczenia dla deweloperów. Stałe przechowywać wartości, które pozostają stałe w trakcie wykonywania aplikacji. Wyliczenia zapewniają wygodny sposób pracy z zestawami pokrewnych stałych i skojarzyć wartości stałych o nazwach.  
  
## <a name="constants"></a>Stałe  
  
### <a name="conditional-compilation-constants"></a>Stałe kompilacji warunkowej  
 Poniższa tabela zawiera listę wstępnie zdefiniowanych stałych dostępne dla kompilacji warunkowej.  
  
|**Stałe**|**Opis**|  
|---|---|  
|`CONFIG`|Ciąg, który odnosi się do bieżącego ustawienia **aktywną konfigurację rozwiązania** pole w **programu Configuration Manager**.|  
|`DEBUG`|A `Boolean` wartość, która może być ustawiona w **właściwości projektu** okno dialogowe. Domyślnie z konfiguracji debugowania dla projektu definiuje `DEBUG`. Gdy `DEBUG` jest zdefiniowany, <xref:System.Diagnostics.Debug> metod klasy generują dane wyjściowe do **dane wyjściowe** okna. Gdy nie jest zdefiniowany, <xref:System.Diagnostics.Debug> metod klasy nie są kompilowane i są generowane nie dane wyjściowe debugowania.|  
|`TARGET`|Ciąg reprezentujący typ danych wyjściowych dla projektu lub ustawienia wiersza polecenia **/target** opcji. Możliwe wartości `TARGET` są:<br /><br /> -"winexe", dla aplikacji Windows.<br />-"exe", dla aplikacji konsoli.<br />-"library" dla biblioteki klas.<br />-"module" dla modułu.<br />**/Target** opcja może być ustawiona w programie Visual Studio zintegrowanego środowiska programistycznego. Aby uzyskać więcej informacji, zobacz [/TARGET (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md).|  
|`TRACE`|A `Boolean` wartość, która może być ustawiona w **właściwości projektu** okno dialogowe. Domyślnie wszystkie konfiguracje dla projektu jest zdefiniowanie `TRACE`. Gdy `TRACE` jest zdefiniowany, <xref:System.Diagnostics.Trace> metod klasy generują dane wyjściowe do **dane wyjściowe** okna. Gdy nie jest zdefiniowany, <xref:System.Diagnostics.Trace> klas, metod nie są kompilowane i nie `Trace` są generowane dane wyjściowe.|  
|`VBC_VER`|Liczba reprezentująca wersja języka Visual Basic w *głównych*. *drobne* formatu. Numer wersji [!INCLUDE[vbprvblong](~/includes/vbprvblong-md.md)] jest 8.0.|  
  
### <a name="print-and-display-constants"></a>Drukowanie i stałe Wyświetl  
 Podczas wywołania wydruku i funkcji wyświetlania, w kodzie zamiast wartości faktycznych można użyć następujących stałych.  
  
|**Stałe**|**Opis**|  
|---|---|  
|`vbCrLf`|Kombinacji znaków powrotu/wysuw wiersza powrotu karetki.|  
|`vbCr`|Znaku powrotu karetki.|  
|`vbLf`|Znak wysuwu wiersza.|  
|`vbNewLine`|Znak nowego wiersza.|  
|`vbNullChar`|Znak null.|  
|`vbNullString`|Nie taka sama, jak ciąg o zerowej długości (""); używany do wywoływania zewnętrznych procedur.|  
|`vbObjectError`|Numer błędu. Numery błędach zdefiniowane przez użytkownika powinna być większa od tej wartości. Na przykład:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|Znak tabulacji.|  
|`vbBack`|Znak Backspace.|  
|`vbFormFeed`|Nie używany w programie Microsoft Windows.|  
|`vbVerticalTab`|Nie jest przydatne w Microsoft Windows.|  
  
## <a name="enumerations"></a>Wyliczenia  
 Poniższej tabeli wymieniono i opisano wyliczenia dostarczane przez program Visual Basic.  
  
|Wyliczenie|Opis|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|Określa styl okna do użycia podczas wywoływania wywołany program <xref:Microsoft.VisualBasic.Interaction.Shell%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|Określa sposób odtwarzania dźwięku podczas wywoływania metody audio.|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|Wskazuje typ roli do sprawdzenia podczas wywoływania <xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> metody.|  
|<xref:Microsoft.VisualBasic.CallType>|Wskazuje typ wywoływana podczas wywoływania procedury <xref:Microsoft.VisualBasic.Interaction.CallByName%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.CompareMethod>|Określa sposób porównywania ciągów znaków podczas wywoływania funkcji porównywania.|  
|<xref:Microsoft.VisualBasic.DateFormat>|Określa sposób wyświetlania dat podczas wywoływania <xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.DateInterval>|Wskazuje, jak określać i formatu dat podczas wywoływania funkcji związane z datami.|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|Określa, co należy zrobić, jeśli zawiera katalog, który ma zostać usunięty, pliki lub katalogi.|  
|<xref:Microsoft.VisualBasic.DueDate>|Wskazuje, kiedy płatności są należne podczas wywoływania metody finansowych.|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|Wskazuje, czy pola tekstowe są rozdzielane lub o stałej szerokości.|  
|<xref:Microsoft.VisualBasic.FileAttribute>|Określa atrybuty pliku do użycia podczas wywoływania funkcji uzyskiwania dostępu do plików.|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|Określa pierwszy dzień tygodnia do użycia podczas wywoływania funkcji związane z datami.|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|Określa pierwszy tydzień roku do użycia podczas wywoływania funkcji związane z datami.|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|Wskazuje, której przycisk został naciśnięty w oknie komunikatu, zwracany przez <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|Wskazuje przycisków wyświetlanych podczas wywoływania <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.OpenAccess>|Wskazuje sposób otwierania pliku podczas wywoływania funkcji uzyskiwania dostępu do plików.|  
|<xref:Microsoft.VisualBasic.OpenMode>|Wskazuje sposób otwierania pliku podczas wywoływania funkcji uzyskiwania dostępu do plików.|  
|<xref:Microsoft.VisualBasic.OpenShare>|Wskazuje sposób otwierania pliku podczas wywoływania funkcji uzyskiwania dostępu do plików.|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|Określa, czy plik powinien być trwale usunięte lub umieszczone w Koszu.|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|Określa, czy przeszukać wszystkie lub tylko katalogi najwyższego poziomu.|  
|<xref:Microsoft.VisualBasic.TriState>|Wskazuje `Boolean` wartość lub tego, czy domyślne powinny być używane podczas wywoływania funkcji formatowania liczby.|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|Określa, co należy zrobić, jeśli użytkownik kliknie **anulować** podczas operacji.|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|Określa, czy ma być wyświetlana okna dialogowego postępu, gdy kopiowanie, usuwanie lub przenoszenie plików lub katalogów.|  
|<xref:Microsoft.VisualBasic.VariantType>|Wskazuje typ obiektu variant zwrócony przez <xref:Microsoft.VisualBasic.Information.VarType%2A> funkcji.|  
|<xref:Microsoft.VisualBasic.VbStrConv>|Wskazuje, jaki rodzaj konwersji do wykonania podczas wywoływania <xref:Microsoft.VisualBasic.Strings.StrConv%2A> funkcji.|  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka Visual Basic](../../visual-basic/language-reference/index.md)
- [Visual Basic](../../visual-basic/index.md)
- [Stałe — przegląd](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Wyliczenia — przegląd](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
