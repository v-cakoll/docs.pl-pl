---
title: 'Instrukcje: Przycinanie i skalowanie obrazów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], cropping
- images [Windows Forms], scaling
ms.assetid: 053e3360-bca0-4b25-9afa-0e77a6f17b03
ms.openlocfilehash: 1f6d721edc4f889c2da8ece63f262c7fb55192bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707703"
---
# <a name="how-to-crop-and-scale-images"></a>Instrukcje: Przycinanie i skalowanie obrazów
<xref:System.Drawing.Graphics> Klasa udostępnia kilka <xref:System.Drawing.Graphics.DrawImage%2A> metod, niektóre z nich ma parametry prostokąt źródłowe i docelowe, które umożliwia przycinanie i skalowanie obrazów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu na podstawie pliku dysku Apple.gif. Kod rysuje obraz całej firmy apple w oryginalnym rozmiarze. Następnie wywołuje kod <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> obiektu, aby narysować część obrazu firmy apple w prostokąta docelowego, który jest większy niż oryginalny obraz firmy apple.  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> Metoda określa, która część firmy apple, aby narysować, analizując prostokąta źródłowego, który jest określony przez trzeci, czwarty, piąty i szósty argument. W tym przypadku przycięcia firmy apple do 75 procent jego szerokość i wysokość 75 procent.  
  
 <xref:System.Drawing.Graphics.DrawImage%2A> Metoda określa, gdzie mają być wyznaczone przycięty firmy apple i jak duży, aby wprowadzić przycięty firmy apple, analizując prostokąta docelowego, która określony przez drugi argument. W tym przypadku prostokąta docelowego jest 30 procent szerszy i 30 procent wyższe niż oryginalny obraz.  
  
 Poniższej ilustracji przedstawiono oryginalne firmy apple i skalowanych, przycięte firmy apple.  
  
 ![Przycinanie i skalowanie](../../../../docs/framework/winforms/advanced/media/cscropscale1.png "csCropScale1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.WorkingWithImages#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń. Upewnij się zastąpić `Apple.gif` za pomocą nazwy pliku obrazu i ścieżki, które są prawidłowe w tym systemie.  
  
## <a name="see-also"></a>Zobacz także
- [Obrazy, mapy bitowe i metapliki](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
