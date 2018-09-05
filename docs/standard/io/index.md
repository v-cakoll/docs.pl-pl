---
title: We/Wy plików i strumieni
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- IO namespace
- files, I/O
- System.IO namespace
- I/O [.NET Framework]
- streams, I/O
- data streams, I/O
ms.assetid: 4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0ffef95c8f9a187d5dac6902462d9747023384d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556938"
---
# <a name="file-and-stream-io"></a>We/Wy plików i strumieni
Termin „We/Wy (wejście/wyjście) plików i strumieni” dotyczy transferu danych do lub z nośnika magazynowania. W .NET Framework `System.IO` przestrzenie nazw zawierają typy umożliwiające odczyt lub zapis, synchronicznie i asynchronicznie, w strumieniach i plikach danych. Te przestrzenie nazw zawierają również typy, które wykonują kompresję i dekompresję plików, oraz typy, które umożliwiają komunikację za pośrednictwem potoków i portów szeregowych.  
  
 Plik to uporządkowana i nazwana kolekcja bajtów, która ma stały magazyn. Podczas pracy z plikami użytkownik pracuje ze ścieżkami katalogów, magazynem dysku oraz nazwami plików i katalogów. Natomiast strumień to sekwencja bajtów służąca do odczytu i zapisu w magazynie zapasowym, który może być jednym z kilku nośników magazynu (na przykład dysk lub pamięć). Tak jak istnieje kilka magazynów zapasowych innych niż dyski, tak samo istnieje kilka rodzajów strumieni innych niż strumienie plików, takie jak strumienie sieci, pamięci i potoku.  
  
## <a name="files-and-directories"></a>Pliki i katalogi  
 Można używać typów z <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw do interakcji z plikami i katalogami. Na przykład można pobierać i ustawiać właściwości plików i katalogów oraz pobierać kolekcje plików i katalogów na podstawie kryteriów wyszukiwania.  

Dla ścieżki konwencji nazewnictwa i sposoby express ścieżkę pliku dla systemów Windows, w tym za pomocą składni urządzenia systemu DOS, które są obsługiwane w programie .NET Core 1.1 i nowszych i .NET Framework 4.6.2 lub nowszy, zobacz [formaty ścieżki plików w systemach Windows](file-path-formats.md). 
  
 Poniżej przedstawiono kilka powszechnie używanych klas związanych z plikami i katalogami:  
  
-   <xref:System.IO.File> — zawiera metody statyczne służące do tworzenia, kopiowania, usuwania, przenoszenia i otwierania plików, a także pomaga utworzyć <xref:System.IO.FileStream> obiektu.  
  
-   <xref:System.IO.FileInfo> — zawiera metody wystąpień służące do tworzenia, kopiowania, usuwania, przenoszenia i otwierania plików, a także pomaga utworzyć <xref:System.IO.FileStream> obiektu.  
  
-   <xref:System.IO.Directory> — zawiera metody statyczne służące do tworzenia, przenoszenia i wyliczania katalogów i podkatalogów.  
  
-   <xref:System.IO.DirectoryInfo> — zawiera metody wystąpień służące do tworzenia, przenoszenia i wyliczania katalogów i podkatalogów.  
  
-   <xref:System.IO.Path> — zawiera metody i właściwości przetwarzania ciągów katalogów w sposób dla wielu platform.  
  
 Oprócz tych klas, użytkowników programu Visual Basic można użyć metod i właściwości dostarczonych przez <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> klasy dla we/wy pliku.  
  
 Zobacz [porady: kopiowanie katalogów](../../../docs/standard/io/how-to-copy-directories.md), [jak: Create a Directory Listing](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69), i [porady: Wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md).  
  
## <a name="streams"></a>Strumienie  
 Abstrakcyjna klasa bazowa <xref:System.IO.Stream> obsługuje Odczyt i zapis bajtów. Wszystkie klasy, które reprezentują strumienie, dziedziczą z <xref:System.IO.Stream> klasy. <xref:System.IO.Stream> Klasy i jej klasy pochodne oferują typowy widok źródeł danych i repozytoriów. Ponadto izolują programistę od specyficznych szczegółów systemu operacyjnego i podstawowych urządzeń.  
  
 Strumienie obejmują trzy podstawowe operacje:  
  
