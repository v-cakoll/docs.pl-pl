---
title: '#wiersz (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d2f42915d214349eebff40949482d7f603c0c2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="line-c-reference"></a>#line (odwołanie w C#)
`#line`Umożliwia modyfikowanie numerów wiersy kompilatora i (opcjonalnie) nazwy plików wyjściowych błędów i ostrzeżeń. W tym przykładzie przedstawiono sposób raportu dwóch ostrzeżeń skojarzonych z numerami wierszy. Dyrektywa `#line 200` wymusza numer wiersza do bycia 200 (mimo że wartość domyślna to #7), i do czasu następnej dyrektywy #line, zgłaszaną nazwą pliku będzie "Special". Dyrektywa #Line  domyślnie zwraca numerowanie wierszy w domyślnej numeracji, która zlicza wiersze, które zostały oznaczone przez poprzednią dyrektywę.  
  
```csharp
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;    // CS0168 on line 200  
        int j;    // CS0168 on line 201  
#line default  
        char c;   // CS0168 on line 9  
        float f;  // CS0168 on line 10  
#line hidden // numbering not affected  
        string s;   
        double d; // CS0168 on line 13  
    }  
}  
```  
  
## <a name="remarks"></a>Uwagi  
 Dyrektywy `#line` mogą być używane w automatycznych, pośrednich krokach w procesie kompilacji. Na przykład, jeśli wiersze zostały usunięte z oryginalnego pliku kodu źródłowego, ale nadal chcesz aby kompilator generował dane wyjściowe oparte na oryginalnym numerowaniu wierszy w pliku, możesz usunąć wiersze i symulować oryginalne numerowanie za pomocą `#line`.  
  
Dyrektywa `#line hidden` ukrywa kolejne wiersze debugera, w taki sposób, że wszystkie linie przez które przejdzie krokowo deweloper, a dokładnie te między wierszami po `#line hidden` oraz następną dyrektywą `#line` (przy założeniu, że nie jest ona kolejną dyrektywą `#line hidden`) zostaną przeskoczone. Ta opcja może zostać użyta w celu umożliwienia ASP.NET odróżnienia kodu zdefiniowanego przez użytkownika oraz maszynę. Mimo że fukcja ta jest używana głównie w ASP.NET , to prawdopodobne jest że będzie z niej korzystać więcej generatorów źródel.  
  
 Dyrektywa `#line hidden` nie wpływa na nazwy plików lub numerów linii w raportowaniu błędów. Oznacza to, że w przypadku napotkania błędu w ukrytym bloku, kompilator zgłosi obecną nazwę pliku oraz numer wiersza, w którym wystąpił błąd.  
  
Dyrektywa `#line filename` określa nazwę pliku, która ma być wyświetlana w danych wyjściowych kompilatora. Domyślnie używana jest rzeczywista nazwa pliku kodu źródłowego. Nazwa pliku musi być ujęta w podwójny cudzysłów ("") oraz musi być poprzedzona numerem wiersza.  
  
 Plik kodu źródłowego może mieć dowolną liczbę wystąpeń dyrektywy `#line`.  
  
## <a name="example-1"></a>Przykład 1  
 W poniższym przykładzie pokazano, jak debuger ignoruje ukryte wiersze w kodzie. Po uruchomieniu przykładu wyświetli trzy wiersze tekstu. Jednak, gdy ustawisz punkt przerwania, jak pokazano w przykładzie i wciśniesz F10, aby wykonywać kod krokami, możesz zauważyć, że debuger zignoruje ukryte wiersze. Należy zauważyć, że nawet w przypadku ustawienia punktu przerwania w ukrytym wieszu, debuger nadal go zignoruje.  
  
```csharp
// preprocessor_linehidden.cs  
using System;  
class MainClass   
{  
    static void Main()   
    {  
        Console.WriteLine("Normal line #1."); // Set break point here.  
#line hidden  
        Console.WriteLine("Hidden line.");  
#line default  
        Console.WriteLine("Normal line #2.");  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
