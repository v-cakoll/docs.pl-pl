---
title: Klasy stosowane w .NET Framework File I/O i systemie plików (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: f9d898756b6b17ae69d1af7dd747c20a26d88417
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347998"
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>Klasy stosowane w .NET Framework File I/O i systemie plików (Visual Basic)
W poniższej tabeli wymieniono klasy często używane dla .NET Framework w pliku we/wy, podzielone na kategorie klas we/wy pliku klasy służące do tworzenia strumieni i klas używanych do odczytu i zapisu do strumieni.  
  
Bardziej złożone lista znajduje się [Przegląd biblioteki klas](../../../../standard/class-library-overview.md).  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Klasy podstawowe operacje We/Wy do plików, dysków i katalogów  
 Poniższej tabeli wymieniono i opisano główne klasy używany dla we/wy pliku.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|Zawiera metody statyczne służące do tworzenia, przenoszenia i wyliczania katalogów i podkatalogów.|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|Zawiera metody wystąpień służące do tworzenia, przenoszenia i wyliczania katalogów i podkatalogów.|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|Zawiera metody wystąpień służące do tworzenia, przenoszenia i wyliczania dysków.|  
|<xref:System.IO.File?displayProperty=nameWithType>|Zawiera metody statyczne służące do tworzenia, kopiowania, usuwania, przenoszenia i otwierania plików, a także pomaga w tworzeniu `FileStream`.|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|Definiuje stałe do odczytu, zapisu lub odczytu i zapisu do pliku.|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|Zawiera atrybuty dla plików i katalogów, takich jak `Archive`, `Hidden`, i `ReadOnly`.|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|Zawiera metody statyczne służące do tworzenia, kopiowania, usuwania, przenoszenia i otwierania plików, a także pomaga w tworzeniu `FileStream`.|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|Określa, jak plik jest otwarty. Ten parametr jest określony w wielu konstruktory dla `FileStream` i `IsolatedStorageFileStream`oraz `Open` metody <xref:System.IO.File> i <xref:System.IO.FileInfo>.|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|Definiuje stałe do kontrolowania typ dostępu do innych strumieni plików może mieć tego samego pliku.|  
|<xref:System.IO.Path?displayProperty=nameWithType>|Udostępnia metody i właściwości dla przetwarzania ciągów katalogów.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|Kontroluje dostęp do plików i folderów, definiując <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> i <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> uprawnienia.|  
  
## <a name="classes-used-to-create-streams"></a>Klasy stosowane do tworzenia strumieni  
 Poniższej tabeli wymieniono i opisano głównych klas, które są używane do tworzenia strumieni.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|Dodaje buforowania warstwę do odczytu i zapisu w innej usłudze stream.|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|Obsługuje losowe dostęp do plików za pomocą jego <xref:System.IO.FileStream.Seek%2A> metody. <xref:System.IO.FileStream> pliki synchronicznie domyślnie otwierany, ale również obsługuje operację asynchroniczną.|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|Tworzy strumień jest którego zapasowy magazyn w pamięci, a nie plikiem.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|Zasadniczy strumień danych zapewnia dostęp do sieci.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|Definiuje strumień, który łączy strumieni danych z przekształceniami kryptograficznymi.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Klasy stosowane do odczytu i zapisu do strumieni  
 W poniższej tabeli przedstawiono określone klasy, służące do odczytywanie z oraz zapisywanie do plików strumieni.  
  
|**Class**|**Opis**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|Odczytuje ciągi zakodowane i typów danych pierwotnych z <xref:System.IO.FileStream>.|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|Zapisuje ciągi zakodowane oraz pierwotne typy danych do <xref:System.IO.FileStream>.|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|Odczytuje znaki z <xref:System.IO.FileStream>przy użyciu <xref:System.IO.StreamReader.CurrentEncoding%2A> Aby skonwertować znaki do i z bajtów. <xref:System.IO.StreamReader> ma Konstruktor, który podejmuje próbę ustalenia prawidłowych <xref:System.IO.StreamReader.CurrentEncoding%2A> dla danego strumienia na podstawie obecności <xref:System.IO.StreamReader.CurrentEncoding%2A>-określonych preambuły, takich jak znacznik kolejności bajtów.|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|Zapisuje znaki `FileStream`przy użyciu <xref:System.IO.StreamWriter.Encoding%2A> Aby skonwertować znaki bajtów.|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|Odczytuje znaki z `String`. Dane wyjściowe mogą być strumień w kodowanie lub `String`.|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|Zapisuje znaki `String`. Dane wyjściowe mogą być strumień w kodowanie lub `String`.|  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie strumieni](../../../../standard/io/composing-streams.md)
- [We/Wy plików i strumieni](../../../../standard/io/index.md)
- [Asynchroniczne operacje We/Wy pliku](../../../../standard/io/asynchronous-file-i-o.md)
- [Podstawowe informacje o .NET Framework File I/O i systemie plików (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
