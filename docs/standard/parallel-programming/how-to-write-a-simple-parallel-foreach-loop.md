---
title: Napisz prosty program równoległy przy użyciu Parallel.ForEach
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 02b94b673dc4468e68a1dadd83aab0e3bfcfaa16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160303"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Jak: Napisz prostą pętlę Parallel.ForEach

W tym przykładzie pokazano, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> jak używać pętli, <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> aby włączyć równoległość danych nad dowolnym lub źródłem danych.

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ. Jeśli nie znasz wyrażeń lambda w języku C# lub Visual Basic, zobacz [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Przykład

W tym przykładzie przyjęto założenie, że w folderze *C:\Users\Public\Public\Pictures\Sample Pictures* znajduje się kilka plików jpg i tworzy nowy podfolder o nazwie *Zmodyfikowano*. Po uruchomieniu przykładu obraca każdy obraz jpg w *przykładowych obrazach* i zapisuje go w *zmodyfikowanej*. W razie potrzeby można zmodyfikować dwie ścieżki.

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

Pętla <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> działa <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> jak pętla. Pętla dzieli kolekcję źródłową i planuje pracę nad wieloma wątkami na podstawie środowiska systemowego. Im więcej procesorów w systemie, tym szybciej działa metoda równoległa. W przypadku niektórych kolekcji źródłowych pętla sekwencyjna może być szybsza, w zależności od rozmiaru źródła i rodzaju pracy wykonywanej przez pętlę. Aby uzyskać więcej informacji na temat wydajności, zobacz [Potencjalne pułapki w równoległości danych i zadań](potential-pitfalls-in-data-and-task-parallelism.md).

Aby uzyskać więcej informacji na temat pętli równoległych, zobacz [Jak: Napisać prostą parallel.For pętli](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).

Aby <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> użyć z kolekcji nierodzajowych, <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> można użyć metody rozszerzenia do konwersji kolekcji do kolekcji ogólnej, jak pokazano w poniższym przykładzie:

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

Można również użyć Równoległego LINQ (PLINQ) do równoległego przetwarzania <xref:System.Collections.Generic.IEnumerable%601> źródeł danych. PLINQ umożliwia użycie deklaratywnej składni kwerendy do wyrażenia zachowania pętli. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).

## <a name="compile-and-run-the-code"></a>Kompilowanie i uruchamianie kodu

Kod można skompilować jako aplikację konsoli dla platformy .NET Framework lub jako aplikację konsoli dla .NET Core.

W programie Visual Studio istnieją szablony aplikacji konsoli Visual Basic i C# dla komputerów stacjonarnych systemu Windows i programu .NET Core.

Z wiersza polecenia można użyć poleceń .NET Core CLI `dotnet new console` `dotnet new console -lang vb`(na przykład lub), lub można utworzyć plik i użyć kompilatora wiersza polecenia dla aplikacji .NET Framework.

W przypadku projektu .NET Core należy odwołać się do pakietu **System.Drawing.Common** NuGet. W programie Visual Studio użyj Menedżera pakietów NuGet, aby zainstalować pakiet. Alternatywnie możesz dodać odwołanie do pakietu \*w pliku .csproj lub \*.vbproj:

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

Aby uruchomić aplikację konsoli .NET Core z `dotnet run` wiersza polecenia, należy użyć z folderu, który zawiera aplikację.

Aby uruchomić aplikację konsoli z programu Visual Studio, naciśnij klawisz **F5**.

## <a name="see-also"></a>Zobacz też

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
