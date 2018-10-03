---
title: Właściwości formantów formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: 37db3f16a17acc7f3a6e594bd284ba368801e70a
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48036875"
---
# <a name="properties-in-windows-forms-controls"></a>Właściwości formantów formularzy systemu Windows
Formant programu Windows Forms dziedziczy wiele formularza właściwości klasy bazowej <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Obejmują one właściwości takich jak <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>i wiele innych. Aby uzyskać szczegółowe informacje o właściwości dziedziczonych, zobacz <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 Można zastąpić właściwości dziedziczonych w kontrolce i jak definiowania nowych właściwości.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Definiowanie właściwości](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 Pokazuje, jak implementować właściwość kontrolkę niestandardową lub składnika i pokazuje, jak zintegrować właściwość środowisko projektowania.  
  
 [Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 Pokazuje jak zdefiniować domyślne wartości właściwości dla składnika lub kontrolki niestandardowej.  
  
 [Zdarzenia zmiany właściwości](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 W tym artykule opisano, jak włączyć powiadomienia o zmianie właściwości po zmianie wartości właściwości.  
  
 [Instrukcje: udostępnianie właściwości kontrolek składowych](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 Pokazuje, jak udostępnianie właściwości formantów składowych w złożonego formantu niestandardowego.  
  
 [Implementacja metody w kontrolkach niestandardowych](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 Opisuje sposób implementacji metody w kontrolkach niestandardowych i składników.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.UserControl>  
 Dokumenty klasę bazową dla implementacji formanty złożone.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 Dokumenty atrybut, który określa <xref:System.ComponentModel.TypeConverter> do użycia w przypadku typu właściwości niestandardowej.  
  
 <xref:System.ComponentModel.EditorAttribute>  
 Dokumenty atrybut, który określa <xref:System.Drawing.Design.UITypeEditor> do użycia dla właściwości niestandardowej.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Atrybuty w kontrolkach formularzy Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 W tym artykule opisano atrybuty, które można zastosować do właściwości lub innym członkom swojej niestandardowych kontrolek i składników.  
  
 [Atrybuty czasu projektowania dla składników](https://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 Wyświetla listę atrybutów metadanych, które mają zastosowanie do składników i formantów, aby były wyświetlane poprawnie w czasie projektowania w projektantów wizualnych.  
  
 [Rozszerzenie obsługi w czasie projektowania](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 Opisuje sposób implementacji klas, takich jak edytorach i projektantach, które zapewniają obsługę projektowania.
