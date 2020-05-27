---
title: Argumenty wiersza polecenia — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: c203716d9bb8298c934a999a496793c294949ddb
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007757"
---
# <a name="command-line-arguments-c-programming-guide"></a>Argumenty wiersza poleceń (Przewodnik programowania w języku C#)

Argumenty do metody można wysłać, `Main` definiując metodę w jeden z następujących sposobów:

[!code-csharp[csProgGuideMain#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#2)]  

[!code-csharp[csProgGuideMain#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#3)]

> [!NOTE]
> Aby włączyć argumenty wiersza polecenia w `Main` metodzie w aplikacji Windows Forms, należy ręcznie zmodyfikować sygnaturę `Main` w *program.cs*. Kod wygenerowany przez projektanta Windows Forms tworzy `Main` bez parametru wejściowego. Można również użyć <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> lub <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType> , aby uzyskać dostęp do argumentów wiersza polecenia z dowolnego punktu w konsoli lub aplikacji systemu Windows.

Parametr `Main` metody jest <xref:System.String> tablicą, która reprezentuje argumenty wiersza polecenia. Zwykle określasz, czy argumenty istnieją przez testowanie `Length` właściwości, na przykład:

[!code-csharp[csProgGuideMain#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#4)]

> [!TIP]
> `args`Tablica nie może mieć wartości null. Dzięki temu można bezpiecznie uzyskać dostęp do `Length` właściwości bez sprawdzania wartości null.

Możesz również skonwertować argumenty ciągu na typy liczbowe przy użyciu <xref:System.Convert> klasy lub `Parse` metody. Na przykład następująca instrukcja konwertuje `string` do `long` liczby przy użyciu <xref:System.Int64.Parse%2A> metody:

```csharp
long num = Int64.Parse(args[0]);
```

Istnieje również możliwość użycia typu C# `long` , którego aliasy `Int64` :

```csharp
long num = long.Parse(args[0]);
```

Można również użyć `Convert` metody klasy, `ToInt64` Aby wykonać tę samą czynność:

```csharp
long num = Convert.ToInt64(s);
```

Aby uzyskać więcej informacji, zobacz <xref:System.Int64.Parse%2A> i <xref:System.Convert>.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać argumentów wiersza polecenia w aplikacji konsolowej. Aplikacja przyjmuje jeden argument w czasie wykonywania, konwertuje argument na liczbę całkowitą i Oblicza silnię liczby. Jeśli nie podano żadnych argumentów, aplikacja wystawia komunikat z wyjaśnieniem prawidłowego użycia programu.

Aby skompilować i uruchomić aplikację z poziomu wiersza polecenia, wykonaj następujące kroki:

1. Wklej poniższy kod do dowolnego edytora tekstów, a następnie Zapisz plik jako plik tekstowy o nazwie *factorial.cs*.

     [!code-csharp[csProgGuideMain#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#16)]

2. Na ekranie **startowym** lub w menu **start** Otwórz okno **wiersz polecenia dla deweloperów** programu Visual Studio, a następnie przejdź do folderu zawierającego plik, który został właśnie utworzony.

3. Wprowadź następujące polecenie, aby skompilować aplikację.
  
     `csc Factorial.cs`  
  
     Jeśli aplikacja nie ma błędów kompilacji, tworzony jest plik wykonywalny o nazwie *silni. exe* .
  
4. Wprowadź następujące polecenie, aby obliczyć silnię 3:
  
     `Factorial 3`  
  
5. To polecenie tworzy następujące dane wyjściowe:`The factorial of 3 is 6.`

> [!NOTE]
> Podczas uruchamiania aplikacji w programie Visual Studio, można określić argumenty wiersza polecenia na [stronie debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).

## <a name="see-also"></a>Zobacz też

- <xref:System.Environment?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../index.md)
- [Main () i argumenty wiersza polecenia](index.md)
- [Wyświetlanie argumentów wiersza polecenia](how-to-display-command-line-arguments.md)
- [Main() — Zwracane wartości](main-return-values.md)
- [Klasy](../classes-and-structs/classes.md)
