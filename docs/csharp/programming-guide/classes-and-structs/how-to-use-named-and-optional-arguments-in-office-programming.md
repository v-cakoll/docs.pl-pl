---
title: Jak używać nazwanych i opcjonalnych argumentów w programowaniu pakietu Office — Przewodnik po programowaniu języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 36b5c8b49404606c8240d24953c3677d5612d30e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714873"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a>Jak używać nazwanych i opcjonalnych argumentów w programowaniu pakietu Office (Przewodnik po programowaniu języka C#)

Nazwane argumenty i opcjonalne argumenty, wprowadzone w języku C# 4, zwiększają wygodę, elastyczność i czytelność w programowaniu języka C#. Ponadto te funkcje znacznie ułatwiają dostęp do interfejsów COM, takich jak interfejsy API automatyzacji pakietu Microsoft Office.

W poniższym przykładzie metoda [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) ma szesnaście parametrów reprezentujących cechy tabeli, takie jak liczba kolumn i wierszy, formatowanie, obramowania, czcionki i kolory. Wszystkie szesnaście parametrów są opcjonalne, ponieważ przez większość czasu nie chcesz określać określonych wartości dla wszystkich z nich. Jednak bez nazwanych i opcjonalnych argumentów należy podać wartość lub wartość zastępczą dla każdego parametru. W przypadku argumentów nazwanych i opcjonalnych można określić wartości tylko dla parametrów, które są wymagane dla projektu.

Aby wykonać te procedury, na komputerze musi być zainstalowany program Microsoft Office Word.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a>Aby utworzyć nową aplikację konsoli

1. Uruchom program Visual Studio.

2. W menu **Plik** wskaż polecenie **Nowy**, a następnie kliknij polecenie **Projekt**.

3. W okienku **Kategorie szablonów** rozwiń węzeł **Visual C#,** a następnie kliknij pozycję **Windows**.

4. Spójrz w górnej części **okienka szablony,** aby upewnić się, że **.NET Framework 4** pojawia się w polu **Platforma docelowa.**

5. W okienku **Szablony** kliknij pozycję **Aplikacja konsoli**.

6. Wpisz nazwę projektu w polu **Nazwa.**

7. Kliknij przycisk **OK**.

     Nowy projekt pojawi się w **Eksploratorze rozwiązań**.

## <a name="to-add-a-reference"></a>Aby dodać odwołanie

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij polecenie **Dodaj odwołanie**. Pojawi się okno dialogowe **Dodawanie odwołania.**

2. Na stronie **.NET** wybierz pozycję **Microsoft.Office.Interop.Word** na liście **Nazwa składnika.**

3. Kliknij przycisk **OK**.

## <a name="to-add-necessary-using-directives"></a>Aby dodać niezbędne za pomocą dyrektyw

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy plik *Program.cs,* a następnie kliknij polecenie **Wyświetl kod**.

2. Dodaj następujące `using` dyrektywy do górnej części pliku kodu:

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a>Aby wyświetlić tekst w dokumencie programu Word

1. W `Program` klasie w *Program.cs*dodaj następującą metodę tworzenia aplikacji programu Word i dokumentu programu Word. [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) Metoda ma cztery parametry opcjonalne. W tym przykładzie użyto ich wartości domyślnych. W związku z tym nie są konieczne żadne argumenty w instrukcji wywołującej.

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. Dodaj następujący kod na końcu metody, aby określić, gdzie ma być wyświetlany tekst w dokumencie i jaki tekst ma być wyświetlany:

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a>Aby uruchomić aplikację

1. Dodaj następującą instrukcję do Main:

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. Naciśnij <kbd>klawisz ctrl</kbd>+<kbd>f5,</kbd> aby uruchomić projekt. Zostanie wyświetlony dokument programu Word zawierający określony tekst.

## <a name="to-change-the-text-to-a-table"></a>Aby zmienić tekst na tabelę
  
1. Użyj `ConvertToTable` metody, aby ująć tekst w tabeli. Metoda ma szesnaście parametrów opcjonalnych. IntelliSense ujmuje opcjonalne parametry w nawiasy, jak pokazano na poniższej ilustracji.

     ![Lista parametrów metody ConvertToTable](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     Argumenty nazwane i opcjonalne umożliwiają określenie wartości tylko dla parametrów, które mają zostać zmienione. Dodaj następujący kod na końcu `DisplayInWord` metody, aby utworzyć prostą tabelę. Argument określa, że przecinki w `range` ciągu tekstowym w oddzielnych komórkach tabeli.

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     We wcześniejszych wersjach języka C#, wywołanie `ConvertToTable` wymaga argumentu odwołania dla każdego parametru, jak pokazano w następującym kodzie:
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. Naciśnij <kbd>klawisz ctrl</kbd>+<kbd>f5,</kbd> aby uruchomić projekt.

## <a name="to-experiment-with-other-parameters"></a>Aby eksperymentować z innymi parametrami

1. Aby zmienić tabelę tak, aby była ona zgodna `DisplayInWord` z jedną kolumną i trzema wierszami, należy zastąpić ostatni wiersz następującą instrukcją, a następnie <kbd>wpisz klawiszctrl</kbd>+<kbd>f5</kbd>.  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. Aby określić wstępnie zdefiniowany format tabeli, zamień ostatni wiersz `DisplayInWord` na następującą instrukcję, a następnie <kbd>wpisz klawiszctrl</kbd>+<kbd>f5</kbd>. Format może być dowolną ze stałych [WdTableFormat.](<xref:Microsoft.Office.Interop.Word.WdTableFormat>)

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a>Przykład

Poniższy kod zawiera pełny przykład:

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a>Zobacz też

- [Argumenty nazwane i opcjonalne](./named-and-optional-arguments.md)