-   Odczyt — transfer danych ze strumienia do struktury danych, takiej jak tablica bajtów.  
  
-   Zapis — transfer danych ze strumienia do źródła danych.  
  
-   Wyszukiwanie — badanie i modyfikowanie bieżącej pozycji w strumieniu.  
  
 W zależności od podstawowego źródła danych lub repozytorium, strumień może obsługiwać tylko niektóre z tych możliwości. Na przykład <xref:System.IO.Pipes.PipeStream> klasa nie obsługuje wyszukiwania. <xref:System.IO.Stream.CanRead%2A>, <xref:System.IO.Stream.CanWrite%2A>, I <xref:System.IO.Stream.CanSeek%2A> właściwości strumienia określają operacje obsługiwane przez strumień.  
  
 Poniżej przedstawiono niektóre powszechnie używane klasy strumieni:  
  
-   <xref:System.IO.FileStream> — do odczytu i zapisu do pliku.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> — do odczytu i zapisu do pliku w wydzielonej pamięci masowej.  
  
-   <xref:System.IO.MemoryStream> — do odczytu i zapisu w pamięci jako magazyn zapasowy.  
  
-   <xref:System.IO.BufferedStream> — dla poprawy wydajność odczytu i zapisu.  
  
-   <xref:System.Net.Sockets.NetworkStream> — do odczytu i zapisu za pośrednictwem gniazd sieciowych.  
  
-   <xref:System.IO.Pipes.PipeStream> — do odczytu i zapisu za pośrednictwem anonimowych i nazwanych potoków.  
  
