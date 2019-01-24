---
title: Argumenty wiersza polecenia — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: 32dcfc8da52fc623473a1cc234e710463f8d28be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722702"
---
# <a name="command-line-arguments-c-programming-guide"></a>Argumenty wiersza poleceń (Przewodnik programowania w języku C#)
Możesz wysyłać argumenty do `Main` metoda definiując metodę na jeden z następujących sposobów:  
  
 [!code-csharp[csProgGuideMain#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_1.cs)]  
  
 [!code-csharp[csProgGuideMain#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_2.cs)]  
  
> [!NOTE]
>  Aby włączyć argumenty wiersza poleceń w `Main` metody w aplikacji Windows Forms, należy ręcznie zmodyfikować podpis `Main` w pliku program.cs. Kod wygenerowany przez projektanta Windows Forms tworzy `Main` bez parametru wejściowego. Można również użyć <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> lub <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> dostęp do argumentów wiersza polecenia z dowolnego punktu w konsoli lub aplikacji Windows.  
  
 Wartość parametru `Main` metodą jest <xref:System.String> tablica reprezentująca argumenty wiersza polecenia. Zwykle określasz, czy argumenty istnieją testując `Length` właściwości, na przykład:  
  
 [!code-csharp[csProgGuideMain#4](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_3.cs)]  
  
 Możesz również konwertować argumenty ciągu na typy liczbowe, za pomocą <xref:System.Convert> klasy lub `Parse` metody. Na przykład następująca instrukcja konwertuje `string` do `long` numeru przy użyciu <xref:System.Int64.Parse%2A> metody:  
  
```  
long num = Int64.Parse(args[0]);  
```  
  
 Istnieje również możliwość użycia typu C# `long`, którego aliasy `Int64`:  
  
```  
long num = long.Parse(args[0]);  
```  
  
 Można również użyć `Convert` metody klasy `ToInt64` aby zrobić to samo:  
  
```  
long num = Convert.ToInt64(s);  
```  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.Int64.Parse%2A> i <xref:System.Convert>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać argumentów wiersza polecenia w aplikacji konsoli. Aplikacja przyjmuje jeden argument w czasie wykonywania, konwertuje argument na liczbę całkowitą i oblicza silnię liczby. Jeśli zostały dostarczone żadne argumenty, aplikacja wyświetli komunikat, który objaśnia poprawne użycie programu.  
  
 Aby skompilować i uruchomić aplikację z poziomu wiersza polecenia, wykonaj następujące kroki:  
  
1.  Wklej następujący kod do dowolnego edytora tekstów, a następnie zapisz plik jako plik tekstowy o nazwie `Factorial.cs`.  
  
     [!code-csharp[csProgGuideMain#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_4.cs)]  
  
2.  Z **Start** ekranu lub **Start** menu, Otwórz program Visual Studio **wiersz polecenia dla deweloperów** okna, a następnie przejdź do folderu, który zawiera plik, który został właśnie utworzony.  
  
3.  Wprowadź następujące polecenie, aby skompilować aplikację.  
  
     `csc Factorial.cs`  
  
     Jeśli aplikacja nie ma żadnych błędów kompilacji, plik wykonywalny, który nosi nazwę `Factorial.exe` zostanie utworzony.  
  
4.  Wprowadź następujące polecenie, aby obliczyć silnię 3:  
  
     `Factorial 3`  
  
5.  Polecenie generuje dane wyjściowe: `The factorial of 3 is 6.`  
  
> [!NOTE]
>  Podczas uruchamiania aplikacji w programie Visual Studio, można określić argumenty wiersza poleceń w [strona debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
 Aby uzyskać więcej przykładów użycia argumentów wiersza polecenia, zobacz [jak: Tworzenie i używanie zestawów przy użyciu wiersza polecenia](../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Environment?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md)
- [Instrukcje: Wyświetlanie argumentów wiersza poleceń](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Instrukcje: Dostęp do argumentów wiersza polecenia za pomocą foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
- [Main() — zwracane wartości](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
- [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)
