---
title: 'Instrukcje: ustawianie tła panelu formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 6927a7118c43ced03623a9764a3ef1e0814c95cb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211642"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Instrukcje: Ustawianie tła panelu formularzy Windows przy użyciu narzędzia Projektant

Formularze Windows <xref:System.Windows.Forms.Panel> formant może wyświetlić kolor tła i obraz tła. <xref:System.Windows.Forms.Control.BackColor%2A> Właściwość ustawia kolor tła kontrolki, które są zawarte w panelu, takich jak etykiety i przycisków radiowych. Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> nie ustawiono właściwości <xref:System.Windows.Forms.Control.BackColor%2A> wypełni wszystkie panelu wyboru. Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość jest ustawiona, obraz, który pojawi się za zaporą formantów, które są zawarte w panelu.

Poniższa procedura wymaga **aplikacji Windows** projektu za pomocą formularza, który zawiera <xref:System.Windows.Forms.Panel> kontroli. Aby dowiedzieć się, jak skonfigurować projekt w programie Visual Studio, zobacz [jak: Utwórz projekt aplikacji Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [jak: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="set-the-background-in-the-windows-forms-designer"></a>Ustawianie tła w programie Windows Forms Designer

1. Otwórz projekt w programie Visual Studio i wybierz <xref:System.Windows.Forms.Panel> kontroli.

2. W **właściwości** , kliknij strzałkę znajdujący się obok <xref:System.Windows.Forms.Control.BackColor%2A> właściwość, aby wyświetlić okno z trzema kartami.

3. Wybierz **niestandardowe** kartę, aby wyświetlić paletę kolorów.

4. Wybierz **Web** lub **systemu** kartę, aby wyświetlić listę nazw wstępnie zdefiniowanych kolorów, a następnie wybierz kolor.

5. W **właściwości** , kliknij strzałkę znajdujący się obok <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości.

6. W **Otwórz** oknie dialogowym Wybierz plik który chcesz wyświetlić.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel, kontrolka](panel-control-windows-forms.md)
- [Panel, kontrolka — omówienie](panel-control-overview-windows-forms.md)
- [Instrukcje: Grupowanie formantów z formantem panelu formularzy Windows przy użyciu narzędzia Projektant](group-controls-with-wf-panel-control-using-the-designer.md)
