---
title: Napisać prosty program równoległego za pomocą Parallel.ForEach
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 599432af178031a85dea4155a8fd2923f879a600
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769216"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Instrukcje: Zapisywanie prostej pętli Parallel.ForEach

W tym przykładzie pokazano, jak używać <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pętli, aby włączyć równoległość danych przez dowolny <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> źródła danych.

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ. Jeśli nie znasz wyrażeń lambda w C# lub Visual Basic, zobacz [wyrażeń Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Przykład

W tym przykładzie przyjęto założenie, masz kilka plików .jpg w *obrazy C:\Users\Public\Pictures\Sample* folder i tworzy nowy folder podrzędny o nazwie *zmodyfikowane*. Po uruchomieniu tego przykładu, obraca się każdy obraz jpg w *przykładowe obrazy* i zapisuje go do *zmodyfikowane*. Można modyfikować tych dwóch ścieżek, zgodnie z potrzebami.

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pętli działa jak <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> pętli. Pętla partycje kolekcji źródłowej oraz planowanie zadań w wielu wątkach, w zależności od środowiska systemu. Więcej procesorów w systemie, tym szybciej parallel — metoda jest uruchamiany. W niektórych kolekcjach źródła pętli sekwencyjnej może być szybsze, w zależności od rozmiaru źródła i rodzaj pracy, który wykonuje pętlę. Aby uzyskać więcej informacji o wydajności, zobacz [potencjalne pułapki związane z równoległości danych i zadań](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)

Aby uzyskać więcej informacji na temat pętli równoległych zobacz [jak: Zapisywanie prostej pętli Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).

Aby użyć <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> z nieogólna kolekcja, możesz użyć <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> metodę rozszerzenia, aby przekonwertować kolekcji do kolekcji ogólnej, jak pokazano w poniższym przykładzie:

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

Umożliwia także Parallel LINQ (PLINQ) do zrównoleglenia przetwarzania <xref:System.Collections.Generic.IEnumerable%601> źródeł danych. PLINQ umożliwia użycie składni zapytań deklaratywne określenie zachowania pętli. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).

## <a name="compile-and-run-the-code"></a>Kompilowanie i uruchamianie kodu

Można skompilować kod jako aplikację konsolową w języku .NET Framework lub aplikacji konsoli dla platformy .NET Core.

W programie Visual Studio są Visual Basic i C# konsoli szablonów aplikacji dla Windows Desktop i .NET Core.

W wierszu polecenia można użyć platformy .NET Core i jego narzędzi interfejsu wiersza polecenia (na przykład `dotnet new console` lub `dotnet new console -lang vb`), lub można utworzyć pliku i używania kompilatora wiersza polecenia dla aplikacji .NET Framework.

Dla projektu .NET Core, należy odwołać **System.Drawing.Common** pakietu NuGet. W programie Visual Studio Użyj Menedżera pakietów NuGet, aby zainstalować pakiet. Alternatywnie, można dodać odwołania do pakietu w swojej \*.csproj lub \*pliku vbproj:
 
```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

Aby uruchomić aplikację konsoli .NET Core z poziomu wiersza polecenia, użyj `dotnet run` z folderu, który zawiera aplikację.

Aby uruchomić aplikację konsoli w programie Visual Studio, naciśnij klawisz **F5**.

## <a name="see-also"></a>Zobacz także

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
