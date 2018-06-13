---
title: 'Porady: wyświetlanie argumentów wiersza poleceń (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 7b9e488e84c78c8fdbf64431f42ea5797fdca916
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334139"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Porady: wyświetlanie argumentów wiersza poleceń (Przewodnik programowania w języku C#)
Argumenty przekazane do pliku wykonywalnego w wierszu polecenia są dostępne za pośrednictwem opcjonalny parametr do `Main`. Argumenty są udostępniane w formie tablicy ciągów. Każdy element tablicy zawiera jeden argument. Odstępu między argumentami zostaną usunięte. Rozważmy na przykład tych wywołań wiersza polecenia fikcyjne pliku wykonywalnego:  
  
|Wprowadź w wierszu polecenia|Tablica ciągów przekazana dla metody Main|  
|----------------------------|-------------------------------------|  
|**executable.exe b c**|""<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe jeden dwa**|"jeden"<br /><br /> "dwa"|  
|**executable.exe "jeden dwa" trzy**|„one two”<br /><br /> "3"|  
  
> [!NOTE]
>  Po uruchomieniu aplikacji w programie Visual Studio, można określić argumentów wiersza polecenia w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyświetlono argumenty wiersza polecenia przekazywane do wiersza polecenia aplikacji. Dane wyjściowe pokazano to pierwszy wpisu w powyższej tabeli.  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Instrukcje: uzyskiwanie dostępu do argumentów wiersza polecenia za pomocą instrukcji foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Main() — zwracane wartości](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
