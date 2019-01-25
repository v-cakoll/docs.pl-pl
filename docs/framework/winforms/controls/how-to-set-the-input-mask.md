---
title: 'Instrukcje: Ustawienie maski wprowadzania'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 68a3e72f23e881bc68441e8aee9674f1a822882a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658916"
---
# <a name="how-to-set-the-input-mask"></a>Instrukcje: Ustawienie maski wprowadzania
Formant pola tekstowego maskowanego jest formant pola tekstowego rozszerzonego, który obsługuje składni deklaratywnej akceptowanie lub odrzucanie dane wejściowe użytkownika. Ustawiając właściwość maski, można określić danych wejściowych użytkownika dozwolony bez konieczności pisania wszelkie logikę niestandardowego sprawdzania poprawności w aplikacji. Aby uzyskać więcej informacji, zobacz sekcję Uwagi <xref:System.Windows.Forms.MaskedTextBox> klasy.  
  
## <a name="setting-the-mask-property-manually"></a>Właściwość maski ręcznie  
 Jeśli znasz znaki, które obsługuje właściwość maska, można go wprowadzić ręcznie. Podsumowanie znaków, które obsługuje właściwość maska, zobacz sekcję Uwagi <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.  
  
#### <a name="to-set-the-mask-property-manually"></a>Aby ręcznie ustawić właściwość maski  
  
1.  W **projektowania** widoku, wybierz opcję <xref:System.Windows.Forms.MaskedTextBox>.  
  
2.  W **właściwości** oknie Znajdź <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.  
  
3.  Wpisz maskę, który ma. Na przykład wpisz `###`.  
  
## <a name="using-the-input-mask-dialog-box"></a>Za pomocą okna dialogowego maska wprowadzania  
 Maska wprowadzania, okno dialogowe zawiera kilka wstępnie zdefiniowanych maski wprowadzania. Można również zmienić maski wstępnie zdefiniowanych lub ręcznie wprowadź własne maski.  
  
#### <a name="to-open-the-input-mask-dialog-box"></a>Aby otworzyć okno dialogowe maska wprowadzania  
  
1.  W **projektowania** widoku, wybierz opcję <xref:System.Windows.Forms.MaskedTextBox>.  
  
    1.  Kliknij tag, aby otworzyć **zadania MaskedTextBox** panelu.  
  
    2.  Kliknij przycisk **ustawienie maski**.  
  
     \- lub —  
  
    1.  W **właściwości** wybierz <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.  
  
    2.  Kliknij przycisk wielokropka w kolumnie wartości właściwości.  
  
     **Maska wprowadzania** pojawi się okno dialogowe.  
  
#### <a name="to-use-the-input-mask-dialog-box"></a>Aby użyć okna dialogowego maska wprowadzania  
  
1.  (Opcjonalnie) Kliknij jeden z wstępnie zdefiniowanych masek na liście.  
  
2.  (Opcjonalnie) Wstępnie zdefiniowane maska w edycji **maski** pole.  
  
3.  (Opcjonalnie) Wpisz nową maskę w **maski** pole. Oznacza to nie trzeba użyć jednego z wstępnie zdefiniowanych maski.  
  
    > [!NOTE]
    >  Okno (wersja zapoznawcza) zawiera znaki, które użytkownik będzie widział w <xref:System.Windows.Forms.MaskedTextBox>. Te znaki znajdują się wskazówki pomagające użytkownik może wprowadzić poprawne dane.  
  
4.  Zaznacz lub wyczyść **ValidatingType użyj** pole wyboru. **ValidatingType użyj** pole wyboru określa, czy typ danych służy do Sprawdź danych wejściowych przez użytkownika. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> właściwości.  
  
5.  Kliknij przycisk **OK**.  
  
     Maska jest wprowadzana w **maski** właściwość **właściwości** okna.  
  
## <a name="see-also"></a>Zobacz także
- [Przewodnik: Praca z formantem MaskedTextBox](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)
