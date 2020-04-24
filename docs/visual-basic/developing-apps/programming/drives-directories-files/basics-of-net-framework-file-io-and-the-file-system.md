---
title: Podstawowe informacje o .NET Framework File I/O i systemie plików
ms.date: 07/20/2015
helpviewer_keywords:
- file access, file I/O in Visual Basic
- file attributes, determining
- streams, fundamental operations
- file permissions
- streams
- streams, definition
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
ms.openlocfilehash: 5d60d0089d042c0be343c741c26de0b4b7778d6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348944"
---
# <a name="basics-of-net-framework-file-io-and-the-file-system-visual-basic"></a>Podstawowe informacje o .NET Framework File I/O i systemie plików (Visual Basic)

Klasy w <xref:System.IO> przestrzeni nazw są używane do pracy z dyskami, plikami i katalogami.

<xref:System.IO> Przestrzeń nazw zawiera klasy <xref:System.IO.File> i <xref:System.IO.Directory> , które zapewniają funkcję .NET Framework, która operuje na plikach i katalogach. Ponieważ metody tych obiektów są statycznymi lub udostępnionymi składowymi, można ich używać bezpośrednio bez tworzenia wystąpienia klasy. Skojarzone z tymi klasami są <xref:System.IO.FileInfo> klasami i <xref:System.IO.DirectoryInfo> , które będą znane użytkownikom `My` funkcji. Aby użyć tych klas, należy w pełni zakwalifikować nazwy lub zaimportować odpowiednie przestrzenie nazw, dołączając `Imports` instrukcje na początku kodu, którego to dotyczy. Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).

> [!NOTE]
> W innych tematach w tej sekcji `My.Computer.FileSystem` Użyj obiektu zamiast `System.IO` klas do pracy z dyskami, plikami i katalogami. `My.Computer.FileSystem` Obiekt jest przeznaczony głównie do użytku w Visual Basic programów. `System.IO`klasy są przeznaczone do użycia w dowolnym języku, który obsługuje .NET Framework, w tym Visual Basic.

## <a name="definition-of-a-stream"></a>Definicja strumienia

.NET Framework używa strumieni do obsługi odczytu i zapisu do plików. Strumień można traktować jako jednowymiarowy zestaw danych ciągłych, który ma początek i koniec oraz miejsce, gdzie kursor wskazuje bieżącą pozycję w strumieniu.

![Kursor wyświetla bieżącą pozycję w strumieniu FILESTREAM.](./media/basics-of-net-framework-file-io-and-the-file-system/filestream-cursor-position.gif)

## <a name="stream-operations"></a>Operacje przesyłania strumieniowego

Dane zawarte w strumieniu mogą pochodzić z pamięci, pliku lub gniazda TCP/IP. Strumienie mają podstawowe operacje, które można zastosować do nich:

- **Odczytywanie**. Można odczytywać ze strumienia, transferować dane ze strumienia do struktury danych, takie jak ciąg lub tablica bajtów.

- **Zapisywanie**. Do strumienia można zapisywać dane ze źródła danych.

- **Wyszukiwanie**. Możesz wysyłać zapytania i modyfikować swoją pozycję w strumieniu.

Aby uzyskać więcej informacji, zobacz [Tworzenie strumieni](../../../../standard/io/composing-streams.md).

## <a name="types-of-streams"></a>Typy strumieni

W .NET Framework strumień jest reprezentowany przez <xref:System.IO.Stream> klasę, która tworzy klasę abstrakcyjną dla wszystkich innych strumieni. Nie można bezpośrednio utworzyć wystąpienia <xref:System.IO.Stream> klasy, ale należy użyć jednej z implementowanych klas.

Istnieje wiele typów strumieni, ale na potrzeby pracy z danymi wejściowymi/wyjściowymi (we/wy), najważniejsze typy to <xref:System.IO.FileStream> Klasa, która zapewnia sposób odczytu i zapisu do plików, a także <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> klasę, która zapewnia sposób tworzenia plików i katalogów w izolowanym magazynie. Inne strumienie, których można używać podczas pracy z plikami we/wy plików:

- <xref:System.IO.BufferedStream>

- <xref:System.Security.Cryptography.CryptoStream>

- <xref:System.IO.MemoryStream>

- <xref:System.Net.Sockets.NetworkStream>.

W poniższej tabeli wymieniono zadania często wykonywane przy użyciu strumienia:

