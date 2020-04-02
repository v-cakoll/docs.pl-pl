---
title: Napisz prosty program równoległy za pomocą Parallel.ForEach
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 0300f8900cd18159ba3a2170cfba96f302f282a0
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588138"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Jak: Napisz prostą pętlę Parallel.ForEach

W tym przykładzie <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pokazano, jak używać pętli, aby włączyć równoległość danych za pomocą dowolnego <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> źródła danych.

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Przykład

W tym przykładzie założono, że w folderze *C:\Users\Public\Pictures\Sample Pictures* znajduje się kilka plików jpg i utworzysz nowy podfolder o nazwie *Zmodyfikowany*. Po uruchomieniu przykładu obraca każdy obraz jpg w *przykładowym obrazie obrazów* i zapisuje go na *zmodyfikowany*. W razie potrzeby można zmodyfikować dwie ścieżki.

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

Pętla <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> działa <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> jak pętla. Pętla partycje kolekcji źródłowej i planuje pracę na wiele wątków na podstawie środowiska systemowego. Im więcej procesorów w systemie, tym szybciej działa metoda równoległa. W przypadku niektórych kolekcji źródłowych pętla sekwencyjna może być szybsza, w zależności od rozmiaru źródła i rodzaju pracy wykonywanej przez pętlę. Aby uzyskać więcej informacji na temat wydajności, zobacz [Potencjalne pułapki w danych i równoległości zadań](potential-pitfalls-in-data-and-task-parallelism.md).

Aby uzyskać więcej informacji na temat pętli równoległych, zobacz [Jak: Napisz prostą pętlę Parallel.For](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).

Aby <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> użyć z kolekcji nierodycznej, można użyć metody <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> rozszerzenia do konwersji kolekcji do kolekcji ogólnej, jak pokazano w poniższym przykładzie:

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

Można również użyć Parallel LINQ (PLINQ) <xref:System.Collections.Generic.IEnumerable%601> do równoległości przetwarzania źródeł danych. PLINQ umożliwia użycie składni kwerendy deklaratywnej do wyrażania zachowania pętli. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md).

## <a name="compile-and-run-the-code"></a>Skompiluj i uruchom kod

Kod można skompilować jako aplikację konsoli dla platformy .NET Framework lub jako aplikację konsoli dla platformy .NET Core.

W programie Visual Studio dostępne są szablony aplikacji konsoli Visual Basic i C# dla pulpitu systemu Windows i programu .NET Core.

Z wiersza polecenia można użyć poleceń .NET Core CLI `dotnet new console` (na przykład lub `dotnet new console -lang vb`), lub utworzyć plik i użyć kompilatora wiersza polecenia dla aplikacji .NET Framework.

W przypadku projektu .NET Core należy odwołać się do pakietu **System.Drawing.Common** NuGet. W programie Visual Studio użyj Menedżera pakietów NuGet, aby zainstalować pakiet. Alternatywnie można dodać odwołanie do pakietu \*w pliku csproj lub \*.vbproj:

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

Aby uruchomić aplikację konsoli .NET Core z `dotnet run` wiersza polecenia, użyj z folderu zawierającego aplikację.

Aby uruchomić aplikację konsoli z programu Visual Studio, naciśnij klawisz **F5**.

## <a name="see-also"></a>Zobacz też

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
