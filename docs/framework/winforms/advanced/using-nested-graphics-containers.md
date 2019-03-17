---
title: Używanie zagnieżdżonych kontenerów grafiki
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
ms.openlocfilehash: a66edd0297b723b81c31675c9b0e6b6def9ed10a
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125866"
---
# <a name="using-nested-graphics-containers"></a>Używanie zagnieżdżonych kontenerów grafiki
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zapewnia kontenery, których można użyć, aby tymczasowo zastąpić, lub rozszerzyć część stanu w <xref:System.Drawing.Graphics> obiektu. Utwórz kontener, wywołując <xref:System.Drawing.Graphics.BeginContainer%2A> metody <xref:System.Drawing.Graphics> obiektu. Możesz wywołać <xref:System.Drawing.Graphics.BeginContainer%2A> wielokrotnie w celu utworzenia zagnieżdżone kontenery. Każde wywołanie <xref:System.Drawing.Graphics.BeginContainer%2A> muszą łączyć się z wywołaniem <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
## <a name="transformations-in-nested-containers"></a>Przekształcenia w zagnieżdżone kontenery  
 Poniższy przykład tworzy <xref:System.Drawing.Graphics> obiektów i kontenerów, w tym <xref:System.Drawing.Graphics> obiektu. Przekształcanie świata <xref:System.Drawing.Graphics> obiekt jest jednostki translacji 100, w kierunku x i 80 jednostek w kierunku y. Transformacja świata kontenera jest 30 stopni. Kod sprawia, że wywołanie `DrawRectangle(pen, -60, -30, 120, 60)` dwa razy. Pierwsze wywołanie <xref:System.Drawing.Graphics.DrawRectangle%2A> znajduje się wewnątrz kontenera; oznacza to wywołanie jest z zakresu od wywołania <xref:System.Drawing.Graphics.BeginContainer%2A> i <xref:System.Drawing.Graphics.EndContainer%2A>. Drugie wywołanie <xref:System.Drawing.Graphics.DrawRectangle%2A> po wywołaniu <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 W poprzednim kodzie prostokąt rysowana od wewnątrz kontenera jest przekształcana najpierw według transformacji świata kontenera (obrotu), a następnie transformacji świata z <xref:System.Drawing.Graphics> obiektu (tłumaczenia). Prostokąt, pobierane z zewnątrz kontenera jest przekształcana tylko przez Przekształcanie świata <xref:System.Drawing.Graphics> obiektu (tłumaczenia). Poniższa ilustracja przedstawia dwoma prostokątami: 
  
 ![Ilustracja przedstawiająca zagnieżdżone kontenery.](./media/using-nested-graphics-containers/nested-containers-illustration.png)  
  
## <a name="clipping-in-nested-containers"></a>Przycinanie zagnieżdżone kontenery  
 Poniższy przykład pokazuje, jak zagnieżdżone kontenery obsługi regionów wycinka. Ten kod tworzy <xref:System.Drawing.Graphics> obiektów i kontenerów, w tym <xref:System.Drawing.Graphics> obiektu. Region wycinka <xref:System.Drawing.Graphics> obiektu jest prostokąt, a obszar przycinania kontenera elipsę. Kod sprawia, że dwa wywołania <xref:System.Drawing.Graphics.DrawLine%2A> metody. Pierwsze wywołanie <xref:System.Drawing.Graphics.DrawLine%2A> znajduje się wewnątrz kontenera, a drugie wywołanie <xref:System.Drawing.Graphics.DrawLine%2A> znajduje się poza kontener (po wywołaniu <xref:System.Drawing.Graphics.EndContainer%2A>). Pierwszy wiersz zostanie obcięta przez przecięcie wycinka dwóch regionach. Drugi wiersz jest przycinana tylko przez region prostokątnego wycinka <xref:System.Drawing.Graphics> obiektu.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 Na poniższej ilustracji przedstawiono dwa wiersze obciętych:
  
 ![Ilustracja przedstawiająca zagnieżdżonych kontenerów przy użyciu obciętych wierszy.](./media/using-nested-graphics-containers/nested-container-clipped-lines.png)  
  
 Jak dwóch poprzednich przykładach, transformacji i regiony wycinka kumulują się w zagnieżdżone kontenery. Jeśli ustawisz transformacji świata kontenera i <xref:System.Drawing.Graphics> obiektu i zastosuje oba przekształcenia elementów pochodzących z wewnątrz kontenera. Transformacja kontenera będą stosowane pierwszy i przekształcenie <xref:System.Drawing.Graphics> zostaną zastosowane po drugie obiektu. Jeśli ustawisz regionów wycinka kontenera i <xref:System.Drawing.Graphics> obiektów i elementów pochodzących z wewnątrz kontenera zostaną przycięte przez przecięcie wycinka dwóch regionach.  
  
