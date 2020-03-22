---
title: Klasy stosowane w operacjach We/Wy platformy .NET Framework i systemie plików
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: fe70f8fb655579049bb36fc324d04530259d25f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348928"
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>Klasy stosowane w .NET Framework File I/O i systemie plików (Visual Basic)

W poniższych tabelach przedstawiono klasy często używane dla plików .NET Framework We/Wy, podzielone na klasy we/wy pliku, klasy używane do tworzenia strumieni i klasy używane do odczytywania i zapisu do strumieni.  
  
Aby uzyskać bardziej wyczerpującą listę, zobacz [Omówienie biblioteki klas](../../../../standard/class-library-overview.md).  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Podstawowe klasy we/wy dla plików, dysków i katalogów  

 W poniższej tabeli wymieniono i opisano główne klasy używane dla we/wy pliku.  
  
|Klasa|Opis|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|Zawiera statyczne metody tworzenia, przenoszenia i wyliczania za pośrednictwem katalogów i podkatalogów.|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|Zawiera metody wystąpienia do tworzenia, przenoszenia i wyliczania za pośrednictwem katalogów i podkatalogów.|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|Zawiera metody wystąpienia do tworzenia, przenoszenia i wyliczania za pośrednictwem dysków.|  
|<xref:System.IO.File?displayProperty=nameWithType>|Zawiera statyczne metody tworzenia, kopiowania, usuwania, przenoszenia i otwierania plików `FileStream`oraz pomocy w tworzeniu pliku .|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|Definiuje stałe dostępu do odczytu, zapisu lub odczytu/zapisu do pliku.|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|Udostępnia atrybuty plików i `Archive`katalogów, takie jak , `Hidden`i `ReadOnly`.|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|Zawiera statyczne metody tworzenia, kopiowania, usuwania, przenoszenia i otwierania plików `FileStream`oraz pomocy w tworzeniu pliku .|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|Określa sposób otwarcia pliku. Ten parametr jest określony w wielu `FileStream` `IsolatedStorageFileStream`konstruktorach `Open` dla <xref:System.IO.File> <xref:System.IO.FileInfo>i , oraz dla metod i .|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|Definiuje stałe do kontrolowania typu dostępu innych strumieni plików może mieć do tego samego pliku.|  
|<xref:System.IO.Path?displayProperty=nameWithType>|Zawiera metody i właściwości przetwarzania ciągów katalogów.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|Steruje dostępem do plików i <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A> <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>folderów, definiując program , <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> i <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> uprawnienia.|  
  
## <a name="classes-used-to-create-streams"></a>Klasy używane do tworzenia strumieni  

 W poniższej tabeli wymieniono i opisano główne klasy używane do tworzenia strumieni.  
  
|Klasa|Opis|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|Dodaje warstwę buforowania do odczytu i zapisu operacji na innym strumieniu.|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|Obsługuje losowy dostęp <xref:System.IO.FileStream.Seek%2A> do plików za pomocą swojej metody. <xref:System.IO.FileStream>domyślnie otwiera pliki synchronicznie, ale obsługuje również działanie asynchroniczne.|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|Tworzy strumień, którego magazyn kopii zapasowych jest pamięci, a nie pliku.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|Udostępnia podstawowy strumień danych dla dostępu do sieci.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|Definiuje strumień, który łączy strumienie danych z przekształceniami kryptograficznymi.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Klasy używane do odczytywania ze strumieni i zapisu do  

 W poniższej tabeli przedstawiono określone klasy używane do odczytywania i zapisywania do plików ze strumieniami.  
  
|**Klasa**|**Opis**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|Odczytuje zakodowane ciągi i pierwotne <xref:System.IO.FileStream>typy danych z pliku .|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|Zapisuje zakodowane ciągi i pierwotne <xref:System.IO.FileStream>typy danych do pliku .|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|Odczytuje znaki <xref:System.IO.FileStream>z <xref:System.IO.StreamReader.CurrentEncoding%2A> programu , używając do konwersji znaków do i z bajtów. <xref:System.IO.StreamReader>ma konstruktora, który <xref:System.IO.StreamReader.CurrentEncoding%2A> próbuje ustalić poprawność dla danego <xref:System.IO.StreamReader.CurrentEncoding%2A>strumienia, na podstawie obecności preambuły specyficznej dla wykonawcy, takiej jak znacznik kolejności bajtów.|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|Zapisuje znaki `FileStream`do <xref:System.IO.StreamWriter.Encoding%2A> programu , używając do konwersji znaków na bajty.|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|Odczytuje znaki `String`z pliku . Dane wyjściowe mogą być strumieniem w `String`dowolnym kodowaniu lub .|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|Zapisuje znaki `String`do pliku . Dane wyjściowe mogą być strumieniem w `String`dowolnym kodowaniu lub .|  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie strumieni](../../../../standard/io/composing-streams.md)
- [We/Wy plików i strumieni](../../../../standard/io/index.md)
- [Asynchroniczne We/Wy pliku](../../../../standard/io/asynchronous-file-i-o.md)
- [Podstawowe informacje o .NET Framework File I/O i systemie plików (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
