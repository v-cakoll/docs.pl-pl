---
title: 'Instrukcje: Tworzenie gradientu liniowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
ms.openlocfilehash: 953a1944073a8cb5b19ef072e2a523baec3a5605
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650005"
---
# <a name="how-to-create-a-linear-gradient"></a>Instrukcje: Tworzenie gradientu liniowego
GDI + zapewnia poziomej, pionowej i ukośne gradienty liniowe. Domyślnie w przypadku gradientu liniowego zmienia kolor równomiernie. Można jednak dostosować gradientu liniowego, tak, aby zmienia kolor w sposób obsługuje technologię niejednolitego.  

> [!NOTE]
> Przykłady w niniejszym artykule są metody, które są wywoływane z poziomu kontroli <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.  

Poniższy przykład wypełnia linię, elipsę i prostokąt o poziomie pędzel gradientów liniowych.  
  
<xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Konstruktor odbiera cztery argumenty: dwa punkty i dwóch kolorów. Pierwszy punkt (0, 10) jest skojarzona z pierwszy kolor (czerwony), a drugi punkt (200, 10) jest skojarzony z drugi kolor (niebieski). Jak można oczekiwać, wiersz z (0, 10) do (200, 10) stopniowo zmienia się z kolor czerwony, niebieski.  
  
 10s w punktach (0, 10) i (200, 10) nie są ważne. Co to jest ważne jest, czy dwa punkty mają tę samą współrzędną. drugi — wiersz, łącząc je jest poziomy. Elipsy i prostokąt również zmienić stopniowo kolor czerwony, niebieski, ponieważ pozioma współrzędne przechodzi z zakresu od 0 do 200.  
  
 Na poniższej ilustracji przedstawiono wiersza, elipsy i prostokąt. Należy pamiętać, że kolor gradientu powtarza się, jak pozioma współrzędne przekroczy 200.  
  
 ![Linear Gradient](./media/cslineargradient1.png "cslineargradient1")  
  
### <a name="to-use-horizontal-linear-gradients"></a>Aby użyć poziomy gradientów liniowych  
  
- Przekaż nieprzezroczyste niebieski czerwonego i nieprzezroczystości jako argument trzecia i czwarta odpowiednio.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 W powyższym przykładzie kolor zmiany składników liniowo po przeniesieniu pozioma współrzędne 0 Aby pozioma współrzędne 200. Na przykład punkt, w której Współrzędna pierwszy jest w połowie zakresu od 0 do 200 mają niebieski składnik, który jest w połowie między 0 a 255.  
  
 GDI + pozwala dostosować sposób, w których kolor, który różni się od jednej krawędzi gradientu do drugiego. Załóżmy, że chcesz utworzyć pędzla gradientu, który zmienia się pomiędzy czarny na czerwony, zgodnie z poniższą tabelą.  
  
|Pozioma współrzędne|Składniki RGB|  
|---------------------------|--------------------|  
|0|(0, 0, 0)|  
|40|(128, 0, 0)|  
|200|(255, 0, 0)|  
  
 Należy pamiętać, że składnik czerwony w wysokości równej połowie intensywność podczas pozioma współrzędne jest tylko 20% sposób z zakresu od 0 do 200.  
  
 Poniższy przykład ustawia <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A?displayProperty=nameWithType> właściwość do skojarzenia z trzech względne natężenia z trzech położenie względne. Tak jak w powyższej tabeli względną intensywność 0,5 jest skojarzony z względne położenie 0.2. Kod wprowadza elipsę i prostokąt z pędzla gradientu.  
  
 Na poniższej ilustracji przedstawiono wynikowe elipsy i prostokąt.  
  
 ![Gradient liniowy](./media/cslineargradient2.png "cslineargradient2")  

### <a name="to-customize-linear-gradients"></a>Aby dostosować gradienty liniowe  
  
- Przekaż nieprzezroczyste red czarne i nieprzezroczystości jako argument trzecia i czwarta odpowiednio.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 Gradienty w powyższych przykładach zostały poziomy; oznacza to zmienia kolor stopniowo po przeniesieniu wzdłuż dowolnej linii poziomej. Można również zdefiniować gradientów pionowych i gradientów ukośne.  
  
 Poniższy przykład przekazuje punkty (0, 0) i (200, 100), aby <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> konstruktora. Kolor niebieski jest skojarzony z (0, 0), a kolor zielony jest skojarzony z (200, 100). Wiersz (przy użyciu szerokości pióro 10) i elipsy są wypełnione pędzel gradientów liniowych.  
  
 Na poniższej ilustracji przedstawiono wiersza i elipsy. Należy pamiętać, kolor zmiany elipsy stopniowo po przeniesieniu wzdłuż żadnego wiersza jest zbliżony do wiersza, przechodzi przez (0, 0) i (200, 100).  
  
 ![Gradient liniowy](./media/cslineargradient3.png "cslineargradient3")  
  
### <a name="to-create-diagonal-linear-gradients"></a>Aby utworzyć w użyciu gradientów liniowych  
  
- Przekaż nieprzezroczyste zielonego nieprzezroczyste i w kolorze niebieskim jako argument trzecia i czwarta, odpowiednio.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Zobacz także

- [Używanie pędzla gradientów do wypełniania kształtów](using-a-gradient-brush-to-fill-shapes.md)
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
