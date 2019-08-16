---
title: 'Instrukcje: blokowanie kontrolek do formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: cbf82f1481ee9779cec5cfbf3fb057b7ea399a1c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039905"
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Instrukcje: blokowanie kontrolek do formularzy systemu Windows
Podczas projektowania interfejsu użytkownika aplikacji systemu Windows, można zablokować kontrolki po ich poprawnym umieszczeniu, aby nie przełączać ani zmieniać ich rozmiaru podczas ustawiania innych właściwości.

 Ponadto można zablokować i odblokować wszystkie kontrolki w formularzu jednocześnie, co jest przydatne w przypadku formularzy z wieloma kontrolkami lub można odblokować poszczególne kontrolki. Po umieszczeniu wszystkich kontrolek, w których chcesz, Zablokuj je wszystkie w miejscu, aby uniknąć błędnego przenoszenia.

## <a name="to-lock-a-control"></a>Aby zablokować kontrolkę

1. W oknie **Właściwości** kliknij właściwość zablokowana i wybierz pozycję `true`. (Dwukrotne kliknięcie nazwy powoduje przełączenie ustawienia właściwości.)

     Alternatywnie kliknij prawym przyciskiem myszy formant i wybierzpolecenie Zablokuj kontrolki.

    > [!NOTE]
    >  Kontrolki blokowania uniemożliwiają przeciągnięcie ich do nowego rozmiaru lub lokalizacji na powierzchni projektowej. Jednak nadal można zmienić rozmiar lub lokalizację kontrolek za pomocą okna **Właściwości** lub kodu.

## <a name="to-lock-all-the-controls-on-a-form"></a>Aby zablokować wszystkie kontrolki w formularzu

1. Z menu **Format** wybierz opcję Zablokuj **kontrolki**.

    > [!NOTE]
    >  To polecenie blokuje również rozmiar formularza, ponieważ formularz jest formantem.

## <a name="to-unlock-all-locked-controls-on-a-form"></a>Aby odblokować wszystkie zablokowane kontrolki w formularzu

1. Z menu **Format** wybierz opcję Zablokuj **kontrolki**.

     Wszystkie poprzednio zablokowane kontrolki w formularzu są teraz odblokowane.

## <a name="to-unlock-locked-controls-individually"></a>Aby odblokować zablokowane kontrolki indywidualnie

1. W oknie **Właściwości** kliknij właściwość zablokowana i wybierz pozycję `false`. (Dwukrotne kliknięcie nazwy powoduje przełączenie ustawienia właściwości.)

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Rozmieszczanie kontrolek na formularzach Windows Forms](arranging-controls-on-windows-forms.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
