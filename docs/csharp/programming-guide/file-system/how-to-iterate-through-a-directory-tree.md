---
title: 'Instrukcje: Iterowanie drzewa katalogu - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
ms.openlocfilehash: 22d3883470f1435a50ae27f9d633ef566fec2913
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237080"
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Instrukcje: Iteracyjne przeglądanie drzewa katalogów (C# Programming Guide)
Wyrażenie "Iterowanie drzewa katalogów" oznacza, że dostęp do każdego pliku w każdej zagnieżdżonej podkatalogu w folderze określonym katalogu głównym, na dowolnym poziomie. Zawsze, nie trzeba otwierać każdego pliku. Możesz po prostu pobrać nazwę pliku lub podkatalog jako `string`, lub można pobrać dodatkowe informacje w formie <xref:System.IO.FileInfo?displayProperty=nameWithType> lub <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> obiektu.  
  
> [!NOTE]
>  W Windows warunki "directory" i "folder" są używane zamiennie. Większość dokumentacji i użytkownika tekst interfejsu używany jest termin "folder", ale [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas używany jest termin "directory".  
  
 W najprostszym przypadku, w którym można ustalić, czy masz uprawnienia dostępu do wszystkich katalogów w określonym katalogu głównym, można użyć `System.IO.SearchOption.AllDirectories` flagi. Ta flaga zwraca wszystkie podkatalogi zagnieżdżonych, pasujących do wzorca określonego. Poniższy przykład pokazuje, jak użyć tej flagi.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 Słabe strony w tym podejściu jest to, że jeśli powoduje, że jeden podkatalogów w określonym katalogu głównym <xref:System.IO.DirectoryNotFoundException> lub <xref:System.UnauthorizedAccessException>, całej metody zakończy się niepowodzeniem i zwraca żadne katalogi. Dotyczy to także gdy używasz <xref:System.IO.DirectoryInfo.GetFiles%2A> metody. Jeśli trzeba obsługiwać wyjątki, te w podfolderach określonych, możesz ręcznie Skontroluj drzewo katalogów, jak pokazano w poniższych przykładach.  
  
 Podczas ręcznie Skontroluj drzewo katalogów, które ułatwią Ci obsługę podkatalogów najpierw (*{przechodzenie kolejności wstępnego*), pliki lub pierwszy (*{przechodzenie kolejności po*). Jeśli wykonujesz przechodzenie przedsprzedaży, możesz zapoznaj się z całego drzewa w bieżącym folderze przed iteracja plików znajdujących się bezpośrednio w ten sam folder. Przykłady w dalszej części tego dokumentu, wykonać {przechodzenie kolejności po, ale można łatwo modyfikować je przeprowadzić {przechodzenie kolejności wstępnego.  
  
 Innym rozwiązaniem jest, czy należy użyć rekursji lub przechodzenia przez oparty na stosie. W przykładach w dalszej części tego dokumentu pokazano oba podejścia.  
  
 W przypadku wykonywania różnych operacji na plikach i folderach mogą modularyzacji te przykłady ramach refaktoryzacji elementu operacji na osobne funkcje, które można wywoływać za pomocą pojedynczego delegata.  
  
> [!NOTE]
>  Systemy plików NTFS może zawierać *punkty ponownej analizy* w formie *punkty połączenia*, *łącza symbolicznego*, i *twarde linki*. Metody .NET Framework, takie jak <xref:System.IO.DirectoryInfo.GetFiles%2A> i <xref:System.IO.DirectoryInfo.GetDirectories%2A> nie zwróci żadnych podkatalogów w ramach punktu ponownej analizy. To zachowanie chroni przed ryzykiem wejść w nieskończoną pętlę, gdy dwa punkty ponownej analizy, zapoznaj się ze sobą. Ogólnie rzecz biorąc należy zachować ostrożność extreme podczas operacji punkty ponownej analizy, aby upewnić się, możesz nie przypadkowo modyfikowania lub usuwania plików. Jeśli potrzebujesz precyzyjną kontrolę nad tym punkty ponownej analizy, użycie wywołania platformy lub kodu natywnego do odpowiedniego pliku Win32 systemu bezpośrednie wywoływanie metod.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak przeprowadzenie drzewo katalogów przy użyciu rekursji. Podejście cykliczne to elegancki, ale może potencjalnie spowodować wyjątek przepełnienia stosu, jeśli drzewo katalogów są duże i głęboko zagnieżdżonych.  
  
 Określonego wyjątki, które są obsługiwane i określonej akcji, które są wykonywane na każdym pliku lub folderu, są dostarczane jako fikcyjne. Należy zmodyfikować pod kątem wymagań dotyczących tego kodu. Zobacz komentarze w kodzie, aby uzyskać więcej informacji.  
  
 [!code-csharp[csFilesandFolders#1](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak iteracja plików i folderów w drzewie katalogu bez użycia rekursji. Ta metoda korzysta z ogólnego <xref:System.Collections.Generic.Stack%601> typ kolekcji, który jest ostatni w stosie pierwszy LIFO ().  
  
 Określonego wyjątki, które są obsługiwane i określonej akcji, które są wykonywane na każdym pliku lub folderu, są dostarczane jako fikcyjne. Należy zmodyfikować pod kątem wymagań dotyczących tego kodu. Zobacz komentarze w kodzie, aby uzyskać więcej informacji.  
  
 [!code-csharp[csFilesandFolders#2](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_2.cs)]  
  
 Zazwyczaj jest zbyt czasochłonne przetestować każdy folder w celu ustalenia, czy aplikacja ma uprawnienia do otwierania go. W związku z tym, przykładowy kod zawiera tylko część operacji w `try/catch` bloku. Możesz zmodyfikować `catch` zablokować tak, aby podczas dostępu do folderu, próby podniesienia poziomu uprawnień użytkownika, a następnie ponownie uzyskać dostęp. Zgodnie z zasadą przechwytywać tylko te wyjątki, które może obsłużyć bez opuszczania aplikacji w nieznanym stanie.  
  
 Jeśli zawartość drzewa katalogów, muszą być przechowywane w pamięci lub na dysku, najlepszym rozwiązaniem jest przechowywanie tylko <xref:System.IO.FileSystemInfo.FullName%2A> właściwości (typu `string`) dla każdego pliku. Można następnie użyć tego ciągu do utworzenia nowego <xref:System.IO.FileInfo> lub <xref:System.IO.DirectoryInfo> obiektu zgodnie z potrzebami, lub otworzyć dowolny plik, który wymaga dodatkowego przetwarzania.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Kod iteracji niezawodne pliku należy wziąć pod uwagę wiele złożoności systemu plików. Aby uzyskać więcej informacji w systemie plików Windows, zobacz [Omówienie systemu plików NTFS](/windows-server/storage/file-server/ntfs-overview).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO>  
- [LINQ i katalogi plików](../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
- [System plików i rejestr (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md)
