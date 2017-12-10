---
title: "Podstawowe informacje o .NET Framework File I/O i systemie plików (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- file access, file I/O in Visual Basic
- file attributes, determining
- streams, fundamental operations
- file permissions
- streams
- streams, definition
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53bd56647d04c40c44a240edcd084f0719c3d4aa
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="basics-of-net-framework-file-io-and-the-file-system-visual-basic"></a>Podstawowe informacje o .NET Framework File I/O i systemie plików (Visual Basic)
Klasy w <xref:System.IO> przestrzeni nazw są używane do pracy z dysków, plików i katalogów.  
  
 <xref:System.IO> Przestrzeń nazw zawiera <xref:System.IO.File> i <xref:System.IO.Directory> klasy, które zawierają [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] funkcje, które obsługuje plików i katalogów. Ponieważ metody te obiekty są statyczne lub udostępniane elementy członkowskie, można ich używać bezpośrednio bez utworzenia wystąpienia klasy najpierw. Skojarzone z tych klas są <xref:System.IO.FileInfo> i <xref:System.IO.DirectoryInfo> klasy, które będzie znany z `My` funkcji. Aby korzystać z tych klas, musisz pełni zakwalifikować nazwy lub zaimportować odpowiednie przestrzenie nazw przy tym `Imports` instrukcji na początku kodu. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
> [!NOTE]
>  Inne tematy w tej sekcji Użyj `My.Computer.FileSystem` obiekt zamiast `System.IO` klasy do pracy z dysków, plików i katalogów. `My.Computer.FileSystem` Obiekt jest przeznaczony głównie do użytku w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programy. `System.IO`klasy są przeznaczone do użytku przez dowolnego języka, który obsługuje [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], takie jak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="definition-of-a-stream"></a>Definicja strumienia  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Używa strumienie do obsługi odczytywanie z oraz zapisywanie do plików. Strumień można traktować jako zbiór jednowymiarowa ciągłe danych, który ma początek i koniec i gdy kursor wskazuje bieżącą pozycję w strumieniu.  
  
 ![Kursor zawiera bieżącą pozycję w strumieniu plików. ] (../../../../visual-basic/developing-apps/programming/drives-directories-files/media/filestream.gif "FileStream")  
  
## <a name="stream-operations"></a>Operacje na strumieniach  
 Dane zawarte w strumieniu może pochodzić z pamięci, plik lub gniazda TCP/IP. Strumienie są podstawowe operacje, które można zastosować do nich:  
  
-   Odczytywanie. Możesz przeczytać ze strumienia, transfer danych ze strumienia do struktury danych, takie jak ciąg lub tablicę bajtów.  
  
-   **Zapisywanie**. Możesz zapisywać w strumieniu transferu danych ze źródła danych do strumienia.  
  
-   **Wyszukiwanie**. Można zbadać i modyfikować z pozycją w strumieniu.  
  
 Aby uzyskać więcej informacji, zobacz [strumieni redagowanie](../../../../../docs/standard/io/composing-streams.md).  
  
## <a name="types-of-streams"></a>Typy strumieni  
 W [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], strumień jest reprezentowana przez <xref:System.IO.Stream> klasy, która stanowi klasa abstrakcyjna, dla wszystkich innych strumieni. Nie można bezpośrednio utworzyć wystąpienia <xref:System.IO.Stream> klasy, ale muszą używać jednej z klas implementuje.  
  
 Istnieje wiele typów strumieni, ale na potrzeby pracy z pliku wejścia/wyjścia (We/Wy) są najważniejsze typy <xref:System.IO.FileStream> klasy, która umożliwia odczytywać i zapisywać pliki, i <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> klasy, która umożliwia tworzenie plików i katalogów w izolowanym magazynie. Innych strumieni, które mogą być używane podczas pracy z We/Wy plików obejmują:  
  
-   <xref:System.IO.BufferedStream>  
  
-   <xref:System.Security.Cryptography.CryptoStream>  
  
-   <xref:System.IO.MemoryStream>  
  
-   <xref:System.Net.Sockets.NetworkStream>.  
  
 W poniższej tabeli wymieniono zadania zazwyczaj są realizowane przy użyciu strumienia:  
  
