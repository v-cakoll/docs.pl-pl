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
ms.openlocfilehash: 92ce4eb8d51fbd25f9a129a629dc47bfb9941f34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-image-metadata"></a>Porady: odczytywanie metadanych obrazu
Niektóre pliki obrazów zawierać metadane, który można odczytać w celu określenia funkcji obrazu. Na przykład cyfrowych fotografii może zawierać metadane, który można odczytać w celu określenia marka i model aparatu służące do przechwytywania obrazu. Z [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], możesz przeczytać istniejące metadane i może także zapisać nowe metadane pliki obrazów.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] przechowuje każdej części metadanych w <xref:System.Drawing.Imaging.PropertyItem> obiektu. Możesz przeczytać <xref:System.Drawing.Image.PropertyItems%2A> właściwość <xref:System.Drawing.Image> obiektu można pobrać wszystkich metadanych z pliku. <xref:System.Drawing.Image.PropertyItems%2A> Właściwość zwraca tablicę <xref:System.Drawing.Imaging.PropertyItem> obiektów.  
  
 A <xref:System.Drawing.Imaging.PropertyItem> obiekt ma cztery następujące właściwości: `Id`, `Value`, `Len`, i `Type`.  
  
## <a name="id"></a>Id  
 Tag, który identyfikuje element metadanych. Niektóre wartości, które można przypisać do <xref:System.Drawing.Imaging.PropertyItem.Id%2A> przedstawiono w poniższej tabeli.  
  
|Wartość szesnastkowa|Opis|  
|-----------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|Nazwa obrazu<br /><br /> Producent urządzenia<br /><br /> Model urządzenia<br /><br /> ExifDTOriginal<br /><br /> Czas ekspozycji EXIF<br /><br /> Tabela jasności<br /><br /> Tabela Chrominance|  
  
## <a name="value"></a>Wartość  
 Tablica wartości. Format wartości jest określany przez <xref:System.Drawing.Imaging.PropertyItem.Type%2A> właściwości.  
  
## <a name="len"></a>Długość  
 Długość (w bajtach) tablicy wartości wskazywanej przez <xref:System.Drawing.Imaging.PropertyItem.Value%2A> właściwości.  
  
## <a name="type"></a>Typ  
 Typ danych wartości w tablicy wskazywana przez `Value` właściwości. Formaty wskazywanym przez `Type` w poniższej tabeli przedstawiono wartości właściwości  
  
|Wartość liczbowa|Opis|  
|-------------------|-----------------|  
|1|A `Byte`|  
|2|Tablica `Byte` obiektów kodowany w formacie ASCII|  
|3|16-bitową liczbę całkowitą|  
|4|32-bitowa liczba całkowita|  
|5|Macierzy dwa `Byte` obiektów, które reprezentują Liczba wymierna|  
|6|Nieużywane|  
|7|Niezdefiniowana|  
|8|Nieużywane|  
|9|`SLong`|  
|10|`SRational`|  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykładowy kod odczytuje i wyświetla siedem części metadane w pliku `FakePhoto.jpg`. Drugi element właściwości (indeks 1) na liście ma <xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F (producenta sprzętu) i <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 (tablicy bajtowej kodowany w formacie ASCII). Przykładowy kod przedstawia wartość elementu właściwości.  
  
 Kod generuje dane wyjściowe podobne do następujących:  
  
 `Property Item 0`  
  
 `id: 0x320`  
  
 `type: 2`  
  
 `length: 16 bytes`  
  
 `Property Item 1`  
  
 `id: 0x10f`  
  
 `type: 2`  
  
 `length: 17 bytes`  
  
 `Property Item 2`  
  
 `id: 0x110`  
  
 `type: 2`  
  
 `length: 7 bytes`  
  
 `Property Item 3`  
  
 `id: 0x9003`  
  
 `type: 2`  
  
 `length: 20 bytes`  
  
 `Property Item 4`  
  
 `id: 0x829a`  
  
 `type: 5`  
  
 `length: 8 bytes`  
  
 `Property Item 5`  
  
 `id: 0x5090`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `Property Item 6`  
  
 `id: 0x5091`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `The equipment make is Northwind Camera.`  
  
### <a name="code"></a>Kod  
 [!code-csharp[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń. Obsługa formularzy <xref:System.Windows.Forms.Control.Paint> zdarzeń i wklej ten kod do malowania programu obsługi zdarzeń. Należy zastąpić `FakePhoto.jpg` z obrazu nazwa i ścieżka prawidłowy systemu i importowania `System.Drawing.Imaging` przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
