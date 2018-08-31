---
title: 'Porady: blokowanie formantów do formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: 8de22ae6667446620867f3c15aac3c4af65582bf
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43253633"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Porady: blokowanie formantów do formularzy systemu Windows
Podczas projektowania interfejsu użytkownika (UI) w aplikacji Windows, można zablokować kontrolki po znajdują się one poprawnie, tak aby wątkami aby przypadkowo nie przenosić lub zmieniać ich rozmiar przy ustawianiu inne właściwości.  
  
 Ponadto można zablokować i odblokować wszystkie formanty w formularzu jednocześnie, co jest przydatne w przypadku formularzy z wieloma formantami, albo można odblokować pojedynczych formantów. Po umieszczeniu wszystkich kontrolek odpowiednie miejsca w formularzu, należy zablokować je w miejscu, aby uniknąć przenoszenia błędne.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-lock-a-control"></a>Aby zablokować kontrolki  
  
1.  W **właściwości** okna, kliknij przycisk **zablokowany** właściwości i wybierz pozycję `true`. (Dwukrotne kliknięcie nazwy Przełącza ustawienie właściwości).  
  
     Alternatywnie, kliknij prawym przyciskiem myszy formant i wybierz **formantów blokady**.  
  
    > [!NOTE]
    >  Blokowanie formantów uniemożliwia ich przeciąganie nowy rozmiar lub lokalizacji na powierzchni projektowej. Jednak nadal można zmienić rozmiar lub położenie kontrolki poprzez **właściwości** oknie lub w kodzie.  
  
### <a name="to-lock-all-the-controls-on-a-form"></a>Aby zablokować wszystkie formanty w formularzu  
  
1.  Z **Format** menu, wybierz **formantów blokady**.  
  
    > [!NOTE]
    >  To polecenie umożliwia zablokowanie rozmiar formularza, ponieważ kontrolki formularza.  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a>Aby odblokować wszystkie zablokowane kontrolek w formularzu  
  
1.  Z **Format** menu, wybierz **formantów blokady**.  
  
     Wszystkie uprzednio zablokowaną kontrolki w formularzu są teraz odblokowane.  
  
### <a name="to-unlock-locked-controls-individually"></a>Aby odblokować zablokowany formantów indywidualnie  
  
1.  W **właściwości** okna, kliknij przycisk **zablokowany** właściwości i wybierz pozycję `false`. (Dwukrotne kliknięcie nazwy Przełącza ustawienie właściwości).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Kontrolki formularzy Windows Forms według funkcji](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