|Do|Zobacz|
|---|---|
|Odczyt i zapis w pliku danych|[Instrukcje: Odczyt i zapis we właśnie utworzonym pliku danych](../../../../standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|
|Odczytaj tekst z pliku|[Instrukcje: Odczytywanie tekstu z pliku](../../../../standard/io/how-to-read-text-from-a-file.md)|
|Zapisz tekst w pliku|[Instrukcje: Zapisywanie tekstu w pliku](../../../../standard/io/how-to-write-text-to-a-file.md)|
|Odczytywanie znaków z ciągu|[Instrukcje: Odczytywanie znaków z ciągu](../../../../standard/io/how-to-read-characters-from-a-string.md)|
|Zapisz znaki w ciągu|[Instrukcje: Zapisywanie znaków w ciągu](../../../../standard/io/how-to-write-characters-to-a-string.md)|
|Szyfrowanie danych|[Szyfrowanie danych](../../../../standard/security/encrypting-data.md)|
|Odszyfruj dane|[Odszyfrowywanie danych](../../../../standard/security/decrypting-data.md)|

## <a name="file-access-and-attributes"></a>Dostęp do plików i atrybuty

Można kontrolować sposób tworzenia, <xref:System.IO.FileAccess>otwierania i udostępniania <xref:System.IO.FileMode>plików, a <xref:System.IO.FileShare> także wyliczenia, które zawierają flagi używane przez konstruktory <xref:System.IO.FileStream> klasy. Na przykład po otwarciu lub utworzeniu nowego <xref:System.IO.FileStream>elementu <xref:System.IO.FileMode> Wyliczenie pozwala określić, czy plik jest otwierany do dołączenia, czy nowy plik zostanie utworzony, jeśli określony plik nie istnieje, niezależnie od tego, czy plik jest zastępowany i tak dalej.

<xref:System.IO.FileAttributes> Wyliczenie umożliwia gromadzenie informacji specyficznych dla pliku. <xref:System.IO.FileAttributes> Wyliczenie zwraca przechowywane atrybuty pliku, na przykład czy jest skompresowany, zaszyfrowany, ukryty, tylko do odczytu, archiwum, katalog, plik systemowy lub plik tymczasowy.

Poniższa tabela zawiera listę zadań związanych z dostępem do plików i atrybutami plików:

|Do|Zobacz|
|---|---|
|Otwieranie i dołączanie tekstu do pliku dziennika|[Instrukcje: Otwieranie pliku dziennika i dołączanie do niego](../../../../standard/io/how-to-open-and-append-to-a-log-file.md)|
|Określanie atrybutów pliku|<xref:System.IO.FileAttributes>|

## <a name="file-permissions"></a>Uprawnienia do pliku

Kontrolowanie dostępu do plików i katalogów można wykonać przy użyciu <xref:System.Security.Permissions.FileIOPermission> klasy. Może to być szczególnie ważne w przypadku deweloperów pracujących z formularzami sieci Web, które domyślnie są uruchamiane w kontekście specjalnego konta użytkownika lokalnego o nazwie ASPNET, który jest tworzony w ramach instalacji ASP.NET i .NET Framework. Gdy taka aplikacja żąda dostępu do zasobu, konto użytkownika ASPNET ma ograniczone uprawnienia, co może uniemożliwić użytkownikowi wykonywanie akcji, takich jak zapisywanie do pliku z aplikacji sieci Web. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.FileIOPermission>.

## <a name="isolated-file-storage"></a>File Storage izolowane

Magazyn izolowany to próba rozwiązania problemów utworzonych podczas pracy z plikami, w których użytkownik lub kod może nie mieć wystarczających uprawnień. Izolowany magazyn przypisuje każdemu użytkownikowi przedział danych, który może zawierać co najmniej jeden magazyn. Magazyny mogą być odizolowane od siebie przez użytkownika i przez zestaw. Tylko użytkownik i zestaw, które utworzyły magazyn, mają do niego dostęp. Magazyn działa jako kompletny wirtualny system plików — w ramach jednego magazynu można tworzyć katalogi i pliki oraz manipulować nimi.

W poniższej tabeli wymieniono zadania często związane z izolowanym magazynem plików.

|Do|Zobacz|
|---|---|
|Tworzenie magazynu izolowanego|[Instrukcje: Uzyskiwanie magazynów dla izolowanego magazynu](../../../../standard/io/how-to-obtain-stores-for-isolated-storage.md)|
|Wyliczanie magazynów izolowanych|[Instrukcje: Wykazywanie magazynów dla izolowanego magazynu](../../../../standard/io/how-to-enumerate-stores-for-isolated-storage.md)|
|Usuwanie magazynu izolowanego|[Instrukcje: Usuwanie danych z izolowanego magazynu](../../../../standard/io/how-to-delete-stores-in-isolated-storage.md)|
|Tworzenie pliku lub katalogu w izolowanym magazynie|[Instrukcje: Tworzenie plików i katalogów w izolowanym magazynie](../../../../standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|
|Znajdowanie pliku w izolowanym magazynie|[Instrukcje: Wyszukiwanie istniejących plików i katalogów w izolowanym magazynie](../../../../standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|
|Odczyt lub zapis do pliku w izolowanym magazynie|[Instrukcje: Odczyt i zapis w plikach w izolowanym magazynie](../../../../standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|
|Usuwanie pliku lub katalogu w izolowanym magazynie|[Instrukcje: Usuwanie plików i katalogów w izolowanym magazynie](../../../../standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|

## <a name="file-events"></a>Zdarzenia plików

<xref:System.IO.FileSystemWatcher> Składnik umożliwia śledzenie zmian w plikach i katalogach w systemie lub na dowolnym komputerze, do którego masz dostęp do sieci. Na przykład, jeśli plik zostanie zmodyfikowany, można wysłać użytkownikowi alert informujący o tym, że została wprowadzona zmiana. Gdy wystąpią zmiany, zgłaszane jest jedno lub więcej zdarzeń, przechowywane w buforze i przekazywane do <xref:System.IO.FileSystemWatcher> składnika do przetwarzania.

## <a name="see-also"></a>Zobacz też

- [Tworzenie strumieni](../../../../standard/io/composing-streams.md)
- [We/wy plików i strumieni](../../../../standard/io/index.md)
- [Asynchroniczne operacje we/wy pliku](../../../../standard/io/asynchronous-file-i-o.md)
- [Klasy stosowane w .NET Framework File I/O i systemie plików (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)
