---
title: Podstawowe informacje o .NET Framework File I/O i systemie plików (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- file access, file I/O in Visual Basic
- file attributes, determining
- streams, fundamental operations
- file permissions
- streams
- streams, definition
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
ms.openlocfilehash: 3ff305a6b22918681561ed7262a7377dbdf7aadc
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591511"
---
# <a name="basics-of-net-framework-file-io-and-the-file-system-visual-basic"></a>Podstawowe informacje o .NET Framework File I/O i systemie plików (Visual Basic)

Klasy w <xref:System.IO> przestrzeni nazw są używane do pracy z stacje, plików i katalogów.

<xref:System.IO> Przestrzeń nazw zawiera <xref:System.IO.File> i <xref:System.IO.Directory> klasy, które udostępniają funkcje środowiska .NET Framework, które obsługuje pliki i katalogi. Ponieważ metody te obiekty są statyczne lub udostępnionych elementów członkowskich, można ich używać bezpośrednio, bez tworzenia wystąpienia klasy najpierw. Skojarzone z tych klas są <xref:System.IO.FileInfo> i <xref:System.IO.DirectoryInfo> klasy, które nie będą niczym nowym użytkownikom `My` funkcji. Aby korzystać z tych klas, muszą w pełni kwalifikowania nazwy lub zaimportować odpowiednie przestrzenie nazw, umieszczając `Imports` instrukcji na początku kodu, których to dotyczy. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).

> [!NOTE]
> Inne tematy w tej sekcji użyto `My.Computer.FileSystem` zamiast obiektu `System.IO` klasy do pracy z stacje, plików i katalogów. `My.Computer.FileSystem` Obiektu jest przeznaczony głównie do użycia w programach Visual Basic. `System.IO` klasy są przeznaczone do użycia za pomocą dowolnego języka, który obsługuje program .NET Framework, w tym Visual Basic.

## <a name="definition-of-a-stream"></a>Definicja Stream

.NET Framework używa strumieni umożliwiają odczytywanie z oraz zapisywanie do plików. Strumień można traktować jako jednowymiarowa zestaw danych ciągłych, która zawiera początek i koniec i gdzie kursor wskazuje bieżącą pozycję w strumieniu.

![Kursor zawiera bieżącą pozycję w strumieniu plików.](./media/basics-of-net-framework-file-io-and-the-file-system/filestream-cursor-position.gif)

## <a name="stream-operations"></a>Operacje Stream

Dane zawarte w strumieniu mogą pochodzić z pamięci, plik lub gniazda TCP/IP. Strumienie są podstawowe operacje, które można zastosować do nich:

- **Odczytywanie**. Możesz przeczytać ze strumienia, transfer danych ze strumienia do struktury danych, takich jak ciąg lub tablicę bajtów.

- **Zapisywanie**. Możesz napisać do strumienia, transfer danych ze źródła danych w strumieniu.

- **Wyszukiwanie**. Można zapytania i modyfikację swojego położenia wśród wątków strumienia.

Aby uzyskać więcej informacji, zobacz [strumieni redagowanie](../../../../standard/io/composing-streams.md).

## <a name="types-of-streams"></a>Typy strumieni

W .NET Framework, strumień jest reprezentowany przez <xref:System.IO.Stream> klasy, która stanowi klasa abstrakcyjna, dla wszystkich innych strumieni. Nie można bezpośrednio utworzyć wystąpienie <xref:System.IO.Stream> klasy, ale należy użyć jednej z klas implementuje.

Istnieje wiele typów strumieni, ale na potrzeby pracy z pliku wejścia/wyjścia (We/Wy) są najważniejsze typy <xref:System.IO.FileStream> klasy, która umożliwia odczytywanie i zapisywanie do plików, a <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> klasy, która umożliwia tworzenie plików i katalogów w wydzielonej pamięci masowej. Inne strumienie, które mogą być używane podczas pracy z we/wy obejmują:

- <xref:System.IO.BufferedStream>

- <xref:System.Security.Cryptography.CryptoStream>

- <xref:System.IO.MemoryStream>

- <xref:System.Net.Sockets.NetworkStream>.

W poniższej tabeli wymieniono zadania najczęściej wykonywane za pomocą usługi stream:

