---
title: 'Instrukcje: Odczytywanie metadanych obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 6c02f7e5744828fd8eddc88be8d7da28f3bc2a2a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505773"
---
# <a name="how-to-read-image-metadata"></a>Instrukcje: Odczytywanie metadanych obrazu
Niektóre pliki obrazu zawierają metadane, które mogą odczytać w celu określenia funkcji obrazu. Na przykład cyfrowych fotografii może zawierać metadane, które mogą odczytać w celu określenia producenta i modelu aparatu używane do przechwytywania obrazu. Za pomocą GDI + mogą odczytywać metadane istniejącego i można także zapisać nowe metadane do plików obrazu.  
  
 GDI + przechowuje wyraźne metadanych w <xref:System.Drawing.Imaging.PropertyItem> obiektu. Może odczytywać <xref:System.Drawing.Image.PropertyItems%2A> właściwość <xref:System.Drawing.Image> obiekt, aby pobrać wszystkie metadane z pliku. <xref:System.Drawing.Image.PropertyItems%2A> Właściwość zwraca tablicę <xref:System.Drawing.Imaging.PropertyItem> obiektów.  
  
 A <xref:System.Drawing.Imaging.PropertyItem> obiekt ma następujące cztery właściwości: `Id`, `Value`, `Len`, i `Type`.  
  
## <a name="id"></a>Id  
 Tag, który identyfikuje element metadanych. Niektóre wartości, które mogą być przypisane do <xref:System.Drawing.Imaging.PropertyItem.Id%2A> przedstawiono w poniższej tabeli.  
  
|Wartość szesnastkowa|Opis|  
|-----------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Tytuł obrazu<br /><br /> Producent sprzętu<br /><br /> Model urządzenia<br /><br /> ExifDTOriginal<br /><br /> Czas narażenia EXIF<br /><br /> Tabela jasności<br /><br /> Tabela Chrominance|  
  
## <a name="value"></a>Wartość  
 Tablica wartości. Format wartości jest określany przez <xref:System.Drawing.Imaging.PropertyItem.Type%2A> właściwości.  
  
## <a name="len"></a>Len  
 Długość (w bajtach) tablica wartości wskazywany przez <xref:System.Drawing.Imaging.PropertyItem.Value%2A> właściwości.  
  
## <a name="type"></a>Typ  
 Typ danych wartości w tablicy, wskazywana przez `Value` właściwości. Formaty wskazywanym przez `Type` w poniższej tabeli przedstawiono wartości właściwości  
  
|Wartość liczbowa|Opis|  
|-------------------|-----------------|  
|1|A `Byte`|  
|2|Tablica `Byte` obiektów zakodowanymi w formacie ASCII|  
|3|16-bitową liczbę całkowitą|  
|4|32-bitowa liczba całkowita|  
|5|Tablica dwóch `Byte` obiekty reprezentujące Liczba wymierna|  
|6|Nieużywane|  
|7|Niezdefiniowane|  
|8|Nieużywane|  
|9|`SLong`|  
|10|`SRational`|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład kodu odczytuje i wyświetla siedem elementów metadanych w pliku `FakePhoto.jpg`. Drugi element właściwości (indeks 1) na liście ma <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (producent sprzętu) i <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (zakodowany w formacie ASCII byte array). Przykład kodu wyświetla wartość tego elementu właściwości.  
  
 Kod generuje dane wyjściowe podobne do następujących:  
 
```
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
  
### <a name="code"></a>Kod  
 [!code-csharp[System.Drawing.WorkingWithImages#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń. Obsługa formularzy <xref:System.Windows.Forms.Control.Paint> zdarzeń i wklej ten kod do obsługi zdarzeń malowania. Należy zastąpić `FakePhoto.jpg` przy użyciu nazwy obrazu i ścieżki prawidłowe dla używanego systemu i importowania `System.Drawing.Imaging` przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](working-with-images-bitmaps-icons-and-metafiles.md)
