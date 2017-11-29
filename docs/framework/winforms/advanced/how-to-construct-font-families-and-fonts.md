---
title: 'Porady: tworzenie rodzin czcionek i czcionek'
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
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 066cf358e43dabb3b952b32ecec34ca77c6e8c38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-construct-font-families-and-fonts"></a>Porady: tworzenie rodzin czcionek i czcionek
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]grupuje czcionek z tej samej krój, ale różnych stylów do rodziny czcionek. Na przykład rodziny czcionek Arial zawiera następujące czcionki:  
  
-   Regularne Arial  
  
-   Arial Bold  
  
-   Arial kursywa  
  
-   Arial pogrubienie, kursywa  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]używa czterech stylów do formularza rodzin: regularne, pogrubienie, kursywa i pogrubienie, kursywa. Określeniem, takich jak *zawęzić* i *zaokrąglona* nie są uznawane za style; a nie są one częścią nazwę rodziny. Na przykład Arial Narrow jest rodzinę czcionek z następujących członków:  
  
-   Arial Regular wąskie  
  
-   Wąskie Arial Bold  
  
-   Arial kursywa wąskie  
  
-   Arial wąskie pogrubiona kursywa  
  
 Przed rozpoczęciem rysowania tekstu w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], musisz utworzyć <xref:System.Drawing.FontFamily> obiektu i <xref:System.Drawing.Font> obiektu. <xref:System.Drawing.FontFamily> Obiektu określa krój (na przykład Arial) i <xref:System.Drawing.Font> obiektu określa rozmiar, styl i jednostki.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy regularne styl czcionki Arial o rozmiarze 16 pikseli. W poniższym kodzie pierwszy argument przekazany do <xref:System.Drawing.Font.%23ctor%2A> Konstruktor jest <xref:System.Drawing.FontFamily> obiektu. Drugi argument określa rozmiar czcionki, mierzona w jednostkach identyfikowane przez czwarty argument. Trzeci argument określa styl.  
  
 <xref:System.Drawing.GraphicsUnit.Pixel>jest elementem członkowskim <xref:System.Drawing.GraphicsUnit> wyliczenia, i <xref:System.Drawing.FontStyle.Regular> jest elementem członkowskim <xref:System.Drawing.FontStyle> wyliczenia.  
  
 [!code-csharp[System.Drawing.FontsAndText#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie czcionek i tekstu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Grafika i rysowanie w formularzach systemu Windows](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
