---
title: '#wiersz (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: f3ebecda7761e6249656e0b9f8543ae1252b844e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43395140"
---
# <a name="line-c-reference"></a>#line (odwołanie w C#)
`#line` Umożliwia modyfikowanie kompilatora numerowanie wierszy i (opcjonalnie) danymi wyjścia nazwy pliku, błędów i ostrzeżeń.

Poniższy przykład pokazuje, jak zgłosić dwa ostrzeżenia skojarzony z numerami wierszy. `#line 200` Dyrektywy wymusza numer następny wiersz jako 200 (mimo że wartość domyślna to #6) i aż do następnego dyrektywy #line, nazwa pliku będą raportowane jako "Specjalne". Dyrektywa #line domyślnie zwraca numerowanie wierszy w wersji domyślnej, czyli zlicza wiersze, które zostały ponumerowane przez poprzednią dyrektywę.  
  
```csharp
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;
        int j;
#line default  
        char c;
        float f;
#line hidden // numbering not affected  
        string s;   
        double d;
    }  
}  
```  
Kompilacja generuje następujące wyniki:

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a>Uwagi  
 Dyrektywa `#line` może być używana w automatycznym, pośrednim etapie procesu kompilacji. Na przykład jeśli z oryginalnego pliku kodu źródłowego zostały usunięte wiersze, ale kompilator nadal ma generować dane wyjściowe na podstawie oryginalnego numerowania wierszy w pliku, możesz usunąć wiersze i zasymulować oryginalne numerowanie za pomocą dyrektywy `#line`.  
  
 Dyrektywa `#line hidden` ukrywa kolejne wiersze przed debugerem, w taki sposób, że podczas wykonywania kodu przez dewelopera wszystkie wiersze między dyrektywą `#line hidden` a następną dyrektywą `#line` (przy założeniu, że nie będzie to kolejna dyrektywa `#line hidden`) zostaną pominięte. Ta opcja pozwala także platformie ASP.NET odróżnić kod zdefiniowany przez użytkownika od kodu wygenerowanego maszynowo. Mimo że funkcja ta jest używana głównie w ASP.NET, to prawdopodobne jest, że będzie z niej korzystać więcej generatorów kodu źródłowego.  
  
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

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
