---
title: "Używanie zagnieżdżonych kontenerów grafiki"
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
- graphics [Windows Forms], nested containers
- graphics [Windows Forms], clipping
- graphics [Windows Forms], transformations in nested objects
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10c5a1b077e4339f17093e5eb935416bb1ae3d1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-nested-graphics-containers"></a>Używanie zagnieżdżonych kontenerów grafiki
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]udostępnia kontenerów, które można użyć, aby tymczasowo zastąpić lub rozszerzyć część stanu w <xref:System.Drawing.Graphics> obiektu. Kontener można utworzyć przez wywołanie metody <xref:System.Drawing.Graphics.BeginContainer%2A> metody <xref:System.Drawing.Graphics> obiektu. Możesz wywołać <xref:System.Drawing.Graphics.BeginContainer%2A> wielokrotnie w celu utworzenia zagnieżdżone kontenery. Każde wywołanie <xref:System.Drawing.Graphics.BeginContainer%2A> muszą łączyć się z wywołania <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
## <a name="transformations-in-nested-containers"></a>Przekształcenia w zagnieżdżonych kontenerów  
 Poniższy przykład tworzy <xref:System.Drawing.Graphics> obiekt i kontener, w tym <xref:System.Drawing.Graphics> obiektu. Transformacja świata z <xref:System.Drawing.Graphics> obiekt jest translacja 100 w kierunku x i 80 jednostek w kierunku y. Transformacja świata kontenera jest 30 stopni. Kod sprawia, że wywołanie `DrawRectangle(pen, -60, -30, 120, 60)` dwa razy. W pierwszym wywołaniu <xref:System.Drawing.Graphics.DrawRectangle%2A> znajduje się wewnątrz kontenera; wywołanie jest Between wywołań <xref:System.Drawing.Graphics.BeginContainer%2A> i <xref:System.Drawing.Graphics.EndContainer%2A>. Drugie wywołanie <xref:System.Drawing.Graphics.DrawRectangle%2A> po wywołaniu <xref:System.Drawing.Graphics.EndContainer%2A>.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 W powyższym kodzie prostokąt pochodzą z wewnątrz kontenera jest przekształcana najpierw według transformacji świata kontenera (obrót), a następnie transformacji świata <xref:System.Drawing.Graphics> obiektu (tłumaczenia). Prostokąt pobierane z zewnątrz kontenera jest przekształcana tylko przez transformacji świata <xref:System.Drawing.Graphics> obiektu (tłumaczenia). Na poniższej ilustracji przedstawiono dwa prostokąty.  
  
 ![Zagnieżdżone kontenery](../../../../docs/framework/winforms/advanced/media/csnestedcontainers1.png "csnestedcontainers1")  
  
## <a name="clipping-in-nested-containers"></a>Przycinanie zagnieżdżone kontenery  
 W poniższym przykładzie pokazano sposób zagnieżdżone kontenery obsługi regionów wycinka. Kod tworzy <xref:System.Drawing.Graphics> obiekt i kontener, w tym <xref:System.Drawing.Graphics> obiektu. Region wycinka <xref:System.Drawing.Graphics> obiektu jest prostokąt, a obszaru przycinania kontenera elipsy. Kod sprawia, że dwa wywołań <xref:System.Drawing.Graphics.DrawLine%2A> metody. W pierwszym wywołaniu <xref:System.Drawing.Graphics.DrawLine%2A> znajduje się wewnątrz kontenera, a drugie wywołanie <xref:System.Drawing.Graphics.DrawLine%2A> znajduje się poza kontenera (po wywołaniu <xref:System.Drawing.Graphics.EndContainer%2A>). Pierwszy wiersz zostanie obcięta przez przecięcie wycinka dwóch regionach. Drugi wiersz jest przycinana tylko przez region Prostokątny wycinek <xref:System.Drawing.Graphics> obiektu.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 Na poniższej ilustracji przedstawiono dwa wiersze przyciętą.  
  
 ![Zagnieżdżone kontenera](../../../../docs/framework/winforms/advanced/media/nestedcontainers2.png "nestedcontainers2")  
  
 Zgodnie z dwóch poprzednich przykładach, transformacji i regiony wycinka kumulują się w zagnieżdżonych kontenerów. Jeśli ustawisz świecie przekształceń kontenera i <xref:System.Drawing.Graphics> obiektu, zarówno przekształcenia będą stosowane do elementów, które pochodzą z wewnątrz kontenera. Kontenera transformacja zostaną zastosowane pierwszy i przekształcenie <xref:System.Drawing.Graphics> zostaną zastosowane drugi obiekt. Jeśli ustawisz regionów wycinka kontenera i <xref:System.Drawing.Graphics> obiektu, elementy, które pochodzą z wewnątrz kontenera obetnie część wspólną dwóch wycinka regionów.  
  
