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

Klasy w <xref:System.IO> obszarze nazw są używane do pracy z dyskami, plikami i katalogami.

Obszar <xref:System.IO> nazw zawiera <xref:System.IO.File> <xref:System.IO.Directory> i klasy, które zapewniają funkcję .NET Framework, która manipuluje plikami i katalogami. Ponieważ metody tych obiektów są statyczne lub udostępnione elementy członkowskie, można ich używać bezpośrednio bez tworzenia wystąpienia klasy pierwszy. Skojarzone z tymi <xref:System.IO.FileInfo> klasami są i <xref:System.IO.DirectoryInfo> klasy, które `My` będą znane użytkownikom funkcji. Aby użyć tych klas, należy w pełni zakwalifikować nazwy lub `Imports` zaimportować odpowiednie przestrzenie nazw, dołączając instrukcje na początku kodu, którego dotyczy problem. Aby uzyskać więcej informacji, zobacz [Oświadczenie importu (.NET Obszar nazw i Typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).

> [!NOTE]
> Inne tematy w tej `My.Computer.FileSystem` sekcji używają `System.IO` obiektu zamiast klas do pracy z dyskami, plikami i katalogami. Obiekt `My.Computer.FileSystem` jest przeznaczony głównie do użytku w programach Visual Basic. `System.IO`klasy są przeznaczone do użytku przez dowolny język, który obsługuje .NET Framework, w tym Visual Basic.

## <a name="definition-of-a-stream"></a>Definicja strumienia

.NET Framework używa strumieni do obsługi odczytu i zapisu do plików. Strumień można myśleć jako jednowymiarowy zestaw ciągłych danych, który ma początek i koniec i gdzie kursor wskazuje bieżącą pozycję w strumieniu.

![Kursor pokazuje bieżącą pozycję w strumieniu plików.](./media/basics-of-net-framework-file-io-and-the-file-system/filestream-cursor-position.gif)

## <a name="stream-operations"></a>Operacje strumienia

Dane zawarte w strumieniu mogą pochodzić z pamięci, pliku lub gniazda TCP/IP. Strumienie mają podstawowe operacje, które mogą być stosowane do nich:

- **Czytanie**. Można odczytać ze strumienia, przesyłając dane ze strumienia do struktury danych, takich jak ciąg lub tablica bajtów.

- **Pisanie**. Można zapisywać do strumienia, przesyłając dane ze źródła danych do strumienia.

- **Szukam**. Można zbadać i zmodyfikować swoją pozycję w strumieniu.

Aby uzyskać więcej informacji, zobacz [Tworzenie strumieni](../../../../standard/io/composing-streams.md).

## <a name="types-of-streams"></a>Typy strumieni

W .NET Framework strumień jest reprezentowany <xref:System.IO.Stream> przez klasę, która tworzy klasę abstrakcyjną dla wszystkich innych strumieni. Nie można bezpośrednio utworzyć wystąpienia <xref:System.IO.Stream> klasy, ale należy użyć jednej z klas, które implementuje.

Istnieje wiele typów strumieni, ale do celów pracy z plikiem input/output (We/Wy), najważniejsze typy są <xref:System.IO.FileStream> klasy, która zapewnia <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> sposób odczytu i zapisu do plików i klasy, która zapewnia sposób tworzenia plików i katalogów w izolowanym magazynie. Inne strumienie, które mogą być używane podczas pracy z we/wy pliku obejmują:

- <xref:System.IO.BufferedStream>

- <xref:System.Security.Cryptography.CryptoStream>

- <xref:System.IO.MemoryStream>

- <xref:System.Net.Sockets.NetworkStream>.

W poniższej tabeli wymieniono zadania często wykonywane za pomocą strumienia:

|Do|Zobacz|
|---|---|
|Odczytywanie i zapisywanie w pliku danych|[Instrukcje: odczyt i zapis we właśnie utworzonym pliku danych](../../../../standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|
|Odczytywanie tekstu z pliku|[Porady: odczyt tekstu z pliku](../../../../standard/io/how-to-read-text-from-a-file.md)|
|Pisanie tekstu do pliku|[Instrukcje: zapisywanie tekstu w pliku](../../../../standard/io/how-to-write-text-to-a-file.md)|
|Odczytywanie znaków z ciągu|[Instrukcje: odczytywanie znaków z ciągu](../../../../standard/io/how-to-read-characters-from-a-string.md)|
|Zapisywanie znaków w ciągu|[Instrukcje: zapisywanie znaków w ciągu](../../../../standard/io/how-to-write-characters-to-a-string.md)|
|Szyfrowanie danych|[Szyfrowanie danych](../../../../standard/security/encrypting-data.md)|
|Odszyfrowywanie danych|[Odszyfrowywanie danych](../../../../standard/security/decrypting-data.md)|

## <a name="file-access-and-attributes"></a>Dostęp do plików i atrybuty

Można kontrolować sposób tworzenia, otwierania i <xref:System.IO.FileAccess>udostępniania <xref:System.IO.FileMode>plików <xref:System.IO.FileShare> programowi , i wyliczeń, które <xref:System.IO.FileStream> zawierają flagi używane przez konstruktorów klasy. Na przykład po otwarciu lub <xref:System.IO.FileStream>utworzeniu nowego , <xref:System.IO.FileMode> wyliczenie pozwala określić, czy plik jest otwarty do dodawania, czy nowy plik jest tworzony, jeśli określony plik nie istnieje, czy plik jest zastępowany i tak dalej.

Wyliczenie <xref:System.IO.FileAttributes> umożliwia zbieranie informacji specyficznych dla pliku. Wyliczenie <xref:System.IO.FileAttributes> zwraca przechowywane atrybuty pliku, takie jak to, czy jest on skompresowany, zaszyfrowany, ukryty, tylko do odczytu, archiwum, katalog, plik systemowy lub plik tymczasowy.

W poniższej tabeli wymieniono zadania związane z dostępem do plików i atrybutami plików:

|Do|Zobacz|
|---|---|
|Otwieranie i dołączanie tekstu do pliku dziennika|[Instrukcje: otwieranie pliku dziennika i dołączanie do niego](../../../../standard/io/how-to-open-and-append-to-a-log-file.md)|
|Określanie atrybutów pliku|<xref:System.IO.FileAttributes>|

## <a name="file-permissions"></a>Uprawnienia do plików

Kontrolowanie dostępu do plików i katalogów można wykonać za <xref:System.Security.Permissions.FileIOPermission> pomocą klasy. Może to być szczególnie ważne dla deweloperów pracujących z formularzami sieci Web, które domyślnie są uruchamiane w kontekście specjalnego konta użytkownika lokalnego o nazwie ASPNET, które jest tworzone jako część instalacji ASP.NET i .NET Framework. Gdy taka aplikacja żąda dostępu do zasobu, konto użytkownika aspnet ma ograniczone uprawnienia, które mogą uniemożliwić użytkownikowi wykonywanie akcji, takich jak zapisywanie do pliku z aplikacji sieci Web. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.FileIOPermission>.

## <a name="isolated-file-storage"></a>Izolowany magazyn plików

Magazyn izolowany jest próbą rozwiązania problemów utworzonych podczas pracy z plikami, w których użytkownik lub kod może nie mieć niezbędnych uprawnień. Izolowane przechowywanie przypisuje każdemu użytkownikowi przedział danych, który może pomieścić jeden lub więcej magazynów. Magazyny mogą być odizolowane od siebie przez użytkownika i przez zestaw. Dostęp do niego ma tylko użytkownik i zestaw, który utworzył magazyn. Sklep działa jako kompletny wirtualny system plików — w jednym sklepie można tworzyć katalogi i pliki oraz manipulować nimi.

W poniższej tabeli wymieniono zadania często skojarzone z izolowanym magazynem plików.

|Do|Zobacz|
|---|---|
|Tworzenie izolowanego magazynu|[Porady: uzyskiwanie magazynów dla izolowanego magazynu](../../../../standard/io/how-to-obtain-stores-for-isolated-storage.md)|
|Wyliczaj izolowane sklepy|[Instrukcje: wyliczanie magazynów dla wydzielonej pamięci masowej](../../../../standard/io/how-to-enumerate-stores-for-isolated-storage.md)|
|Usuwanie izolowanego magazynu|[Porady: usuwanie danych z izolowanego magazynu](../../../../standard/io/how-to-delete-stores-in-isolated-storage.md)|
|Tworzenie pliku lub katalogu w magazynie izolowanym|[Instrukcje: tworzenie plików i katalogów w wydzielonej pamięci masowej](../../../../standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|
|Znajdowanie pliku w izolowanym magazynie|[Instrukcje: znajdowanie istniejących plików i katalogów w wydzielonej pamięci masowej](../../../../standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|
|Odczyt lub zapis do pliku w izolowanym magazynie|[Instrukcje: odczyt i zapis w plikach w wydzielonej pamięci masowej](../../../../standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|
|Usuwanie pliku lub katalogu w magazynie izolowanym|[Instrukcje: usuwanie plików i katalogów w wydzielonej pamięci masowej](../../../../standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|

## <a name="file-events"></a>Zdarzenia pliku

Składnik <xref:System.IO.FileSystemWatcher> umożliwia obserwowanie zmian w plikach i katalogach w systemie lub na dowolnym komputerze, do którego masz dostęp do sieci. Na przykład jeśli plik jest modyfikowany, można wysłać użytkownikowi alert, że zmiana miała miejsce. Gdy wystąpią zmiany, jedno lub więcej zdarzeń są wywoływane, przechowywane w buforze i przekazywane do składnika <xref:System.IO.FileSystemWatcher> do przetwarzania.

## <a name="see-also"></a>Zobacz też

- [Tworzenie strumieni](../../../../standard/io/composing-streams.md)
- [We/Wy plików i strumieni](../../../../standard/io/index.md)
- [Asynchroniczne We/Wy pliku](../../../../standard/io/asynchronous-file-i-o.md)
- [Klasy stosowane w .NET Framework File I/O i systemie plików (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)
