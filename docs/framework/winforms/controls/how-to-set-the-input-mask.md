---
title: 'Porady: ustawienie maski wprowadzania'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.MaskPropertyEditor
helpviewer_keywords: MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c136bd5bdacec04a011f728694550fb66ae6d897
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-set-the-input-mask"></a>Porady: ustawienie maski wprowadzania
Kontrolki pola tekstowego maskowanego jest rozszerzony polu tekstowym obsługująca składni deklaratywnej akceptowanie lub odrzucanie danych wejściowych użytkownika. Przez ustawienie właściwości maski, można określić danych wejściowych użytkownika dopuszczalny bez pisania wszelka logika niestandardowego sprawdzania poprawności w aplikacji. Aby uzyskać więcej informacji, zobacz sekcję uwag <xref:System.Windows.Forms.MaskedTextBox> klasy.  
  
## <a name="setting-the-mask-property-manually"></a>Ustawienie właściwości maski ręcznie  
 Jeśli znasz znaki, które obsługuje właściwość maska, można go wprowadzić ręcznie. Podsumowanie znaki, które obsługuje właściwość maska, zobacz sekcję uwag <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.  
  
#### <a name="to-set-the-mask-property-manually"></a>Aby ręcznie ustawić właściwość maska  
  
1.  W **projekt** widok, wybierz opcję <xref:System.Windows.Forms.MaskedTextBox>.  
  
2.  W **właściwości** okna, zlokalizuj <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.  
  
3.  Wpisz maskę, który ma. Na przykład wpisz `###`.  
  
## <a name="using-the-input-mask-dialog-box"></a>Za pomocą okna dialogowego maska wprowadzania  
 Okno dialogowe maska wprowadzania zawiera kilka wstępnie zdefiniowanych maski wprowadzania. Można również zmienić maski wstępnie zdefiniowanych lub ręcznie wprowadź własne maski.  
  
#### <a name="to-open-the-input-mask-dialog-box"></a>Aby otworzyć okno dialogowe maska wprowadzania  
  
1.  W **projekt** widok, wybierz opcję <xref:System.Windows.Forms.MaskedTextBox>.  
  
    1.  Kliknij tag, aby otworzyć **zadania MaskedTextBox** panelu.  
  
    2.  Kliknij przycisk **ustawić maski**.  
  
     \-lub -  
  
    1.  W **właściwości** wybierz <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> właściwości.  
  
    2.  Kliknij przycisk wielokropka w kolumnie wartość właściwości.  
  
     **Maska wprowadzania** zostanie wyświetlone okno dialogowe.  
  
#### <a name="to-use-the-input-mask-dialog-box"></a>Aby użyć okna dialogowego maska wprowadzania  
  
1.  (Opcjonalnie) Kliknij jeden z wstępnie zdefiniowanych masek na liście.  
  
2.  (Opcjonalnie) Edytuj maski wstępnie zdefiniowanych w **maski** pole.  
  
3.  (Opcjonalnie) Wpisz nową maskę w **maski** pole. Oznacza to nie trzeba użyć jednej z wstępnie zdefiniowanych maski.  
  
    > [!NOTE]
    >  Pole podglądu zawiera znaki, które użytkownik będzie widział w <xref:System.Windows.Forms.MaskedTextBox>. Te znaki są także przewodnik ułatwiający użytkownik może wprowadzić dane poprawnie.  
  
4.  Wybierz lub wyczyść **ValidatingType użyj** pole wyboru. **ValidatingType użyj** pole wyboru określa, czy typ danych jest używana do Sprawdź wprowadzania danych przez użytkownika. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> właściwości.  
  
5.  Kliknij przycisk **OK**.  
  
     Maska została wprowadzona w **maski** właściwości w **właściwości** okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Praca z formantem MaskedTextBox](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)
