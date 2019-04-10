---
title: 'Instrukcje: blokowanie kontrolek do formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: ac5fbf33564ed2dd1a030132a35b36164f777519
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59301701"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Instrukcje: blokowanie kontrolek do formularzy systemu Windows
Podczas projektowania interfejsu użytkownika (UI) w aplikacji Windows, można zablokować kontrolki po znajdują się one poprawnie, tak aby wątkami aby przypadkowo nie przenosić lub zmieniać ich rozmiar przy ustawianiu inne właściwości.  
  
 Ponadto można zablokować i odblokować wszystkie formanty w formularzu jednocześnie, co jest przydatne w przypadku formularzy z wieloma formantami, albo można odblokować pojedynczych formantów. Po umieszczeniu wszystkich kontrolek odpowiednie miejsca w formularzu, należy zablokować je w miejscu, aby uniknąć przenoszenia błędne.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-lock-a-control"></a>Aby zablokować kontrolki  
  
1. W **właściwości** okna, kliknij przycisk **zablokowany** właściwości i wybierz pozycję `true`. (Dwukrotne kliknięcie nazwy Przełącza ustawienie właściwości).  
  
     Alternatywnie, kliknij prawym przyciskiem myszy formant i wybierz **formantów blokady**.  
  
    > [!NOTE]
    >  Blokowanie formantów uniemożliwia ich przeciąganie nowy rozmiar lub lokalizacji na powierzchni projektowej. Jednak nadal można zmienić rozmiar lub położenie kontrolki poprzez **właściwości** oknie lub w kodzie.  
  
### <a name="to-lock-all-the-controls-on-a-form"></a>Aby zablokować wszystkie formanty w formularzu  
  
1. Z **Format** menu, wybierz **formantów blokady**.  
  
    > [!NOTE]
    >  To polecenie umożliwia zablokowanie rozmiar formularza, ponieważ kontrolki formularza.  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a>Aby odblokować wszystkie zablokowane kontrolek w formularzu  
  
1. Z **Format** menu, wybierz **formantów blokady**.  
  
     Wszystkie uprzednio zablokowaną kontrolki w formularzu są teraz odblokowane.  
  
### <a name="to-unlock-locked-controls-individually"></a>Aby odblokować zablokowany formantów indywidualnie  
  
1. W **właściwości** okna, kliknij przycisk **zablokowany** właściwości i wybierz pozycję `false`. (Dwukrotne kliknięcie nazwy Przełącza ustawienie właściwości).  
  
## <a name="see-also"></a>Zobacz także

- [Formanty formularzy systemu Windows](index.md)
- [Rozmieszczanie formantów na formularzach systemu Windows](arranging-controls-on-windows-forms.md)
- [Etykietowanie pojedynczych formantów formularzy systemu Windows i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md)
- [Formanty formularzy systemu Windows według funkcji](windows-forms-controls-by-function.md)
