---
title: 'Instrukcje: Poprawianie wydajności dzięki unikaniu automatycznego skalowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- automatic scaling
- images [Windows Forms], improving performance
- images [Windows Forms], using without automatic scaling
- performance [Windows Forms], improving image
ms.assetid: 5fe2c95d-8653-4d55-bf0d-e5afa28f223b
ms.openlocfilehash: dd1a1545dce33de1ce11938db8495ebf311dadda
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506204"
---
# <a name="how-to-improve-performance-by-avoiding-automatic-scaling"></a>Instrukcje: Poprawianie wydajności dzięki unikaniu automatycznego skalowania
GDI + mogą skalować automatycznie obrazu podczas rysowania, które mogłoby obniżyć wydajność. Alternatywnie, można kontrolować, skalowanie obrazu, przekazując wymiary prostokąta docelowego, aby <xref:System.Drawing.Graphics.DrawImage%2A> metody.  
  
 Na przykład, następujące wywołanie do <xref:System.Drawing.Graphics.DrawImage%2A> metody określa lewego górnego rogu (50, 30), ale nie określa prostokąta docelowego.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.WorkingWithImages#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#31)]  
  
 Mimo że jest to najprostszy wersję <xref:System.Drawing.Graphics.DrawImage%2A> metoda pod względem liczby wymaganych argumentów nie jest koniecznie najbardziej efektywny. Jeśli rozwiązanie używane przez interfejs GDI + (zazwyczaj 96 punktów na cal) różni się od rozdzielczości, przechowywane w <xref:System.Drawing.Image> obiektu, a następnie <xref:System.Drawing.Graphics.DrawImage%2A> metoda przeprowadza skalowanie w obrazie. Na przykład, załóżmy, że <xref:System.Drawing.Image> obiekt ma szerokość 216 pikseli i wartości przechowywanej rozdzielczość pozioma 72 dpi. Ponieważ 216/72 to 3, <xref:System.Drawing.Graphics.DrawImage%2A> skaluje obraz, tak aby mieć szerokość 3 cala przy rozdzielczości 96 dpi. Oznacza to, że <xref:System.Drawing.Graphics.DrawImage%2A> wyświetli obraz, który ma szerokość 96 x 3 = 288 pikseli.  
  
 Nawet jeśli rozdzielczość ekranu jest inny niż 96 punktów na cal, GDI + będzie prawdopodobnie skaluje obraz tak, jakby rozdzielczość ekranu zostały 96 punktów na cal. Wynika to z użyciem interfejsu GDI + <xref:System.Drawing.Graphics> obiekt jest skojarzony z kontekstem urządzenia i GDI + kwerendę dotyczącą kontekst urządzenia dla rozdzielczość ekranu, wynik jest zazwyczaj 96, niezależnie od rzeczywistej rozdzielczości. Możesz uniknąć automatycznego skalowania, określając prostokąta docelowego w <xref:System.Drawing.Graphics.DrawImage%2A> metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera ten sam obraz, dwa razy. W pierwszym przypadku szerokość i wysokość prostokąta docelowego nie są określone, a obraz jest automatycznie skalowany. W drugim przypadku szerokość i wysokość (mierzonego w pikselach) prostokąta docelowego są określane być taka sama jak szerokość i wysokość oryginalnego obrazu. Poniższa ilustracja przedstawia obrazu renderowania dwa razy:  
  
 ![Zrzut ekranu pokazujący obrazów za pomocą skalowane tekstury.](./media/how-to-improve-performance-by-avoiding-automatic-scaling/two-scaled-texture-images.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.WorkingWithImages#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#32)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń. Zamień na Texture.jpg nazwy obrazu i ścieżki, które są prawidłowe w tym systemie.  
  
## <a name="see-also"></a>Zobacz także

- [Obrazy, mapy bitowe i metapliki](images-bitmaps-and-metafiles.md)
- [Praca z obrazami, mapami bitowymi, ikonami i metaplikami](working-with-images-bitmaps-icons-and-metafiles.md)