|Do|Zobacz|
|---|---|   
|Odczyt i zapis do pliku danych|[Porady: Odczyt i zapis do pliku danych nowo utworzony](../../../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Odczytaj tekst z pliku|[Porady: Odczyt tekstu z pliku](../../../../../docs/standard/io/how-to-read-text-from-a-file.md)|  
|Zapisywanie tekstu do pliku|[Porady: zapisywanie tekstu do pliku](../../../../../docs/standard/io/how-to-write-text-to-a-file.md)|  
|Odczytywanie znaków z ciągu|[Porady: odczytywanie znaków z ciągu](../../../../../docs/standard/io/how-to-read-characters-from-a-string.md)|  
|Zapisywanie do ciągu znaków|[Porady: zapisywanie znaków ciągu](../../../../../docs/standard/io/how-to-write-characters-to-a-string.md)|  
|Szyfrowanie danych|[Szyfrowanie danych](../../../../../docs/standard/security/encrypting-data.md)|  
|Odszyfrowywanie danych|[Odszyfrowywanie danych](../../../../../docs/standard/security/decrypting-data.md)|  
  
## <a name="file-access-and-attributes"></a>Dostęp do plików i atrybuty  
 Można kontrolować sposób tworzenia plików, otwarty i udostępnione <xref:System.IO.FileAccess>, <xref:System.IO.FileMode>, i <xref:System.IO.FileShare> wyliczenia, zawierające flagi używane przez konstruktorów <xref:System.IO.FileStream> klasy. Na przykład, gdy można otworzyć lub utworzyć nowy <xref:System.IO.FileStream>, <xref:System.IO.FileMode> wyliczenie umożliwia określenie, czy plik jest otwarty dołączania, czy zostanie utworzony nowy plik, jeśli określony plik nie istnieje, czy plik jest zastępowany i tak dalej.  
  
 <xref:System.IO.FileAttributes> Wyliczenie umożliwia zbieranie informacji na temat określonego pliku. <xref:System.IO.FileAttributes> Wyliczenie zwraca przechowywanych atrybuty pliku, np. czy jest skompresowany, zaszyfrowane, ukryta, tylko do odczytu, archiwum, katalog, plik systemowy lub pliku tymczasowego.  
  
 W poniższej tabeli wymieniono zadania dotyczące uzyskiwania dostępu do plików i atrybutów pliku:  
  
|Do|Zobacz|  
|---|---|
|Otwórz i dołączać tekstu do pliku dziennika|[Porady: otwieranie i Dołącz do pliku dziennika](../../../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)|  
|Określić atrybutów pliku|<xref:System.IO.FileAttributes>|  
  
## <a name="file-permissions"></a>Uprawnienia do pliku  
 Kontrolowanie dostępu do plików i katalogów można zrobić za pomocą <xref:System.Security.Permissions.FileIOPermission> klasy. Może to być szczególnie ważne dla deweloperów korzystających z formularzy sieci Web, która domyślnie uruchamiane w kontekście konta użytkownika lokalnego specjalne o nazwie ASPNET, który jest tworzony jako część [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] instalacji. Podczas takich aplikacji żądań dostępu do zasobu, konto ASPNET ma ograniczone uprawnienia, które mogą uniemożliwić użytkownikowi wykonywanie akcji, takich jak zapis do pliku z aplikacji sieci Web. Aby uzyskać więcej informacji, zobacz [uprawnień zabezpieczeń](http://msdn.microsoft.com/en-us/b03757b4-e926-4196-b738-3733ced2bda0)i <xref:System.Security.Permissions.FileIOPermission>.  
  
## <a name="isolated-file-storage"></a>Pliku izolowanego magazynu  
 Izolowany magazyn jest próba rozwiązywania problemów podczas pracy z plikami, gdy użytkownik lub kod może nie niezbędne uprawnienia. Izolowany magazyn przypisuje każdego użytkownika przedział danych, które mogą zawierać jeden lub więcej magazynów. Magazyny można odizolować od siebie przez użytkownika i przez zestaw. Tylko użytkownika i zestawu, który utworzono magazyn jest do niego dostęp. Magazyn działa jako zakończenie wirtualnym systemie plików — w ramach jednego magazynu można utworzyć i manipulowania katalogów i plików.  
  
 Poniższa tabela zawiera listę zadań zwykle powiązanych z magazynu izolowanego pliku.  
  
|Do|Zobacz|
|---|---|  
|Tworzenie izolowanego magazynu|[Porady: uzyskiwanie magazynów dla izolowanego magazynu](../../../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)|  
|Wyliczanie izolowanych magazynów|[Porady: wykazywanie magazynów dla izolowanego magazynu](../../../../../docs/standard/io/how-to-enumerate-stores-for-isolated-storage.md)|  
|Usuwanie izolowanego magazynu|[Porady: Usuń magazyny w izolowanym magazynie](../../../../../docs/standard/io/how-to-delete-stores-in-isolated-storage.md)|  
|Utwórz plik lub katalog w izolowanym magazynie|[Porady: tworzenie plików i katalogów w izolowanym magazynie](../../../../../docs/standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|  
|Znajdź plik w izolowanym magazynie|[Porady: wyszukiwanie istniejących plików i katalogów w izolowanym magazynie](../../../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|  
|Odczytywanie i zapisywanie do pliku w magazynie insolated|[Porady: Odczyt i zapis w plikach w izolowanym magazynie](../../../../../docs/standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|  
|Usuń plik lub katalog w izolowanym magazynie|[Porady: usuwanie plików i katalogów w izolowanym magazynie](../../../../../docs/standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|  
  
## <a name="file-events"></a>Zdarzenia pliku  
 <xref:System.IO.FileSystemWatcher> Składnik umożliwia oczekiwał na zmiany plików i katalogów w systemie lub na dowolnym komputerze, do których masz dostęp do sieci. Na przykład jeśli plik został zmodyfikowany, możesz powiadomi użytkownika czy miała miejsce zmiana. Podczas wprowadzania zmian, co najmniej jednego zdarzenia wywoływane, przechowywane w buforze i przekazać do <xref:System.IO.FileSystemWatcher> składnika do przetwarzania.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie strumieni](../../../../../docs/standard/io/composing-streams.md)  
 [We/Wy plików i strumieni](https://msdn.microsoft.com/library/k3352a4t)  
 [Asynchroniczne We/Wy pliku](https://msdn.microsoft.com/library/kztecsys)  
 [Klasy stosowane w .NET Framework File I/O i systemie plików (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)
