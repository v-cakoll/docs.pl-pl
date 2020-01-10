---
title: Jak czytać z pliku tekstowego — C# Przewodnik programowania
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705018"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Jak czytać z pliku tekstowego (C# Przewodnik programowania)
Ten przykład odczytuje zawartość pliku tekstowego przy użyciu metod statycznych <xref:System.IO.File.ReadAllText%2A> i <xref:System.IO.File.ReadAllLines%2A> z klasy <xref:System.IO.File?displayProperty=nameWithType>.  
  
Aby zapoznać się z przykładem, który używa <xref:System.IO.StreamReader>, zobacz [jak czytać plik tekstowy po jednym wierszu naraz](./how-to-read-a-text-file-one-line-at-a-time.md).
  
> [!NOTE]
> Pliki, które są używane w tym przykładzie, są tworzone w temacie [jak zapisywać w pliku tekstowym](./how-to-write-to-a-text-file.md).
  
## <a name="example"></a>Przykład  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj kod i wklej go do aplikacji C# konsolowej.  
  
Jeśli nie używasz plików tekstowych z [metody zapisywania do pliku tekstowego](./how-to-write-to-a-text-file.md), Zastąp argument `ReadAllText` i `ReadAllLines` z odpowiednią ścieżką i nazwą pliku na komputerze.
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
- Plik nie istnieje lub nie istnieje w określonej lokalizacji. Sprawdź ścieżkę i pisownię nazwy pliku.  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Nie należy polegać na nazwie pliku, aby ustalić zawartość pliku. Na przykład plik `myFile.cs` może nie być plikiem C# źródłowym.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../index.md)
- [System plików i Rejestr (C# Przewodnik programowania)](./index.md)
