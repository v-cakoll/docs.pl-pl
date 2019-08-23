---
title: 'Instrukcje: Wykonaj iterację w drzewie katalogów C# — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
ms.openlocfilehash: ec48b9ff5a9ebe352bf0361b9e52ee0fb48576a8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923978"
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Instrukcje: Wykonaj iterację drzewa katalogów (C# Przewodnik programowania)
Fraza "Iterowanie drzewa katalogów" oznacza, że uzyskuje dostęp do każdego pliku w każdym zagnieżdżonym podkatalogu w określonym folderze głównym, na dowolną głębokość. Nie trzeba otwierać każdego pliku. Można po prostu pobrać nazwę pliku lub podkatalogu jako `string`lub można pobrać dodatkowe informacje w postaci <xref:System.IO.FileInfo?displayProperty=nameWithType> obiektu lub <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> .  
  
> [!NOTE]
> W systemie Windows terminy "katalog" i "folder" są używane zamiennie. Większość dokumentacji i tekstu interfejsu użytkownika używa terminu "folder", ale Biblioteka klas .NET Framework używa terminu "Directory".  
  
 W najprostszym przypadku, w którym wiadomo, że masz uprawnienia dostępu do wszystkich katalogów w określonym katalogu głównym, możesz użyć `System.IO.SearchOption.AllDirectories` flagi. Ta flaga zwraca wszystkie zagnieżdżone podkatalogi zgodne z określonym wzorcem. Poniższy przykład pokazuje, jak używać tej flagi.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 Przyczyną tej metody jest to, że jeśli którykolwiek z podkatalogów w ramach określonego elementu głównego <xref:System.IO.DirectoryNotFoundException> wykaże lub <xref:System.UnauthorizedAccessException>, cała Metoda zakończy się niepowodzeniem i nie zwróci żadnych katalogów. Ta sama wartość jest prawdziwa w przypadku używania <xref:System.IO.DirectoryInfo.GetFiles%2A> metody. Jeśli musisz obsługiwać te wyjątki w określonych podfolderach, musisz ręcznie przeprowadzić drzewo katalogów, jak pokazano w poniższych przykładach.  
  
 W przypadku ręcznego przeszukiwania drzewa katalogów można najpierw obsłużyć podkatalogi (*Przechodzenie*przedrzędne) lub pliki pierwsze (*Przechodzenie po kolejności*). W przypadku przeprowadzania przechodzenia przed kolejnością należy przeszukać całe drzewo w bieżącym folderze przed przeprowadzeniem iteracji w plikach, które znajdują się bezpośrednio w tym folderze. Przykłady w dalszej części tego dokumentu wykonują przechodzenie po kolejności, ale można je łatwo modyfikować, aby wykonać przechodzenie w kolejności wstępnej.  
  
 Inną opcją jest użycie rekursji lub przechodzenie oparte na stosie. W przykładach w dalszej części tego dokumentu przedstawiono oba podejścia.  
  
 Jeśli trzeba wykonać różne operacje na plikach i folderach, można modularyzacji te przykłady przez refaktoryzację operacji do oddzielnych funkcji, które można wywołać za pomocą pojedynczego delegata.  
  
> [!NOTE]
> Systemy plików NTFS mogą zawierać *punkty ponownej analizy* w postaci *punktów połączenia*, *linków symbolicznych*i *twardych linków*. Metody .NET Framework, takie jak <xref:System.IO.DirectoryInfo.GetFiles%2A> i <xref:System.IO.DirectoryInfo.GetDirectories%2A> , nie zwracają żadnych podkatalogów w punkcie ponownej analizy. To zachowanie chroni przed ryzykiem wprowadzenia do pętli nieskończonej, gdy dwa punkty ponownej analizy odnoszą się do siebie. Ogólnie rzecz biorąc, należy zachować szczególną ostrożność podczas postępowania z punktami ponownej analizy, aby upewnić się, że nie można przypadkowo modyfikować ani usuwać plików. Jeśli potrzebujesz precyzyjnej kontroli nad punktami ponownej analizy, użyj wywołania platformy lub kodu natywnego, aby bezpośrednio wywołać odpowiednie metody systemu plików Win32.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak przeprowadzić drzewo katalogów za pomocą rekursji. Podejście cykliczne to elegancki, ale może powodować wyjątek przepełnienia stosu, jeśli drzewo katalogów jest duże i głęboko zagnieżdżone.  
  
 Określone wyjątki, które są obsługiwane, oraz określone akcje wykonywane na każdym pliku lub folderze są dostępne jako tylko przykłady. Należy zmodyfikować ten kod w celu spełnienia określonych wymagań. Aby uzyskać więcej informacji, zobacz komentarze w kodzie.  
  
 [!code-csharp[csFilesandFolders#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#1)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak wykonać iterację plików i folderów w drzewie katalogów bez użycia rekursji. W tej metodzie jest <xref:System.Collections.Generic.Stack%601> używany typ kolekcji generycznej, który jest ostatnim wyjściem ze stosu (LIFO).  
  
 Określone wyjątki, które są obsługiwane, oraz określone akcje wykonywane na każdym pliku lub folderze są dostępne jako tylko przykłady. Należy zmodyfikować ten kod w celu spełnienia określonych wymagań. Aby uzyskać więcej informacji, zobacz komentarze w kodzie.  
  
 [!code-csharp[csFilesandFolders#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#2)]  
  
 Przetestowanie każdego folderu jest zwykle zbyt czasochłonne, aby określić, czy aplikacja ma uprawnienia do otwierania go. W związku z tym, przykładowy kod po prostu umieszcza tę część operacji w `try/catch` bloku. Możesz zmodyfikować `catch` blok tak, aby po odmowie dostępu do folderu próbować podnieść uprawnienia, a następnie uzyskać do niego dostęp. Jako reguła, należy jedynie przechwytywać te wyjątki, które można obsłużyć bez opuszczania aplikacji w nieznanym stanie.  
  
 Jeśli zawartość drzewa katalogów ma być przechowywana w pamięci lub na dysku, najlepszym rozwiązaniem jest przechowywanie tylko <xref:System.IO.FileSystemInfo.FullName%2A> właściwości (typu `string`) dla każdego pliku. Następnie można użyć tego ciągu do utworzenia nowego <xref:System.IO.FileInfo> lub <xref:System.IO.DirectoryInfo> obiektu w razie potrzeby lub otworzyć dowolny plik, który wymaga dodatkowego przetwarzania.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Niezawodny kod iteracji pliku musi uwzględniać wiele złożoności systemu plików. Aby uzyskać więcej informacji o systemie plików systemu Windows, zobacz [NTFS — Omówienie](/windows-server/storage/file-server/ntfs-overview).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IO>
- [LINQ i katalogi plików](../concepts/linq/linq-and-file-directories.md)
- [System plików i Rejestr (C# Przewodnik programowania)](./index.md)
