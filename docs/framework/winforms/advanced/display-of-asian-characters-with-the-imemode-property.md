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
ms.openlocfilehash: 25602e1a878443bd54411dfd6481581abebda5c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755483"
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a>Wyświetlanie znaków azjatyckich za pomocą właściwości ImeMode
<xref:System.Windows.Forms.Control.ImeMode%2A> Właściwość jest używana przez formularze i formanty, aby wymusić określony tryb na edytor input method editor (IME). Edytora IME jest istotnym elementem do pisania skryptów języka chińskiego, japońskiego i koreańskiego, ponieważ te systemy pisania mieć więcej znaków niż może być zakodowany na potrzeby regularnego klawiatury. Na przykład można zezwolić tylko znaki ASCII w określonym polu. W takim przypadku można ustawić <xref:System.Windows.Forms.Control.ImeMode%2A> właściwość <xref:System.Windows.Forms.ImeMode> i użytkowników tylko wtedy będzie można wprowadzić znaki ASCII określonego pola. Wartość domyślna <xref:System.Windows.Forms.Control.ImeMode%2A> właściwość <xref:System.Windows.Forms.ImeMode>, więc jeśli ustawisz właściwość formularza, wszystkie formanty w formularzu będą dziedziczyć tego ustawienia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.Control.ImeMode%2A> ) i <xref:System.Windows.Forms.ImeMode>.  
  
## <a name="see-also"></a>Zobacz także

- [Globalizowanie aplikacji Windows Forms](globalizing-windows-forms.md)
