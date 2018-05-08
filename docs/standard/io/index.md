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
ms.openlocfilehash: 63767a3ba2831ca9cadd9b99998eb871780143e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="file-and-stream-io"></a>We/Wy plików i strumieni
Termin „We/Wy (wejście/wyjście) plików i strumieni” dotyczy transferu danych do lub z nośnika magazynowania. W programie .NET Framework `System.IO` przestrzenie nazw zawierają typy umożliwiające odczytywanie i zapisywanie synchronicznego i asynchronicznego, strumienie danych i plików. Te przestrzenie nazw zawierają również typy, które wykonują kompresję i dekompresję plików, oraz typy, które umożliwiają komunikację za pośrednictwem potoków i portów szeregowych.  
  
 Plik to uporządkowana i nazwana kolekcja bajtów, która ma stały magazyn. Podczas pracy z plikami użytkownik pracuje ze ścieżkami katalogów, magazynem dysku oraz nazwami plików i katalogów. Natomiast strumień to sekwencja bajtów służąca do odczytu i zapisu w magazynie zapasowym, który może być jednym z kilku nośników magazynu (na przykład dysk lub pamięć). Tak jak istnieje kilka magazynów zapasowych innych niż dyski, tak samo istnieje kilka rodzajów strumieni innych niż strumienie plików, takie jak strumienie sieci, pamięci i potoku.  
  
## <a name="files-and-directories"></a>Pliki i katalogi  
 Można używać typów w <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw do interakcji z plików i katalogów. Na przykład można pobierać i ustawiać właściwości plików i katalogów oraz pobierać kolekcje plików i katalogów na podstawie kryteriów wyszukiwania.  
  
 Poniżej przedstawiono kilka powszechnie używanych klas związanych z plikami i katalogami:  
  
-   <xref:System.IO.File> -udostępnia metody statyczne do tworzenia, kopiowanie, usuwanie, przenoszenie i otwieranie plików i ułatwia utworzenie <xref:System.IO.FileStream> obiektu.  
  
-   <xref:System.IO.FileInfo> — zapewnia wystąpienia metody tworzenia, kopiowanie, usuwanie, przenoszenie i otwieranie plików i ułatwia utworzenie <xref:System.IO.FileStream> obiektu.  
  
-   <xref:System.IO.Directory> -udostępnia metody statyczne do tworzenia, przenoszenie i wyliczania katalogów i jego podkatalogach.  
  
-   <xref:System.IO.DirectoryInfo> -udostępnia wystąpienie metody tworzenia, przenoszenie i wyliczania katalogów i jego podkatalogach.  
  
-   <xref:System.IO.Path> -udostępnia metody i właściwości dla przetwarzania ciągów katalogu w sposób między platformami.  
  
 Oprócz używania tych klas, Visual Basic użytkownicy mogą używać metody i właściwości udostępniane przez <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> klasy dla we/wy pliku.  
  
 Zobacz [jak: kopiowania katalogów](../../../docs/standard/io/how-to-copy-directories.md), [porady: Tworzenie listy katalogów](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69), i [jak: Wyliczanie katalogów i plików](../../../docs/standard/io/how-to-enumerate-directories-and-files.md).  
  
## <a name="streams"></a>Strumienie  
 Abstrakcyjna klasa podstawowa <xref:System.IO.Stream> obsługuje odczytuje i zapisuje bajty. Wszystkie klasy, które reprezentują strumieni dziedziczyć <xref:System.IO.Stream> klasy. <xref:System.IO.Stream> Klasy pochodne zapewniają dostęp do źródła danych i repozytoriów i izolowanie programisty z szczegóły urządzeń podstawowych i systemu operacyjnego.  
  
 Strumienie obejmują trzy podstawowe operacje:  
  
-   Odczyt — transfer danych ze strumienia do struktury danych, takiej jak tablica bajtów.  
  
-   Zapis — transfer danych ze strumienia do źródła danych.  
  
-   Wyszukiwanie — badanie i modyfikowanie bieżącej pozycji w strumieniu.  
  
 W zależności od podstawowego źródła danych lub repozytorium, strumień może obsługiwać tylko niektóre z tych możliwości. Na przykład <xref:System.IO.Pipes.PipeStream> klasa nie obsługuje wyszukiwania. <xref:System.IO.Stream.CanRead%2A>, <xref:System.IO.Stream.CanWrite%2A>, I <xref:System.IO.Stream.CanSeek%2A> właściwości strumienia Określ operacje, które obsługuje strumienia.  
  
 Poniżej przedstawiono niektóre powszechnie używane klasy strumieni:  
  
-   <xref:System.IO.FileStream> — do odczytu i zapisu do pliku.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> — do odczytu i zapisu do pliku w magazynie izolowanym.  
  
-   <xref:System.IO.MemoryStream> — za odczytywanie i zapisywanie w pamięci jako magazynu zapasowego.  
  
-   <xref:System.IO.BufferedStream> — dla poprawia wydajność odczytu i zapisu.  
  
-   <xref:System.Net.Sockets.NetworkStream> — do odczytywania i zapisywania za pośrednictwem sieci gniazda.  
  
