---
title: Klasy stosowane w .NET Framework File I/O i systemie plików (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: fe70f8fb655579049bb36fc324d04530259d25f2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348928"
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
|<xref:System.IO.File?displayProperty=nameWithType>|Zapewnia statyczne metody tworzenia, kopiowania, usuwania, przemieszczania i otwierania plików oraz ułatwia tworzenie `FileStream`.|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|Definiuje stałe dla dostępu Odczyt, zapis lub odczyt/zapis do pliku.|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|Zawiera atrybuty dla plików i katalogów, takich jak `Archive`, `Hidden`i `ReadOnly`.|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|Zapewnia statyczne metody tworzenia, kopiowania, usuwania, przemieszczania i otwierania plików oraz ułatwia tworzenie `FileStream`.|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|Kontroluje sposób otwierania pliku. Ten parametr jest określony w wielu konstruktorach dla `FileStream` i `IsolatedStorageFileStream`i dla `Open` metod <xref:System.IO.File> i <xref:System.IO.FileInfo>.|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|Definiuje stałe do kontrolowania typu dostępu inne strumienie plików mogą mieć ten sam plik.|  
|<xref:System.IO.Path?displayProperty=nameWithType>|Dostarcza metody i właściwości do przetwarzania ciągów katalogów.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|Kontroluje dostęp do plików i folderów przez definiowanie uprawnień <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> i <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>.|  
  
## <a name="classes-used-to-create-streams"></a>Klasy służące do tworzenia strumieni  

 W poniższej tabeli wymieniono i opisano główne klasy służące do tworzenia strumieni.  
  
|Klasa|Opis|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|Dodaje warstwę buforowania do operacji odczytu i zapisu w innym strumieniu.|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|Obsługuje losowy dostęp do plików za poorednictwem metody <xref:System.IO.FileStream.Seek%2A>. <xref:System.IO.FileStream> domyślnie otwiera pliki synchronicznie, ale obsługuje również operację asynchroniczną.|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|Tworzy strumień, którego magazyn pomocniczy jest pamięcią, a nie plikiem.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|Zapewnia źródłowy strumień danych dla dostępu do sieci.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|Definiuje strumień, który łączy strumienie danych z transformacjami kryptograficznymi.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Klasy służące do odczytu i zapisu do strumieni  

 W poniższej tabeli przedstawiono konkretne klasy służące do odczytu i zapisu do plików ze strumieniami.  
  
|**Określonej**|**Opis**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|Odczytuje zakodowane ciągi i pierwotne typy danych z <xref:System.IO.FileStream>.|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|Zapisuje zakodowane ciągi i typy danych pierwotnych do <xref:System.IO.FileStream>.|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|Odczytuje znaki z <xref:System.IO.FileStream>przy użyciu <xref:System.IO.StreamReader.CurrentEncoding%2A> do konwersji znaków na i z bajtów. <xref:System.IO.StreamReader> ma konstruktora, który podejmuje próbę sprawdzenia poprawnej <xref:System.IO.StreamReader.CurrentEncoding%2A> dla danego strumienia, w oparciu o obecność <xref:System.IO.StreamReader.CurrentEncoding%2A>j preambuły, takiej jak znacznik kolejności bajtów.|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|Zapisuje znaki w `FileStream`przy użyciu <xref:System.IO.StreamWriter.Encoding%2A> do konwertowania znaków na bajty.|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|Odczytuje znaki z `String`. Wyjście może być strumieniem w dowolnym kodowaniu lub `String`.|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|Zapisuje znaki w `String`. Wyjście może być strumieniem w dowolnym kodowaniu lub `String`.|  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie strumieni](../../../../standard/io/composing-streams.md)
- [We/Wy plików i strumieni](../../../../standard/io/index.md)
- [Asynchroniczne operacje We/Wy pliku](../../../../standard/io/asynchronous-file-i-o.md)
- [Podstawowe informacje dotyczące .NET Framework we/wy pliku i systemu plików (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
