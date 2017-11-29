---
title: 'Porady: tworzenie gradientu liniowego'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- linear gradients [Windows Forms], creating
- gradients [Windows Forms], creating linear
- colors [Windows Forms], creating linear gradients
- gradients
ms.assetid: 6c88e1cc-1217-4399-ac12-cb37592b9f01
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bbf3b1657a5a6b91ba88a0968b6b92d4e4bdbf0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-linear-gradient"></a>Porady: tworzenie gradientu liniowego
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]udostępnia pozioma, pionowych i ukośnych gradienty liniowe. Domyślnie w przypadku gradientu liniowego zmienia kolor jednakowo. Można jednak dostosować gradientu liniowego tak, aby w sposób niejednolitego zmienia kolor.  
  
 Poniższy przykład wypełnia linii, elipsy i prostokąt o poziomie pędzla gradientu liniowego.  
  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> Konstruktor odbiera cztery argumenty: dwa punkty i dwa kolory. Pierwszy punkt (0, 10) jest skojarzona z pierwszego koloru (czerwony), a drugi punkt (200, 10) jest skojarzona z drugi kolor (niebieski). Jak można oczekiwać, wiersz z (0, 10) do (200, 10) zmieni się stopniowo z kolor czerwony, niebieski.  
  
 10s w punktach (50, 10) i (200, 10) nie są ważne. Co to jest ważne jest, że dwa punkty ma tę samą współrzędną. drugi — wiersz, łącząc je jest poziomy. Elipsy i prostokąt również zmienić stopniowo kolor czerwony, niebieski, ponieważ Współrzędna pozioma przechodzi od 0 do 200.  
  
 Na poniższej ilustracji przedstawiono wiersza, elipsy i prostokąta. Należy pamiętać, że kolor gradientu powtarza się, jak współrzędnych poziomych przekroczy 200.  
  
 ![Gradient liniowy](../../../../docs/framework/winforms/advanced/media/cslineargradient1.png "cslineargradient1")  
  
### <a name="to-use-horizontal-linear-gradients"></a>Aby użyć poziome gradienty liniowe  
  
-   Przekaż nieprzezroczyste niebiesko czerwona i przezroczystości jako trzeci i czwarty argument odpowiednio.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#21)]
     [!code-vb[System.Drawing.UsingaGradientBrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#21)]  
  
 W powyższym przykładzie kolor zmiany składników liniowo podczas przenoszenia z poziome współrzędną 0 poziome współrzędną 200. Na przykład punkt, w których pierwszy współrzędnych jest w połowie zakresu od 0 do 200 ma niebieski składnik, który jest w połowie pomiędzy 0 a 255.  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]Pozwala dopasować sposób kolor zależą od jednej krawędzi gradientu do drugiego. Załóżmy, że chcesz utworzyć pędzla gradientu, który zmienia się z czarnym czerwony zgodnie z poniższą tabelą.  
  
|Współrzędna pozioma|Składniki RGB|  
|---------------------------|--------------------|  
|0|(0, 0, 0)|  
|40|(128, 0, 0)|  
|200|(255, 0, 0)|  
  
 Należy pamiętać, że składnik red w połowie intensywność przy poziomie Współrzędna jest tylko 20% sposób z zakresu od 0 do 200.  
  
 W poniższym przykładzie <xref:System.Drawing.Drawing2D.LinearGradientBrush.Blend%2A> właściwość <xref:System.Drawing.Drawing2D.LinearGradientBrush> obiektu trzy względne natężenia z trzech położenia. W powyższej tabeli względną intensywność 0,5 jest skojarzony z względne położenie 0,2. Kod wypełnia elipsy i prostokąt z pędzla gradientu.  
  
 Na poniższej ilustracji przedstawiono wynikowy elipsy i prostokąta.  
  
 ![Gradient liniowy](../../../../docs/framework/winforms/advanced/media/cslineargradient2.png "cslineargradient2")  
  
### <a name="to-customize-linear-gradients"></a>Aby dostosować gradienty liniowe  
  
-   Przekaż nieprzezroczyste czerwone czarne i przezroczystości jako trzeci i czwarty argument odpowiednio.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#22)]
     [!code-vb[System.Drawing.UsingaGradientBrush#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#22)]  
  
 Gradienty w powyższych przykładach zostały poziome; oznacza to, że zmienia kolor stopniowo podczas wykonywania czynności dowolnej linii poziomej. Można również zdefiniować pionowy gradientach i przekątnej gradientu.  
  
 Poniższy przykład przekazuje punktów (0, 0) i (200, 100) do <xref:System.Drawing.Drawing2D.LinearGradientBrush.%23ctor%2A> konstruktora. Kolor niebieski jest skojarzony z (0, 0), i jest skojarzony kolor zielony (200, 100). Wiersz (szerokość 10) i elipsy są wypełniane pędzla gradientu liniowego.  
  
 Na poniższej ilustracji przedstawiono elipsy i wiersza. Należy zauważyć, że kolor zmian elipsy stopniowo podczas wykonywania czynności żadnego wiersza jest zbliżony do linii przechodzącej przez (0, 0) i (200, 100).  
  
 ![Gradient liniowy](../../../../docs/framework/winforms/advanced/media/cslineargradient3.png "cslineargradient3")  
  
### <a name="to-create-diagonal-linear-gradients"></a>Aby utworzyć ukośnych gradienty liniowe  
  
-   Przekazywane nieprzezroczyste zielony niebieska i przezroczystości jako trzeci i czwarty argument odpowiednio.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#23)]
     [!code-vb[System.Drawing.UsingaGradientBrush#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie pędzla gradientów do wypełniania kształtów](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)  
 [Grafika i rysowanie w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
