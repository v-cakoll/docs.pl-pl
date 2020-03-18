---
title: Jak czytać z pliku tekstowego - Przewodnik po programowaniu C#
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: d401a1d1bb2c6fccb203c440f367bd14c80e70e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705018"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Jak czytać z pliku tekstowego (C# Programming Guide)
W tym przykładzie odczytuje zawartość pliku tekstowego <xref:System.IO.File.ReadAllText%2A> przy <xref:System.IO.File.ReadAllLines%2A> użyciu <xref:System.IO.File?displayProperty=nameWithType> metod statycznych i z klasy.  
  
Na przykład, <xref:System.IO.StreamReader>który używa , zobacz [Jak czytać plik tekstowy po jednym wierszu naraz](./how-to-read-a-text-file-one-line-at-a-time.md).
  
> [!NOTE]
> Pliki, które są używane w tym przykładzie są tworzone w temacie [Jak napisać do pliku tekstowego](./how-to-write-to-a-text-file.md).
  
## <a name="example"></a>Przykład  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj kod i wklej go do aplikacji konsoli C#.  
  
Jeśli nie używasz plików tekstowych z [Jak zapisać do pliku tekstowego,](./how-to-write-to-a-text-file.md)zastąp argument do `ReadAllText` i `ReadAllLines` z odpowiednią ścieżką i nazwą pliku na komputerze.
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Plik nie istnieje lub nie istnieje w określonej lokalizacji. Sprawdź ścieżkę i pisownię nazwy pliku.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nie należy polegać na nazwie pliku, aby określić zawartość pliku. Na przykład plik `myFile.cs` może nie być plikiem źródłowym Języka C#.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania języka C#](../index.md)
- [System plików i rejestr (Przewodnik programowania w języku C#)](./index.md)