## <a name="quality-settings-in-nested-containers"></a>Ustawienia jakości w zagnieżdżone kontenery  
 Ustawienia jakości (<xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.TextRenderingHint%2A>i tym podobne) w zagnieżdżone kontenery nie kumulują się; zamiast ustawień jakości kontenera tymczasowo zastąpić ustawienia jakości <xref:System.Drawing.Graphics> obiektu. Podczas tworzenia nowego kontenera ustawienia jakości dla tego kontenera są ustawione wartości domyślne. Załóżmy, że masz <xref:System.Drawing.Graphics> obiektu z trybu wygładzania <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Podczas tworzenia kontenera tryb wygładzania wewnątrz kontenera jest domyślny tryb wygładzania. Jest bezpłatna ustawić tryb wygładzania kontenera i wszystkie elementy pobrane z wewnątrz kontenera będą rysowane zgodnie z tryb w którym można ustawić. Elementy rysowania po wywołaniu <xref:System.Drawing.Graphics.EndContainer%2A> będą rysowane zgodnie z tryb wygładzania (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>) była w miejscu przed wywołaniem do <xref:System.Drawing.Graphics.BeginContainer%2A>.  
  
## <a name="several-layers-of-nested-containers"></a>Kilka warstw zagnieżdżone kontenery  
 Nie są ograniczone do jednego kontenera w <xref:System.Drawing.Graphics> obiektu. Można utworzyć sekwencji, kontenerów, każda zagnieżdżona w poprzednim i określić transformacji świata, obszaru przycinania i ustawienia jakości każdej z tych zagnieżdżone kontenery. Wywołanie metody rysowania z wewnątrz kontenera najbardziej przekształcenia będą stosowane w kolejności, począwszy od najbardziej kontenera, a kończąc na najbardziej zewnętrznej kontenera. Elementy pobrane z wewnątrz kontenera najbardziej obetnie przecięcia wszystkich regionów wycinka.  
  
 Poniższy przykład tworzy <xref:System.Drawing.Graphics> obiektu i ustawia jego wskazówkę dotyczącą renderowania tekstu <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Ten kod tworzy dwa kontenery, jeden zagnieżdżone w innych. Wskazówka renderowanie tekstu zewnętrzne kontenera jest ustawiona na <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>, a wskazówkę dotyczącą renderowania tekst wewnętrzny kontenera jest ustawiona na <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Kod rysuje trzy ciągi: jeden z kontener wewnętrzny: jeden z zewnętrznego kontenera i jeden z <xref:System.Drawing.Graphics> sam obiekt.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 Poniższa ilustracja przedstawia trzy ciągi. Ciągi rysowany z kontener wewnętrzny i <xref:System.Drawing.Graphics> obiektu są wygładzone przez antialiasingu. Ciąg, z zewnętrznym kontenera nie jest wygładzone przez antialiasingu, ponieważ <xref:System.Drawing.Graphics.TextRenderingHint%2A> właściwość jest ustawiona na <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.  
  
 ![Ilustracja przedstawiająca ciągów, pochodzących z zagnieżdżone kontenery.](./media/using-nested-graphics-containers/nested-containers-three-strings.png)  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Drawing.Graphics>
- [Zarządzanie stanem obiektu graficznego](managing-the-state-of-a-graphics-object.md)