-   <xref:System.IO.Pipes.PipeStream> — do odczytywania i zapisywania w potokach nazwane i anonimowe.  
  
-   <xref:System.Security.Cryptography.CryptoStream> — Łączenie strumieni danych z usług kryptograficznych przekształcenia.  
  
 Na przykład pracy strumieni asynchronicznie, zobacz [asynchroniczne We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="readers-and-writers"></a>Czytniki i moduły zapisujące  
 <xref:System.IO?displayProperty=nameWithType> Przestrzeń nazw zawiera także typy odczytu zakodowane znaków ze strumieni i zapisaniu ich do strumieni. Zazwyczaj strumienie są projektowane do obsługi bajtowych danych wejściowych i wyjściowych. Typy czytników i składników zapisywania obsługują konwersję zakodowanych znaków do i z postaci bajtowej, więc strumień może ukończyć operację. Każda klasa składników zapisywania i odczytywania jest skojarzony z strumienia, który można pobrać za pomocą klasy `BaseStream` właściwości.  
  
 Poniżej przedstawiono niektóre powszechnie używane klasy czytników i składników zapisywania:  
  
-   <xref:System.IO.BinaryReader> i <xref:System.IO.BinaryWriter> — do odczytywania i zapisywania typów pierwotnych danych jako dane binarne wartości.  
  
-   <xref:System.IO.StreamReader> i <xref:System.IO.StreamWriter> — do odczytywania i zapisywania znaków za pomocą kodowania wartości do konwersji znaków do i z bajtów.  
  
-   <xref:System.IO.StringReader> i <xref:System.IO.StringWriter> — do odczytywania i zapisywania znaków, do i z ciągów.  
  
-   <xref:System.IO.TextReader> i <xref:System.IO.TextWriter> — służyć jako abstrakcyjnych klas podstawowych dla innych czytelników i zapisywania odczytu i zapisu znaków i ciągi, ale nie dane binarne.  
  
 Zobacz [jak: Odczyt tekstu z pliku](../../../docs/standard/io/how-to-read-text-from-a-file.md), [porady: zapisywanie tekstu do pliku](../../../docs/standard/io/how-to-write-text-to-a-file.md), [jak: odczytywanie znaków z ciągu](../../../docs/standard/io/how-to-read-characters-from-a-string.md), i [porady: zapisywanie znaków ciągu](../../../docs/standard/io/how-to-write-characters-to-a-string.md).  
  
## <a name="asynchronous-io-operations"></a>Asynchroniczne operacje wejścia/wyjścia  
 Odczyt lub zapis dużej ilości danych może wymagać użycia wielu zasobów. Te zadania należy wykonywać asynchronicznie, jeśli aplikacja ma ciągle reagować na działania użytkownika. Podczas synchronicznych operacji We/Wy wątek interfejsu użytkownika jest blokowany, aż do zakończenia wykonywania zasobochłonnej operacji.  Użyj asynchronicznej operacji We/Wy podczas tworzenia [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, aby uniemożliwić tworzenie wrażenie, że aplikacja przestanie działać.  
  
 Asynchroniczne elementy członkowskie `Async` w nazwach, takich jak <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, i <xref:System.IO.Stream.WriteAsync%2A> metody. Użycie tych metod z `async` i `await` słów kluczowych.  
  
 Aby uzyskać więcej informacji, zobacz [asynchroniczne We/Wy pliku](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="compression"></a>Kompresja  
 Termin „kompresja” dotyczy procesu zmniejszania rozmiaru pliku, który ma być przechowywany. Dekompresja to proces wyodrębniania zawartości skompresowanego pliku, dzięki czemu będzie on miał format umożliwiający używanie go. <xref:System.IO.Compression?displayProperty=nameWithType> Przestrzeń nazw zawiera typy kompresji i dekompresji plików i strumieni.  
  
 Następujące klasy są często używane podczas kompresowania i dekompresowania plików i strumieni:  
  
-   <xref:System.IO.Compression.ZipArchive> — w celu tworzenia i pobierania wpisów w archiwum zip.  
  
-   <xref:System.IO.Compression.ZipArchiveEntry> — reprezentujący skompresowany plik.  
  
-   <xref:System.IO.Compression.ZipFile> — do tworzenia, wyodrębnianie i otwieranie skompresowanym pakietem.  
  
-   <xref:System.IO.Compression.ZipFileExtensions> — do tworzenia i wyodrębnianie wpisów w skompresowanym pakietem.  
  
-   <xref:System.IO.Compression.DeflateStream> — kompresji i dekompresji strumieni przy użyciu algorytmu Deflate.  
  
-   <xref:System.IO.Compression.GZipStream> — kompresji i dekompresji strumieni w dane w formacie gzip.  
  
 Zobacz [porady: kompresowanie i wyodrębnianie plików](../../../docs/standard/io/how-to-compress-and-extract-files.md).  
  
## <a name="isolated-storage"></a>Izolowany magazyn  
 Wydzielona pamięć masowa to mechanizm magazynu, który dostarcza izolację i bezpieczeństwo przez definiowanie ustandaryzowanych metod kojarzenia kodu z zapisanymi danymi. Ta pamięć masowa oferuje wirtualny system plików, który jest izolowany dla konkretnego użytkownika, zestawu i (opcjonalnie) domeny. Wydzielona pamięć masowa jest szczególnie użyteczna, gdy aplikacja nie ma uprawnień dostępu do plików użytkownika. Można zapisać ustawienia lub pliki aplikacji w sposób, który jest kontrolowany przez zasady zabezpieczeń komputera.  
  
 Izolowanych magazynów nie jest dostępna dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji; zamiast tego należy użyć klasy danych aplikacji w [Windows.Storage](/uwp/api/Windows.Storage) przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [danych aplikacji](/previous-versions/windows/apps/hh464917(v=win.10)) w Centrum deweloperów systemu Windows.  
  
 Podczas implementowania wydzielonej pamięci masowej często używane są następujące klasy:  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorage> — udostępnia klasę podstawową dla implementacji izolowanych magazynów.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile> — zapewnia obszaru izolowanego magazynu, który zawiera pliki i katalogi.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> -przedstawia do pliku w magazynie izolowanym.  
  
 Zobacz [izolowanego magazynu](../../../docs/standard/io/isolated-storage.md).  
  
## <a name="io-operations-in-windows-store-apps"></a>Operacje We/Wy w aplikacji magazynu systemu Windows  
 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] Zawiera wiele typów odczytywanie z oraz zapisywanie do strumieni; jednak ten zestaw nie zawiera wszystkich typów .NET Framework we/wy.  
  
 Kilka istotnych różnic, należy pamiętać, korzystając z operacji We/Wy w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji:  
  
-   Typy dotyczące operacji na plikach, takich jak <xref:System.IO.File>, <xref:System.IO.FileInfo>, <xref:System.IO.Directory> i <xref:System.IO.DirectoryInfo>, nie są uwzględniane w [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Użyj typów w [Windows.Storage](http://msdn.microsoft.com/library/windows/apps/windows.storage.aspx) przestrzeń nazw [!INCLUDE[wrt](../../../includes/wrt-md.md)], takich jak [pliku magazynu](http://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.aspx) i [StorageFolder](http://msdn.microsoft.com/library/windows/apps/windows.storage.storagefolder.aspx).  
  
-   Izolowany magazyn jest niedostępny; Zamiast tego należy użyć [danych aplikacji](/previous-versions/windows/apps/hh464917(v=win.10)).  
  
-   Używanie metod asynchronicznych, takiej jak <xref:System.IO.Stream.ReadAsync%2A> i <xref:System.IO.Stream.WriteAsync%2A>, aby zapobiec blokuje wątku interfejsu użytkownika.  
  
-   Typy kompresję opartą na ścieżkę <xref:System.IO.Compression.ZipFile> i <xref:System.IO.Compression.ZipFileExtensions> nie są dostępne. Użyj typów w [Windows.Storage.Compression](http://msdn.microsoft.com/library/windows/apps/windows.storage.compression.aspx) przestrzeni nazw.  
  
 W razie potrzeby można wykonywać konwersje między strumieniami programu .NET Framework i strumieniami środowiska wykonawczego systemu Windows. Aby uzyskać więcej informacji, zobacz [porady: konwertowanie między .NET Framework i strumieni środowiska wykonawczego systemu Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md) lub [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx). <!--zz TODO: <xref:System.IO.WindowsRuntimeStreamExtensions>--> 
  
 Aby uzyskać więcej informacji o operacjach we/wy w [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji, zobacz [Szybki Start: Odczyt i zapis plików](/previous-versions/windows/apps/hh758325(v=win.10)).  
  
## <a name="io-and-security"></a>Moduł We/Wy i zabezpieczenia  
 Kiedy używać klas w <xref:System.IO?displayProperty=nameWithType> przestrzeni nazw, należy wykonać, wymagania dotyczące zabezpieczeń systemu operacyjnego takie jak listy kontroli dostępu (ACL) do kontrolowania dostępu do plików i katalogów. To wymaganie dotyczy oprócz żadnego <xref:System.Security.Permissions.FileIOPermission> wymagania. Listami ACL można zarządzać programowo. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie lub usuwanie pozycji listy kontroli dostępu](../../../docs/standard/io/how-to-add-or-remove-access-control-list-entries.md).  
  
 Domyślne zasady zabezpieczeń uniemożliwiają aplikacjom internetowym i intranetowym dostęp do plików na komputerze użytkownika. W związku z tym podczas pisania kodu, który zostanie pobrany przez Internet lub intranet, nie należy używać klas We/Wy, które wymagają ścieżki do pliku fizycznego. Zamiast tego należy użyć [izolowanego magazynu](../../../docs/standard/io/isolated-storage.md) do tradycyjnych aplikacji .NET Framework lub użyj [danych aplikacji](/previous-versions/windows/apps/hh464917(v=win.10)) dla [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikacji.  
  
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
