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
ms.openlocfilehash: 460ebb37ee62691a1e282f756840121fd378ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182464"
---
# <a name="using-nested-graphics-containers"></a>Używanie zagnieżdżonych kontenerów grafiki
GDI+ udostępnia kontenery, których można użyć do tymczasowego zastąpienia <xref:System.Drawing.Graphics> lub rozszerzenia części stanu w obiekcie. Tworzenie kontenera przez <xref:System.Drawing.Graphics.BeginContainer%2A> wywołanie <xref:System.Drawing.Graphics> metody obiektu. Można wywołać <xref:System.Drawing.Graphics.BeginContainer%2A> wielokrotnie do tworzenia kontenerów zagnieżdżonych. Każde wywołanie <xref:System.Drawing.Graphics.BeginContainer%2A> musi być sparowane <xref:System.Drawing.Graphics.EndContainer%2A>z wywołaniem .  
  
## <a name="transformations-in-nested-containers"></a>Przekształcenia w zagnieżdżonych kontenerach  
 Poniższy przykład <xref:System.Drawing.Graphics> tworzy obiekt i <xref:System.Drawing.Graphics> kontener w tym obiekcie. Transformacja świata <xref:System.Drawing.Graphics> obiektu jest tłumaczeniem 100 jednostek w kierunku x i 80 jednostek w kierunku y. Transformacja świata kontenera jest obrót 30 stopni. Kod sprawia, `DrawRectangle(pen, -60, -30, 120, 60)` że połączenie dwa razy. Pierwsze wywołanie <xref:System.Drawing.Graphics.DrawRectangle%2A> znajduje się wewnątrz kontenera; oznacza to, że połączenie znajduje <xref:System.Drawing.Graphics.BeginContainer%2A> się <xref:System.Drawing.Graphics.EndContainer%2A>między połączeniami do i . Drugie połączenie <xref:System.Drawing.Graphics.DrawRectangle%2A> jest po wywołaniu . <xref:System.Drawing.Graphics.EndContainer%2A>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 W poprzednim kodzie prostokąt rysowany z wnętrza kontenera jest przekształcany najpierw przez transformację świata kontenera <xref:System.Drawing.Graphics> (obrót), a następnie przez transformację świata obiektu (tłumaczenie). Prostokąt rysowany spoza kontenera jest przekształcany tylko przez <xref:System.Drawing.Graphics> transformację świata obiektu (tłumaczenie). Na poniższej ilustracji przedstawiono dwa prostokąty:
  
 ![Ilustracja przedstawiająca zagnieżdżone kontenery.](./media/using-nested-graphics-containers/nested-containers-illustration.png)  
  
## <a name="clipping-in-nested-containers"></a>Przycinanie w zagnieżdżonych pojemnikach  
 W poniższym przykładzie pokazano, jak zagnieżdżone kontenery obsługują regiony przycinania. Kod tworzy <xref:System.Drawing.Graphics> obiekt i kontener <xref:System.Drawing.Graphics> w tym obiekcie. Obszar przycinania <xref:System.Drawing.Graphics> obiektu jest prostokątem, a obszar przycinania kontenera jest elipsą. Kod sprawia, że <xref:System.Drawing.Graphics.DrawLine%2A> dwa wywołania metody. Pierwsze wywołanie <xref:System.Drawing.Graphics.DrawLine%2A> znajduje się wewnątrz kontenera, <xref:System.Drawing.Graphics.DrawLine%2A> a drugie wywołanie znajduje <xref:System.Drawing.Graphics.EndContainer%2A>się poza kontenerem (po wywołaniu). Pierwsza linia jest przycięta przez przecięcie dwóch regionów przycinania. Druga linia jest przycinana tylko przez prostokątny obszar <xref:System.Drawing.Graphics> przycinania obiektu.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 Na poniższej ilustracji przedstawiono dwie przycięte linie:
  
 ![Ilustracja przedstawiająca zagnieżdżony kontener z przyciętymi liniami.](./media/using-nested-graphics-containers/nested-container-clipped-lines.png)  
  
 Jak pokazują dwa poprzednie przykłady, przekształcenia i regiony przycinania są kumulowane w zagnieżdżonych kontenerach. Jeśli ustawisz przekształcenia świata <xref:System.Drawing.Graphics> kontenera i obiektu, oba przekształcenia będą stosowane do elementów pobranych z wewnątrz kontenera. Transformacja kontenera zostanie zastosowana jako pierwsza, <xref:System.Drawing.Graphics> a transformacja obiektu zostanie zastosowana w drugim miejscu. Jeśli ustawisz obszary przycinania kontenera i <xref:System.Drawing.Graphics> obiektu, elementy rysowane z wnętrza kontenera zostaną przycięte przez przecięcie dwóch regionów przycinania.  
  
