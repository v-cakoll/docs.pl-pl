---
title: Napisz prosty program równoległy używający metody Parallel. ForEach
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
ms.openlocfilehash: 9d54f06c1fc774a2e73b3b99a7d5bb24dd8baf3f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835262"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Instrukcje: zapisywanie prostej pętli Parallel. ForEach

W tym przykładzie pokazano, jak używać pętli <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, aby umożliwić równoległość danych na dowolnym <xref:System.Collections.IEnumerable?displayProperty=nameWithType> lub <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> źródle danych.

> [!NOTE]
> Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w PLINQ. Jeśli nie znasz wyrażeń lambda w C# lub Visual Basic, zobacz [wyrażenia lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Przykład

W tym przykładzie założono, że masz kilka plików jpg w folderze *C:\Users\Public\Pictures\Sample obrazy* i utworzysz nowy podfolder o nazwie *zmodyfikowano*. Gdy uruchamiasz ten przykład, obraca każdy obraz jpg w *przykładowych* obrazach i zapisuje je do *zmodyfikowania*. W razie potrzeby można zmodyfikować dwie ścieżki.

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

Pętla <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> działa jak pętla <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>. Pętla jest partycją źródłową kolekcji i planuje prace na wielu wątkach na podstawie środowiska systemowego. Im więcej procesorów w systemie, tym szybsze jest uruchamianie metody równoległej. W przypadku niektórych kolekcji źródłowych pętla sekwencyjna może być szybsza, w zależności od rozmiaru źródła i rodzaju pracy wykonywanej przez pętlę. Aby uzyskać więcej informacji o wydajności, zobacz [potencjalne pułapek w zakresie danych i równoległości zadań](potential-pitfalls-in-data-and-task-parallelism.md).

Aby uzyskać więcej informacji na temat pętli równoległych, zobacz [How to: Write a Simple Parallel. for](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).

Aby użyć <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> z kolekcją nieogólną, można użyć metody rozszerzenia <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> do przekonwertowania kolekcji na kolekcję ogólną, jak pokazano w następującym przykładzie:

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

Można również użyć równoległego LINQ (PLINQ) do zrównoleglanie przetwarzania źródeł danych <xref:System.Collections.Generic.IEnumerable%601>. PLINQ umożliwia użycie deklaracyjnej składni zapytań, aby wyrazić zachowanie pętli. Aby uzyskać więcej informacji, zobacz [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).

## <a name="compile-and-run-the-code"></a>Kompiluj i uruchamiaj kod

Można skompilować kod jako aplikację konsolową dla .NET Framework lub jako aplikację konsolową dla platformy .NET Core.

W programie Visual Studio istnieją Visual Basic i C# szablony aplikacji konsolowych dla systemów Windows Desktop i .NET Core.

W wierszu polecenia można użyć programu .NET Core i jego narzędzi interfejsu wiersza polecenia (na przykład `dotnet new console` lub `dotnet new console -lang vb`) albo utworzyć plik i użyć kompilatora z wierszem poleceń dla aplikacji .NET Framework.

W przypadku projektu .NET Core należy odwołać się do pakietu NuGet **System. Drawing. Common** . W programie Visual Studio Użyj Menedżera pakietów NuGet, aby zainstalować pakiet. Alternatywnie można dodać odwołanie do pakietu w pliku @no__t -0. csproj lub @no__t -1. vbproj:
 
```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

Aby uruchomić aplikację konsolową .NET Core z poziomu wiersza polecenia, należy użyć `dotnet run` z folderu, który zawiera aplikację.

Aby uruchomić aplikację konsolową z poziomu programu Visual Studio, naciśnij klawisz **F5**.

## <a name="see-also"></a>Zobacz także

- [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md)
- [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
