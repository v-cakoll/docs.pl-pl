---
title: 'Porady: tworzenie prostego formantu powiązanego na formularzu systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: ce4585a1c5c2b9acbdb7ec33c62a1e91851b720e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>Porady: tworzenie prostego formantu powiązanego na formularzu systemu Windows
Z *proste powiązanie*, element danych, np. wartość kolumny z tabeli zestawu danych, można wyświetlić w formancie. Możesz można prosty — wiązanie żadnej właściwości formantu do wartości danych.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-simple-bind-a-control"></a>Prosty polecenia BIND formant  
  
1.  Połączenie ze źródłem danych. Aby uzyskać więcej informacji, zobacz [połączenie ze źródłem danych](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).  
  
2.  W formularzu, wybierz kontrolkę i wyświetlić **właściwości** okna.  
  
3.  Rozwiń węzeł **(DataBindings)** właściwości.  
  
     Właściwości często powiązane są wyświetlane poniżej **(DataBindings)** właściwości. Na przykład w przypadku większości formantów **tekst** właściwości najczęściej jest powiązany.  
  
4.  Jeśli właściwość ma zostać powiązania nie jest jednym z często powiązane właściwości, kliknij pozycję **wielokropka** przycisk (![VisualStudioEllipsesButton — zrzut ekranu](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton") ) w **(zaawansowane)** pole, aby wyświetlić **formatowanie i zaawansowane powiązanie** okno dialogowe z pełną listę właściwości dla tego formantu.  
  
5.  Wybierz właściwość, aby powiązać i kliknij strzałkę listy rozwijanej w obszarze **powiązanie**.  
  
     Zostanie wyświetlona lista dostępnych źródeł danych.  
  
6.  Rozwiń źródło danych, które chcesz powiązać do momentu znalezienia element danych, który ma. Na przykład są wiązane wartość kolumny w tabeli zestawu danych, rozwiń nazwę zestawu danych, a następnie rozwiń nazwę tabeli, aby wyświetlić nazwy kolumn.  
  
7.  Kliknij nazwę elementu, aby powiązać.  
  
8.  Podczas pracy **formatowanie i zaawansowane powiązanie** okno dialogowe, kliknij przycisk **OK** aby powrócić do **właściwości** okna.  
  
9. Jeśli chcesz powiązać dodatkowe właściwości formantu, powtórz kroki od 3 do 7.  
  
    > [!NOTE]
    >  Ponieważ formanty powiązane z prostą Pokaż tylko danych jednego elementu, jest bardzo typowy do uwzględnienia w formularzu systemu Windows z formantów powiązanych z prostą logiki nawigacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Binding>  
 [Wiązanie danych formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Wiązanie danych i formularzy Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
