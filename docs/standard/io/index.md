---
title: We/Wy plików i strumienia — .NET
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
ms.openlocfilehash: 3c69e0fd23b1f8bc11fe908c66ba492f31a53f30
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706598"
---
# <a name="file-and-stream-io"></a>We/Wy plików i strumieni

Termin „We/Wy (wejście/wyjście) plików i strumieni” dotyczy transferu danych do lub z nośnika magazynowania. W platformie .NET `System.IO` Framework przestrzenie nazw zawierają typy, które umożliwiają odczyt i zapis, zarówno synchronicznie, jak i asynchronicznie, w strumieniach danych i plikach. Te przestrzenie nazw zawierają również typy, które wykonują kompresję i dekompresję plików, oraz typy, które umożliwiają komunikację za pośrednictwem potoków i portów szeregowych.

Plik to uporządkowana i nazwana kolekcja bajtów, która ma stały magazyn. Podczas pracy z plikami użytkownik pracuje ze ścieżkami katalogów, magazynem dysku oraz nazwami plików i katalogów. Natomiast strumień to sekwencja bajtów służąca do odczytu i zapisu w magazynie zapasowym, który może być jednym z kilku nośników magazynu (na przykład dysk lub pamięć). Tak jak istnieje kilka magazynów zapasowych innych niż dyski, tak samo istnieje kilka rodzajów strumieni innych niż strumienie plików, takie jak strumienie sieci, pamięci i potoku.

## <a name="files-and-directories"></a>Pliki i katalogi

Typy w obszarze <xref:System.IO?displayProperty=nameWithType> nazw można używać do interakcji z plikami i katalogami. Na przykład można pobierać i ustawiać właściwości plików i katalogów oraz pobierać kolekcje plików i katalogów na podstawie kryteriów wyszukiwania.

Aby zapoznać się z konwencjami nazewnictwa ścieżek i sposobami wyrażania ścieżki pliku dla systemów Windows, w tym ze składnią urządzenia DOS obsługiwaną w programie .NET Core 1.1 i nowszych oraz w programie .NET Framework 4.6.2 i [nowszych, zobacz Formaty ścieżek plików w systemach Windows](file-path-formats.md).

Poniżej przedstawiono kilka powszechnie używanych klas związanych z plikami i katalogami:

- <xref:System.IO.File>- zapewnia statyczne metody tworzenia, kopiowania, usuwania, przenoszenia i otwierania plików oraz pomaga w tworzeniu <xref:System.IO.FileStream> obiektu.

- <xref:System.IO.FileInfo>- udostępnia metody instancji do tworzenia, kopiowania, usuwania, przenoszenia <xref:System.IO.FileStream> i otwierania plików oraz pomaga utworzyć obiekt.

- <xref:System.IO.Directory>- zapewnia statyczne metody tworzenia, przenoszenia i wyliczania za pośrednictwem katalogów i podkatalogów.

- <xref:System.IO.DirectoryInfo>- udostępnia metody instancji do tworzenia, przenoszenia i wyliczania za pośrednictwem katalogów i podkatalogów.

- <xref:System.IO.Path>- udostępnia metody i właściwości przetwarzania ciągów katalogów w sposób wieloplatformowy.

Podczas wywoływania metod systemu plików należy zawsze zapewnić niezawodną obsługę wyjątków. Aby uzyskać więcej informacji, zobacz [Obsługa błędów we/wy](handling-io-errors.md).

Oprócz korzystania z tych klas użytkownicy języka Visual Basic mogą używać <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> metod i właściwości dostarczonych przez klasę dla we/wy pliku.

Zobacz [Jak: Kopiowanie katalogów](how-to-copy-directories.md), [Jak: Tworzenie listy katalogów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))i [Jak: Wyliczanie katalogów i plików](how-to-enumerate-directories-and-files.md).

## <a name="streams"></a>Strumienie

Abstrakcyjna klasa <xref:System.IO.Stream> podstawowa obsługuje odczytianie i pisanie bajtów. Wszystkie klasy reprezentujące strumienie <xref:System.IO.Stream> dziedziczą z klasy. Klasa <xref:System.IO.Stream> i jej klasy pochodne zapewniają wspólny widok źródeł danych i repozytoriów oraz izolować programistę od szczegółowych informacji o systemie operacyjnym i urządzeniach źródłowych.

