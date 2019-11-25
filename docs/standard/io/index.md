---
title: File and Stream I/O - .NET
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
ms.openlocfilehash: 889271ca41fb84b44757adfffc61ffbfbc0a03a8
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204798"
---
# <a name="file-and-stream-io"></a>We/Wy plików i strumieni

Termin „We/Wy (wejście/wyjście) plików i strumieni” dotyczy transferu danych do lub z nośnika magazynowania. In the .NET Framework, the `System.IO` namespaces contain types that enable reading and writing, both synchronously and asynchronously, on data streams and files. Te przestrzenie nazw zawierają również typy, które wykonują kompresję i dekompresję plików, oraz typy, które umożliwiają komunikację za pośrednictwem potoków i portów szeregowych.

Plik to uporządkowana i nazwana kolekcja bajtów, która ma stały magazyn. Podczas pracy z plikami użytkownik pracuje ze ścieżkami katalogów, magazynem dysku oraz nazwami plików i katalogów. Natomiast strumień to sekwencja bajtów służąca do odczytu i zapisu w magazynie zapasowym, który może być jednym z kilku nośników magazynu (na przykład dysk lub pamięć). Tak jak istnieje kilka magazynów zapasowych innych niż dyski, tak samo istnieje kilka rodzajów strumieni innych niż strumienie plików, takie jak strumienie sieci, pamięci i potoku.

## <a name="files-and-directories"></a>Files and directories

You can use the types in the <xref:System.IO?displayProperty=nameWithType> namespace to interact with files and directories. Na przykład można pobierać i ustawiać właściwości plików i katalogów oraz pobierać kolekcje plików i katalogów na podstawie kryteriów wyszukiwania.

For path naming conventions and the ways to express a file path for Windows systems, including with the DOS device syntax supported in .NET Core 1.1 and later and the .NET Framework 4.6.2 and later, see [File path formats on Windows systems](file-path-formats.md).

Poniżej przedstawiono kilka powszechnie używanych klas związanych z plikami i katalogami:

- <xref:System.IO.File> - provides static methods for creating, copying, deleting, moving, and opening files, and helps create a <xref:System.IO.FileStream> object.

- <xref:System.IO.FileInfo> - provides instance methods for creating, copying, deleting, moving, and opening files, and helps create a <xref:System.IO.FileStream> object.

- <xref:System.IO.Directory> - provides static methods for creating, moving, and enumerating through directories and subdirectories.

- <xref:System.IO.DirectoryInfo> - provides instance methods for creating, moving, and enumerating through directories and subdirectories.

- <xref:System.IO.Path> - provides methods and properties for processing directory strings in a cross-platform manner.

You should always provide robust exception handling when calling filesystem methods. For more information, see [Handling I/O errors](handling-io-errors.md).

In addition to using these classes, Visual Basic users can use the methods and properties provided by the <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> class for file I/O.

See [How to: Copy Directories](how-to-copy-directories.md), [How to: Create a Directory Listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100)), and [How to: Enumerate Directories and Files](how-to-enumerate-directories-and-files.md).

## <a name="streams"></a>Strumienie

The abstract base class <xref:System.IO.Stream> supports reading and writing bytes. All classes that represent streams inherit from the <xref:System.IO.Stream> class. The <xref:System.IO.Stream> class and its derived classes provide a common view of data sources and repositories, and isolate the programmer from the specific details of the operating system and underlying devices.

Strumienie obejmują trzy podstawowe operacje:

- Odczyt — transfer danych ze strumienia do struktury danych, takiej jak tablica bajtów.

- Zapis — transfer danych ze strumienia do źródła danych.

- Wyszukiwanie — badanie i modyfikowanie bieżącej pozycji w strumieniu.

W zależności od podstawowego źródła danych lub repozytorium, strumień może obsługiwać tylko niektóre z tych możliwości. For example, the <xref:System.IO.Pipes.PipeStream> class does not support seeking. The <xref:System.IO.Stream.CanRead%2A>, <xref:System.IO.Stream.CanWrite%2A>, and <xref:System.IO.Stream.CanSeek%2A> properties of a stream specify the operations that the stream supports.

Poniżej przedstawiono niektóre powszechnie używane klasy strumieni:

- <xref:System.IO.FileStream> – for reading and writing to a file.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – for reading and writing to a file in isolated storage.

- <xref:System.IO.MemoryStream> – for reading and writing to memory as the backing store.

- <xref:System.IO.BufferedStream> – for improving performance of read and write operations.

