---
title: 'Instrukcje: Wyświetlanie argumentów wiersza polecenia — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 030fd2bd3286bd4f25513e26b3de9e87eaee9029
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588897"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Instrukcje: Wyświetlanie argumentów wiersza polecenia (C# Przewodnik programowania)
Argumenty dostarczone do pliku wykonywalnego w wierszu polecenia są dostępne za pomocą opcjonalnego parametru do `Main`. Argumenty są podane w postaci tablicy ciągów. Każdy element tablicy zawiera jeden argument. Odstęp między argumentami jest usuwany. Rozważmy na przykład następujące wywołania wiersza polecenia fikcyjnego pliku wykonywalnego:  
  
|Dane wejściowe w wierszu polecenia|Tablica ciągów przeniesiona do głównej|  
|----------------------------|-------------------------------------|  
|**plik wykonywalny. exe a b c**|z<br /><br /> b<br /><br /> s|  
|**plik wykonywaln. exe 1 2**|je<br /><br /> tymi|  
|**wykonywalny. exe "1 2" trzy**|„one two”<br /><br /> trzecim|  
  
> [!NOTE]
>  W przypadku uruchamiania aplikacji w programie Visual Studio, można określić argumenty wiersza polecenia na [stronie debugowanie, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Przykład  
 Ten przykład wyświetla argumenty wiersza polecenia przekazane do aplikacji wiersza polecenia. Wyświetlane dane wyjściowe dotyczą pierwszego wpisu w powyższej tabeli.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Main() i argumenty wiersza polecenia](./index.md)
- [Main() — zwracane wartości](./main-return-values.md)
