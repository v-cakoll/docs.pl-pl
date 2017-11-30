---
title: "Porady: kotwiczenie formantów na formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c6f7cc527c7409ffecab2ac67386d0f819cce3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>Porady: kotwiczenie formantów na formularzach systemu Windows
W przypadku projektowania formularza, który użytkownik może zmienić rozmiar w czasie wykonywania, formantów w formularzu należy zmienić rozmiar i zmienia położenie poprawnie. Aby zmienić rozmiar kontrolki dynamicznie za pomocą formularza, można użyć <xref:System.Windows.Forms.Control.Anchor%2A> właściwości formantów formularzy systemu Windows. <xref:System.Windows.Forms.Control.Anchor%2A> Właściwość definiuje pozycji zakotwiczenia dla formantu. Gdy formant jest zakotwiczony do formularza i rozmiarów formularza, formant zachowuje odległość między formantem a pozycji zakotwiczenia. Na przykład, jeśli masz <xref:System.Windows.Forms.TextBox> formant, który jest zakotwiczona lewy, prawy i dolnej krawędzi formularza, ponieważ rozmiarów formularza <xref:System.Windows.Forms.TextBox> kontroli zmienia rozmiar w poziomie, aby przechowuje takiej samej odległości od prawej i lewej stronie formularza. Ponadto kontrolka umieszcza się pionowo tak, aby jego lokalizacji jest zawsze tej samej odległości od dolnej krawędzi formularza. Jeśli formant jest zakotwiczony nie zmieni się rozmiar formularza, pozycja kontroli względem krawędzi formularzu zostanie zmieniona.  
  
 <xref:System.Windows.Forms.Control.Anchor%2A> Właściwości współdziała z <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości. Aby uzyskać więcej informacji, zobacz [AutoSize — Przegląd właściwości](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-anchor-a-control-on-a-form"></a>Aby móc zakotwiczyć kontrolkę w formularzu  
  
1.  Wybierz formant, który ma być zakotwiczenia.  
  
    > [!NOTE]
    >  Można zakotwiczyć jednocześnie wiele formantów, klawisz CTRL, klikając każdego formantu, aby go zaznaczyć, a następnie po pozostałą część tej procedury.  
  
2.  W **właściwości** okna, kliknij strzałkę po prawej stronie <xref:System.Windows.Forms.Control.Anchor%2A> właściwości.  
  
     Zostanie wyświetlony Edytor, pokazujący krzyżyk.  
  
3.  Aby ustawić zakotwiczenie, kliknij przycisk, lewego górnego, prawej lub dolnej części krzyżyk.  
  
     Formanty są zakotwiczony górnego i lewego domyślnie.  
  
4.  Aby wyczyścić po stronie formantu, który ma zostać zakotwiczony, kliknij tego arm krzyżyk.  
  
5.  Aby zamknąć <xref:System.Windows.Forms.Control.Anchor%2A> Edytor właściwości, kliknij przycisk <xref:System.Windows.Forms.Control.Anchor%2A> ponownie nazwę właściwości.  
  
 Gdy formularz jest wyświetlany w czasie wykonywania, pozostaje pozycjonowane w tej samej odległości od krawędzi formularza zmienia rozmiar formantu. Odległość od krawędzi zakotwiczonej zawsze pozostaje taki sam jak odległość zdefiniowana, jeśli kontrolka znajduje się w narzędziu Projektant dla formularzy systemu Windows.  
  
> [!NOTE]
>  Niektóre formanty, takie jak <xref:System.Windows.Forms.ComboBox> kontrolować, mają limit ich wysokość. Zakotwiczanie formantu z dolną krawędzią jego formularza lub kontenera nie może wymusić przekroczenie limitu wysokość formantu.  
  
 Formanty dziedziczone muszą być `Protected` mógł być zakotwiczona. Aby zmienić poziom dostępu do formantu, ustaw jej `Modifiers` właściwości w **właściwości** okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty formularzy systemu Windows](../../../../docs/framework/winforms/controls/index.md)  
 [Rozmieszczanie formantów na formularzach systemu Windows](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [AutoSize — Przegląd właściwości](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Porady: dokowanie formantów na formularzach systemu Windows](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Wskazówki: Tworzenie Windows formantów formularzy dopełnienie, marginesami oraz właściwościami AutoSize właściwość](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
