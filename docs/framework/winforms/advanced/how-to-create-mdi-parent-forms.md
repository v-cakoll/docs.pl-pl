---
title: 'Porady: tworzenie formularzy nadrzędnych MDI'
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: 8d7a25b771488540d4867143a62c5c2487803a95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525194"
---
# <a name="how-to-create-mdi-parent-forms"></a>Porady: tworzenie formularzy nadrzędnych MDI
> [!IMPORTANT]
>  W tym temacie używa <xref:System.Windows.Forms.MainMenu> formant, który został zastąpiony przez <xref:System.Windows.Forms.MenuStrip> formantu. <xref:System.Windows.Forms.MainMenu> Formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.  Informacje o tworzeniu MDI nadrzędnego formularza za pomocą <xref:System.Windows.Forms.MenuStrip>, zobacz [porady: tworzenie List okien MDI za pomocą elementu MenuStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).  
  
 Foundation aplikacji interfejsu wielu dokumentów (MDI) to formularza nadrzędnego MDI. Jest to formularz, który zawiera okien podrzędnych MDI, które są podrzędne windows, w którym użytkownik wchodzi w interakcję z aplikacją MDI. Tworzenie formularza nadrzędnego MDI jest łatwe, zarówno w narzędziu Projektant dla formularzy systemu Windows, jak i programowo.  
  
### <a name="to-create-an-mdi-parent-form-at-design-time"></a>Aby utworzyć formularza nadrzędnego MDI w czasie projektowania  
  
1.  Utwórz projekt aplikacji systemu Windows.  
  
2.  W **właściwości** ustaw <xref:System.Windows.Forms.Form.IsMdiContainer%2A> właściwości **true**.  
  
     Określa formularza jako kontenera okien podrzędnych MDI.  
  
    > [!NOTE]
    >  Podczas ustawiania właściwości **właściwości** okna, można również ustawić `WindowState` właściwości **Maximized**, jeśli chcesz, ponieważ jest najłatwiejsza do manipulowania okien podrzędnych MDI formularz nadrzędny jest zmaksymalizowane. Ponadto należy pamiętać, że krawędzi formularza nadrzędnego MDI przejmą kolorów systemu (zestaw w Panelu sterowania systemu Windows), zamiast kolor tyłu można ustawić za pomocą <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> właściwości.  
  
3.  Z **przybornika**, przeciągnij **MenuStrip** sterowania do formularza. Utwórz element menu najwyższego poziomu z **tekst** ustawioną właściwość **& pliku** z elementami podmenu o nazwie **& nowym** i **& Zamknij**. Również utworzyć wywołuje element menu najwyższego poziomu **& okna**.  
  
     Pierwszy menu utworzy i ukrywanie elementów menu w czasie wykonywania, i drugie menu będzie śledzenie okien podrzędnych MDI. W tym momencie utworzono nadrzędnego okna MDI.  
  
4.  Naciśnij klawisz **F5** do uruchomienia aplikacji. Informacji o tworzeniu formularz podrzędny MDI systemu windows, które działają w ramach formularza nadrzędnego MDI, zobacz [porady: tworzenie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje interfejsu wielu dokumentów (MDI)](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)  
 [Instrukcje: tworzenie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Instrukcje: określanie elementu podrzędnego MDI Active](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)  
 [Instrukcje: wysyłanie danych do Active MDI Child](../../../../docs/framework/winforms/advanced/how-to-send-data-to-the-active-mdi-child.md)  
 [Instrukcje: aranżowanie formularzy podrzędnych MDI](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
