---
title: 'Porady: utworzenie pliku lub folderu (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: d69885b420d28878072a70dfd2288905cf13de1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Porady: utworzenie pliku lub folderu (Przewodnik programowania w języku C#)
Można programowo Utwórz folder na komputerze, utwórz podfolder, Utwórz plik w podfolderze i zapisywania danych do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-create-a-file-or-folder_1.cs)]  
  
 Jeśli folder już istnieje, <xref:System.IO.Directory.CreateDirectory%2A> ma nothing i żaden wyjątek zostanie zgłoszony. Jednak <xref:System.IO.File.Create%2A?displayProperty=nameWithType> zastępuje istniejący plik przy użyciu nowego pliku. W przykładzie użyto `if` - `else` instrukcji, aby zapobiec zastąpienia istniejącego pliku.  
  
 Wprowadzając następujące zmiany w tym przykładzie, można określić różne wyniki według tego, czy plik niektórych nazwą już istnieje. Jeśli taki plik nie istnieje, kod tworzy go. Jeśli plik jest dostępny, kod dołącza dane do tego pliku.  
  
-   Określ nazwę pliku losowych.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
-   Zastąp `if` - `else` instrukcji z `using` instrukcji w poniższym kodzie.  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 Uruchom kilka razy w przykładzie do Sprawdź, czy dane są dodawane do pliku zawsze.  
  
 Aby uzyskać więcej `FileMode` wartości, których można spróbować, zobacz <xref:System.IO.FileMode>.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nazwa folderu jest nieprawidłowo sformułowany. Na przykład zawiera niedozwolone znaki lub jest tylko znak odstępu (<xref:System.ArgumentException> klasy). Użyj <xref:System.IO.Path> klasy w celu utworzenia nazwy prawidłową ścieżkę.  
  
-   Folder, który ma zostać utworzony folder nadrzędny jest tylko do odczytu (<xref:System.IO.IOException> klasy).  
  
-   Nazwa folderu jest `null` (<xref:System.ArgumentNullException> klasy).  
  
-   Nazwa folderu jest za długa (<xref:System.IO.PathTooLongException> klasy).  
  
-   Nazwa folderu jest tylko dwukropka ":" (<xref:System.IO.PathTooLongException> klasy).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Wystąpienie <xref:System.Security.SecurityException> klasa może zostać zgłoszony w sytuacjach częściowego zaufania.  
  
 Jeśli nie masz uprawnień do tworzenia folderu przykładzie zgłasza wystąpienia <xref:System.UnauthorizedAccessException> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO?displayProperty=nameWithType>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [System plików i rejestr (C# przewodnik programowania w języku)](../../../csharp/programming-guide/file-system/index.md)
