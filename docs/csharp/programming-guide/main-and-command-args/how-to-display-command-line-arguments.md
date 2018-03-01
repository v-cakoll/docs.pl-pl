---
title: "Porady: wyświetlanie argumentów wiersza poleceń (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6ae495eef227c6e4d9fb9ca0d4d0c031163fd52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Za pomocą wiersza polecenia z csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Porady: za pomocą argumentów wiersza polecenia dostępu instrukcji foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Main() — zwracane wartości](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
