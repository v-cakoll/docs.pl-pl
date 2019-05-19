---
title: 'Instrukcje: Wyświetlanie argumentów wiersza polecenia — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: c88219d03d40c814338a1b09ccd37cfc03c2d577
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881015"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Instrukcje: Wyświetlanie argumentów wiersza poleceń (C# Programming Guide)
Argumenty dostarczone do pliku wykonywalnego w wierszu polecenia są dostępne za pośrednictwem opcjonalny parametr do `Main`. Argumenty są udostępniane w formie tablicy ciągów. Każdy element tablicy zawiera jeden argument. Odstępy między argumentami zostaną usunięte. Na przykład należy wziąć pod uwagę te wywołania wiersza polecenia fikcyjne pliku wykonywalnego:  
  
|Dane wejściowe w wiersza polecenia|Tablica ciągów przekazywane dla metody Main|  
|----------------------------|-------------------------------------|  
|**executable.exe b c.**|""<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe jeden dwa**|"jeden"<br /><br /> "dwóch"|  
|**executable.exe "jeden dwa" trzy**|„one two”<br /><br /> "trzy"|  
  
> [!NOTE]
>  Po uruchomieniu aplikacji w programie Visual Studio, można określić argumenty wiersza poleceń w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Przykład  
 Ten przykład wyświetla argumenty wiersza polecenia przekazywane do wiersza polecenia aplikacji. Jest wyświetlone dane wyjściowe do pierwszej pozycji w powyższej tabeli.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md)
- [Main() — zwracane wartości](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
