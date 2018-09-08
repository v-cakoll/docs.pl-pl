---
title: 'Porady: użycie argumentów nazwanych i opcjonalnych w programowaniu Office (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: f86509b7257f25e8faaadfc107ad70ca794aeee0
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129749"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>Porady: użycie argumentów nazwanych i opcjonalnych w programowaniu Office (Przewodnik programowania w języku C#)
Nazwy argumentów i argumenty opcjonalne, wprowadzona w [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], zwiększenia wygody, elastyczność i czytelności w programowaniu w języku C#. Ponadto funkcje te znacznie ułatwiają dostęp do interfejsów COM, takich jak interfejsów API automatyzacji programu Microsoft Office.  
  
 W poniższym przykładzie metoda [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) ma szesnastu parametrów, które reprezentują cech tabeli, takie jak liczba kolumn i wierszy, formatowanie, obramowania, czcionki i kolory. Wszystkie parametry szesnastu są opcjonalne, ponieważ w większości przypadków nie chcesz określać wartości określonej dla wszystkich z nich. Jednak bez argumenty nazwane i opcjonalne, wartość lub wartość symbolu zastępczego musi zostać dostarczona dla każdego parametru. Argumenty nazwane i opcjonalne należy określić tylko wartości parametrów, które są wymagane dla projektu.  
  
 Konieczne jest posiadanie programu Microsoft Office Word zainstalowany na tym komputerze do wykonania tych procedur.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a>Aby utworzyć nową aplikację konsoli  
  
1.  Uruchom program Visual Studio.  
  
2.  Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
3.  W **kategorie szablonów** okienku rozwiń **Visual C#**, a następnie kliknij przycisk **Windows**.  
  
4.  Szukaj w górnej części **szablony** okienko, aby upewnić się, że **.NET Framework 4** pojawia się w **platformę docelową** pole.  
  
5.  W **szablony** okienku kliknij **aplikację Konsolową**.  
  
6.  Wpisz nazwę dla projektu w **nazwa** pola.  
  
7.  Kliknij przycisk **OK**.  
  
     Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.  
  
### <a name="to-add-a-reference"></a>Aby dodać odwołanie  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj odwołanie**. **Dodaj odwołanie** pojawi się okno dialogowe.  
  
2.  Na **.NET** wybierz opcję **Microsoft.Office.Interop.Word** w **nazwa składnika** listy.  
  
3.  Kliknij przycisk **OK**.  
  
### <a name="to-add-necessary-using-directives"></a>Aby dodać niezbędne dyrektyw using  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Program.cs** pliku, a następnie kliknij przycisk **Wyświetl kod**.  
  
2.  Dodaj następujący kod `using` dyrektywy na górze pliku kodu.  
  
     [!code-csharp[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]  
  
### <a name="to-display-text-in-a-word-document"></a>Do wyświetlania tekstu w dokumencie programu Word  
  
1.  W `Program` klasy w pliku Program.cs, dodaj następującą metodę do tworzenia aplikacji programu Word i dokument programu Word. [Dodaj](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) metoda ma cztery następujące parametry opcjonalne. W tym przykładzie użyto wartości domyślnych. W związku z tym bez argumentów są niezbędne w instrukcji wywołujące.  
  
     [!code-csharp[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]  
  
2.  Dodaj następujący kod na końcu metody do definiowania miejsca do wyświetlania tekstu w dokumencie i jakie tekst do wyświetlenia.  
  
     [!code-csharp[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]  
  
### <a name="to-run-the-application"></a>Aby uruchomić aplikację  
  
1.  Dodaj następującą instrukcję dla metody Main.  
  
     [!code-csharp[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]  
  
2.  Naciśnij klawisze CTRL + F5, aby uruchomić projekt. Dokument programu Word pojawia się, który zawiera określony tekst.  
  
### <a name="to-change-the-text-to-a-table"></a>Aby zmienić tekst na tabelę  
  
1.  Użyj `ConvertToTable` metodę, aby umieścić tekst w tabeli. Metoda ma szesnastu parametrów opcjonalnych. Funkcja IntelliSense zawiera następujące parametry opcjonalne w nawiasach kwadratowych, jak pokazano na poniższej ilustracji.  
  
     ![Lista parametrów dla metody ConvertToTable. ](../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")  
Parametry ConvertToTable  
  
     Nazwane i opcjonalne argumenty umożliwiają określenie wartości parametrów, które chcesz zmienić. Dodaj następujący kod na końcu metody `DisplayInWord` do utworzenia prostej tabeli. Argument określa, że przecinkami w tekście ciągu w `range` oddziel komórki tabeli.  
  
     [!code-csharp[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]  
  
     We wcześniejszych wersjach języka C#, wywołanie `ConvertToTable` wymaga argumentu odwołania dla każdego parametru, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]  
  
2.  Naciśnij klawisze CTRL + F5, aby uruchomić projekt.  
  
### <a name="to-experiment-with-other-parameters"></a>Aby eksperymentować z innych parametrów  
  
1.  Zmiany w tabeli, aby jedna kolumna i trzema wierszami, Zamień w ostatnim wierszu `DisplayInWord` z następującą instrukcję, a następnie wpisz kombinację klawiszy CTRL + F5.  
  
     [!code-csharp[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]  
  
2.  Aby określić wstępnie zdefiniowany format dla tabeli, należy zastąpić w ostatnim wierszu `DisplayInWord` z następującą instrukcję, a następnie wpisz kombinację klawiszy CTRL + F5. Format może być dowolny z [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) stałe.  
  
     [!code-csharp[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod zawiera pełny przykład.  
  
 [!code-csharp[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Argumenty nazwane i opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
