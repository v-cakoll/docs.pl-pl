---
title: 'Instrukcje: Iteracja katalogów plików przy użyciu klas równoległych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to iterate directories
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
ms.openlocfilehash: 5639f4bdb83906273b60ed20494c288286f32560
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288202"
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a>Instrukcje: Iteracja katalogów plików przy użyciu klas równoległych
W wielu przypadkach, iteracja po plikach jest operacją, która może zostać łatwo zrównoleglona. Temat [jak: Iterowanie katalogów plików przy użyciu PLINQ](how-to-iterate-file-directories-with-plinq.md) pokazuje najprostszy sposób wykonywania tego zadania w wielu scenariuszach. Jednak mogą pojawić się komplikacje, gdy w kodzie trzeba sobie poradzić z wieloma rodzajami wyjątków, które mogą zostać zgłoszone podczas dostępu do systemu plików. W poniższym przykładzie pokazano jedno z podejść do problemu. Użyto w nim iteracji opartej na stosie, aby przejść przez wszystkie pliki i foldery w określonym katalogu, co umożliwia przechwytywanie i obsługę różnych wyjątków w kodzie. Oczywiście sposób obsługi wyjątków zależy od dewelopera.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie iteracja po katalogach jest wykonywana sekwencyjnie, ale przetwarzanie plików jest równoległe. Prawdopodobnie jest to najlepsze podejście, gdy stosunek liczby plików do liczby katalogów jest wysoki. Możliwe jest również zrównoleglenie iteracji po katalogach i sekwencyjny dostęp do każdego pliku. Zrównoleglanie obu pętli będzie prawdopodobnie nieskuteczne, dopóki nie określisz komputera docelowego z dużą liczbą procesorów. Jednak we wszystkich przypadkach należy dokładnie przetestować aplikację, aby określić najlepsze podejście.  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 W tym przykładzie, operacje We/Wy na pliku są wykonywane synchronicznie. Podczas pracy z dużymi plikami lub wolnymi połączeniami sieciowymi, preferowany może być dostęp asynchroniczny do plików. Techniki asynchronicznego We/Wy można połączyć z iteracjami równoległymi. Aby uzyskać więcej informacji, zobacz [TPL i tradycyjny .NET Framework programowanie asynchroniczne](tpl-and-traditional-async-programming.md).  
  
 W przykładzie użyto zmiennej lokalnej `fileCount` do utrzymywania licznika całkowitej liczby przetworzonych plików. Ponieważ dostęp do zmiennej może być uzyskiwany współbieżnie, przez wiele zadań, jest on synchronizowany przez wywołanie metody <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType>.  
  
 Zauważ, że jeśli w głównym wątku zgłoszony zostanie wyjątek, wątki uruchomione w metodzie <xref:System.Threading.Tasks.Parallel.ForEach%2A> mogą kontynuować działanie. Aby zatrzymać te wątki, możesz ustawić zmienną logiczną w metodach obsługi wyjątków i sprawdzać jej wartość podczas każdej iteracji pętli równoległej. Jeśli wartość wskazuje, że zgłoszony został wyjątek, użyj zmiennej <xref:System.Threading.Tasks.ParallelLoopState>, aby zatrzymać lub przerwać pętlę. Aby uzyskać więcej informacji, zobacz [jak: zatrzymać lub przerwać pętlę Parallel. for](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także

- [Równoległość danych](data-parallelism-task-parallel-library.md)
