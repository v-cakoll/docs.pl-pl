---
title: 'Porady: odczytywanie metadanych obrazu'
desription: Learn how to read the Windows Forms PropertyItems property of an Image object to retrieve all the metadata from a file.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 814cb17feba1e1e3a42b2bc403b0b4c828caf90e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174669"
---
# <a name="how-to-read-image-metadata"></a>Porady: odczytywanie metadanych obrazu

Niektóre pliki obrazów zawierają metadane, które można odczytać w celu określenia funkcji obrazu. Na przykład zdjęcie cyfrowe może zawierać metadane, które można odczytać, aby określić Marka i model aparatu używane do przechwytywania obrazu. Za pomocą interfejsu GDI+ można odczytać istniejące metadane, a także zapisać nowe metadane w plikach obrazów.

Interfejs GDI+ przechowuje poszczególne fragmenty metadanych w <xref:System.Drawing.Imaging.PropertyItem> obiekcie. Można odczytać <xref:System.Drawing.Image.PropertyItems%2A> Właściwość <xref:System.Drawing.Image> obiektu, aby pobrać wszystkie metadane z pliku. <xref:System.Drawing.Image.PropertyItems%2A>Właściwość zwraca tablicę <xref:System.Drawing.Imaging.PropertyItem> obiektów.

<xref:System.Drawing.Imaging.PropertyItem>Obiekt ma następujące cztery właściwości: `Id` , `Value` , `Len` , i `Type` .

## <a name="id"></a>Identyfikator

Tag, który identyfikuje element metadanych. Niektóre wartości, do których można przypisać, <xref:System.Drawing.Imaging.PropertyItem.Id%2A> są pokazane w poniższej tabeli:

|Wartość szesnastkowa|Opis|
|-----------------------|-----------------|
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Tytuł obrazu<br /><br /> Producent sprzętu<br /><br /> Model sprzętu<br /><br /> ExifDTOriginal<br /><br /> Czas ekspozycji EXIF<br /><br /> Tabela luminancji<br /><br /> Tabela chrominance|

## <a name="value"></a>Wartość

Tablica wartości. Format wartości jest określany przez <xref:System.Drawing.Imaging.PropertyItem.Type%2A> Właściwość.

## <a name="len"></a>Len

Długość (w bajtach) tablicy wartości wskazywanej przez <xref:System.Drawing.Imaging.PropertyItem.Value%2A> Właściwość.

## <a name="type"></a>Typ

Typ danych wartości w tablicy wskazywanej przez `Value` Właściwość. Formaty wskazywane przez `Type` wartości właściwości są pokazane w poniższej tabeli:

|Wartość liczbowa|Opis|
|-------------------|-----------------|
|1|Polecenie `Byte`|
|2|Tablica `Byte` obiektów zakodowanych jako ASCII|
|3|16-bitowa liczba całkowita|
|4|32-bitowa liczba całkowita|
|5|Tablica dwóch `Byte` obiektów, które reprezentują liczbę wymierną|
|6|Nieużywane|
|7|Niezdefiniowane|
|8|Nieużywane|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a>Przykład
  
Poniższy przykład kodu odczytuje i wyświetla siedem fragmentów metadanych w pliku `FakePhoto.jpg` . Drugi element właściwości (index 1) na liście ma <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (producent sprzętu) i <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (tablica bajtowa zakodowana w formacie ASCII). W przykładzie kodu jest wyświetlana wartość tego elementu właściwości.

[!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
[!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]

Kod generuje dane wyjściowe podobne do następujących:

```output
 Property Item 0
  
 id: 0x320
  
 type: 2

 length: 16 bytes
  
 Property Item 1
  
 id: 0x10f
  
 type: 2
  
 length: 17 bytes
  
 Property Item 2
  
 id: 0x110
  
 type: 2
  
 length: 7 bytes
  
 Property Item 3
  
 id: 0x9003
  
 type: 2
  
 length: 20 bytes
  
 Property Item 4
  
 id: 0x829a
  
 type: 5
  
 length: 8 bytes
  
 Property Item 5
  
 id: 0x5090
  
 type: 3
  
 length: 128 bytes
  
 Property Item 6
  
 id: 0x5091
  
 type: 3
  
 length: 128 bytes
  
 The equipment make is Northwind Camera.
 ```

## <a name="compiling-the-code"></a>Kompilowanie kodu

Poprzedni przykład jest przeznaczony do użycia z Windows Forms i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e` , który jest parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń. Obsługuj <xref:System.Windows.Forms.Control.Paint> zdarzenie formularza i wklej ten kod do programu obsługi zdarzeń malowania. Należy zastąpić `FakePhoto.jpg` nazwą obrazu i ścieżką prawidłową w systemie i zaimportować `System.Drawing.Imaging` przestrzeń nazw.

## <a name="see-also"></a>Zobacz też

- [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](working-with-images-bitmaps-icons-and-metafiles.md)
