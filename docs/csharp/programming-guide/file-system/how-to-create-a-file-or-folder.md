---
title: Jak utworzyć plik lub folder — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: 5efe3b7dc600645488816d6f931df57fc236efc9
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241646"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Jak utworzyć plik lub folder (Przewodnik programowania w języku C#)
Można programowo utworzyć folder na komputerze, utworzyć podfolder, utworzyć plik w podfolderze i zapisać dane do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 Jeśli folder już istnieje, <xref:System.IO.Directory.CreateDirectory%2A> nie robi nic i żaden wyjątek nie jest zgłaszany. Jednak <xref:System.IO.File.Create%2A?displayProperty=nameWithType> zastępuje istniejący plik nowym plikiem. W przykładzie używa się `if` - `else` instrukcji, aby zapobiec zastąpieniu istniejącego pliku.  
  
 Wprowadzając następujące zmiany w przykładzie, można określić różne wyniki w zależności od tego, czy plik o określonej nazwie już istnieje. Jeśli taki plik nie istnieje, kod tworzy jeden. Jeśli taki plik istnieje, kod dołącza dane do tego pliku.  
  
- Określ nielosową nazwę pliku.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- Zastąp instrukcję instrukcją `if` - `else` `using` w poniższym kodzie.  
  
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
  
 Aby uzyskać więcej `FileMode` wartości, które można wypróbować, zobacz <xref:System.IO.FileMode> .  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa folderu jest źle sformułowana. Na przykład zawiera niedozwolone znaki lub jest tylko białym znakiem ( <xref:System.ArgumentException> Klasa). Użyj <xref:System.IO.Path> klasy, aby utworzyć prawidłowe nazwy ścieżek.  
  
- Folder nadrzędny folderu, który ma zostać utworzony, jest tylko do odczytu ( <xref:System.IO.IOException> Klasa).  
  
- Nazwa folderu to `null` ( <xref:System.ArgumentNullException> Klasa).  
  
- Nazwa folderu jest za długa ( <xref:System.IO.PathTooLongException> Klasa).  
  
- Nazwa folderu jest tylko dwukropek, ":" ( <xref:System.IO.PathTooLongException> Klasa).  
  
## <a name="net-security"></a>Zabezpieczenia platformy .NET  
 Wystąpienie <xref:System.Security.SecurityException> klasy może być zgłaszane w sytuacjach częściowej relacji zaufania.  
  
 Jeśli nie masz uprawnień do utworzenia folderu, przykład zgłosi wystąpienie <xref:System.UnauthorizedAccessException> klasy.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../index.md)
- [System plików i rejestr (Przewodnik programowania w języku C#)](./index.md)
