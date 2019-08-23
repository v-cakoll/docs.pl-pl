---
title: 'Instrukcje: ustawienie maski wprowadzania'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 06dee48765653ac7a659246cc3dfe865c795ca21
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949150"
---
# <a name="how-to-set-the-input-mask"></a>Instrukcje: ustawienie maski wprowadzania
Formant pole tekstowe z maską jest ulepszoną kontrolką pola tekstowego, która obsługuje deklaratywną składnię akceptowania lub odrzucania danych wejściowych użytkownika. Ustawiając właściwość mask, można określić dozwolone dane wejściowe użytkownika bez pisania niestandardowej logiki walidacji w aplikacji. Aby uzyskać więcej informacji, zobacz sekcję <xref:System.Windows.Forms.MaskedTextBox> uwagi klasy.  
  
## <a name="setting-the-mask-property-manually"></a>Ręczne ustawianie właściwości maski  
 Jeśli znasz znaki obsługiwane przez właściwość maski, możesz wprowadzić ją ręcznie. Aby uzyskać podsumowanie znaków obsługiwanych przez właściwość maski, zobacz sekcję <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> uwagi właściwości.  
  
### <a name="to-set-the-mask-property-manually"></a>Aby ustawić właściwość maski ręcznie  
  
1. W widoku **projekt** wybierz pozycję a <xref:System.Windows.Forms.MaskedTextBox>.  
  
2. W oknie **Właściwości** Znajdź <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwość.  
  
3. Wpisz żądaną maskę. Na przykład wpisz `###`.  
  
## <a name="using-the-input-mask-dialog-box"></a>Korzystanie z okna dialogowego Maska wprowadzania  
 Okno dialogowe Maska wprowadzania zawiera kilka wstępnie zdefiniowanych masek wejściowych. Możesz również zmienić wstępnie zdefiniowane maski lub ręcznie wprowadzić własną maskę.  
  
### <a name="to-open-the-input-mask-dialog-box"></a>Aby otworzyć okno dialogowe Maska wprowadzania  
  
1. W widoku **projekt** wybierz pozycję a <xref:System.Windows.Forms.MaskedTextBox>.  
  
    1. Kliknij tag inteligentny, aby otworzyć panel **zadania formantem MaskedTextBox** .  
  
    2. Kliknij pozycję **Ustaw maskę**.  
  
     \- lub —  
  
    1. W oknie **Właściwości** wybierz <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwość.  
  
    2. Kliknij przycisk wielokropka w kolumnie wartość właściwości.  
  
     Zostanie wyświetlone okno dialogowe **Maska wprowadzania** .  
  
### <a name="to-use-the-input-mask-dialog-box"></a>Aby użyć okna dialogowego Maska wprowadzania  
  
1. Obowiązkowe Kliknij jedną ze wstępnie zdefiniowanych masek na liście.  
  
2. Obowiązkowe Edytuj wstępnie zdefiniowaną maskę w polu **maska** .  
  
3. Obowiązkowe W polu **maska** wpisz nową maskę. Oznacza to, że nie trzeba używać jednej ze wstępnie zdefiniowanych masek.  
  
    > [!NOTE]
    > W polu Podgląd wyświetlane są znaki, które użytkownik widzi w <xref:System.Windows.Forms.MaskedTextBox>. Te znaki to przewodnik ułatwiający prawidłowe wprowadzanie danych przez użytkownika.  
  
4. Zaznacz lub wyczyść pole wyboru **Użyj walidacji** . Pole wyboru **Użyj walidacji** określa, czy typ danych jest używany do weryfikowania danych wejściowych przez użytkownika. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> właściwość.  
  
5. Kliknij przycisk **OK**.  
  
     Maska jest wprowadzana we właściwości **Mask** w oknie **Właściwości** .  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik: Praca z kontrolką formantem MaskedTextBox](walkthrough-working-with-the-maskedtextbox-control.md)
