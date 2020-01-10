---
title: Jak utworzyć plik lub folder — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: e0d0a7fbbc7e6a5c9a0bd00dec1188c5cfdcf896
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705252"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a>Jak utworzyć plik lub folder (C# Przewodnik programowania)
Można programowo utworzyć folder na komputerze, utworzyć podfolder, utworzyć plik w podfolderze i zapisać dane do pliku.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 Jeśli folder już istnieje, <xref:System.IO.Directory.CreateDirectory%2A> nic nie robi i żaden wyjątek nie jest zgłaszany. Jednak <xref:System.IO.File.Create%2A?displayProperty=nameWithType> zastępuje istniejący plik nowym plikiem. W przykładzie jest używana instrukcja `if`-`else`, aby zapobiec zastąpieniu istniejącego pliku.  
  
 Wprowadzając następujące zmiany w przykładzie, można określić różne wyniki w zależności od tego, czy plik o określonej nazwie już istnieje. Jeśli taki plik nie istnieje, kod tworzy jeden. Jeśli taki plik istnieje, kod dołącza dane do tego pliku.  
  
- Określ nielosową nazwę pliku.  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- Zastąp instrukcję `if`-`else` instrukcją `using` w poniższym kodzie.  
  
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
  
 Aby uzyskać więcej `FileMode` wartości, które można wypróbować, zobacz <xref:System.IO.FileMode>.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
- Nazwa folderu jest źle sformułowana. Na przykład zawiera niedozwolone znaki lub jest tylko białym znakiem (<xref:System.ArgumentException> Class). Użyj klasy <xref:System.IO.Path>, aby utworzyć prawidłowe nazwy ścieżek.  
  
- Folder nadrzędny folderu, który ma zostać utworzony, jest tylko do odczytu (Klasa<xref:System.IO.IOException>).  
  
- Nazwa folderu jest `null` (Klasa<xref:System.ArgumentNullException>).  
  
- Nazwa folderu jest za długa (Klasa<xref:System.IO.PathTooLongException>).  
  
- Nazwa folderu jest tylko dwukropek, ":" (Klasa<xref:System.IO.PathTooLongException>).  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Wystąpienie klasy <xref:System.Security.SecurityException> może być zgłaszane w sytuacjach częściowej relacji zaufania.  
  
 Jeśli nie masz uprawnień do utworzenia folderu, przykład zgłosi wystąpienie klasy <xref:System.UnauthorizedAccessException>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO?displayProperty=nameWithType>
- [Przewodnik programowania w języku C#](../index.md)
- [System plików i Rejestr (C# Przewodnik programowania)](./index.md)
