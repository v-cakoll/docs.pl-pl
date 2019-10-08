---
title: 'Instrukcje: użycie argumentów nazwanych i opcjonalnych w programowaniu pakietu C# Office — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 90b60a6410ffbe7f9802b01bf3303b6e842a1424
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002789"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>Porady: użycie argumentów nazwanych i opcjonalnych w programowaniu Office (Przewodnik programowania w języku C#)

Argumenty nazwane i opcjonalne argumenty, wprowadzone w C# 4, zwiększają wygodę, elastyczność i czytelność C# w programowaniu. Ponadto te funkcje znacznie ułatwiają dostęp do interfejsów COM, takich jak interfejsy API automatyzacji Microsoft Office.

W poniższym przykładzie metoda [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) ma szesnaste parametry, które reprezentują cechy tabeli, takie jak liczba kolumn i wierszy, formatowanie, obramowania, czcionki i kolory. Wszystkie 16 parametrów są opcjonalne, ponieważ większość z nich nie chce określać konkretnych wartości dla wszystkich z nich. Jednakże bez argumentów nazwanych i opcjonalnych należy podać wartość lub symbol zastępczy dla każdego parametru. Za pomocą argumentów nazwanych i opcjonalnych można określić wartości tylko dla parametrów, które są wymagane dla projektu.

Aby wykonać te procedury, na komputerze musi być zainstalowany program Microsoft Office Word.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Aby utworzyć nową aplikację konsolową

1. Uruchom program Visual Studio.

2. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

3. W okienku **Kategorie szablonów** rozwiń **element Wizualizacja C#** , a następnie kliknij pozycję **Windows**.

4. Poszukaj w górnej części okienka **Szablony** , aby upewnić się, że **.NET Framework 4** pojawia się w polu **platforma docelowa** .

5. W okienku **Szablony** kliknij pozycję **Aplikacja konsolowa**.

6. Wpisz nazwę projektu w polu **Nazwa** .

7. Kliknij przycisk **OK**.

     Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.

## <a name="to-add-a-reference"></a>Aby dodać odwołanie

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij pozycję **Dodaj odwołanie**. Zostanie wyświetlone okno dialogowe **Dodawanie odwołania** .

2. Na stronie **.NET** wybierz pozycję **Microsoft. Office. Interop. Word** na liście **Nazwa składnika** .

3. Kliknij przycisk **OK**.

## <a name="to-add-necessary-using-directives"></a>Aby dodać wymagane dyrektywy using

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *program.cs* , a następnie kliknij polecenie **Wyświetl kod**.

2. Dodaj następujące dyrektywy `using` na początku pliku kodu:

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a>Aby wyświetlić tekst w dokumencie programu Word

1. W klasie `Program` w *program.cs*Dodaj następującą metodę w celu utworzenia aplikacji programu Word i dokumentu programu Word. Metoda [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) ma cztery parametry opcjonalne. W tym przykładzie używane są wartości domyślne. W związku z tym nie są wymagane żadne argumenty w instrukcji wywołującej.

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. Dodaj następujący kod na końcu metody, aby określić, gdzie ma być wyświetlany tekst w dokumencie i jaki tekst ma być wyświetlany:

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a>Aby uruchomić aplikację

1. Dodaj następującą instrukcję do głównej:

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. Naciśnij <kbd>klawisze CTRL</kbd>+<kbd>F5</kbd> , aby uruchomić projekt. Zostanie wyświetlony dokument programu Word zawierający określony tekst.

## <a name="to-change-the-text-to-a-table"></a>Aby zmienić tekst na tabelę
  
1. Użyj metody `ConvertToTable`, aby ująć tekst w tabeli. Metoda ma szesnaste parametry opcjonalne. Funkcja IntelliSense ujmuje opcjonalne parametry w nawiasach, jak pokazano na poniższej ilustracji.

     ![Lista parametrów dla metody ConvertToTable](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     Argumenty nazwane i opcjonalne umożliwiają określenie wartości tylko dla parametrów, które mają zostać zmienione. Dodaj następujący kod na końcu metody `DisplayInWord`, aby utworzyć prostą tabelę. Argument określa, że przecinki w ciągu tekstowym w `range` oddzielają komórki tabeli.

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     We wcześniejszych wersjach programu C#wywołanie `ConvertToTable` wymaga argumentu odwołania dla każdego parametru, jak pokazano w poniższym kodzie:
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. Naciśnij <kbd>klawisze CTRL</kbd>+<kbd>F5</kbd> , aby uruchomić projekt.

## <a name="to-experiment-with-other-parameters"></a>Aby eksperymentować z innymi parametrami

1. Aby zmienić tabelę tak, aby stała się jedną kolumną i trzema wierszami, Zastąp ostatni wiersz w `DisplayInWord` następującą instrukcją, a następnie wpisz <kbd>CTRL</kbd>+<kbd>F5</kbd>.  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. Aby określić wstępnie zdefiniowany format tabeli, Zastąp ostatni wiersz w `DisplayInWord` następującą instrukcją, a następnie wpisz <kbd>CTRL</kbd>+<kbd>F5</kbd>. Format może być dowolną ze stałych [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) .

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a>Przykład

Poniższy kod zawiera pełny przykład:

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a>Zobacz także

- [Argumenty nazwane i opcjonalne](./named-and-optional-arguments.md)
