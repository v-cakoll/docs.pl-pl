---
title: "Argumenty wiersza poleceń (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 025ed2c451c0a657ce71db56df603302097fc7ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="command-line-arguments-c-programming-guide"></a>Argumenty wiersza poleceń (Przewodnik programowania w języku C#)
Możesz wysłać argumenty `Main` metody, definiując metody w jednym z następujących sposobów:  
  
 [!code-csharp[csProgGuideMain#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_1.cs)]  
  
 [!code-csharp[csProgGuideMain#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_2.cs)]  
  
> [!NOTE]
>  Aby włączyć argumenty wiersza polecenia w `Main` metody w aplikacji formularzy systemu Windows, należy ręcznie zmodyfikować podpis `Main` w pliku program.cs. Kod wygenerowany przez projektanta formularzy systemu Windows tworzy `Main` bez parametru wejściowego. Można również użyć <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> lub <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> dostępu do argumentów wiersza polecenia w dowolnym momencie w konsoli lub w aplikacji systemu Windows.  
  
 Parametr `Main` jest metoda <xref:System.String> tablica, która reprezentuje argumenty wiersza polecenia. Zazwyczaj można stwierdzić, czy argumenty testując `Length` właściwości, na przykład:  
  
 [!code-csharp[csProgGuideMain#4](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_3.cs)]  
  
 Argumenty ciągu można przekonwertować na typy liczbowe, za pomocą <xref:System.Convert> klasy lub `Parse` metody. Na przykład następująca instrukcja konwertuje `string` do `long` numeru przy użyciu <xref:System.Int64.Parse%2A> metody:  
  
```  
long num = Int64.Parse(args[0]);  
```  
  
 Istnieje również możliwość użycia typu C# `long`, które aliasy `Int64`:  
  
```  
long num = long.Parse(args[0]);  
```  
  
 Można również użyć `Convert` metoda klasy `ToInt64` do tak samo postąpić:  
  
```  
long num = Convert.ToInt64(s);  
```  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Int64.Parse%2A> i <xref:System.Convert>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie argumentów wiersza polecenia w aplikacji konsoli. Aplikacja pobiera jeden argument w czasie wykonywania, konwertuje argument na liczbę całkowitą i oblicza silnię liczby. Jeśli nie jest dostarczony bez argumentów, aplikacja wyświetla komunikat o opisujące prawidłowe użycie programu.  
  
 Aby skompilować i uruchomić aplikację w wierszu polecenia, wykonaj następujące kroki:  
  
1.  Wklej następujący kod w edytorze tekstu, a następnie zapisz plik jako plik tekstowy o nazwie `Factorial.cs`.  
  
     [!code-csharp[csProgGuideMain#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_4.cs)]  
  
2.  Z **Start** ekranu lub **Start** menu, Otwórz program Visual Studio **wiersza polecenia dewelopera** okna, a następnie przejdź do folderu, który zawiera plik, który został właśnie utworzony.  
  
3.  Wprowadź następujące polecenie, aby skompilować aplikację.  
  
     `csc Factorial.cs`  
  
     Jeśli aplikacja nie ma błędów kompilacji, plik wykonywalny o nazwie `Factorial.exe` jest tworzony.  
  
4.  Wprowadź następujące polecenie, aby obliczyć silnię liczby 3:  
  
     `Factorial 3`  
  
5.  Polecenie powoduje te dane wyjściowe:`The factorial of 3 is 6.`  
  
> [!NOTE]
>  Podczas uruchamiania aplikacji w programie Visual Studio, można określić argumentów wiersza polecenia w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
 Więcej przykładów na temat używania argumentów wiersza polecenia, zobacz [porady: tworzenie i użyj zestawów przy użyciu wiersza polecenia](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Environment?displayProperty=nameWithType>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Porady: wyświetlanie argumentów wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [Porady: za pomocą argumentów wiersza polecenia dostępu instrukcji foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Main() — zwracane wartości](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)  
 [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)