Strumienie obejmują trzy podstawowe operacje:

- Odczyt — transfer danych ze strumienia do struktury danych, takiej jak tablica bajtów.

- Zapis — transfer danych ze strumienia do źródła danych.

- Wyszukiwanie — badanie i modyfikowanie bieżącej pozycji w strumieniu.

W zależności od podstawowego źródła danych lub repozytorium, strumień może obsługiwać tylko niektóre z tych możliwości. Na przykład <xref:System.IO.Pipes.PipeStream> klasa nie obsługuje szukania. , <xref:System.IO.Stream.CanRead%2A> <xref:System.IO.Stream.CanWrite%2A>i <xref:System.IO.Stream.CanSeek%2A> właściwości strumienia określić operacje, które obsługuje strumień.

Poniżej przedstawiono niektóre powszechnie używane klasy strumieni:

- <xref:System.IO.FileStream>– do czytania i zapisu do pliku.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>– do czytania i zapisu do pliku w izolowanym magazynie.

- <xref:System.IO.MemoryStream>– do czytania i zapisywania w pamięci jako magazynu podkładowego.

- <xref:System.IO.BufferedStream>– dla poprawy wydajności operacji odczytu i zapisu.

- <xref:System.Net.Sockets.NetworkStream>– do czytania i pisania przez gniazda sieciowe.

- <xref:System.IO.Pipes.PipeStream>– do czytania i pisania za anonimowych i nazwanych potoków.

- <xref:System.Security.Cryptography.CryptoStream>– do łączenia strumieni danych z przekształceniami kryptograficznymi.

Na przykład pracy ze strumieniami asynchronicznie zobacz [Asynchroniczne we/wy pliku](asynchronous-file-i-o.md).

## <a name="readers-and-writers"></a>Czytelnicy i pisarze

Obszar <xref:System.IO?displayProperty=nameWithType> nazw zawiera również typy do odczytywania zakodowanych znaków ze strumieni i zapisywania ich do strumieni. Zazwyczaj strumienie są projektowane do obsługi bajtowych danych wejściowych i wyjściowych. Typy czytników i składników zapisywania obsługują konwersję zakodowanych znaków do i z postaci bajtowej, więc strumień może ukończyć operację. Każda klasa czytnika i modułu zapisującego jest skojarzona `BaseStream` ze strumieniem, który można pobrać za pośrednictwem właściwości klasy.

Poniżej przedstawiono niektóre powszechnie używane klasy czytników i składników zapisywania:

- <xref:System.IO.BinaryReader>oraz <xref:System.IO.BinaryWriter> – do odczytywania i zapisywania pierwotnych typów danych jako wartości binarnych.

- <xref:System.IO.StreamReader>oraz <xref:System.IO.StreamWriter> – do odczytywania i pisania znaków przy użyciu wartości kodowania do konwertowania znaków do i z bajtów.

- <xref:System.IO.StringReader>oraz <xref:System.IO.StringWriter> – do czytania i pisania znaków do i z ciągów.

- <xref:System.IO.TextReader>i <xref:System.IO.TextWriter> — służyć jako abstrakcyjne klasy podstawowe dla innych czytelników i pisarzy, które odczytują i zapisują znaki i ciągi, ale nie dane binarne.

Zobacz [jak: Czytać tekst z pliku](how-to-read-text-from-a-file.md), [Jak: Pisanie tekstu do pliku](how-to-write-text-to-a-file.md), [Jak: Odczytywanie znaków z ciągu](how-to-read-characters-from-a-string.md)i [Jak: Pisanie znaków do ciągu](how-to-write-characters-to-a-string.md).

## <a name="asynchronous-io-operations"></a>Operacje we/wy asynchronicznej

Odczyt lub zapis dużej ilości danych może wymagać użycia wielu zasobów. Te zadania należy wykonywać asynchronicznie, jeśli aplikacja ma ciągle reagować na działania użytkownika. Podczas synchronicznych operacji We/Wy wątek interfejsu użytkownika jest blokowany, aż do zakończenia wykonywania zasobochłonnej operacji.  Podczas tworzenia aplikacji ze Sklepu Windows 8.x używaj operacji asynchronicznych, aby zapobiec tworzeniu wrażenia, że aplikacja przestała działać.

