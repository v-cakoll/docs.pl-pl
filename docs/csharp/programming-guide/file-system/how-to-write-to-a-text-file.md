---
title: Jak napisać do pliku tekstowego - C# Programming Guide
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: ac16fb971eae5654a55e2f1753d78a6458f03315
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712250"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Jak zapisać do pliku tekstowego (C# Programming Guide)
W poniższych przykładach pokazano różne sposoby zapisywania tekstu w pliku. Pierwsze dwa przykłady używają statycznych <xref:System.IO.File?displayProperty=nameWithType> metod wygody w `IEnumerable<string>` klasie, aby zapisać każdy element dowolnego i ciąg do pliku tekstowego. W przykładzie 3 pokazano, jak dodać tekst do pliku, gdy trzeba przetwarzać każdy wiersz indywidualnie podczas pisania do pliku. Przykłady 1-3 zastępują całą istniejącą zawartość w pliku, ale przykład 4 pokazuje, jak dołączać tekst do istniejącego pliku.  
  
 Te przykłady wszystkie literały ciągu zapisu do plików. Jeśli chcesz sformatować tekst napisany w <xref:System.String.Format%2A> pliku, użyj funkcji [interpolacji ciągu](../../language-reference/tokens/interpolated.md) C# lub c#.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Plik istnieje i jest tylko do odczytu.  
  
- Nazwa ścieżki może być za długa.  
  
- Dysk może być zapełniony.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [System plików i rejestr (Przewodnik programowania w języku C#)](./index.md)
- [Przykład: Zapisywanie kolekcji w magazynie aplikacji](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
