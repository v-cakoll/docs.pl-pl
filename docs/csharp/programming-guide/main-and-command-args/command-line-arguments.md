---
title: Argumenty wiersza polecenia — przewodnik programowania c#
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: d6775263e6f1afb227aa263b01d60f5181da74f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093513"
---
# <a name="command-line-arguments-c-programming-guide"></a>Argumenty wiersza poleceń (Przewodnik programowania w języku C#)

Argumenty można wysyłać do metody, `Main` definiując metodę w jeden z następujących sposobów:

[!code-csharp[csProgGuideMain#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#2)]  

[!code-csharp[csProgGuideMain#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#3)]

> [!NOTE]
> Aby włączyć argumenty wiersza polecenia w `Main` metodzie w aplikacji Formularze systemu Windows, należy ręcznie zmodyfikować podpis `Main` w *program.cs*. Kod wygenerowany przez projektanta formularzy systemu Windows tworzy bez `Main` parametru wejściowego. Można również <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> użyć <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> lub uzyskać dostęp do argumentów wiersza polecenia z dowolnego punktu w konsoli lub aplikacji systemu Windows.

Parametr `Main` metody jest tablicą reprezentującą <xref:System.String> argumenty wiersza polecenia. Zazwyczaj można określić, czy `Length` istnieją argumenty, testując właściwość, na przykład:

[!code-csharp[csProgGuideMain#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#4)]

Można również przekonwertować argumenty ciągu na <xref:System.Convert> typy `Parse` liczbowe przy użyciu klasy lub metody. Na przykład następująca instrukcja `string` konwertuje liczbę na `long` liczbę przy użyciu <xref:System.Int64.Parse%2A> metody:

```csharp
long num = Int64.Parse(args[0]);
```

Istnieje również możliwość użycia typu `long`C#, które `Int64`aliasy:

```csharp
long num = long.Parse(args[0]);
```

Można również użyć `Convert` metody `ToInt64` klasy, aby zrobić to samo:

```csharp
long num = Convert.ToInt64(s);
```

Aby uzyskać więcej informacji, zobacz <xref:System.Int64.Parse%2A> i <xref:System.Convert>.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak używać argumentów wiersza polecenia w aplikacji konsoli. Aplikacja przyjmuje jeden argument w czasie wykonywania, konwertuje argument na liczbę całkowitą i oblicza współczynnik liczby. Jeśli nie podano żadnych argumentów, aplikacja wystawia komunikat, który wyjaśnia prawidłowe użycie programu.

Aby skompilować i uruchomić aplikację z wiersza polecenia, wykonaj następujące kroki:

1. Wklej poniższy kod do dowolnego edytora tekstu, a następnie zapisz plik jako plik tekstowy o nazwie *Factorial.cs*.

     [!code-csharp[csProgGuideMain#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#16)]

2. Z menu **Start** lub **Start** otwórz okno **wiersza polecenia dewelopera** programu Visual Studio, a następnie przejdź do folderu zawierającego właśnie utworzony plik.

3. Wprowadź następujące polecenie, aby skompilować aplikację.
  
     `csc Factorial.cs`  
  
     Jeśli aplikacja nie ma błędów kompilacji, tworzony jest plik wykonywalny o nazwie *Factorial.exe.*
  
4. Wprowadź następujące polecenie, aby obliczyć współczynnik 3:
  
     `Factorial 3`  
  
5. Polecenie generuje następujące dane wyjściowe:`The factorial of 3 is 6.`

> [!NOTE]
> Podczas uruchamiania aplikacji w programie Visual Studio można określić argumenty wiersza polecenia na [stronie debugowania, projektancie projektów](/visualstudio/ide/reference/debug-page-project-designer).

## <a name="see-also"></a>Zobacz też

- <xref:System.Environment?displayProperty=nameWithType>
- [Przewodnik programowania języka C#](../index.md)
- [Main() i argumenty wiersza polecenia](index.md)
- [Jak wyświetlić argumenty wiersza polecenia](how-to-display-command-line-arguments.md)
- [Main() — zwracane wartości](main-return-values.md)
- [Klasy](../classes-and-structs/classes.md)