## <a name="quality-settings-in-nested-containers"></a>Ustawienia jakości w zagnieżdżonych kontenerów  
 Ustawienia jakości (<xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.TextRenderingHint%2A>itp) w zagnieżdżonych kontenerów nie kumulują się; zamiast ustawień jakości kontenera tymczasowo zastąpić ustawienia jakości <xref:System.Drawing.Graphics> obiektu. Podczas tworzenia nowego kontenera ustawienia jakości dla tego kontenera są ustawiane na wartości domyślne. Na przykład, załóżmy, że masz <xref:System.Drawing.Graphics> obiektu o tryb wygładzania <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Po utworzeniu kontenera tryb wygładzania wewnątrz kontenera jest domyślny tryb wygładzania. Mogą ustawić tryb wygładzania kontenera, a wszystkie elementy, które pochodzą z wewnątrz kontenera będzie rysowany zgodnie z tryb, w którym można ustawić. Elementy rysowane po wywołaniu <xref:System.Drawing.Graphics.EndContainer%2A> będzie rysowany zgodnie z tryb wygładzania (<xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>) który był zainstalowany przed wywołaniem do <xref:System.Drawing.Graphics.BeginContainer%2A>.  
  
## <a name="several-layers-of-nested-containers"></a>Zagnieżdżone kontenery kilku warstw  
 Nie są ograniczone do jednego kontenera w <xref:System.Drawing.Graphics> obiektu. Można utworzyć sekwencję kontenerów, każdy zagnieżdżony w poprzednim i można określić transformacja świata obszar przycinania, a ustawienia jakości każdego z tych kontenerach zagnieżdżonych. Wywołanie metody rysowania z wewnątrz kontenera najbardziej przekształceń będą stosowane w kolejności, począwszy od najbardziej kontenera i kończąc peryferyjnych kontenera. Elementy, które pochodzą z wewnątrz kontenera najbardziej obetnie przecięcia regionów wycinka.  
  
 Poniższy przykład tworzy <xref:System.Drawing.Graphics> obiektów i ustawia jej wskazówkę dotyczącą renderowania tekstu <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Kod tworzy dwa kontenery, jedną zagnieżdżone w innych. Ustawiono wskazówkę dotyczącą renderowania tekstu zewnętrzne kontenera <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>, i ma ustawioną wartość wskazówkę dotyczącą renderowania tekst wewnętrzny kontenera <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias>. Kod rysuje trzy parametry: jeden z kontenera wewnętrzny: jeden z zewnętrznym kontenera i jeden z <xref:System.Drawing.Graphics> samego obiektu.  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 Na poniższej ilustracji przedstawiono trzy ciągi. Ciągi rysowane z kontenera wewnętrzny i <xref:System.Drawing.Graphics> obiektu są wygładzane przez antialiasingu. Ciąg z kontenera nie jest wygładzane przez antialiasingu, ponieważ <xref:System.Drawing.Graphics.TextRenderingHint%2A> właściwość jest ustawiona na <xref:System.Drawing.Text.TextRenderingHint.SingleBitPerPixel>.  
  
 ![Zagnieżdżone kontenery](../../../../docs/framework/winforms/advanced/media/nestedcontainers3.png "nestedcontainers3")  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Drawing.Graphics>  
 [Zarządzaniu stanem obiektu graficznego](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)
