---
title: 'Instrukcje: Zapisz w pliku tekstowym — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: d08fe23f2dbfe46c0a58084b05610dfe7db3dda9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589920"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Instrukcje: Zapisz w pliku tekstowym (C# Przewodnik programowania)
W poniższych przykładach pokazano różne sposoby zapisywania tekstu w pliku. Pierwsze dwa przykłady używają statycznych metod dogodnych na <xref:System.IO.File?displayProperty=nameWithType> klasie, aby napisać każdy element dowolnego `IEnumerable<string>` i ciągu do pliku tekstowego. Przykład 3 pokazuje, jak dodać tekst do pliku, gdy trzeba przetwarzać każdy wiersz indywidualnie podczas zapisu w pliku. Przykłady 1-3 Zastąp całą istniejącą zawartość pliku, ale przykład 4 pokazuje, jak dołączyć tekst do istniejącego pliku.  
  
 Te przykłady umożliwiają zapisanie literałów ciągu do plików. Jeśli chcesz sformatować tekst zapisany w pliku, użyj <xref:System.String.Format%2A> funkcji interpolacji metody lub C# [ciągu](../../language-reference/tokens/interpolated.md) .  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Plik istnieje i jest tylko do odczytu.  
  
- Nazwa ścieżki może być za długa.  
  
- Dysk może być zapełniony.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [System plików i Rejestr (C# Przewodnik programowania)](./index.md)
- [Northwind Zapisywanie kolekcji w magazynie aplikacji](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
