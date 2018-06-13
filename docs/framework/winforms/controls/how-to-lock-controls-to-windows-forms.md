---
title: 'Porady: blokowanie formantów do formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: f05da53f134f13bf5edbbe7ab8c5973f79bbca4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534748"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Porady: blokowanie formantów do formularzy systemu Windows
Podczas projektowania interfejsu użytkownika (UI) aplikacji systemu Windows, można zablokować formantów po znajdują się one poprawnie, tak aby nie mogą przypadkowo przenieść lub zmienić ich rozmiar przy ustawianiu inne właściwości.  
  
 Ponadto można zablokować i odblokować wszystkich kontrolek w formularzu jednocześnie, co jest przydatne w przypadku wielu formantów, lub można odblokować pojedynczych formantów. Po umieszczeniu wszystkich kontrolek żądanym na formularzu, należy zablokować je w miejscu, aby zapobiec błędnej przepływu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-lock-a-control"></a>Aby zablokować formantu  
  
1.  W **właściwości** okna, kliknij przycisk **zablokowany** właściwości i wybierz `true`. (Dwukrotne kliknięcie nazwy Przełącza ustawienie właściwości).  
  
     Alternatywnie kliknij formant prawym przyciskiem myszy i wybierz polecenie **formanty blokady**.  
  
    > [!NOTE]
    >  Blokowanie formantów zapobiega ich przeciąganie do nowego rozmiaru lub lokalizacji na powierzchni projektu. Jednak nadal zmianą rozmiaru lub lokalizacji formantów za pomocą klasy **właściwości** okna lub w kodzie.  
  
### <a name="to-lock-all-the-controls-on-a-form"></a>Aby zablokować wszystkich kontrolek w formularzu  
  
1.  Z **Format** menu, wybierz **formanty blokady**.  
  
    > [!NOTE]
    >  To polecenie blokuje również rozmiar formularza, ponieważ formularz jest formantem.  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a>Aby odblokować wszystkie zablokowane formantów w formularzu  
  
1.  Z **Format** menu, wybierz **formanty blokady**.  
  
     Wszystkie poprzednio zablokowanymi kontrolek w formularzu są teraz odblokowane.  
  
### <a name="to-unlock-locked-controls-individually"></a>Aby odblokować formanty zablokowane indywidualnie  
  
1.  W **właściwości** okna, kliknij przycisk **zablokowany** właściwości i wybierz `false`. (Dwukrotne kliknięcie nazwy Przełącza ustawienie właściwości).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Kontrolki formularzy Windows Forms według funkcji](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