- <xref:System.Net.Sockets.NetworkStream> – for reading and writing over network sockets.

- <xref:System.IO.Pipes.PipeStream> – for reading and writing over anonymous and named pipes.

- <xref:System.Security.Cryptography.CryptoStream> – for linking data streams to cryptographic transformations.

For an example of working with streams asynchronously, see [Asynchronous File I/O](asynchronous-file-i-o.md).

## <a name="readers-and-writers"></a>Readers and writers

The <xref:System.IO?displayProperty=nameWithType> namespace also provides types for reading encoded characters from streams and writing them to streams. Zazwyczaj strumienie są projektowane do obsługi bajtowych danych wejściowych i wyjściowych. Typy czytników i składników zapisywania obsługują konwersję zakodowanych znaków do i z postaci bajtowej, więc strumień może ukończyć operację. Each reader and writer class is associated with a stream, which can be retrieved through the class's `BaseStream` property.

Poniżej przedstawiono niektóre powszechnie używane klasy czytników i składników zapisywania:

- <xref:System.IO.BinaryReader> and <xref:System.IO.BinaryWriter> – for reading and writing primitive data types as binary values.

- <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> – for reading and writing characters by using an encoding value to convert the characters to and from bytes.

- <xref:System.IO.StringReader> and <xref:System.IO.StringWriter> – for reading and writing characters to and from strings.

- <xref:System.IO.TextReader> and <xref:System.IO.TextWriter> – serve as the abstract base classes for other readers and writers that read and write characters and strings, but not binary data.

See [How to: Read Text from a File](how-to-read-text-from-a-file.md), [How to: Write Text to a File](how-to-write-text-to-a-file.md), [How to: Read Characters from a String](how-to-read-characters-from-a-string.md), and [How to: Write Characters to a String](how-to-write-characters-to-a-string.md).

## <a name="asynchronous-io-operations"></a>Asynchronous I/O operations

Odczyt lub zapis dużej ilości danych może wymagać użycia wielu zasobów. Te zadania należy wykonywać asynchronicznie, jeśli aplikacja ma ciągle reagować na działania użytkownika. Podczas synchronicznych operacji We/Wy wątek interfejsu użytkownika jest blokowany, aż do zakończenia wykonywania zasobochłonnej operacji.  Use asynchronous I/O operations when developing Windows 8.x Store apps to prevent creating the impression that your app has stopped working.

The asynchronous members contain `Async` in their names, such as the <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>,  <xref:System.IO.Stream.ReadAsync%2A>, and <xref:System.IO.Stream.WriteAsync%2A> methods. You use these methods with the `async` and `await` keywords.

For more information, see [Asynchronous File I/O](asynchronous-file-i-o.md).

## <a name="compression"></a>Kompresja

Termin „kompresja” dotyczy procesu zmniejszania rozmiaru pliku, który ma być przechowywany. Dekompresja to proces wyodrębniania zawartości skompresowanego pliku, dzięki czemu będzie on miał format umożliwiający używanie go. The <xref:System.IO.Compression?displayProperty=nameWithType> namespace contains types for compressing and decompressing files and streams.

Następujące klasy są często używane podczas kompresowania i dekompresowania plików i strumieni:

- <xref:System.IO.Compression.ZipArchive> – for creating and retrieving entries in the zip archive.

- <xref:System.IO.Compression.ZipArchiveEntry> – for representing a compressed file.

- <xref:System.IO.Compression.ZipFile> – for creating,  extracting, and opening a compressed package.

- <xref:System.IO.Compression.ZipFileExtensions> – for creating and extracting entries in a compressed package.

- <xref:System.IO.Compression.DeflateStream> – for compressing and decompressing streams using the Deflate algorithm.

- <xref:System.IO.Compression.GZipStream> – for compressing and decompressing streams in gzip data format.

See [How to: Compress and Extract Files](how-to-compress-and-extract-files.md).

## <a name="isolated-storage"></a>Isolated storage

Wydzielona pamięć masowa to mechanizm magazynu, który dostarcza izolację i bezpieczeństwo przez definiowanie ustandaryzowanych metod kojarzenia kodu z zapisanymi danymi. Ta pamięć masowa oferuje wirtualny system plików, który jest izolowany dla konkretnego użytkownika, zestawu i (opcjonalnie) domeny. Wydzielona pamięć masowa jest szczególnie użyteczna, gdy aplikacja nie ma uprawnień dostępu do plików użytkownika. Można zapisać ustawienia lub pliki aplikacji w sposób, który jest kontrolowany przez zasady zabezpieczeń komputera.

