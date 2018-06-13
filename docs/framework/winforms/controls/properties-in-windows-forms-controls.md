---
title: Właściwości formantów formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], properties overview (using code)
- controls [Windows Forms], properties
- properties [Windows Forms]
ms.assetid: 2785279b-fb57-4937-8f6b-2050e475db6f
ms.openlocfilehash: aa7d8be158f4e0a7b2b95bf02cb0d1e173041f59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538132"
---
# <a name="properties-in-windows-forms-controls"></a>Właściwości formantów formularzy systemu Windows
Formant formularzy systemu Windows dziedziczy wiele formularza właściwości klasy podstawowej <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Te właściwości obejmują takie jak <xref:System.Windows.Forms.Control.Font%2A>, <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Bounds%2A>, <xref:System.Windows.Forms.Control.ClientRectangle%2A>, <xref:System.Windows.Forms.Control.DisplayRectangle%2A>, <xref:System.Windows.Forms.Control.Enabled%2A>, <xref:System.Windows.Forms.Control.Focused%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>, <xref:System.Windows.Forms.Control.Visible%2A>, <xref:System.Windows.Forms.Control.AutoSize%2A>i wiele innych. Aby uzyskać szczegółowe informacje o właściwości dziedziczone, zobacz <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.  
  
 Można zastąpić właściwości dziedziczone formantu oraz jak definiowania nowych właściwości.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Definiowanie właściwości](../../../../docs/framework/winforms/controls/defining-a-property-in-windows-forms-controls.md)  
 Pokazuje, jak implementować właściwość dla kontrolek niestandardowych lub składnik oraz sposób integracji właściwość w środowisku projektowania.  
  
 [Definiowanie wartości domyślnych za pomocą metod ShouldSerialize i Reset](../../../../docs/framework/winforms/controls/defining-default-values-with-the-shouldserialize-and-reset-methods.md)  
 Pokazuje, jak można definiować wartości właściwości domyślnej dla składnika lub kontrolki niestandardowej.  
  
 [Zdarzenia zmiany właściwości](../../../../docs/framework/winforms/controls/property-changed-events.md)  
 Opisuje sposób włączenia powiadomień zmiany właściwości, gdy wartość właściwości zostanie zmieniona.  
  
 [Instrukcje: udostępnianie właściwości kontrolek składowych](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)  
 Pokazuje, jak do udostępnienia właściwości formantów składowych w złożonych kontrolek niestandardowych.  
  
 [Implementacja metody w kontrolkach niestandardowych](../../../../docs/framework/winforms/controls/method-implementation-in-custom-controls.md)  
 Zawiera opis sposobu implementacji metod w niestandardowych kontrolek i składników.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.UserControl>  
 Dokumenty klasę podstawową dla implementacji formanty złożone.  
  
 <xref:System.ComponentModel.TypeConverterAttribute>  
 Dokumenty atrybut, który określa <xref:System.ComponentModel.TypeConverter> do użycia w przypadku typu właściwości niestandardowej.  
  
 <xref:System.ComponentModel.EditorAttribute>  
 Dokumenty atrybut, który określa <xref:System.Drawing.Design.UITypeEditor> dla właściwości niestandardowej.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Atrybuty w kontrolkach formularzy Windows Forms](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
 Zawiera opis atrybutów, które można zastosować do właściwości lub innych elementach członkowskich niestandardowe formanty i składniki.  
  
 [Atrybuty czasu projektowania dla składników](http://msdn.microsoft.com/library/12050fe3-9327-4509-9e21-4ee2494b95c3)  
 Wyświetla listę atrybutów metadanych do zastosowania do składników i formantów, dzięki czemu są wyświetlane poprawnie w czasie projektowania w wizualnych projektantów.  
  
 [Rozszerzenie obsługi w czasie projektowania](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 Zawiera opis sposobu implementacji klasy, takie jak edytory i projektantów, które zapewniają obsługę w czasie projektowania.
