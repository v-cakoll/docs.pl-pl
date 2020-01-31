---
title: Właściwości kontrolek
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 82bfab15cef4946661a37d2d88fbe1b797f3d816
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741180"
---
# <a name="properties-in-windows-forms-controls"></a>Właściwości formantów formularzy systemu Windows
Formant Windows Forms dziedziczy wiele właściwości w klasie bazowej <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Obejmują one takie właściwości, jak <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>i wielu innych. Aby uzyskać szczegółowe informacje na temat właściwości dziedziczonych, zobacz <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 Dziedziczone właściwości można przesłonić w kontrolce, a także definiować nowe właściwości.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Definiowanie właściwości](defining-a-property-in-windows-forms-controls.md)  
 Pokazuje, jak zaimplementować Właściwość niestandardowego formantu lub składnika oraz pokazuje, jak zintegrować właściwość w środowisku projektowym.  
  
 [Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset](defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 Pokazuje, w jaki sposób definiować domyślne wartości właściwości dla niestandardowego formantu lub składnika.  
  
 [Zdarzenia zmiany właściwości](property-changed-events.md)  
 Opisuje sposób włączania powiadomień o zmianach właściwości w przypadku zmiany wartości właściwości.  
  
 [Instrukcje: udostępnianie właściwości kontrolek składowych](how-to-expose-properties-of-constituent-controls.md)  
 Pokazuje, jak uwidocznić właściwości formantów składników w niestandardowej kontrolce złożonej.  
  
 [Implementacja metody w kontrolkach niestandardowych](method-implementation-in-custom-controls.md)  
 Opisuje sposób implementowania metod w niestandardowych kontrolkach i składnikach.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.UserControl>  
 Dokumentuje klasę bazową do implementowania formantów złożonych.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 Dokumentuje atrybut, który określa <xref:System.ComponentModel.TypeConverter> do użycia dla niestandardowego typu właściwości.  
  
 <xref:System.ComponentModel.EditorAttribute>  
 Dokumentuje atrybut, który określa <xref:System.Drawing.Design.UITypeEditor> do użycia dla właściwości niestandardowej.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Atrybuty w kontrolkach formularzy Windows Forms](attributes-in-windows-forms-controls.md)  
 Opisuje atrybuty, które można zastosować do właściwości lub innych elementów niestandardowych formantów i składników.  
  
 [Atrybuty czasu projektowania dla składników](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))  
 Wyświetla listę atrybutów metadanych, które mają zostać zastosowane do składników i formantów, aby były wyświetlane prawidłowo w czasie projektowania w projektantach wizualizacji.  
  
 [Rozszerzanie obsługi czasu projektowania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))  
 Opisuje sposób implementacji klas, takich jak redaktorzy i projektanci, które zapewniają obsługę czasu projektowania.
