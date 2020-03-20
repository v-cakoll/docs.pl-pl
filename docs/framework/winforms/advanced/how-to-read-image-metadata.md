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
ms.openlocfilehash: e2b56175e625281a920c390e5feb4238e3cb7f44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182525"
---
# <a name="how-to-read-image-metadata"></a>Porady: odczytywanie metadanych obrazu

Niektóre pliki obrazów zawierają metadane, które można odczytać w celu określenia funkcji obrazu. Na przykład fotografia cyfrowa może zawierać metadane, które można odczytać w celu określenia formy i modelu aparatu używanego do przechwytywania obrazu. Za pomocą GDI+, można odczytać istniejące metadane, a także można zapisać nowe metadane do plików obrazów.

GDI+ przechowuje pojedynczy fragment metadanych w <xref:System.Drawing.Imaging.PropertyItem> obiekcie. Można odczytać <xref:System.Drawing.Image.PropertyItems%2A> właściwość <xref:System.Drawing.Image> obiektu, aby pobrać wszystkie metadane z pliku. Właściwość <xref:System.Drawing.Image.PropertyItems%2A> zwraca tablicę <xref:System.Drawing.Imaging.PropertyItem> obiektów.

Obiekt <xref:System.Drawing.Imaging.PropertyItem> ma następujące cztery `Id`właściwości: `Value` `Len`, `Type`, , i .

## <a name="id"></a>Identyfikator

Tag identyfikujący element metadanych. Niektóre wartości, do <xref:System.Drawing.Imaging.PropertyItem.Id%2A> których można przypisać, są pokazane w poniższej tabeli:

|Wartość szesnastkowa|Opis|
|-----------------------|-----------------|
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Tytuł obrazu<br /><br /> Producent sprzętu<br /><br /> Model wyposażenia<br /><br /> Eksyfdtoriginal<br /><br /> Czas ekspozycji Exif<br /><br /> Tabela luminancji<br /><br /> Tabela chrominancji|

## <a name="value"></a>Wartość

Tablica wartości. Format wartości jest określany <xref:System.Drawing.Imaging.PropertyItem.Type%2A> przez właściwość.

## <a name="len"></a>Len

Długość (w bajtach) tablicy wartości wskazywali przez <xref:System.Drawing.Imaging.PropertyItem.Value%2A> właściwość.

## <a name="type"></a>Typ

Typ danych wartości w tablicy wskazywu przez `Value` właściwość. Formaty wskazane przez `Type` wartości właściwości są wyświetlane w poniższej tabeli:

|Wartość liczbowa|Opis|
|-------------------|-----------------|
|1|Element `Byte`.|
|2|Tablica `Byte` obiektów zakodowanych jako ASCII|
|3|16-bitowa 10-bitowa ćowiaczka całkowita|
|4|32-bitowa czkawce całkowitej|
|5|Tablica dwóch `Byte` obiektów, które reprezentują racjonalną liczbę|
|6|Nieużywane|
|7|Niezdefiniowane|
|8|Nieużywane|
|9|`SLong`|
|10|`SRational`|

## <a name="example"></a>Przykład
  
Poniższy przykład kodu odczytuje i wyświetla siedem elementów metadanych w pliku `FakePhoto.jpg`. Drugi (indeks 1) element właściwości <xref:System.Drawing.Imaging.PropertyItem.Id%2A> na liście ma 0x010F (producent sprzętu) i <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (ascii kodowany tablicy bajtów). Przykład kodu wyświetla wartość tego elementu właściwości.

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

Powyższy przykład jest przeznaczony do użytku z <xref:System.Windows.Forms.PaintEventArgs> `e`formularzami systemu Windows <xref:System.Windows.Forms.Control.Paint> i wymaga , który jest parametrem obsługi zdarzeń. Obsługa <xref:System.Windows.Forms.Control.Paint> zdarzenia formularza i wklej ten kod do programu obsługi zdarzeń malowania. Należy zastąpić `FakePhoto.jpg` nazwą obrazu i ścieżką prawidłową `System.Drawing.Imaging` w systemie i zaimportować obszar nazw.

## <a name="see-also"></a>Zobacz też

- [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](working-with-images-bitmaps-icons-and-metafiles.md)