Asynchroniczne elementy `Async` członkowskie zawierają w swoich <xref:System.IO.Stream.CopyToAsync%2A> <xref:System.IO.Stream.FlushAsync%2A>nazwach, takie jak , , <xref:System.IO.Stream.ReadAsync%2A>, i <xref:System.IO.Stream.WriteAsync%2A> metody. Używasz tych metod ze `async` `await` słowami kluczowymi i.

Aby uzyskać więcej informacji, zobacz [Asynchronous File We/Wy](asynchronous-file-i-o.md).

## <a name="compression"></a>Kompresja

Termin „kompresja” dotyczy procesu zmniejszania rozmiaru pliku, który ma być przechowywany. Dekompresja to proces wyodrębniania zawartości skompresowanego pliku, dzięki czemu będzie on miał format umożliwiający używanie go. Obszar <xref:System.IO.Compression?displayProperty=nameWithType> nazw zawiera typy kompresji i dekompresji plików i strumieni.

Następujące klasy są często używane podczas kompresowania i dekompresowania plików i strumieni:

- <xref:System.IO.Compression.ZipArchive>– do tworzenia i pobierania wpisów w archiwum zip.

- <xref:System.IO.Compression.ZipArchiveEntry>– do reprezentowania skompresowanego pliku.

- <xref:System.IO.Compression.ZipFile>– do tworzenia, wydobywania i otwierania skompresowanego opakowania.

- <xref:System.IO.Compression.ZipFileExtensions>– do tworzenia i wyodrębniania wpisów w pakiecie skompresowanym.

- <xref:System.IO.Compression.DeflateStream>– do kompresji i dekompresji strumieni za pomocą algorytmu Deflate.

- <xref:System.IO.Compression.GZipStream>– do kompresji i dekompresji strumieni w formacie danych gzip.

Zobacz [jak: Kompresować i wyodrębniać pliki](how-to-compress-and-extract-files.md).

## <a name="isolated-storage"></a>Magazyn odizolowany

Wydzielona pamięć masowa to mechanizm magazynu, który dostarcza izolację i bezpieczeństwo przez definiowanie ustandaryzowanych metod kojarzenia kodu z zapisanymi danymi. Ta pamięć masowa oferuje wirtualny system plików, który jest izolowany dla konkretnego użytkownika, zestawu i (opcjonalnie) domeny. Wydzielona pamięć masowa jest szczególnie użyteczna, gdy aplikacja nie ma uprawnień dostępu do plików użytkownika. Można zapisać ustawienia lub pliki aplikacji w sposób, który jest kontrolowany przez zasady zabezpieczeń komputera.

Izolowana pamięć nie jest dostępna dla aplikacji ze Sklepu Windows 8.x; Zamiast tego należy użyć <xref:Windows.Storage?displayProperty=nameWithType> klas danych aplikacji w obszarze nazw. Aby uzyskać więcej informacji, zobacz [Dane aplikacji](https://docs.microsoft.com/previous-versions/windows/apps/hh464917%28v=win.10%29).

Podczas implementowania wydzielonej pamięci masowej często używane są następujące klasy:

- <xref:System.IO.IsolatedStorage.IsolatedStorage>– zapewnia klasę podstawową dla implementacji magazynu izolowanego.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>– zapewnia izolowany obszar przechowywania zawierający pliki i katalogi.

- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>- udostępnia plik w izolowanym magazynie.

Zobacz [Izolowany magazyn](isolated-storage.md).

## <a name="io-operations-in-windows-store-apps"></a>Operacje we/wy w aplikacjach ze Sklepu Windows

Aplikacje .NET dla systemu Windows 8.x Store zawierają wiele typów do odczytu i zapisu do strumieni; Jednak ten zestaw nie zawiera wszystkich typów we/wy .NET Framework.

Niektóre ważne różnice, które należy zauważyć podczas korzystania z operacji we/wy w aplikacjach ze Sklepu Windows 8.x:

- Typy związane z operacjami plików, <xref:System.IO.FileInfo> <xref:System.IO.Directory> takie <xref:System.IO.DirectoryInfo>jak <xref:System.IO.File>, , i , nie są uwzględniane w aplikacjach sklepu .NET dla systemu Windows 8.x. Zamiast tego należy użyć <xref:Windows.Storage?displayProperty=nameWithType> typów w przestrzeni nazw środowiska <xref:Windows.Storage.StorageFile> <xref:Windows.Storage.StorageFolder>uruchomieniowego systemu Windows, takich jak i .

- Magazyn izolowany nie jest dostępny; zamiast tego użyj [danych aplikacji](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)).