Isolated storage is not available for Windows 8.x Store apps; instead, use application data classes in the <xref:Windows.Storage?displayProperty=nameWithType> namespace. For more information, see [Application data](https://docs.microsoft.com/previous-versions/windows/apps/hh464917%28v=win.10%29).

Podczas implementowania wydzielonej pamięci masowej często używane są następujące klasy:

- <xref:System.IO.IsolatedStorage.IsolatedStorage> – provides the base class for isolated storage implementations.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile> – provides an isolated storage area that contains files and directories.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> - exposes a file within isolated storage.

See [Isolated Storage](isolated-storage.md).

## <a name="io-operations-in-windows-store-apps"></a>I/O operations in Windows Store apps

The [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] contains many of the types for reading from and writing to streams; however, this set does not include all the .NET Framework I/O types.

Some important differences to note when using I/O operations in Windows 8.x Store apps:

- Types specifically related to file operations, such as <xref:System.IO.File>, <xref:System.IO.FileInfo>, <xref:System.IO.Directory> and <xref:System.IO.DirectoryInfo>, are not included in the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Instead, use the types in the <xref:Windows.Storage?displayProperty=nameWithType> namespace of the Windows Runtime, such as <xref:Windows.Storage.StorageFile> and <xref:Windows.Storage.StorageFolder>.

- Isolated storage is not available; instead, use [application data](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)).

- Use asynchronous methods, such as <xref:System.IO.Stream.ReadAsync%2A> and <xref:System.IO.Stream.WriteAsync%2A>, to prevent blocking the UI thread.

- The path-based compression types <xref:System.IO.Compression.ZipFile> and <xref:System.IO.Compression.ZipFileExtensions> are not available. Instead, use the types in the <xref:Windows.Storage.Compression?displayProperty=nameWithType> namespace.

W razie potrzeby można wykonywać konwersje między strumieniami programu .NET Framework i strumieniami środowiska wykonawczego systemu Windows. For more information, see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md) or <xref:System.IO.WindowsRuntimeStreamExtensions>.

For more information about I/O operations in a Windows 8.x Store app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).

## <a name="io-and-security"></a>I/O and security

When you use the classes in the <xref:System.IO?displayProperty=nameWithType> namespace, you must follow operating system security requirements such as access control lists (ACLs) to control access to files and directories. This requirement is in addition to any <xref:System.Security.Permissions.FileIOPermission> requirements. Listami ACL można zarządzać programowo. For more information, see [How to: Add or Remove Access Control List Entries](how-to-add-or-remove-access-control-list-entries.md).

Domyślne zasady zabezpieczeń uniemożliwiają aplikacjom internetowym i intranetowym dostęp do plików na komputerze użytkownika. W związku z tym podczas pisania kodu, który zostanie pobrany przez Internet lub intranet, nie należy używać klas We/Wy, które wymagają ścieżki do pliku fizycznego. Instead, use [isolated storage](isolated-storage.md) for traditional .NET Framework applications, or use [application data](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) for Windows 8.x Store apps.

Sprawdzanie zabezpieczeń jest wykonywane tylko wtedy, gdy jest konstruowany strumień. W związku z tym nie należy otwierać strumienia, a następnie przekazywać go do kodu lub domeny aplikacji o niższym poziomie zaufania.

## <a name="related-topics"></a>Tematy pokrewne

- [Common I/O Tasks](common-i-o-tasks.md)\
Lista zadań We/Wy skojarzonych z plikami, katalogami, i strumieniami oraz łącza do odpowiedniej zawartości i przykładów dla każdego zadania.

- [Asynchronous File I/O](asynchronous-file-i-o.md)\
Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.

- [Isolated Storage](isolated-storage.md)\
Opis mechanizmu pamięci masowej danych, który dostarcza izolację i bezpieczeństwo przez definiowanie ustandaryzowanych opcji kojarzenia kodu z zapisanymi danymi.

- [Pipes](pipe-operations.md)\
Opis operacji wykonywanych w anonimowych i nazwanych potokach w programie .NET Framework.

- [Memory-Mapped Files](memory-mapped-files.md)\
Opis plików zamapowanych w pamięci, które zawierają zawartość plików znajdujących się na dysku w pamięci wirtualnej. Zamapowanych w pamięci plików można używać, aby edytować bardzo duże pliki i tworzyć współużytkowaną pamięć służącą do komunikacji między procesami.
