---
title: 'Instrukcje: Tworzenie rodzin czcionek i czcionek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- font families [Windows Forms], constructing
- fonts [Windows Forms], constructing
ms.assetid: d3a4a223-9492-4b54-9afd-db1c31c3cefd
ms.openlocfilehash: d3c4b5b4293b62cfec0f8471f90be673854e9009
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590363"
---
# <a name="how-to-construct-font-families-and-fonts"></a>Instrukcje: Tworzenie rodzin czcionek i czcionek
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grupuje czcionki o tej samej krój czcionki, ale różnych stylów do rodziny czcionek. Na przykład rodziny czcionka Arial zawiera następujące czcionki:  
  
- Regularne Arial  
  
- Arial pogrubienia  
  
- Kursywa Arial  
  
- Arial Bold Italic  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] używa czterech stylów do formularza rodzin: regularnych, pogrubienie, kursywa i pogrubiona kursywa. Określeniem, takie jak *zawęzić* i *zaokrąglone* nie są uważane za style; przeciwnie są one częścią nazwę rodziny. Na przykład Arial Narrow jest rodzinę czcionek, za pomocą następujących elementów członkowskich:  
  
- Arial zwykłych Narrow  
  
- Wąski Arial pogrubienia  
  
- Arial wąskie kursywa  
  
- Arial wąskie pogrubiona kursywa  
  
 Zanim można rysować tekst z [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], musisz utworzyć <xref:System.Drawing.FontFamily> obiektu i <xref:System.Drawing.Font> obiektu. <xref:System.Drawing.FontFamily> Obiektu określa krój czcionki (na przykład Arial), a <xref:System.Drawing.Font> obiekt Określa rozmiar, styl i jednostek.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy stylu normalnego czcionka Arial o rozmiarze 16 pikseli. W poniższym kodzie pierwszy argument przekazany do <xref:System.Drawing.Font.%23ctor%2A> Konstruktor jest <xref:System.Drawing.FontFamily> obiektu. Drugi argument określa rozmiar czcionki, mierzoną w jednostkach identyfikowane przez czwarty argument. Trzeci argument określa styl.  
  
 <xref:System.Drawing.GraphicsUnit.Pixel> jest elementem członkowskim <xref:System.Drawing.GraphicsUnit> wyliczenia, a <xref:System.Drawing.FontStyle.Regular> jest elementem członkowskim <xref:System.Drawing.FontStyle> wyliczenia.  
  
 [!code-csharp[System.Drawing.FontsAndText#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.FontsAndText#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Zobacz także

- [Używanie czcionek i tekstu](using-fonts-and-text.md)
- [Grafika i rysowanie w formularzach Windows Forms](graphics-and-drawing-in-windows-forms.md)
