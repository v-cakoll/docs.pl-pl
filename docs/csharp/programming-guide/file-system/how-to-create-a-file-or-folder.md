---
title: Jak utworzyć plik lub folder - Przewodnik po programowaniu C#
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: cdcc0a375aa1eca29c024d1e0c9008f337d0c772
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167560"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Jak utworzyć plik lub folder (Przewodnik programowania C#)
Można programowo utworzyć folder na komputerze, utworzyć podfolder, utworzyć plik w podfolderze i zapisać dane w pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 Jeśli folder już <xref:System.IO.Directory.CreateDirectory%2A> istnieje, nic nie robi i nie jest zgłaszany żaden wyjątek. Jednak <xref:System.IO.File.Create%2A?displayProperty=nameWithType> zastępuje istniejący plik nowym plikiem. W przykładzie `if` - `else` użyto instrukcji, aby zapobiec zastępowaniu istniejącego pliku.  
  
 Dokonując następujących zmian w przykładzie, można określić różne wyniki na podstawie tego, czy plik o określonej nazwie już istnieje. Jeśli taki plik nie istnieje, kod go tworzy. Jeśli taki plik istnieje, kod dołącza dane do tego pliku.  
  
- Określ nielosową nazwę pliku.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- Zastąp `if` - `else` instrukcję instrukcją `using` w poniższym kodzie.  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 Uruchom przykład kilka razy, aby sprawdzić, czy dane są dodawane do pliku za każdym razem.  
  
 Aby `FileMode` uzyskać więcej wartości, <xref:System.IO.FileMode>które można wypróbować, zobacz .  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa folderu jest nieprawidłowo sformułowana. Na przykład zawiera niedozwolone znaki lub<xref:System.ArgumentException> jest tylko biały znak (klasa). Użyj <xref:System.IO.Path> klasy, aby utworzyć prawidłowe nazwy ścieżek.  
  
- Folder nadrzędny folderu, który ma zostać<xref:System.IO.IOException> utworzony, jest tylko do odczytu (klasa).  
  
- Nazwa folderu `null` <xref:System.ArgumentNullException> to (klasa).  
  
- Nazwa folderu jest<xref:System.IO.PathTooLongException> za długa (klasa).  
  
- Nazwa folderu jest tylko dwukropkiem, ":" (<xref:System.IO.PathTooLongException> klasa).  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Wystąpienie <xref:System.Security.SecurityException> klasy mogą być generowane w sytuacjach częściowego zaufania.  
  
 Jeśli nie masz uprawnień do tworzenia folderu, przykład zgłasza <xref:System.UnauthorizedAccessException> wystąpienie klasy.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania języka C#](../index.md)
- [System plików i rejestr (Przewodnik programowania w języku C#)](./index.md)
