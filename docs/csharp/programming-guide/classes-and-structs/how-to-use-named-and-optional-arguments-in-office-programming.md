---
title: "Porady: użycie argumentów nazwanych i opcjonalnych w programowaniu Office (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a453699591397224435fba1e602c305f18e84a11
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>Porady: użycie argumentów nazwanych i opcjonalnych w programowaniu Office (Przewodnik programowania w języku C#)
Nazwane argumenty i argumentów opcjonalnych, wprowadzone w systemie [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], zwiększenia wygody, elastyczność i możliwość odczytania w C# — programowanie. Ponadto te funkcje znacznie ułatwienia dostępu do interfejsów modelu COM, takich jak Microsoft Office automatyzacji interfejsów API.  
  
 W poniższym przykładzie metoda [ConvertToTable](http://go.microsoft.com/fwlink/?LinkId=145378) ma parametry, które reprezentują właściwości tabeli, takie jak liczba kolumn i wierszy, formatowanie, obramowania szesnastu, czcionki i kolory. Wszystkie szesnastu parametry są opcjonalne, ponieważ w większości przypadków nie chcesz określać wartości określonej dla wszystkich z nich. Jednak bez argumenty nazwane i opcjonalne, wartość lub wartość symbolu zastępczego musi zostać podany dla każdego parametru. Z argumenty nazwane i opcjonalne możesz określić wartości tylko dla parametrów, które są wymagane dla projektu.  
  
 Musi mieć program Microsoft Office Word zainstalowany na tym komputerze do wykonania tych procedur.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a>Aby utworzyć nową aplikację konsoli  
  
1.  Uruchom program Visual Studio.  
  
2.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu**.  
  
3.  W **kategorii Szablony** okienku rozwiń **Visual C#**, a następnie kliknij przycisk **Windows**.  
  
4.  Szukaj w górnej części **szablony** okienko, aby upewnić się, że **.NET Framework 4** pojawia się w **platformy docelowej** pole.  
  
5.  W **szablony** okienku, kliknij przycisk **aplikacji konsoli**.  
  
6.  Wpisz nazwę projektu w **nazwa** pola.  
  
7.  Kliknij przycisk **OK**.  
  
     Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.  
  
### <a name="to-add-a-reference"></a>Aby dodać odwołanie  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **Dodaj odwołanie**. **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.  
  
2.  Na **.NET** wybierz pozycję **Microsoft.Office.Interop.Word** w **nazwa składnika** listy.  
  
3.  Kliknij przycisk **OK**.  
  
### <a name="to-add-necessary-using-directives"></a>Aby dodać niezbędne przy użyciu dyrektyw  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Program.cs** pliku, a następnie kliknij przycisk **kod widoku**.  
  
2.  Dodaj następujące `using` dyrektywy na początku pliku kodu.  
  
     [!code-csharp[csProgGuideNamedAndOptional#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_1.cs)]  
  
### <a name="to-display-text-in-a-word-document"></a>Do wyświetlania tekstu w dokumencie programu Word  
  
1.  W `Program` klasy w pliku Program.cs, dodaj następującą metodę do tworzenia aplikacji programu Word i dokument programu Word. [Dodaj](http://go.microsoft.com/fwlink/?LinkId=145381) metoda ma cztery następujące parametry opcjonalne. W tym przykładzie używane wartości domyślne. W związku z tym bez argumentów są niezbędne w instrukcji wywoływania.  
  
     [!code-csharp[csProgGuideNamedAndOptional#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_2.cs)]  
  
2.  Dodaj następujący kod na końcu metody, aby określić, gdzie do wyświetlania tekstu w dokumencie i tekst do wyświetlenia.  
  
     [!code-csharp[csProgGuideNamedAndOptional#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_3.cs)]  
  
### <a name="to-run-the-application"></a>Aby uruchomić aplikację  
  
1.  Dodaj następującą instrukcję do widoku głównego.  
  
     [!code-csharp[csProgGuideNamedAndOptional#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_4.cs)]  
  
2.  Naciśnij klawisze CTRL + F5, aby uruchomić projekt. Pojawia się dokument programu Word, który zawiera określony tekst.  
  
### <a name="to-change-the-text-to-a-table"></a>Aby zmienić tekst do tabeli  
  
1.  Użyj `ConvertToTable` metodę, aby umieścić tekst w tabeli. Metoda ma następujące parametry opcjonalne szesnastu. IntelliSense obejmuje następujące parametry opcjonalne w nawiasach, jak pokazano na poniższej ilustracji.  
  
     ![Lista parametrów dla metody ConvertToTable. ] (../../../csharp/programming-guide/classes-and-structs/media/convert_tableparameters.png "Convert_TableParameters")  
Parametry ConvertToTable  
  
     Nazwane i opcjonalne argumenty umożliwiają określenie wartości parametrów, które chcesz zmienić. Dodaj następujący kod na końcu metody `DisplayInWord` utworzyć prostą tabelę. Argument określa, że przecinkami w tekście ciąg w `range` oddzielnych komórek tabeli.  
  
     [!code-csharp[csProgGuideNamedAndOptional#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_5.cs)]  
  
     We wcześniejszych wersjach języka C#, wywołanie `ConvertToTable` wymaga argumentu odwołania dla każdego parametru, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[csProgGuideNamedAndOptional#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_6.cs)]  
  
2.  Naciśnij klawisze CTRL + F5, aby uruchomić projekt.  
  
### <a name="to-experiment-with-other-parameters"></a>Aby wypróbować inne parametry  
  
1.  Aby zmienić tabeli, dzięki czemu zawiera jedną kolumnę i trzy wiersze, należy zastąpić w ostatnim wierszu `DisplayInWord` z poniższych instrukcji, a następnie wpisz CTRL + F5.  
  
     [!code-csharp[csProgGuideNamedAndOptional#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_7.cs)]  
  
2.  Aby określić format wstępnie zdefiniowane dla tabeli, należy zastąpić w ostatnim wierszu `DisplayInWord` z poniższych instrukcji, a następnie wpisz CTRL + F5. Format może być dowolny z [WdTableFormat](http://go.microsoft.com/fwlink/?LinkId=145382) stałe.  
  
     [!code-csharp[csProgGuideNamedAndOptional#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_8.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod obejmuje pełny przykład.  
  
 [!code-csharp[csProgGuideNamedAndOptional#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-named-and-optional-arguments-in-office-programming_9.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Argumenty nazwane i opcjonalne](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
