---
title: 'Porady: przycinanie i skalowanie obrazów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: d5acda50a1aa0f0cae6e77a748b011908fcc8c34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-crop-and-scale-images"></a>Porady: przycinanie i skalowanie obrazów
<xref:System.Drawing.Graphics> Klasa udostępnia kilka <xref:System.Drawing.Graphics.DrawImage%2A> metod, niektóre z nich ma parametry prostokąt źródłowych i docelowych, które umożliwia przycinanie i skalowanie obrazów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu z dysku Apple.gif. Kod rysuje obraz całej firmy apple w jego oryginalny rozmiar. Kod wywołuje <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu do rysowania część obrazu firmy apple w prostokącie docelowego, który jest większy niż oryginalny obraz firmy apple.  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> Metoda określa, która część firmy apple do rysowania analizując prostokąta źródła jest określona przez trzecią, czwarty, argumenty piątego i szóstego. W takim przypadku przycięcia 75 procent szerokości i wysokości 75 procent firmy apple.  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> Metoda określa, gdzie do rysowania przycięte firmy apple i jak duży, aby wprowadzić przycięte apple analizując docelowy prostokąt, czyli drugiego argumentu. W takim przypadku prostokąt docelowy jest 30 procent szersze i 30 procent wyższe niż oryginalnego obrazu.  
  
 Na poniższej ilustracji przedstawiono oryginalne firmy apple i skalowana, przycięte firmy apple.  
  
 ![Przycinanie i skalowanie](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń. Upewnij się zastąpić `Apple.gif` nazwę pliku obrazu oraz ścieżki, które są prawidłowe w tym systemie.  
  
## <a name="see-also"></a>Zobacz też  
 [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
