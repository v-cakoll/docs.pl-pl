---
title: 'Instrukcje: Wywoływanie kompilatora wiersza polecenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: a81d5b4f4eae76b0306e2d27475cb8527bda0ff2
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054218"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>Instrukcje: Wywoływanie kompilatora wiersza polecenia (Visual Basic)

Kompilator wiersza polecenia można wywołać, wpisując nazwę pliku wykonywalnego w wierszu polecenia, znanego również jako monit MS-DOS. Jeśli kompilujesz z domyślnego wiersza polecenia systemu Windows, musisz wpisać w pełni kwalifikowaną ścieżkę do pliku wykonywalnego. Aby zastąpić to zachowanie domyślne, można użyć wiersz polecenia dla deweloperów dla programu Visual Studio lub zmodyfikować zmienną środowiskową PATH. Oba umożliwiają kompilowanie z dowolnego katalogu przez wpisanie nazwy kompilatora.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>Aby wywołać kompilator przy użyciu wiersz polecenia dla deweloperów dla programu Visual Studio

1. Otwórz folder programu Visual Studio Tools w grupie programów Microsoft Visual Studio.

2. Możesz użyć wiersz polecenia dla deweloperów dla programu Visual Studio, aby uzyskać dostęp do kompilatora z dowolnego katalogu na komputerze, jeśli jest zainstalowany program Visual Studio.

3. Wywołaj wiersz polecenia dla deweloperów dla programu Visual Studio.

4. W wierszu polecenia wpisz `vbc.exe` *sourceFileName* , a następnie naciśnij klawisz ENTER.

    Na przykład jeśli kod źródłowy został zapisany w katalogu o nazwie `SourceFiles`, należy otworzyć wiersz polecenia i wpisać `cd SourceFiles` zmiany w tym katalogu. Jeśli katalog zawiera plik źródłowy o nazwie `Source.vb`, można go skompilować, wpisując. `vbc.exe Source.vb`

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Aby ustawić zmienną środowiskową PATH na kompilator dla wiersza polecenia systemu Windows

1. Użyj funkcji wyszukiwania systemu Windows, aby znaleźć VBC. exe na dysku lokalnym.

    Dokładna nazwa katalogu, w którym znajduje się kompilator, zależy od lokalizacji katalogu systemu Windows i zainstalowanej wersji programu ".NET Framework". Jeśli masz zainstalowaną więcej niż jedną wersję ".NET Framework", musisz określić, która wersja ma być używana (zazwyczaj Najnowsza wersja).

2. W menu **Start** kliknij prawym przyciskiem myszy pozycję **mój komputer**, a następnie kliknij polecenie **Właściwości** w menu skrótów.

3. Kliknij kartę **Zaawansowane** , a następnie kliknij pozycję **zmienne środowiskowe**.

4. W okienku zmienne **systemowe** wybierz pozycję **ścieżka** z listy, a następnie kliknij pozycję **Edytuj**.

5. W oknie dialogowym **Edycja zmiennej systemowej** przesuń punkt wstawiania do końca ciągu w polu **wartość zmiennej** i wpisz średnika (;) a następnie pełna nazwa katalogu znaleziona w kroku 1.

6. Kliknij przycisk **OK** , aby potwierdzić zmiany i zamknąć okna dialogowe.

     Po zmianie zmiennej środowiskowej PATH można uruchomić kompilator Visual Basic w wierszu polecenia systemu Windows z dowolnego katalogu na komputerze.

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Aby wywołać kompilator przy użyciu wiersza polecenia systemu Windows

1. W menu **Start** kliknij folder **akcesoria** , a następnie otwórz **wiersz polecenia systemu Windows**.

2. W wierszu polecenia wpisz `vbc.exe` *sourceFileName* , a następnie naciśnij klawisz ENTER.

     Na przykład jeśli kod źródłowy został zapisany w katalogu o nazwie `SourceFiles`, należy otworzyć wiersz polecenia i wpisać `cd SourceFiles` zmiany w tym katalogu. Jeśli katalog zawiera plik źródłowy o nazwie `Source.vb`, można go skompilować, wpisując. `vbc.exe Source.vb`

## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
