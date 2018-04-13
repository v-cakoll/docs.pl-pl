---
title: 'Porady: wpisywanie do pliku tekstowego (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fa6de76e3981e0f05b5b192045043422a8a912aa
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Porady: wpisywanie do pliku tekstowego (Przewodnik programowania w języku C#)
W poniższych przykładach pokazano różne sposoby zapisywania tekstu w pliku. Pierwsze dwa przykłady użycia metod statycznych wygody na <xref:System.IO.File?displayProperty=nameWithType> klasa umożliwiająca zapisanie każdy element dowolnego `IEnumerable<string>` i ciąg do pliku tekstowego. Przykład 3 przedstawiono sposób dodawania tekstu do pliku, jeśli masz Przetwarzaj każdego wiersza indywidualnie zapis do pliku. Przykłady 1 – 3 zastąpić istniejącą zawartość pliku, ale przykład 4 przedstawiono sposób dołączać tekstu do istniejącego pliku.  
  
 Te przykłady dają zapis literałów ciągów w plikach. Jeśli chcesz sformatować zapisywane w pliku tekstowym, użyj <xref:System.String.Format%2A> metody lub C# [ciągu interpolacji](../../../csharp/language-reference/tokens/interpolated.md) funkcji.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Plik istnieje i jest tylko do odczytu.  
  
-   Nazwa ścieżki może być za długa.  
  
-   Dysk może być zapełniony.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [System plików i rejestr (C# przewodnik programowania w języku)](../../../csharp/programming-guide/file-system/index.md)  
 [Przykład: Zapisz kolekcję do przechowywania danych aplikacji](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
