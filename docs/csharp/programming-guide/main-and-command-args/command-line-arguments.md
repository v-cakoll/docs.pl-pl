---
title: Argumenty wiersza poleceń (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: ccfac6bd2688a2e02a1b3fcc14748d357acb1aa2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43464340"
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
  
 Aby uzyskać więcej przykładów użycia argumentów wiersza polecenia, zobacz [jak: utworzyć i używać zestawów przy użyciu wiersza polecenia](https://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Environment?displayProperty=nameWithType>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Main() i argumenty wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Instrukcje: wyświetlanie argumentów wiersza polecenia](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [Instrukcje: uzyskiwanie dostępu do argumentów wiersza polecenia za pomocą instrukcji foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Main() — zwracane wartości](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)  
 [Klasy](../../../csharp/programming-guide/classes-and-structs/classes.md)
