---
title: Argumenty wiersza polecenia — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
ms.openlocfilehash: f74f374f13aef5135b81d59f94bc2c6913766763
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039316"
---
# <a name="command-line-arguments-c-programming-guide"></a>Argumenty wiersza poleceń (Przewodnik programowania w języku C#)

Argumenty do metody `Main` można wysłać, definiując metodę w jeden z następujących sposobów:

[!code-csharp[csProgGuideMain#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#2)]  

[!code-csharp[csProgGuideMain#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#3)]

> [!NOTE]
> Aby włączyć argumenty wiersza polecenia w metodzie `Main` w aplikacji Windows Forms, należy ręcznie zmodyfikować sygnaturę `Main` w *program.cs*. Kod wygenerowany przez projektanta Windows Forms tworzy `Main` bez parametru wejściowego. Można również użyć <xref:System.Environment.CommandLine%2A?displayProperty=nameWithType> lub <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=nameWithType>, aby uzyskać dostęp do argumentów wiersza polecenia z dowolnego punktu w konsoli lub aplikacji systemu Windows.

Parametr metody `Main` jest tablicą <xref:System.String>, która reprezentuje argumenty wiersza polecenia. Zwykle określasz, czy argumenty istnieją przez testowanie właściwości `Length`, na przykład:

[!code-csharp[csProgGuideMain#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class3.cs#4)]

Możesz również skonwertować argumenty ciągu na typy liczbowe przy użyciu klasy <xref:System.Convert> lub metody `Parse`. Na przykład poniższa instrukcja konwertuje `string` na numer `long` przy użyciu metody <xref:System.Int64.Parse%2A>:

```csharp
long num = Int64.Parse(args[0]);
```

Istnieje również możliwość użycia C# typu `long`, który aliasy`Int64`:

```csharp
long num = long.Parse(args[0]);
```

Można również użyć metody `Convert` Class `ToInt64`, aby wykonać tę samą czynność:

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
  
5. To polecenie tworzy następujące dane wyjściowe: `The factorial of 3 is 6.`

> [!NOTE]
> Podczas uruchamiania aplikacji w programie Visual Studio, można określić argumenty wiersza polecenia na [stronie debugowania, Projektant projektu](/visualstudio/ide/reference/debug-page-project-designer).

## <a name="see-also"></a>Zobacz także

- <xref:System.Environment?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../index.md)
- [Main() i argumenty wiersza polecenia](index.md)
- [Instrukcje: wyświetlanie argumentów wiersza polecenia](how-to-display-command-line-arguments.md)
- [Main() — zwracane wartości](main-return-values.md)
- [Klasy](../classes-and-structs/classes.md)
