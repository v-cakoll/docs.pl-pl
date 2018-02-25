---
title: "Porady: iterowanie drzewa katalogów (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f45bdc4a08922842b079be3ef9d112693ca5d7a
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/24/2018
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Porady: iterowanie drzewa katalogów (Przewodnik programowania w języku C#)
Wyrażenie "Iterowanie drzewa katalogów" oznacza, że dostęp do każdego pliku w każdej zagnieżdżonej podkatalogu w folderze określonym katalogu głównym, wszelkie głębokość. Użytkownik nie musi mieć do otwierania każdego pliku. Podobnie można pobrać nazwy pliku lub podkatalogu co `string`, lub można pobrać dodatkowe informacje w postaci <xref:System.IO.FileInfo?displayProperty=nameWithType> lub <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> obiektu.  
  
> [!NOTE]
>  W systemie Windows warunki "directory" i "folder" są używane zamiennie. Większość dokumentacji i użytkownika interfejsu tekstu używany jest termin "folder", ale [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas używany jest termin "directory".  
  
 Ogólnie rzecz biorąc, w którym można ustalić, czy masz uprawnienia dostępu do wszystkich katalogów w określonym katalogu głównym, można użyć `System.IO.SearchOption.AllDirectories` flagi. Ta flaga zwraca wszystkie podkatalogi zagnieżdżonych zgodnych z określonym wzorcem. Poniższy przykład przedstawia użycie tej flagi.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 Osłabienie tej metody oznacza, że jeśli dowolny podkatalogów w określonym katalogu głównym powoduje, że <xref:System.IO.DirectoryNotFoundException> lub <xref:System.UnauthorizedAccessException>, całej metody kończy się niepowodzeniem i zwraca żadne katalogi. To samo dotyczy korzystając z <xref:System.IO.DirectoryInfo.GetFiles%2A> metody. Jeśli masz obsługę tych wyjątków dla określonych podfolderów, musi ręcznie Przeprowadź drzewa katalogów, jak pokazano w poniższych przykładach.  
  
 Gdy należy ręcznie przeprowadzić drzewa katalogów, podkatalogi może obsłużyć najpierw (*przechodzenie kolejność wstępnej*), lub pliki pierwszy (*przechodzenie po kolejności*). Po wykonaniu przechodzenie kolejność wstępnej całego drzewa możesz objaśniono w bieżącym folderze przed iteracja przez pliki, które znajdują się bezpośrednio w ten sam folder. Przechodzenie po kolejność wykonywania przykłady w dalszej części tego dokumentu, ale można łatwo zmodyfikować je, aby wykonać przechodzenie kolejność wstępnej.  
  
 Innym rozwiązaniem jest czy użyć rekursji lub przejście przez opartego na stosie. W dalszej części tego dokumentu przykładach obu podejść.  
  
 Jeśli masz do wykonywania różnych operacji na plikach i folderach, można modularyzacji te przykłady przez refaktoryzacji operacji w osobnych funkcji, które można wywołać za pomocą pojedynczego obiektu delegowanego.  
  
> [!NOTE]
>  Systemy plików NTFS może zawierać *punkty ponownej analizy* w formie *punkty połączenia*, *łącza symbolicznego*, i *twarde linki*. Metod .NET Framework, takich jak <xref:System.IO.DirectoryInfo.GetFiles%2A> i <xref:System.IO.DirectoryInfo.GetDirectories%2A> nie zwróci żadnych podkatalogów podrzędne względem ścieżki punktu ponownej analizy. To zachowanie chroni przed ryzykiem wejść w nieskończonej pętli, jeśli dwa punkty ponownej analizy odwoływać się do siebie. Ogólnie rzecz biorąc należy używać wyjątkową ostrożność podczas operacji punkty ponownej analizy, aby upewnić się, że nie przypadkowo modyfikowania lub usuwania plików. Jeśli potrzebna jest ścisła kontrola nad punkty ponownej analizy, użycie wywołania platformy i kod natywny odpowiedniego pliku Win32 systemu bezpośrednie wywoływanie metod.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak przeprowadzenie drzewa katalogów za pomocą rekursji. Podejście cykliczne jest elegancki, ale może spowodować wyjątek witryny stack overflow, jeśli drzewa katalogów jest duży i głęboko zagnieżdżone.  
  
 Określonego wyjątki, które są obsługiwane i określonej akcji, które są wykonywane dla każdego pliku lub folderu, są udostępniane tylko przykładowe. Należy zmodyfikować ten kod do własnych wymagań. Zobacz komentarze w kodzie Aby uzyskać więcej informacji.  
  
 [!code-csharp[csFilesandFolders#1](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak do iteracji pliki i foldery w drzewie katalogu bez za pomocą rekursji. Ta metoda korzysta z ogólnego <xref:System.Collections.Generic.Stack%601> typ kolekcji, który jest ostatnim w stos LIFO.  
  
 Określonego wyjątki, które są obsługiwane i określonej akcji, które są wykonywane dla każdego pliku lub folderu, są udostępniane tylko przykładowe. Należy zmodyfikować ten kod do własnych wymagań. Zobacz komentarze w kodzie Aby uzyskać więcej informacji.  
  
 [!code-csharp[csFilesandFolders#2](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_2.cs)]  
  
 Zazwyczaj jest zbyt dużo czasu do testowania każdego folderu w celu ustalenia, czy aplikacja ma uprawnienia do otwierania go. W związku z tym przykładowy kod obejmuje tylko część operacji w `try/catch` bloku. Można zmodyfikować `catch` zablokować tak, aby w przypadku odmowy dostępu do folderu, zostanie podjęta próba podniesienia poziomu uprawnień użytkownika, a następnie ponownie uzyskać dostęp. Zgodnie z zasadą catch tylko te wyjątki, które może obsłużyć bez opuszczania aplikacji w nieznanym stanie.  
  
 Jeśli zawartość drzewa katalogów, muszą być przechowywane w pamięci lub na dysku, najlepszym rozwiązaniem jest przechowywanie tylko <xref:System.IO.FileSystemInfo.FullName%2A> właściwości (typu `string`) dla każdego pliku. Ten ciąg następnie służy do tworzenia nowego <xref:System.IO.FileInfo> lub <xref:System.IO.DirectoryInfo> obiektu w razie potrzeby, lub Otwórz każdego pliku, który wymaga dodatkowego przetwarzania.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Kod iteracji niezawodne pliku musi uwzględniać wiele złożoności systemu plików. Aby uzyskać więcej informacji dotyczących systemu plików, zobacz [informacje techniczne dotyczące systemu plików NTFS](https://technet.microsoft.com/library/81cc8a8a-bd32-4786-a849-03245d68d8e4).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO>  
 [LINQ i katalogi plików](../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 [System plików i rejestr (C# przewodnik programowania w języku)](../../../csharp/programming-guide/file-system/index.md)
