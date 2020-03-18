---
title: Jak iterate przez drzewo katalogów - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- iterating through folders [C#]
- file iteration [C#]
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
ms.openlocfilehash: be3931a23e7a88affcf4d0abf617ec00bd35297a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712263"
---
# <a name="how-to-iterate-through-a-directory-tree-c-programming-guide"></a>Jak iterate przez drzewo katalogów (C# Programming Guide)
Fraza "iterować drzewo katalogów" oznacza dostęp do każdego pliku w każdym zagnieżdżonym podkatalogu w określonym folderze głównym, do dowolnej głębokości. Nie koniecznie trzeba otworzyć każdy plik. Można po prostu pobrać nazwę pliku lub `string`podkatalogu jako , lub można pobrać <xref:System.IO.FileInfo?displayProperty=nameWithType> <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> dodatkowe informacje w postaci lub obiektu.  
  
> [!NOTE]
> W systemie Windows terminy "katalog" i "folder" są używane zamiennie. Większość dokumentacji i tekstu interfejsu użytkownika używa terminu "folder", ale biblioteka klas .NET Framework używa terminu "katalog".  
  
 W najprostszym przypadku, w którym wiesz na pewno, że masz uprawnienia dostępu do wszystkich `System.IO.SearchOption.AllDirectories` katalogów w określonym katalogu głównym, można użyć flagi. Ta flaga zwraca wszystkie zagnieżdżone podkatalogi, które pasują do określonego wzorca. W poniższym przykładzie pokazano, jak używać tej flagi.  
  
```csharp  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 Słabość w tym podejściu jest to, że jeśli jeden z <xref:System.IO.DirectoryNotFoundException> <xref:System.UnauthorizedAccessException>podkatalogów w ramach określonego katalogu głównego powoduje lub , cała metoda nie powiedzie się i zwraca żadnych katalogów. To samo dotyczy korzystania <xref:System.IO.DirectoryInfo.GetFiles%2A> z metody. Jeśli musisz obsłużyć te wyjątki w określonych podfolderach, musisz ręcznie przejść drzewo katalogów, jak pokazano w poniższych przykładach.  
  
 Podczas ręcznego przechodzenia drzewa katalogów można najpierw obsługiwać podkatalogi *(przechodzenie w przedsprzedaży)* lub pliki jako pierwsze *(przechodzenie po zakończeniu zamówienia).* Jeśli wykonujesz przechodzenie w przedsprzedaży, chodzisz po całym drzewie pod bieżącym folderem przed iteracji za pośrednictwem plików, które znajdują się bezpośrednio w tym folderze. Przykłady w dalszej części tego dokumentu wykonać przechodzenie po kolejności, ale można łatwo zmodyfikować je do wykonywania przechodzenia w przedsprzedaży.  
  
 Inną opcją jest, czy użyć rekursji lub przechodzenia opartego na stosie. Przykłady w dalszej części tego dokumentu pokazują obie podejścia.  
  
 Jeśli trzeba wykonać różne operacje na plikach i folderach, można modularyzować te przykłady, refaktoryzując operację na oddzielne funkcje, które można wywołać przy użyciu jednego pełnomocnika.  
  
> [!NOTE]
> Systemy plików NTFS mogą zawierać *punkty ponownej analizy* w postaci *punktów połączenia,* *łączy symbolicznych*i *twardych łączy.* Metody .NET Framework, <xref:System.IO.DirectoryInfo.GetFiles%2A> takie <xref:System.IO.DirectoryInfo.GetDirectories%2A> jak i nie zwróci żadnych podkatalogów w punkcie ponownej analizy. To zachowanie chroni przed ryzykiem wejścia w nieskończoną pętlę, gdy dwa punkty ponownej analizy odnoszą się do siebie. Ogólnie rzecz biorąc należy zachować szczególną ostrożność podczas zajmowania się punktami ponownej analizy, aby upewnić się, że nie przypadkowo zmodyfikujesz lub nie usuniesz plików. Jeśli potrzebujesz precyzyjnej kontroli nad punktami ponownej analizy, użyj wywołania platformy lub kodu macierzystego, aby bezpośrednio wywołać odpowiednie metody systemu plików Win32.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak przejść drzewa katalogów przy użyciu rekursji. Podejście cykliczne jest elegancki, ale ma potencjał, aby spowodować wyjątek przepełnienia stosu, jeśli drzewo katalogów jest duży i głęboko zagnieżdżone.  
  
 Szczególne wyjątki, które są obsługiwane, a określone akcje, które są wykonywane w każdym pliku lub folderze, są podane tylko jako przykłady. Należy zmodyfikować ten kod, aby spełnić określone wymagania. Zobacz komentarze w kodzie, aby uzyskać więcej informacji.  
  
 [!code-csharp[csFilesandFolders#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#1)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak iterować pliki i foldery w drzewie katalogów bez użycia rekursji. Ta technika <xref:System.Collections.Generic.Stack%601> używa ogólnego typu kolekcji, który jest ostatnim w stosie lifo (first out).  
  
 Szczególne wyjątki, które są obsługiwane, a określone akcje, które są wykonywane w każdym pliku lub folderze, są podane tylko jako przykłady. Należy zmodyfikować ten kod, aby spełnić określone wymagania. Zobacz komentarze w kodzie, aby uzyskać więcej informacji.  
  
 [!code-csharp[csFilesandFolders#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#2)]  
  
 Zazwyczaj jest zbyt czasochłonne, aby przetestować każdy folder, aby ustalić, czy aplikacja ma uprawnienia do jego otwarcia. W związku z tym przykład kodu po prostu `try/catch` otacza tę część operacji w bloku. Blok można `catch` zmodyfikować w taki sposób, aby po odmowie dostępu do folderu, spróbuj podnieść swoje uprawnienia, a następnie uzyskać do niego dostęp ponownie. Z reguły tylko przechwycić te wyjątki, które można obsłużyć bez pozostawienia aplikacji w nieznanym stanie.  
  
 Jeśli zawartość drzewa katalogów musi być przechowywana w pamięci lub na dysku, <xref:System.IO.FileSystemInfo.FullName%2A> najlepszym rozwiązaniem `string`jest przechowywanie tylko właściwości (typu) dla każdego pliku. Następnie można użyć tego ciągu, <xref:System.IO.FileInfo> <xref:System.IO.DirectoryInfo> aby utworzyć nowy lub obiekt w razie potrzeby lub otworzyć dowolny plik, który wymaga dodatkowego przetwarzania.  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Niezawodny kod iteracji pliku musi uwzględniać wiele złożoności systemu plików. Aby uzyskać więcej informacji na temat systemu plików Systemu Windows, zobacz [omówienie systemu plików NTFS](/windows-server/storage/file-server/ntfs-overview).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IO>
- [LINQ i katalogi plików](../concepts/linq/linq-and-file-directories.md)
- [System plików i rejestr (Przewodnik programowania w języku C#)](./index.md)
