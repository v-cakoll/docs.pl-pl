---
title: "Porady: ustawienie pozycji tabulatorów w rysowanym tekście"
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
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e561e8096780301230071e869dac482a6a908a5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a>Porady: ustawienie pozycji tabulatorów w rysowanym tekście
Można ustawić tabulatorów tekstu przez wywołanie metody <xref:System.Drawing.StringFormat.SetTabStops%2A> metody <xref:System.Drawing.StringFormat> obiektu, a następnie przekazywanie, który <xref:System.Drawing.StringFormat> do obiektu <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> Ma obsługuje dodawanie punktów tabulacji narysowanego tekstu, mimo że można rozszerzyć istniejącą kartę przestanie używać <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flagi.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia tabulatorów 150, 250 i 350. Następnie kod wyświetla listę z kartami nazwy i wyniki testu.  
  
 Na poniższej ilustracji przedstawiono tekst z kartami.  
  
 ![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")  
  
 Poniższy kod powoduje przekazanie dwa argumenty <xref:System.Drawing.StringFormat.SetTabStops%2A> metody. Drugi argument jest tablica zawierająca kartę przesunięcia. Pierwszy argument przekazany do <xref:System.Drawing.StringFormat.SetTabStops%2A> ma wartość 0, co oznacza, że pierwsze przesunięcie w tablicy jest mierzony z pozycji 0, do lewej krawędzi prostokątem.  
  
 [!code-csharp[System.Drawing.FontsAndText#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie czcionek i tekstu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Porady: Rysowanie tekstu z GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
