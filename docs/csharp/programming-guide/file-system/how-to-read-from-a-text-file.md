---
title: 'Instrukcje: Odczytaj z pliku tekstowego — C# Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 2b98f24da7f13ae752f248eb8f26c75c1d47a824
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923952"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Instrukcje: Odczytaj z pliku tekstowego (C# Przewodnik programowania)
Ten przykład odczytuje zawartość pliku tekstowego przy użyciu metod <xref:System.IO.File.ReadAllText%2A> statycznych i <xref:System.IO.File.ReadAllLines%2A> z <xref:System.IO.File?displayProperty=nameWithType> klasy.  
  
 Przykład użycia <xref:System.IO.StreamReader>programu można znaleźć w temacie [How to: Odczytaj plik tekstowy jeden wiersz jednocześnie](./how-to-read-a-text-file-one-line-at-a-time.md).  
  
> [!NOTE]
> Pliki, które są używane w tym przykładzie, są tworzone w temacie [How to: Zapisz w pliku](./how-to-write-to-a-text-file.md)tekstowym.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj kod i wklej go do aplikacji C# konsolowej.  
  
 Jeśli nie używasz plików tekstowych z [: Zapisz w pliku](./how-to-write-to-a-text-file.md)tekstowym, Zastąp argument do `ReadAllText` i `ReadAllLines` z odpowiednią ścieżką i nazwą pliku na komputerze.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Plik nie istnieje lub nie istnieje w określonej lokalizacji. Sprawdź ścieżkę i pisownię nazwy pliku.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nie należy polegać na nazwie pliku, aby ustalić zawartość pliku. Na przykład plik `myFile.cs` może nie być plikiem C# źródłowym.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../index.md)
- [System plików i Rejestr (C# Przewodnik programowania)](./index.md)
