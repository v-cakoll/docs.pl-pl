---
title: Opracowywanie formantów formularzy systemu Windows w czasie projektowania
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
ms.openlocfilehash: b58318a3e0e9881725d3c260251288c720fa4132
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44041345"
---
# <a name="developing-windows-forms-controls-at-design-time"></a>Opracowywanie formantów formularzy systemu Windows w czasie projektowania
Dla autorów kontroli programu .NET Framework zapewnia wiele technologii do tworzenia kontrolki. Autorzy nie są już ograniczony do projektowania formanty złożone, które działają jako kolekcję istniejących kontrolek. Poprzez dziedziczenie można utworzyć własne kontrolki z istniejących kontrolek złożonych lub istniejących kontrolek Windows Forms. Istnieje również możliwość projektowania własnych kontrolek, które implementują niestandardowe malowania. Te opcje umożliwiają dużą elastyczność w projekcie i funkcjonalność interfejsu wizualnego. Aby móc korzystać z tych funkcji, należy zapoznać się z koncepcjami opartej na obiektach.  
  
> [!NOTE]
>  Nie jest konieczne dogłębną wiedzę na temat dziedziczenia, ale może okazać się przydatne do odwoływania się do [podstawowe informacje o dziedziczeniu (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Jeśli chcesz utworzyć niestandardowe formanty do użycia w formularzach sieci Web, zobacz artykuł [tworzenie niestandardowe formanty serwera ASP.NET](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 Przedstawia sposób tworzenia prostego formantu złożonego w języku Visual Basic.  
  
 [Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 Przedstawia sposób tworzenia prostego formantu złożonego w języku C#.  
  
 [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 Przedstawia sposób tworzenia prostego formantu Windows Forms za pomocą dziedziczenia w języku Visual Basic.  
  
 [Przewodnik: dziedziczenie z kontrolki formularzy Windows Forms za pomocą języka Visual C#](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 Przedstawia sposób tworzenia prostego formantu Windows Forms za pomocą dziedziczenia w języku C#.  
  
 [Przewodnik: przeprowadzanie typowych zadań z tagami inteligentnymi na kontrolkach formularzy Windows Forms](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 Pokazuje, jak korzystać z funkcji tagu inteligentnego kontrolek Windows Forms.  
  
 [Przewodnik: serializowanie kolekcji standardowych typów za pomocą elementu DesignerSerializationVisibilityAttribute](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 Ilustruje sposób używania <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> atrybutu do serializacji kolekcji.  
  
 [Przewodnik: debugowanie niestandardowych kontrolek formularzy Windows Forms w czasie projektowania](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 Pokazuje, jak można debugować zachowania formantu Windows Forms w czasie projektowania.  
  
 [Przewodnik: tworzenie kontrolki formularzy Windows Forms wykorzystującej funkcje czasu projektowania programu Visual Studio](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 Pokazuje, jak ściśle zintegrowane formantu złożonego w środowisku projektowym.  
  
 [Instrukcje: tworzenie kontrolek dla formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 Zawiera omówienie zagadnienia dotyczące implementacji formantu Windows Forms.  
  
 [Instrukcje: tworzenie kontrolek złożonych](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 Pokazuje, jak utworzyć formant przez dziedziczenie z kontrolki złożonej.  
  
 [Instrukcje: dziedziczenie z klasy UserControl](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 Zawiera omówienie procedury tworzenia kontrolek złożonych.  
  
 [Instrukcje: dziedziczenie z istniejących kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 Pokazuje, jak tworzenie formantu rozszerzonego przez dziedziczenie z <xref:System.Windows.Forms.Button> kontrolować klasy.  
  
 [Instrukcje: dziedziczenie z klasy kontrolek](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 Omówienie Tworzenie formantu rozszerzonego.  
  
 [Instrukcje: wyrównywanie kontrolki z krawędziami formularzy w czasie projektowania](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 Ilustruje sposób używania <xref:System.Windows.Forms.Control.Dock%2A> właściwość wyrównywanie formantu do krawędzi formularza zajmuje.  
  
 [Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 Zawiera procedury dotyczące instalowania formantu, aby była ona wyświetlana w **Dostosowywanie przybornika** okno dialogowe.  
  
 [Instrukcje: dostarczanie mapy bitowej przybornika dla kontrolki](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 Ilustruje sposób używania <xref:System.Drawing.ToolboxBitmapAttribute> Aby wyświetlić ikonę obok niestandardową kontrolkę w **przybornika**.  
  
 [Instrukcje: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 Ilustruje sposób używania **UserControl — kontener testu** się testowanie zachowania formantu złożonego.  
  
 [Błędy czasu projektowania w narzędziu Projektant dla formularzy Windows Forms](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 Wyjaśnia znaczenie i użyj listy błędów projektowania, który pojawia się w programie Microsoft Visual Studio, gdy nie może załadować projektanta Windows Forms.  
  
 [Rozwiązywanie problemów związanych z kontrolkami oraz tworzeniem składników](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Pokazuje, jak diagnozować i rozwiązywać typowe problemy, które mogą wystąpić podczas tworzenia niestandardowego składnika lub kontrolki.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 Zawiera opis tej klasy i zawiera linki do wszystkich jej członków.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 W tym artykule omówiono sposób tworzenia Kontrolki niestandardowe za pomocą programu .NET Framework.  
  
 [Niezależność od języka i składniki niezależne od języka](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 Wprowadza wykonywalnych języka wspólnego upraszcza tworzenie i używanie składników. Ważnym aspektem uproszczenie to jest rozszerzone możliwości współdziałania między składnikami napisanymi przy użyciu różnych języków programowania. Common Language Specification (CLS) umożliwia tworzenie, narzędzia i składniki, które działają z wielu języków programowania.  
  
 [Przewodnik: automatyczne zapełnianie Przybornika składnikami niestandardowymi](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 Opisuje sposób włączania usługi składnika lub kontrolki, które mają być wyświetlane w **Dostosowywanie przybornika** okno dialogowe.
