---
title: Klasy stosowane w operacjach We/Wy platformy .NET Framework i systemie plików
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: 2c696d5b8c83ae55caf61e4710630ad1e34c088d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401774"
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>Klasy stosowane w .NET Framework File I/O i systemie plików (Visual Basic)

W poniższej tabeli wymieniono klasy, które są często używane dla .NET Framework plików we/wy, pogrupowane według klas we/wy plików, klasy służące do tworzenia strumieni i klasy służące do odczytu i zapisu w strumieniach.  
  
Aby zapoznać się z bardziej kompleksową listą, zobacz [Omówienie biblioteki klas](../../../../standard/class-library-overview.md).  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Podstawowe klasy we/wy dla plików, dysków i katalogów  

 W poniższej tabeli wymieniono i opisano główne klasy używane dla operacji we/wy na plikach.  
  
|Klasa|Opis|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|Zapewnia statyczne metody tworzenia, przechodzenia i wyliczania katalogów i podkatalogów.|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|Zawiera metody wystąpień służące do tworzenia, przechodzenia i wyliczania katalogów i podkatalogów.|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|Zawiera metody wystąpień służące do tworzenia, przechodzenia i wyliczania na dyskach.|  
|<xref:System.IO.File?displayProperty=nameWithType>|Zapewnia statyczne metody tworzenia, kopiowania, usuwania, przemieszczania i otwierania plików oraz ułatwia tworzenie `FileStream` .|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|Definiuje stałe dla dostępu Odczyt, zapis lub odczyt/zapis do pliku.|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|Zawiera atrybuty plików i katalogów, takich jak `Archive` , `Hidden` , i `ReadOnly` .|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|Zapewnia statyczne metody tworzenia, kopiowania, usuwania, przemieszczania i otwierania plików oraz ułatwia tworzenie `FileStream` .|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|Kontroluje sposób otwierania pliku. Ten parametr jest określony w wielu konstruktorach dla `FileStream` i `IsolatedStorageFileStream` , oraz dla `Open` metod <xref:System.IO.File> i <xref:System.IO.FileInfo> .|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|Definiuje stałe do kontrolowania typu dostępu inne strumienie plików mogą mieć ten sam plik.|  
|<xref:System.IO.Path?displayProperty=nameWithType>|Dostarcza metody i właściwości do przetwarzania ciągów katalogów.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|Kontroluje dostęp do plików i folderów przez definiowanie <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A> , <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A> <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> i <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> uprawnień.|  
  
## <a name="classes-used-to-create-streams"></a>Klasy służące do tworzenia strumieni  

 W poniższej tabeli wymieniono i opisano główne klasy służące do tworzenia strumieni.  
  
|Klasa|Opis|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|Dodaje warstwę buforowania do operacji odczytu i zapisu w innym strumieniu.|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|Obsługuje losowy dostęp do plików za poorednictwem <xref:System.IO.FileStream.Seek%2A> metody. <xref:System.IO.FileStream>domyślnie otwiera pliki synchronicznie, ale obsługuje również operację asynchroniczną.|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|Tworzy strumień, którego magazyn pomocniczy jest pamięcią, a nie plikiem.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|Zapewnia źródłowy strumień danych dla dostępu do sieci.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|Definiuje strumień, który łączy strumienie danych z transformacjami kryptograficznymi.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Klasy służące do odczytu i zapisu do strumieni  

 W poniższej tabeli przedstawiono konkretne klasy służące do odczytu i zapisu do plików ze strumieniami.  
  
|**Klasa**|**Opis**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|Odczytuje zakodowane ciągi i pierwotne typy danych z <xref:System.IO.FileStream> .|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|Zapisuje zakodowane ciągi i typy danych pierwotnych do <xref:System.IO.FileStream> .|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|Odczytuje znaki z <xref:System.IO.FileStream> , używając <xref:System.IO.StreamReader.CurrentEncoding%2A> do konwersji znaków na i z bajtów. <xref:System.IO.StreamReader>ma Konstruktor, który podejmuje próbę sprawdzenia poprawności <xref:System.IO.StreamReader.CurrentEncoding%2A> dla danego strumienia, na podstawie obecności <xref:System.IO.StreamReader.CurrentEncoding%2A> konkretnej preambuły, takiej jak znacznik kolejności bajtów.|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|Zapisuje znaki w `FileStream` , używając <xref:System.IO.StreamWriter.Encoding%2A> do konwersji znaków na bajty.|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|Odczytuje znaki z `String` . Wyjście może być strumieniem w dowolnym kodowaniu lub `String` .|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|Zapisuje znaki w `String` . Wyjście może być strumieniem w dowolnym kodowaniu lub `String` .|  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie strumieni](../../../../standard/io/composing-streams.md)
- [We/wy plików i strumieni](../../../../standard/io/index.md)
- [Asynchroniczne operacje we/wy pliku](../../../../standard/io/asynchronous-file-i-o.md)
- [Podstawowe informacje o .NET Framework File I/O i systemie plików (Visual Basic)](basics-of-net-framework-file-io-and-the-file-system.md)