- Użyj metod asynchronicznych, <xref:System.IO.Stream.ReadAsync%2A> takich <xref:System.IO.Stream.WriteAsync%2A>jak i , aby zapobiec blokowaniu wątku interfejsu użytkownika.

- Typy <xref:System.IO.Compression.ZipFile> kompresji oparte <xref:System.IO.Compression.ZipFileExtensions> na ścieżkach i nie są dostępne. Zamiast tego należy użyć <xref:Windows.Storage.Compression?displayProperty=nameWithType> typów w obszarze nazw.

W razie potrzeby można wykonywać konwersje między strumieniami programu .NET Framework i strumieniami środowiska wykonawczego systemu Windows. Aby uzyskać więcej informacji, zobacz [Jak: Konwertować między strumieniami programu .NET Framework i strumieniami środowiska uruchomieniowego systemu Windows](how-to-convert-between-dotnet-streams-and-winrt-streams.md) lub <xref:System.IO.WindowsRuntimeStreamExtensions>.

Aby uzyskać więcej informacji na temat operacji we/wy w aplikacji ze Sklepu Windows 8.x, zobacz [Szybki start: Odczytywanie i zapisywanie plików](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).

## <a name="io-and-security"></a>We/Wy i bezpieczeństwo

Korzystając z klas w <xref:System.IO?displayProperty=nameWithType> obszarze nazw, należy przestrzegać wymagań zabezpieczeń systemu operacyjnego, takich jak listy kontroli dostępu (ACL), aby kontrolować dostęp do plików i katalogów. Wymóg ten jest uzupełniony o wszelkie <xref:System.Security.Permissions.FileIOPermission> wymagania. Listami ACL można zarządzać programowo. Aby uzyskać więcej informacji, zobacz [Jak: Dodawanie lub usuwanie wpisów listy kontroli dostępu](how-to-add-or-remove-access-control-list-entries.md).

Domyślne zasady zabezpieczeń uniemożliwiają aplikacjom internetowym i intranetowym dostęp do plików na komputerze użytkownika. W związku z tym podczas pisania kodu, który zostanie pobrany przez Internet lub intranet, nie należy używać klas We/Wy, które wymagają ścieżki do pliku fizycznego. Zamiast tego należy użyć [izolowanego magazynu](isolated-storage.md) dla tradycyjnych aplikacji .NET Framework lub użyć [danych aplikacji](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) dla aplikacji ze Sklepu Windows 8.x.

Sprawdzanie zabezpieczeń jest wykonywane tylko wtedy, gdy jest konstruowany strumień. W związku z tym nie należy otwierać strumienia, a następnie przekazywać go do kodu lub domeny aplikacji o niższym poziomie zaufania.

## <a name="related-topics"></a>Powiązane tematy

- [Typowe zadania we/wy](common-i-o-tasks.md)\
Lista zadań We/Wy skojarzonych z plikami, katalogami, i strumieniami oraz łącza do odpowiedniej zawartości i przykładów dla każdego zadania.

- [We/Wy pliku asynchronicznego](asynchronous-file-i-o.md)\
Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.

- [Magazyn izolowany](isolated-storage.md)\
Opis mechanizmu pamięci masowej danych, który dostarcza izolację i bezpieczeństwo przez definiowanie ustandaryzowanych opcji kojarzenia kodu z zapisanymi danymi.

- [Rury](pipe-operations.md)\
Opis operacji wykonywanych w anonimowych i nazwanych potokach w programie .NET Framework.

- [Pliki mapowane w pamięci](memory-mapped-files.md)\
Opis plików zamapowanych w pamięci, które zawierają zawartość plików znajdujących się na dysku w pamięci wirtualnej. Zamapowanych w pamięci plików można używać, aby edytować bardzo duże pliki i tworzyć współużytkowaną pamięć służącą do komunikacji między procesami.
