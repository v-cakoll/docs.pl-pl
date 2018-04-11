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
`#line`Umożliwia modyfikowanie kompilatora numer wiersza i (opcjonalnie) Nazwa plik wyjściowy błędów i ostrzeżeń. W tym przykładzie przedstawiono sposób raportu dwóch ostrzeżenia skojarzony z numerów wierszy. `#line 200` Dyrektywy wymusza numer wiersza jako 200 (mimo że wartość domyślna to #7), a do czasu następnego dyrektywy #line, nazwa pliku będą raportowane jako "Special". #Line — dyrektywa domyślne zwraca numerowanie do jego numerowanie domyślne wierszy, które zlicza wiersze, które zostały oznaczenie w poprzedniej dyrektywie.  
  
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
 `#line` Dyrektywy mogą być używane w automatycznych, pośredniego kroku w procesie kompilacji. Na przykład, jeśli wiersze zostały usunięte z oryginalnego pliku kodu źródłowego, ale nadal potrzebujesz kompilatorowi Generowanie danych wyjściowych na podstawie wiersza oryginalnej numerowanie w pliku, możesz można usunąć wiersze i następnie symulować oryginalnego numerowania wierszy z `#line`.  
  
 `#line hidden` Dyrektywy ukrywa z kolejnych wierszy debugera, w taki sposób, że deweloper przechodzi przez kod, po dowolnej linii między `#line hidden` Następna `#line` — dyrektywa (przy założeniu, że nie jest on inny `#line hidden` dyrektywy) oparta na. Tej opcji można również umożliwić ASP.NET w celu rozróżnienia kod użytkownika i wygenerowane maszynowo. Mimo że program ASP.NET konsumenta podstawowej tej funkcji, najprawdopodobniej z niego korzystać więcej źródło, które wprowadzi generatory.  
  
 A `#line hidden` dyrektywy nie wpływa na nazwy plików lub numerów linii w raportowaniu błędów. Oznacza to w przypadku napotkania błędu w bloku ukryte, kompilator będzie zgłaszać bieżącego pliku nazwa i wiersz numer błędu.  
  
 `#line filename` Dyrektywa określa nazwę pliku, która ma być wyświetlana w danych wyjściowych kompilatora. Domyślnie używany jest rzeczywistą nazwą pliku kodu źródłowego. Nazwa pliku musi być w podwójny cudzysłów ("") i musi być poprzedzona numer wiersza.  
  
 Pliku kodu źródłowego może mieć dowolną liczbę `#line` dyrektywy.  
  
## <a name="example-1"></a>Przykład 1  
 W poniższym przykładzie pokazano, jak debuger ignoruje ukryte wiersze w kodzie. Po uruchomieniu przykładzie wyświetli trzy wiersze tekstu. Jednak gdy ustawić punkt przerwania, jak pokazano w przykładzie i trafień F10, aby wykonywać krokowo kodu, można zauważyć, że debuger ignoruje ukryte wiersza. Należy zauważyć, że nawet w przypadku ustawienia punktu przerwania w wierszu ukryte, debuger nadal zignoruje.  
  
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
