---
title: Klasy stosowane w .NET Framework File I/O i systemie plików (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
ms.openlocfilehash: 4c13b482ddbb3c1c109ca8dfe36ed76a2025d61a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>Klasy stosowane w .NET Framework File I/O i systemie plików (Visual Basic)
W poniższej tabeli wymieniono klasy powszechnie używane dla .NET Framework plik we/wy, podzielić na klasy używany do odczytu i zapisu do strumieni, klasy służące do tworzenia strumieni i klasy We/Wy plików.  
  
 Aby wprowadzić [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] dokumentacji i Znajdź wyczerpujący listę, zobacz [Przegląd biblioteki klas](../../../../standard/class-library-overview.md).  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Klasy podstawowe we/wy dla plików, dysków i katalogów  
 W poniższej tabeli wymieniono i opisano klasy głównym plik we/wy.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=nameWithType>|Udostępnia metody statyczne do tworzenia, przenoszenie i wyliczania katalogów i jego podkatalogach.|  
|<xref:System.IO.DirectoryInfo?displayProperty=nameWithType>|Udostępnia metody wystąpienia tworzenie, przenoszenie i wyliczania katalogów i jego podkatalogach.|  
|<xref:System.IO.DriveInfo?displayProperty=nameWithType>|Udostępnia metody wystąpienia tworzenie, przenoszenie i wyliczania dysków.|  
|<xref:System.IO.File?displayProperty=nameWithType>|Udostępnia metody statyczne do tworzenia, kopiowanie, usuwanie, przenoszenie i otwieranie plików i pomaga w tworzeniu `FileStream`.|  
|<xref:System.IO.FileAccess?displayProperty=nameWithType>|Określa stałe odczytu, zapisu lub odczytu i zapisu do pliku.|  
|<xref:System.IO.FileAttributes?displayProperty=nameWithType>|Udostępnia atrybuty dla plików i katalogów, takich jak `Archive`, `Hidden`, i `ReadOnly`.|  
|<xref:System.IO.FileInfo?displayProperty=nameWithType>|Udostępnia metody statyczne do tworzenia, kopiowanie, usuwanie, przenoszenie i otwieranie plików i pomaga w tworzeniu `FileStream`.|  
|<xref:System.IO.FileMode?displayProperty=nameWithType>|Określa, jak plik jest otwarty. Ten parametr jest określony w wiele konstruktorów dla `FileStream` i `IsolatedStorageFileStream`oraz `Open` metody <xref:System.IO.File> i <xref:System.IO.FileInfo>.|  
|<xref:System.IO.FileShare?displayProperty=nameWithType>|Określa stałe kontroli rodzaju dostępu do innych strumieni plików może mieć do tego samego pliku.|  
|<xref:System.IO.Path?displayProperty=nameWithType>|Udostępnia metody i właściwości dla przetwarzania ciągów katalogu.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>|Kontroluje dostęp do plików i folderów, definiując <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> i <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> uprawnienia.|  
  
## <a name="classes-used-to-create-streams"></a>Klasy używane do tworzenia strumieni  
 W poniższej tabeli wymieniono i opisano klasy głównym, używany do tworzenia strumieni.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=nameWithType>|Dodaje buforowania warstwy do odczytu i zapisu dla innego strumienia.|  
|<xref:System.IO.FileStream?displayProperty=nameWithType>|Obsługuje losowe dostęp do plików za pomocą jego <xref:System.IO.FileStream.Seek%2A> metody. <xref:System.IO.FileStream> zostanie otwarte pliki synchronicznie domyślnie, ale obsługuje również operację asynchroniczną.|  
|<xref:System.IO.MemoryStream?displayProperty=nameWithType>|Tworzy strumień, którego magazynu zapasowego jest pamięć, a nie plikiem.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=nameWithType>|Zasadniczy strumień danych zapewnia dostęp do sieci.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=nameWithType>|Definiuje strumienia, który łączy strumienie danych do przekształcenia kryptograficznych.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Klasy stosowane do odczytu i zapisu do strumieni  
 W poniższej tabeli przedstawiono określonej klasy, służące do odczytywanie z oraz zapisywanie do plików strumieni.  
  
|**Class**|**Opis**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=nameWithType>|Odczytuje zakodowanego parametry i typy pierwotne danych z <xref:System.IO.FileStream>.|  
|<xref:System.IO.BinaryWriter?displayProperty=nameWithType>|Zapisuje zakodowanego parametry i typy pierwotne danych do <xref:System.IO.FileStream>.|  
|<xref:System.IO.StreamReader?displayProperty=nameWithType>|Odczytuje znaków z <xref:System.IO.FileStream>za pomocą <xref:System.IO.StreamReader.CurrentEncoding%2A> można konwertować znaków do i z bajtów. <xref:System.IO.StreamReader> ma podejmowanych w celu ustalenia odpowiedniego konstruktora <xref:System.IO.StreamReader.CurrentEncoding%2A> dla danego strumienia, na podstawie obecności <xref:System.IO.StreamReader.CurrentEncoding%2A>-określonych preambuły, takich jak znacznik kolejności bajtów.|  
|<xref:System.IO.StreamWriter?displayProperty=nameWithType>|Zapisuje znaki `FileStream`za pomocą <xref:System.IO.StreamWriter.Encoding%2A> można konwertować znaków bajtów.|  
|<xref:System.IO.StringReader?displayProperty=nameWithType>|Odczytuje znaków z `String`. Dane wyjściowe może być strumień w kodowanie lub `String`.|  
|<xref:System.IO.StringWriter?displayProperty=nameWithType>|Zapisuje znaków `String`. Dane wyjściowe może być strumień w kodowanie lub `String`.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie strumieni](../../../../standard/io/composing-streams.md)  
 [We/Wy plików i strumieni](../../../../standard/io/index.md)  
 [Asynchroniczne operacje We/Wy pliku](../../../../standard/io/asynchronous-file-i-o.md)  
 [Podstawowe informacje o .NET Framework File I/O i systemie plików (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)
