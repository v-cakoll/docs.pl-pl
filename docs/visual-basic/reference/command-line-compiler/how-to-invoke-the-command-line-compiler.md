---
title: 'Instrukcje: Wywoływanie kompilatora wiersza polecenia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: d2d193f8c3d483ff87fe719919982e8c3473ec0b
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221846"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>Instrukcje: Wywoływanie kompilatora wiersza polecenia (Visual Basic)
Można wywołać kompilatora wiersza polecenia, wpisując nazwę jego pliku wykonywalnego do wiersza polecenia, znany także jako wiersz systemu MS-DOS. Jeśli kompilujesz w wierszu polecenia Windows domyślnej, należy wpisać w pełni kwalifikowana ścieżka do pliku wykonywalnego. Aby zastąpić to zachowanie domyślne, można użyć wiersza polecenia dewelopera dla programu Visual Studio lub zmodyfikować zmiennej środowiskowej PATH. Obie umożliwiają kompilowanie z dowolnego katalogu, po prostu wpisując nazwę kompilatora.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>Aby wywołać kompilatora przy użyciu wiersza polecenia dla deweloperów programu Visual Studio  
  
1.  Otwórz folder programu Visual Studio Tools w obrębie grupy programu Microsoft Visual Studio.  
  
2.  Jeśli zainstalowano program Visual Studio, można użyć wiersza polecenia dewelopera dla programu Visual Studio dostęp do kompilatora z dowolnego katalogu na komputerze.  
  
3.  Wywołaj wiersz polecenia programisty dla programu Visual Studio.  
  
4.  W wierszu polecenia wpisz polecenie `vbc.exe` *sourceFileName* i naciśnij klawisz ENTER.  
  
     Na przykład, jeśli kod źródłowy jest przechowywany w katalogu o nazwie `SourceFiles`, czy otworzyć wiersz polecenia i wpisz `cd SourceFiles` zmiany do tego katalogu. Jeśli katalog zawiera plik źródłowy o nazwie `Source.vb`, można go skompilować, wpisując `vbc.exe Source.vb`.  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Aby ustawić zmiennej środowiskowej PATH kompilatora wiersza polecenia dla Windows  
  
1.  Użyj funkcji Windows Search, aby znaleźć Vbc.exe na dysku lokalnym.  
  
     Dokładną nazwę katalogu, w którym znajduje się kompilator zależy od tego, lokalizację katalogu Windows i wersji "Systemu.NET Framework". Jeśli masz więcej niż jedna wersja "Systemu.NET Framework", musisz określić wyborze wersji do użycia (zwykle najnowszą).  
  
2.  Z usługi **Start** Menu, kliknij prawym przyciskiem myszy **Mój komputer**, a następnie kliknij przycisk **właściwości** z menu skrótów.  
  
3.  Kliknij przycisk **zaawansowane** kartę, a następnie kliknij przycisk **zmienne środowiskowe**.  
  
4.  W **systemu** Okienko zmiennych, wybierz opcję **ścieżki** z listy i kliknij przycisk **Edytuj**.  
  
5.  W **edycji systemu** okno dialogowe zmiennej, przesuń punkt wstawiania do końca ciągu w **wartość zmiennej** pola, a następnie wpisz je średnikiem (;) następuje nazwa pełny katalog, w kroku 1.  
  
6.  Kliknij przycisk **OK** aby potwierdzić zmiany i zamknąć okno dialogowe.  
  
     Po zmianie zmiennej środowiskowej PATH, można uruchomić kompilator Visual Basic w wierszu polecenia Windows z dowolnego katalogu na komputerze.  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Aby wywołać kompilatora przy użyciu wiersza polecenia Windows  
  
1.  Z **Start** menu, kliknij pozycję **Akcesoria** folder, a następnie otwórz **wiersza polecenia Windows**.  
  
2.  W wierszu polecenia wpisz polecenie `vbc.exe` *sourceFileName* i naciśnij klawisz ENTER.  
  
     Na przykład, jeśli kod źródłowy jest przechowywany w katalogu o nazwie `SourceFiles`, czy otworzyć wiersz polecenia i wpisz `cd SourceFiles` zmiany do tego katalogu. Jeśli katalog zawiera plik źródłowy o nazwie `Source.vb`, można go skompilować, wpisując `vbc.exe Source.vb`.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja warunkowa](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