-   <xref:System.Security.Cryptography.CryptoStream> — do łączenia strumieni danych z przekształceniami kryptograficznymi.  
  
 Aby uzyskać przykład pracy ze strumieniami asynchronicznie, zobacz [asynchroniczne We/Wy](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="readers-and-writers"></a>Czytniki i moduły zapisujące  
 <xref:System.IO?displayProperty=nameWithType> Przestrzeń nazw zawiera także typy do odczytywania zakodowanych znaków ze strumieni oraz zapisywania ich w strumieniach. Zazwyczaj strumienie są projektowane do obsługi bajtowych danych wejściowych i wyjściowych. Typy czytników i składników zapisywania obsługują konwersję zakodowanych znaków do i z postaci bajtowej, więc strumień może ukończyć operację. Każda klasa czytników i składników zapisywania jest skojarzona ze strumieniem, który można pobrać za pośrednictwem klasy `BaseStream` właściwości.  
  
 Poniżej przedstawiono niektóre powszechnie używane klasy czytników i składników zapisywania:  
  
-   <xref:System.IO.BinaryReader> i <xref:System.IO.BinaryWriter> — służy do odczytywania i zapisywania pierwotnych typów danych jako wartości binarnych.  
  
-   <xref:System.IO.StreamReader> i <xref:System.IO.StreamWriter> — służy do odczytywania i zapisywania znaków przy użyciu wartości kodowania w celu konwertowania znaków na i z bajtów.  
  
-   <xref:System.IO.StringReader> i <xref:System.IO.StringWriter> — służy do odczytywania i zapisywania znaków, do i z ciągów znaków.  
  
-   <xref:System.IO.TextReader> i <xref:System.IO.TextWriter> — pełnić rolę abstrakcyjnych klas bazowych dla innych czytników i składników zapisywania, które odczytują i zapisują znaki oraz ciągi, ale nie dane binarne.  
  
 Zobacz [jak: odczytywanie tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md), [porady: zapisywanie tekstu do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md), [jak: odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md), i [instrukcje: zapisywanie znaków w ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md).  
  
## <a name="asynchronous-io-operations"></a>Asynchroniczne operacje wejścia/wyjścia  
 Odczyt lub zapis dużej ilości danych może wymagać użycia wielu zasobów. Te zadania należy wykonywać asynchronicznie, jeśli aplikacja ma ciągle reagować na działania użytkownika. Podczas synchronicznych operacji We/Wy wątek interfejsu użytkownika jest blokowany, aż do zakończenia wykonywania zasobochłonnej operacji.  Użyj operacji asynchronicznych operacji We/Wy podczas opracowywania [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji można zapobiec powstawaniu wrażenia, że Twoja aplikacja przestała działać.  
  
 Asynchroniczne elementy Członkowskie zawierają `Async` w nazwach, takich jak <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, i <xref:System.IO.Stream.WriteAsync%2A> metody. Użycie tych metod z `async` i `await` słów kluczowych.  
  
 Aby uzyskać więcej informacji, zobacz [asynchroniczne We/Wy](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="compression"></a>Kompresja  
 Termin „kompresja” dotyczy procesu zmniejszania rozmiaru pliku, który ma być przechowywany. Dekompresja to proces wyodrębniania zawartości skompresowanego pliku, dzięki czemu będzie on miał format umożliwiający używanie go. <xref:System.IO.Compression?displayProperty=nameWithType> Przestrzeń nazw zawiera typy służące do kompresowania i dekompresowania plików i strumieni.  
  
 Następujące klasy są często używane podczas kompresowania i dekompresowania plików i strumieni:  
  
-   <xref:System.IO.Compression.ZipArchive> — do tworzenia i pobierania wpisów w archiwum zip.  
  
-   <xref:System.IO.Compression.ZipArchiveEntry> — do reprezentowania skompresowanego pliku.  
  
-   <xref:System.IO.Compression.ZipFile> — do tworzenia, wyodrębniania i otwierania skompresowanego pakietu.  
  
-   <xref:System.IO.Compression.ZipFileExtensions> — do tworzenia i wyodrębniania wpisów w skompresowanym pakiecie.  
  
-   <xref:System.IO.Compression.DeflateStream> — do kompresowania i dekompresowania strumieni przy użyciu algorytmu Deflate.  
  
-   <xref:System.IO.Compression.GZipStream> — do kompresowania i dekompresowania strumieni w formacie danych gzip.  
  
 Zobacz [porady: kompresowanie i wyodrębnianie plików](../../../docs/standard/io/how-to-compress-and-extract-files.md).  
  
## <a name="isolated-storage"></a>Izolowany magazyn  
 Wydzielona pamięć masowa to mechanizm magazynu, który dostarcza izolację i bezpieczeństwo przez definiowanie ustandaryzowanych metod kojarzenia kodu z zapisanymi danymi. Ta pamięć masowa oferuje wirtualny system plików, który jest izolowany dla konkretnego użytkownika, zestawu i (opcjonalnie) domeny. Wydzielona pamięć masowa jest szczególnie użyteczna, gdy aplikacja nie ma uprawnień dostępu do plików użytkownika. Można zapisać ustawienia lub pliki aplikacji w sposób, który jest kontrolowany przez zasady zabezpieczeń komputera.  
  
 Wydzielona pamięć masowa nie jest dostępna dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji; zamiast tego należy użyć klas danych [Windows.Storage](/uwp/api/Windows.Storage) przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [dane aplikacji](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) w Centrum deweloperów Windows.  
  
 Podczas implementowania wydzielonej pamięci masowej często używane są następujące klasy:  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorage> — dostarcza klasę bazową dla implementacji wydzielonej pamięci masowej.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile> — dostarcza obszar wydzielonej pamięci masowej, który zawiera pliki i katalogi.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> — uwidacznia plik w wydzielonej pamięci masowej.  
  
 Zobacz [Isolated Storage](../../../docs/standard/io/isolated-storage.md).  
  
## <a name="io-operations-in-windows-store-apps"></a>Operacje We/Wy w aplikacji magazynu systemu Windows  
 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] Zawiera wiele typów odczytywanie z oraz zapisywanie do strumieni; jednak ten zestaw nie obejmuje wszystkie typy operacji We/Wy programu .NET Framework.  
  
 Kilka poważnych różnic, należy pamiętać, korzystając z operacji We/Wy w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji:  
  
-   Typy związane z operacjami na plikach, takich jak <xref:System.IO.File>, <xref:System.IO.FileInfo>, <xref:System.IO.Directory> i <xref:System.IO.DirectoryInfo>, nie są uwzględnione w [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Zamiast tego należy używać typów z [Windows.Storage](https://msdn.microsoft.com/library/windows/apps/windows.storage.aspx) przestrzeń nazw [!INCLUDE[wrt](../../../includes/wrt-md.md)], takich jak [obiektu StorageFile](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.aspx) i [StorageFolder](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefolder.aspx).  
  
-   Wydzielona pamięć masowa nie jest dostępna; Zamiast tego należy użyć [dane aplikacji](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)).  
  
-   Używanie metod asynchronicznych, takiej jak <xref:System.IO.Stream.ReadAsync%2A> i <xref:System.IO.Stream.WriteAsync%2A>, aby zapobiec blokowaniu wątku interfejsu użytkownika.  
  
-   Typy kompresji opartej na ścieżkach <xref:System.IO.Compression.ZipFile> i <xref:System.IO.Compression.ZipFileExtensions> nie są dostępne. Zamiast tego należy używać typów z [Windows.Storage.Compression](https://msdn.microsoft.com/library/windows/apps/windows.storage.compression.aspx) przestrzeni nazw.  
  
 W razie potrzeby można wykonywać konwersje między strumieniami programu .NET Framework i strumieniami środowiska wykonawczego systemu Windows. Aby uzyskać więcej informacji, zobacz [porady: konwertowanie między .NET Framework i strumieni środowiska wykonawczego Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md) lub [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx). <!--zz TODO: <xref:System.IO.WindowsRuntimeStreamExtensions>--> 
  
 Aby uzyskać więcej informacji na temat operacji We/Wy w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, zobacz [Szybki Start: odczytywanie i zapisywanie plików](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).  
  
## <a name="io-and-security"></a>Moduł We/Wy i zabezpieczenia  
 Kiedy używać klas w <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw, należy wykonać, wymagania dotyczące zabezpieczeń systemu operacyjnego takie jak listy kontroli dostępu (ACL) do kontrolowania dostępu do plików i katalogów. To wymaganie nie jest dodatek do wszelkich <xref:System.Security.Permissions.FileIOPermission> wymagania. Listami ACL można zarządzać programowo. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie pozycji listy kontroli dostępu](../../../docs/standard/io/how-to-add-or-remove-access-control-list-entries.md).  
  
 Domyślne zasady zabezpieczeń uniemożliwiają aplikacjom internetowym i intranetowym dostęp do plików na komputerze użytkownika. W związku z tym podczas pisania kodu, który zostanie pobrany przez Internet lub intranet, nie należy używać klas We/Wy, które wymagają ścieżki do pliku fizycznego. Zamiast tego należy użyć [isolated storage](../../../docs/standard/io/isolated-storage.md) dla tradycyjnych aplikacji programu .NET Framework lub użyj [dane aplikacji](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
 Sprawdzanie zabezpieczeń jest wykonywane tylko wtedy, gdy jest konstruowany strumień. W związku z tym nie należy otwierać strumienia, a następnie przekazywać go do kodu lub domeny aplikacji o niższym poziomie zaufania.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
-   [Typowe zadania We/Wy](../../../docs/standard/io/common-i-o-tasks.md)  
  
 Lista zadań We/Wy skojarzonych z plikami, katalogami, i strumieniami oraz łącza do odpowiedniej zawartości i przykładów dla każdego zadania.  
  
-   [Asynchroniczne operacje We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md)  
  
 Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.  
  
-   [Wydzielona pamięć masowa](../../../docs/standard/io/isolated-storage.md)  
  
 Opis mechanizmu pamięci masowej danych, który dostarcza izolację i bezpieczeństwo przez definiowanie ustandaryzowanych opcji kojarzenia kodu z zapisanymi danymi.  
  
-   [Potoki](../../../docs/standard/io/pipe-operations.md)  
  
 Opis operacji wykonywanych w anonimowych i nazwanych potokach w programie .NET Framework.  
  
-   [Pliki mapowane w pamięci](../../../docs/standard/io/memory-mapped-files.md)  
  
 Opis plików zamapowanych w pamięci, które zawierają zawartość plików znajdujących się na dysku w pamięci wirtualnej. Zamapowanych w pamięci plików można używać, aby edytować bardzo duże pliki i tworzyć współużytkowaną pamięć służącą do komunikacji między procesami.
