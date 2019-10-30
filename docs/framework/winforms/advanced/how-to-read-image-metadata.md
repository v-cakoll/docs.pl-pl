---
title: 'Porady: odczytywanie metadanych obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: cd3b636f8f0058d4a8eacc656f95d5f46b8967e2
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040754"
---
# <a name="how-to-read-image-metadata"></a>Porady: odczytywanie metadanych obrazu

Niektóre pliki obrazów zawierają metadane, które można odczytać w celu określenia funkcji obrazu. Na przykład zdjęcie cyfrowe może zawierać metadane, które można odczytać, aby określić Marka i model aparatu używane do przechwytywania obrazu. Za pomocą interfejsu GDI+ można odczytać istniejące metadane, a także zapisać nowe metadane w plikach obrazów.

Interfejs GDI+ przechowuje poszczególne fragmenty metadanych w obiekcie <xref:System.Drawing.Imaging.PropertyItem>. Można odczytać właściwość <xref:System.Drawing.Image.PropertyItems%2A> obiektu <xref:System.Drawing.Image>, aby pobrać wszystkie metadane z pliku. Właściwość <xref:System.Drawing.Image.PropertyItems%2A> zwraca tablicę obiektów <xref:System.Drawing.Imaging.PropertyItem>.

Obiekt <xref:System.Drawing.Imaging.PropertyItem> ma cztery następujące właściwości: `Id`, `Value`, `Len`i `Type`.

## <a name="id"></a>#C1

Tag, który identyfikuje element metadanych. Niektóre wartości, które można przypisać do <xref:System.Drawing.Imaging.PropertyItem.Id%2A> są przedstawione w poniższej tabeli:

|Wartość szesnastkowa|Opis|
|-----------------------|-----------------|
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Tytuł obrazu<br /><br /> Producent sprzętu<br /><br /> Model sprzętu<br /><br /> ExifDTOriginal<br /><br /> Czas ekspozycji EXIF<br /><br /> Tabela luminancji<br /><br /> Tabela chrominance|

## <a name="value"></a>Wartość

Tablica wartości. Format wartości jest określany przez właściwość <xref:System.Drawing.Imaging.PropertyItem.Type%2A>.

## <a name="len"></a>Funkcja

Długość (w bajtach) tablicy wartości wskazywanej przez właściwość <xref:System.Drawing.Imaging.PropertyItem.Value%2A>.

## <a name="type"></a>Typ

Typ danych wartości w tablicy wskazywanej przez właściwość `Value`. Formaty wskazywane przez wartości właściwości `Type` są przedstawione w poniższej tabeli:

|Wartość liczbowa|Opis|
|-------------------|-----------------|
|1|`Byte`|
|2|Tablica obiektów `Byte` zakodowanych jako ASCII|
|3|16-bitowa liczba całkowita|
|4|32-bitowa liczba całkowita|
|5|Tablica dwóch `Byte` obiektów, które reprezentują liczbę wymierną|
|6|Nieużywane|
|7|definicji|
|8|Nieużywane|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a>Przykład
  
Poniższy przykład kodu odczytuje i wyświetla siedem fragmentów metadanych w pliku `FakePhoto.jpg`. Drugi element właściwości (index 1) na liście ma <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (producent sprzętu) i <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (tablica bajtowa zakodowana w formacie ASCII). W przykładzie kodu jest wyświetlana wartość tego elementu właściwości.

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

Poprzedni przykład jest przeznaczony do użytku z Windows Forms i wymaga `e`<xref:System.Windows.Forms.PaintEventArgs>, który jest parametrem programu obsługi zdarzeń <xref:System.Windows.Forms.Control.Paint>. Obsługuj zdarzenie <xref:System.Windows.Forms.Control.Paint> formularza i wklej ten kod do programu obsługi zdarzeń malowania. Należy zastąpić `FakePhoto.jpg` nazwą obrazu i ścieżką prawidłową w systemie i zaimportować przestrzeń nazw `System.Drawing.Imaging`.

## <a name="see-also"></a>Zobacz także

- [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](working-with-images-bitmaps-icons-and-metafiles.md)
