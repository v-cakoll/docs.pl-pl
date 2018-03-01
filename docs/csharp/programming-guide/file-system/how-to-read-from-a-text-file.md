---
title: "Porady: odczyt z pliku tekstowego (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2af6102ac6793b4612a6fbc41f8c50189cc24d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Porady: odczyt z pliku tekstowego (Przewodnik programowania w języku C#)
Ten przykład odczytuje zawartość pliku tekstowego za pomocą metod statycznych <xref:System.IO.File.ReadAllText%2A> i <xref:System.IO.File.ReadAllLines%2A> z <xref:System.IO.File?displayProperty=nameWithType> klasy.  
  
 Na przykład, który używa <xref:System.IO.StreamReader>, zobacz [porady: jeden wiersz pliku tekstowego do odczytu w czasie](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).  
  
> [!NOTE]
>  Pliki, które są używane w tym przykładzie są tworzone w temacie [porady: zapis do pliku tekstowego](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj kod i wklej go w aplikacji konsolowej C#.  
  
 Jeśli nie używasz plików tekstowych z [porady: zapis do pliku tekstowego](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), Zastąp argument `ReadAllText` i `ReadAllLines` z odpowiednią ścieżkę i nazwę komputera.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Plik nie istnieje lub nie istnieje w określonej lokalizacji. Sprawdź ścieżkę i pisownię nazwy pliku.  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Nie należy polegać na nazwę pliku, aby określić zawartość pliku. Na przykład plik `myFile.cs` może nie być pliku źródłowego C#.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO?displayProperty=nameWithType>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [System plików i rejestr (C# przewodnik programowania w języku)](../../../csharp/programming-guide/file-system/index.md)