## <a name="quality-settings-in-nested-containers"></a>Ustawienia jakości w zagnieżdżonych kontenerach  
 Ustawienia jakości<xref:System.Drawing.Graphics.SmoothingMode%2A> <xref:System.Drawing.Graphics.TextRenderingHint%2A>( , i tym podobne) w zagnieżdżonych pojemnikach nie kumulują się; ustawienia jakości kontenera tymczasowo zastępują ustawienia jakości <xref:System.Drawing.Graphics> obiektu. Podczas tworzenia nowego kontenera ustawienia jakości dla tego kontenera są ustawione na wartości domyślne. Załóżmy na przykład, że <xref:System.Drawing.Graphics> masz obiekt <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>z trybem wygładzania . Podczas tworzenia kontenera tryb wygładzania wewnątrz kontenera jest domyślnym trybem wygładzania. Możesz ustawić tryb wygładzania kontenera, a wszystkie elementy pobrane z wnętrza kontenera zostaną narysowane zgodnie z ustawionym trybem. Elementy rysowane po <xref:System.Drawing.Graphics.EndContainer%2A> wywołaniu zostaną narysowane zgodnie<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>z trybem wygładzania ( ), który był na miejscu przed wywołaniem <xref:System.Drawing.Graphics.BeginContainer%2A>.  
  
## <a name="several-layers-of-nested-containers"></a>Kilka warstw zagnieżdżonych kontenerów  
 Nie są ograniczone do jednego <xref:System.Drawing.Graphics> kontenera w obiekcie. Można utworzyć sekwencję kontenerów, każdy zagnieżdżony w poprzednim i można określić transformację świata, region przycinania i ustawienia jakości każdego z tych zagnieżdżonych kontenerów. Jeśli wywołasz metodę rysowania z wewnątrz kontenera najbardziej wewnętrzny, przekształcenia zostaną zastosowane w kolejności, począwszy od najbardziej wewnętrznego kontenera, a kończąc na najbardziej zewnętrznym kontenerze. Elementy rysowane z wnętrza najbardziej wewnętrznego kontenera zostaną przycięte przez przecięcie wszystkich regionów przycinania.  
  
 Poniższy przykład <xref:System.Drawing.Graphics> tworzy obiekt i ustawia jego <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>wskazówkę renderowania tekstu . Kod tworzy dwa kontenery, jeden zagnieżdżony w drugim. Wskazówka renderowania tekstu zewnętrznego kontenera <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>jest ustawiona na , a wskazówka <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>renderowania tekstu w kontenerze wewnętrznym jest ustawiona na . Kod rysuje trzy ciągi: jeden z kontenera wewnętrznego, jeden <xref:System.Drawing.Graphics> z zewnętrznego kontenera i jeden z samego obiektu.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 Na poniższej ilustracji przedstawiono trzy ciągi. Struny pobierane z wewnętrznego <xref:System.Drawing.Graphics> pojemnika i z obiektu są wygładzone przez antyaliasing. Ciąg rysowany z zewnętrznego kontenera nie jest wygładzony przez antyaliasing, <xref:System.Drawing.Graphics.TextRenderingHint%2A> ponieważ właściwość jest ustawiona na <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.  
  
 ![Ilustracja przedstawiająca ciągi rysowane z zagnieżdżonych kontenerów.](./media/using-nested-graphics-containers/nested-containers-three-strings.png)  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Drawing.Graphics>
- [Zarządzanie stanem obiektu graficznego](managing-the-state-of-a-graphics-object.md)
