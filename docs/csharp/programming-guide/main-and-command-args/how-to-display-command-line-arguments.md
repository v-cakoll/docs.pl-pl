---
title: Jak wyświetlić argumenty wiersza polecenia — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 210dad71220572535a0325fac925b0453b0d4e03
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712029"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Wyświetlanie argumentów wiersza polecenia (C# Przewodnik programowania)
Argumenty dostarczone do pliku wykonywalnego w wierszu polecenia są dostępne za pomocą opcjonalnego parametru do `Main`. Argumenty są podane w postaci tablicy ciągów. Każdy element tablicy zawiera jeden argument. Odstęp między argumentami jest usuwany. Rozważmy na przykład następujące wywołania wiersza polecenia fikcyjnego pliku wykonywalnego:  
  
|Dane wejściowe w wierszu polecenia|Tablica ciągów przeniesiona do głównej|  
|----------------------------|-------------------------------------|  
|**plik wykonywalny. exe a b c**|z<br /><br /> b<br /><br /> s|  
|**plik wykonywaln. exe 1 2**|je<br /><br /> tymi|  
|**wykonywalny. exe "1 2" trzy**|„one two”<br /><br /> trzecim|  
  
> [!NOTE]
> W przypadku uruchamiania aplikacji w programie Visual Studio, można określić argumenty wiersza polecenia na [stronie debugowanie, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Przykład  
 Ten przykład wyświetla argumenty wiersza polecenia przekazane do aplikacji wiersza polecenia. Wyświetlane dane wyjściowe dotyczą pierwszego wpisu w powyższej tabeli.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Main() i argumenty wiersza polecenia](./index.md)
- [Main() — zwracane wartości](./main-return-values.md)
