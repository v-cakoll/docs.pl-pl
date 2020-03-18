---
title: Jak wyświetlić argumenty wiersza polecenia - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 210dad71220572535a0325fac925b0453b0d4e03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712029"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Jak wyświetlić argumenty wiersza polecenia (Przewodnik programowania C#)
Argumenty dostarczone do pliku wykonywalnego w wierszu polecenia są dostępne za pośrednictwem opcjonalnego parametru . `Main` Argumenty są dostarczane w postaci tablicy ciągów. Każdy element tablicy zawiera jeden argument. Odstęp między argumentami jest usuwany. Rozważmy na przykład te wywołania wiersza polecenia fikcyjnego pliku wykonywalnego:  
  
|Wejście w wierszu polecenia|Tablica ciągów przekazywanych do Main|  
|----------------------------|-------------------------------------|  
|**executable.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe jeden dwa**|"jeden"<br /><br /> "dwa"|  
|**executable.exe "jeden dwa" trzy**|„one two”<br /><br /> "trzy"|  
  
> [!NOTE]
> Podczas uruchamiania aplikacji w programie Visual Studio można określić argumenty wiersza polecenia na [stronie debugowania, projektancie projektów](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyświetlane są argumenty wiersza polecenia przekazane do aplikacji wiersza polecenia. Dane wyjściowe są dla pierwszego wpisu w powyższej tabeli.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Kompilacja za pomocą wiersza polecenia przy użyciu csc.exe](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Main() i argumenty wiersza polecenia](./index.md)
- [Main() — zwracane wartości](./main-return-values.md)
