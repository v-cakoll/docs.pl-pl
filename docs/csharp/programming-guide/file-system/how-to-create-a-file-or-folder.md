---
title: 'Porady: utworzenie pliku lub folderu (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: 34919efe32730fe0db11cb881b8e07629a3094fd
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776327"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Porady: utworzenie pliku lub folderu (Przewodnik programowania w języku C#)
Można programowo utworzyć folder na komputerze, utwórz podfolder, Utwórz plik w podfolderze i zapisać dane do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-create-a-file-or-folder_1.cs)]  
  
 Jeśli folder już istnieje, <xref:System.IO.Directory.CreateDirectory%2A> robi nic, a żaden wyjątek jest zgłaszany. Jednak <xref:System.IO.File.Create%2A?displayProperty=nameWithType> zastępuje istniejący plik nowym plikiem. W przykładzie użyto `if` - `else` instrukcję, aby uniemożliwić zastąpienia istniejącego pliku.  
  
 Wprowadzając następujące zmiany w przykładzie, można określić różne wyniki oparte na tego, czy plik o określonej nazwie już istnieje. Jeśli taki plik nie istnieje, kod tworzy go. Jeśli taki plik istnieje, kod dołącza dane do tego pliku.  
  
-   Określ nielosową nazwę.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
-   Zastąp `if` - `else` instrukcję, określając `using` instrukcji w poniższym kodzie.  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 Uruchom przykład kilka razy, aby sprawdzić, czy dane są dodawane do pliku każdorazowo.  
  
 Aby uzyskać więcej informacji `FileMode` wartości, które można wypróbować, zobacz <xref:System.IO.FileMode>.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nazwa folderu jest nieprawidłowo sformułowany. Na przykład zawiera niedozwolone znaki lub jest tylko spacją (<xref:System.ArgumentException> klasy). Użyj <xref:System.IO.Path> klasy, aby utworzyć prawidłowe ścieżki nazw.  
  
-   Folderem nadrzędnym folderu, który ma zostać utworzony jest tylko do odczytu (<xref:System.IO.IOException> klasy).  
  
-   Nazwa folderu jest `null` (<xref:System.ArgumentNullException> klasy).  
  
-   Nazwa folderu jest zbyt długa (<xref:System.IO.PathTooLongException> klasy).  
  
-   Nazwa folderu jest tylko dwukropek, ":" (<xref:System.IO.PathTooLongException> klasy).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Wystąpienie <xref:System.Security.SecurityException> klasy mogą być generowane w sytuacjach częściowego zaufania.  
  
 Jeśli nie masz uprawnień do utworzenia folderu, przykład generuje wystąpienie <xref:System.UnauthorizedAccessException> klasy.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO?displayProperty=nameWithType>  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [System plików i rejestr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)