|Zadanie|Zobacz|
|---|---|
|Odczyt i zapis do pliku danych|[Instrukcje: Odczyt i zapis w nowo utworzonym pliku danych](../../../../standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|
|Odczytywanie tekstu z pliku|[Instrukcje: Odczytywanie tekstu z pliku](../../../../standard/io/how-to-read-text-from-a-file.md)|
|Zapisywanie tekstu do pliku|[Instrukcje: Zapisywanie tekstu do pliku](../../../../standard/io/how-to-write-text-to-a-file.md)|
|Odczytywanie znaków z ciągu|[Instrukcje: Odczytywanie znaków z ciągu](../../../../standard/io/how-to-read-characters-from-a-string.md)|
|Zapisywanie znaków w ciągu|[Instrukcje: Zapisywanie znaków w ciągu](../../../../standard/io/how-to-write-characters-to-a-string.md)|
|Szyfrowanie danych|[Szyfrowanie danych](../../../../standard/security/encrypting-data.md)|
|Odszyfrowywanie danych|[Odszyfrowywanie danych](../../../../standard/security/decrypting-data.md)|

## <a name="file-access-and-attributes"></a>Dostęp do plików i atrybuty

Można kontrolować, jak pliki są tworzone, otwarty i udostępniane <xref:System.IO.FileAccess>, <xref:System.IO.FileMode>, i <xref:System.IO.FileShare> wyliczenia, zawierające flagi używane przez konstruktorów z <xref:System.IO.FileStream> klasy. Na przykład, gdy możesz otworzyć lub utworzyć nowy <xref:System.IO.FileStream>, <xref:System.IO.FileMode> wyliczenie umożliwia określenie, czy plik jest otwarty do wykonania operacji dołączania, czy nowy plik jest utworzony, jeśli określony plik nie istnieje, czy plik jest zastępowany i tak dalej.

<xref:System.IO.FileAttributes> Wyliczenie umożliwia zebranie informacji specyficznych dla pliku. <xref:System.IO.FileAttributes> Wyliczenie zwraca przechowywanych atrybuty pliku, np. czy jest skompresowany, szyfrowanie, ukryty, tylko do odczytu, archiwum, katalog, plik systemowy lub pliku tymczasowego.

Poniższa tabela zawiera listę zadań obejmujących dostęp do plików i atrybuty plików:

|Zadanie|Zobacz|
|---|---|
|Otwieranie i dołączanie tekstu do pliku dziennika|[Instrukcje: Otwieranie i dołączanie do pliku dziennika](../../../../standard/io/how-to-open-and-append-to-a-log-file.md)|
|Określania atrybutów pliku|<xref:System.IO.FileAttributes>|

## <a name="file-permissions"></a>Uprawnienia do pliku

Kontrolowanie dostępu do plików i katalogów może odbywać się przy użyciu <xref:System.Security.Permissions.FileIOPermission> klasy. Może to być szczególnie ważne dla deweloperów korzystających z formularzy sieci Web, które domyślnie są uruchamiane w kontekście specjalne lokalnego konta użytkownika o nazwie ASPNET, który jest tworzony w ramach instalacji programu ASP.NET i .NET Framework. W przypadku takich żądań dostępu do aplikacji do zasobu, konto ASPNET ma ograniczoną uprawnienia, które mogą uniemożliwić wykonywanie akcji, takich jak zapisywanie do pliku z aplikacji sieci Web przez użytkownika. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.FileIOPermission>.

## <a name="isolated-file-storage"></a>Izolowany magazyn plików

Wydzielona pamięć masowa jest próba do rozwiązywania problemów, utworzony podczas pracy z plikami, gdzie użytkownika lub kod może nie mają wystarczających uprawnień. Wydzielona pamięć masowa przypisuje każdemu użytkownikowi przedział danych, który może zawierać co najmniej jeden. Sklepy mogą być od siebie odizolowane według użytkownika i zestawu. Tylko użytkownika i zestawu, który utworzono magazyn dla mieć do niego dostęp. Magazyn działa jak Pełna wirtualny system plików — w ramach jednego magazynu można tworzyć i modyfikować pliki i katalogi.

Poniższa tabela zawiera listę zadań zwykle powiązanych ze izolowany magazyn plików.

|Zadanie|Zobacz|
|---|---|
|Utwórz w izolowanym magazynie|[Instrukcje: Uzyskiwanie magazynów dla wydzielonej pamięci masowej](../../../../standard/io/how-to-obtain-stores-for-isolated-storage.md)|
|Wyliczanie izolowanych magazynów|[Instrukcje: Wyliczanie magazynów dla wydzielonej pamięci masowej](../../../../standard/io/how-to-enumerate-stores-for-isolated-storage.md)|
|Usuń izolowanym magazynie|[Instrukcje: Usuwanie magazynów w wydzielonej pamięci masowej](../../../../standard/io/how-to-delete-stores-in-isolated-storage.md)|
|Tworzenie pliku lub katalogu w wydzielonej pamięci masowej|[Instrukcje: Tworzenie plików i katalogów w wydzielonej pamięci masowej](../../../../standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|
|Znajdź plik w wydzielonej pamięci masowej|[Instrukcje: Wyszukiwanie istniejących plików i katalogów w wydzielonej pamięci masowej](../../../../standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|
|Odczytać lub zapisać do pliku w wydzielonej pamięci masowej|[Instrukcje: Odczyt i zapis w plikach w wydzielonej pamięci masowej](../../../../standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|
|Usuwanie pliku lub katalogu w wydzielonej pamięci masowej|[Instrukcje: Usuwanie plików i katalogów w wydzielonej pamięci masowej](../../../../standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|

## <a name="file-events"></a>Plik zdarzeń

<xref:System.IO.FileSystemWatcher> Składnik umożliwia obserwowanie zmian plików i katalogów w systemie lub na dowolnym komputerze, do których masz dostęp do sieci. Na przykład jeśli plik zostanie zmodyfikowany, możesz chcieć powiadomi użytkownika czy miała miejsce zmiana. O zmianach, jedno lub więcej zdarzeń są wywoływane, przechowywane w buforze i przekazywane <xref:System.IO.FileSystemWatcher> składnik do przetworzenia.

## <a name="see-also"></a>Zobacz także

- [Tworzenie strumieni](../../../../standard/io/composing-streams.md)
- [We/Wy plików i strumieni](../../../../standard/io/index.md)
- [Asynchroniczne operacje We/Wy pliku](../../../../standard/io/asynchronous-file-i-o.md)
- [Klasy stosowane w .NET Framework File I/O i systemie plików (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)
