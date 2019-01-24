---
title: 'Instrukcje: Odczyt z pliku tekstowego — C# przewodnik programowania'
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
ms.openlocfilehash: f7ddfbec13fad073272c75c3e68a4f5c9c3eef9e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672243"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Instrukcje: Odczyt z pliku tekstowego (C# Programming Guide)
Ten przykład odczytuje zawartość pliku tekstowego przy użyciu metod statycznych <xref:System.IO.File.ReadAllText%2A> i <xref:System.IO.File.ReadAllLines%2A> z <xref:System.IO.File?displayProperty=nameWithType> klasy.  
  
 Aby uzyskać przykład, który używa <xref:System.IO.StreamReader>, zobacz [jak: Odczyt pliku jednego wiersza tekstu w danym momencie](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).  
  
> [!NOTE]
>  Pliki, które są używane w tym przykładzie są tworzone w temacie [jak: Zapis do pliku tekstowego](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj kod i wklej go w aplikacji konsolowej C#.  
  
 Jeśli nie używasz plików tekstowych z [jak: Zapis do pliku tekstowego](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), Zastąp argument `ReadAllText` i `ReadAllLines` z odpowiednią ścieżkę i nazwę pliku na komputerze.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Plik nie istnieje lub nie istnieje w określonej lokalizacji. Sprawdź ścieżkę i pisownię nazwy pliku.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nie należy polegać na nazwę pliku, aby określić zawartość pliku. Na przykład plik `myFile.cs` może nie być plik źródłowy C#.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [System plików i rejestr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)
