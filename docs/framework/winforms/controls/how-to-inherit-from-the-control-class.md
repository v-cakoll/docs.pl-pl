---
title: 'Instrukcje: dziedziczenie z klasy kontrolek'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: b173f322018921ef1c0fec6aa785ae6c9d9e6957
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141989"
---
# <a name="how-to-inherit-from-the-control-class"></a>Instrukcje: dziedziczenie z klasy kontrolek
Jeśli chcesz utworzyć formant całkowicie niestandardowy do użycia w formularzu Windows, możesz powinien dziedziczyć <xref:System.Windows.Forms.Control> klasy. Podczas dziedziczenie z <xref:System.Windows.Forms.Control> klasy wymaga wykonania więcej planowania i wdrażania go oferuje także funkcje największej gamy opcji. Gdy dziedziczenie z <xref:System.Windows.Forms.Control>, dziedziczą bardzo podstawowe funkcje, który sprawia, że formanty, które działają. Funkcje związane z <xref:System.Windows.Forms.Control> klasy obsługuje danych wejściowych użytkownika za pomocą klawiatury i myszy, definiuje granice i rozmiar formantu, zapewnia uchwytów okien i zapewnia Obsługa komunikatów i bezpieczeństwo. Zawierają wszelkie rysowania, czyli w tym przypadku rzeczywistego renderowania interfejsu graficznego kontrolki, nie jest włączyć wszystkie funkcje interakcji użytkownika. Należy podać wszystkie te aspekty poprzez kod niestandardowy.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-custom-control"></a>Aby utworzyć formant niestandardowy  
  
1.  Utwórz nową **aplikacji Windows** lub **Biblioteka formantów Windows** projektu.  
  
2.  Z **projektu** menu, wybierz **Dodaj klasę**.  
  
3.  W **Dodaj nowy element** okno dialogowe, kliknij przycisk **kontrolkę niestandardową**.  
  
     Nowy formant niestandardowy zostanie dodany do projektu.  
  
4.  Naciśnij klawisz F7, aby otworzyć **Edytor kodu** kontrolki niestandardowej.  
  
5.  Znajdź <xref:System.Windows.Forms.Control.OnPaint%2A> metody, która będzie pusta, z wyjątkiem wywołanie <xref:System.Windows.Forms.Control.OnPaint%2A> metody klasy bazowej.  
  
6.  Zmodyfikuj kod, aby zastosować niestandardowe rysowania, które kontrolki.  
  
     Informacje na temat pisania kodu w celu renderowania grafiki dla formantów, zobacz [niestandardowe malowanie i renderowanie formantu](custom-control-painting-and-rendering.md).  
  
7.  Implementuje żadnych niestandardowych metod, właściwości lub zdarzeń, zawierające Twoją kontrolą.  
  
8.  Zapisz i przetestuj formantu.  
  
## <a name="see-also"></a>Zobacz także

- [Różne typy formantów niestandardowych](varieties-of-custom-controls.md)
- [Instrukcje: dziedziczenie z klasy UserControl](how-to-inherit-from-the-usercontrol-class.md)
- [Instrukcje: dziedziczenie z istniejących kontrolek formularzy systemu Windows](how-to-inherit-from-existing-windows-forms-controls.md)
- [Instrukcje: kontrolki autoryzacji dla formularzy systemu Windows](how-to-author-controls-for-windows-forms.md)
- [Rozwiązywanie problemów związanych z odziedziczonymi programami obsługi zdarzeń w Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [Opracowywanie formantów formularzy systemu Windows w czasie projektowania](developing-windows-forms-controls-at-design-time.md)
