---
title: 'Instrukcje: Zapis do pliku tekstowego — C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: e753f10acd33234d7f5e0c1a4203125ab880e2ae
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237145"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Instrukcje: Zapis do pliku tekstowego (C# Programming Guide)
W poniższych przykładach pokazano różne sposoby zapisywania tekstu w pliku. Pierwszych dwóch przykładach użyto metody statycznej wygody na <xref:System.IO.File?displayProperty=nameWithType> klasę umożliwiającą zapisanie każdy element dowolnego `IEnumerable<string>` i ciąg do pliku tekstowego. Przykład 3 pokazuje, jak dodać tekst do pliku, gdy trzeba osobno przetworzyć każdy wiersz zapisać do pliku. W przykładach 1 – 3 zastępowana cała istniejąca zawartość w pliku, ale w przykładzie 4 pokazano, jak dołączyć tekst do istniejącego pliku.  
  
 Wszystkie te przykłady zapisują literały ciągów znaków do plików. Aby sformatować tekst zapisany do pliku, należy użyć <xref:System.String.Format%2A> metody lub C# [Interpolacja ciągów](../../../csharp/language-reference/tokens/interpolated.md) funkcji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Plik istnieje i jest tylko do odczytu.  
  
-   Nazwa ścieżki może być za długa.  
  
-   Dysk może być zapełniony.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [System plików i rejestr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)  
- [Przykład: Zapisywanie kolekcji do przechowywania danych aplikacji](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
