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
Dyrektywa `#line` umożliwia modyfikowanie numerów wierszy kompilatora i (opcjonalnie) danych wyjściowych nazw plików pod kątem błędów i ostrzeżeń. W tym przykładzie przedstawiono sposób zgłaszania dwóch ostrzeżeń skojarzonych z numerami wierszy. Dyrektywa `#line 200` wymusza numer wiersza o wartości 200 (mimo że wartość domyślna to #7), przez co do momentu aktywowania następnej dyrektywy #line zgłaszaną nazwą pliku będzie „Special”. Dyrektywa #line domyślnie zwraca numerowanie wierszy w wersji domyślnej, czyli zlicza wiersze, które zostały ponumerowane przez poprzednią dyrektywę. 
  
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
 Dyrektywa `#line` może być używana w automatycznym, pośrednim etapie procesu kompilacji. Na przykład jeśli z oryginalnego pliku kodu źródłowego zostały usunięte wiersze, ale kompilator nadal ma generować dane wyjściowe na podstawie oryginalnego numerowania wierszy w pliku, możesz usunąć wiersze i zasymulować oryginalne numerowanie za pomocą dyrektywy `#line`.
  
Dyrektywa `#line hidden` ukrywa kolejne wiersze przed debugerem, w taki sposób, że podczas wykonywania kodu przez dewelopera wszystkie wiersze między dyrektywą `#line hidden` a następną dyrektywą `#line` (przy założeniu, że nie będzie to kolejna dyrektywa `#line hidden`) zostaną pominięte. Ta opcja pozwala także platformie ASP.NET odróżnić kod zdefiniowany przez użytkownika od kodu wygenerowanego maszynowo. Mimo że funkcja ta jest używana głównie w ASP.NET , to prawdopodobne jest, że będzie z niej korzystać więcej generatorów kodu źródłowego.
  
 Dyrektywa `#line hidden` nie wpływa na nazwy plików ani numery wierszy w raportowaniu błędów. Oznacza to, że w przypadku napotkania błędu w ukrytym bloku kompilator zgłosi obecną nazwę pliku oraz numer wiersza, w którym wystąpił błąd. 
  
Dyrektywa `#line filename` określa nazwę pliku, która ma być wyświetlana w danych wyjściowych kompilatora. Domyślnie używana jest rzeczywista nazwa pliku kodu źródłowego. Nazwa pliku musi być ujęta w podwójny cudzysłów ("") oraz musi być poprzedzona numerem wiersza.  
  
 Plik kodu źródłowego może mieć dowolną liczbę wystąpeń dyrektywy `#line`.  
  
## <a name="example-1"></a>Przykład 1  
 W poniższym przykładzie pokazano, jak debuger ignoruje ukryte wiersze w kodzie. Po uruchomieniu przykładu zostaną wyświetlone trzy wiersze tekstu. Jednak gdy ustawisz punkt przerwania (jak pokazano w przykładzie) i naciśniesz klawisz F10, aby wykonywać kod krokowo, zobaczysz, że debuger zignoruje ukryty wiersz. Nawet jeśli ustawisz punkt przerwania w ukrytym wierszu, debuger go zignoruje. 
  
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
