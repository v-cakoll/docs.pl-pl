---
title: Wyświetlanie znaków azjatyckich za pomocą właściwości ImeMode
ms.date: 03/30/2017
helpviewer_keywords:
- Asian languages [Windows Forms], displaying with ImeMode
- Chinese characters [Windows Forms], displaying with ImeMode
- IME mode
- Japanese characters [Windows Forms], displaying with ImeMode
- international applications [Windows Forms], character display
- international characters
- Korean characters
- Asian languages
- Input Method Editor (IME), mode
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: c60ae399-0dab-4f07-9dea-6dbfb15ec0ae
ms.openlocfilehash: d3733f642d4218c851040582ee5637b5486a7804
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208467"
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a>Wyświetlanie znaków azjatyckich za pomocą właściwości ImeMode
<xref:System.Windows.Forms.Control.ImeMode%2A> Właściwość jest używana przez formularzy i kontrolek, aby wymusić określony tryb edytora metody wprowadzania (IME). Edytora IME jest istotnym elementem do pisania skryptów chińskich, japońskich i koreańskich, ponieważ te systemy zapisu mają więcej znaków niż mogą być kodowane w regularnych klawiatury. Na przykład można zezwolić tylko znaki ASCII w określonym polu. W takim przypadku można ustawić <xref:System.Windows.Forms.Control.ImeMode%2A> właściwości <xref:System.Windows.Forms.ImeMode> i użytkownicy będą mogli tylko do wprowadzania znaków ASCII określonego pola. Wartość domyślna <xref:System.Windows.Forms.Control.ImeMode%2A> właściwość jest <xref:System.Windows.Forms.ImeMode>, więc po ustawieniu właściwości formularza wszystkich kontrolek w formularzu będzie dziedziczyć tego ustawienia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.Control.ImeMode%2A> ) i <xref:System.Windows.Forms.ImeMode>.  
  
## <a name="see-also"></a>Zobacz także

[Globalizowanie aplikacji Windows Forms](globalizing-windows-forms.md)
