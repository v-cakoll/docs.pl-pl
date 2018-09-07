---
title: 'Porady: tworzenie prostego formantu powiązanego na formularzu systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: 26bc136ea2b7e5bda4a57c5dad65ec3522efcd3d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44066457"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>Porady: tworzenie prostego formantu powiązanego na formularzu systemu Windows
Za pomocą *proste powiązanie*, można wyświetlić elementu danych jednego, takiego jak wartość kolumny z tabeli zestawu danych w formancie. Użytkownik może prosty wiązania dowolnej właściwości kontrolki z wartością danych.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-simple-bind-a-control"></a>Do wiązania prostego formantu  
  
1.  Łączenie ze źródłem danych. Aby uzyskać więcej informacji, zobacz [nawiązania połączenia ze źródłem danych](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).  
  
2.  W formularzu wybierz kontrolkę i wyświetlić **właściwości** okna.  
  
3.  Rozwiń **(powiązania danych)** właściwości.  
  
     Właściwości najczęściej powiązane są wyświetlane poniżej **(powiązania danych)** właściwości. Na przykład w przypadku większości kontrolek **tekstu** właściwość najczęściej jest powiązana.  
  
4.  Jeśli właściwość, którą chcesz powiązania nie jest jednym z powszechnie powiązanych właściwości, kliknij pozycję **wielokropka** przycisku (![VisualStudioEllipsesButton — zrzut ekranu](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton") ) w **(zaawansowane)** pole, aby wyświetlić **formatowanie i powiązywanie zaawansowane** okno dialogowe z pełną listę właściwości dla tej kontrolki.  
  
5.  Wybierz właściwość do powiązania, a następnie kliknij strzałkę listy rozwijanej w obszarze **powiązanie**.  
  
     Zostanie wyświetlona lista dostępnych źródeł danych.  
  
6.  Rozwiń źródło danych, które chcesz powiązać, dopóki nie znajdziesz element danych jednego, który ma. Na przykład jeśli dokonywane jest wiązanie wartość kolumny w tabeli zestawu danych, rozwiń węzeł z nazwą zestawu danych, a następnie rozwiń nazwę tabeli, aby wyświetlić nazwy kolumn.  
  
7.  Kliknij nazwę elementu można powiązać.  
  
8.  Jeśli pracujesz **formatowanie i powiązywanie zaawansowane** okno dialogowe, kliknij przycisk **OK** aby powrócić do **właściwości** okna.  
  
9. Jeśli chcesz powiązać dodatkowe właściwości formantu, powtórz kroki od 3 do 7.  
  
    > [!NOTE]
    >  Ponieważ formanty powiązane z prostego pokazać tylko danych jednego elementu, to bardzo typowy do uwzględnienia nawigacji logiki w formularzu Windows za pomocą formantów powiązanych z prostego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Binding>  
 [Wiązanie danych formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Wiązanie danych i formularzy Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
