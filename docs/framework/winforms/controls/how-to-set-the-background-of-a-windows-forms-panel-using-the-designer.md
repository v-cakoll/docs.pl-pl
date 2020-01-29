---
title: Ustawianie tła panelu przy użyciu narzędzia Projektant
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 8bdefba433632f7ba02f549a549c52c7aa56c2d7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731923"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Instrukcje: Ustawianie tła panelu Windows Forms przy użyciu narzędzia Projektant

Kontrolka <xref:System.Windows.Forms.Panel> Windows Forms może wyświetlać zarówno kolor tła, jak i obraz tła. Właściwość <xref:System.Windows.Forms.Control.BackColor%2A> ustawia kolor tła dla kontrolek, które są zawarte w panelu, takich jak etykiety i przyciski radiowe. Jeśli właściwość <xref:System.Windows.Forms.Control.BackgroundImage%2A> nie jest ustawiona, wybór <xref:System.Windows.Forms.Control.BackColor%2A> spowoduje wypełnienie wszystkich paneli. Jeśli właściwość <xref:System.Windows.Forms.Control.BackgroundImage%2A> jest ustawiona, obraz będzie wyświetlany za kontrolkami, które są zawarte w panelu.

Poniższa procedura wymaga projektu **aplikacji systemu Windows** z formularzem zawierającym formant <xref:System.Windows.Forms.Panel>. Aby uzyskać informacje na temat sposobu konfigurowania takiego projektu w programie Visual Studio, zobacz [How to: Create a Windows Forms Project Application](/visualstudio/ide/step-1-create-a-windows-forms-application-project) i [How to: Add controls to Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="set-the-background-in-the-windows-forms-designer"></a>Ustaw tło w Projektant formularzy systemu Windows

1. Otwórz projekt w programie Visual Studio i wybierz formant <xref:System.Windows.Forms.Panel>.

2. W oknie **Właściwości** kliknij przycisk strzałki obok właściwości <xref:System.Windows.Forms.Control.BackColor%2A>, aby wyświetlić okno z trzema kartami.

3. Wybierz kartę **niestandardową** , aby wyświetlić paletę kolorów.

4. Wybierz kartę **Sieć Web** lub **system** , aby wyświetlić listę wstępnie zdefiniowanych nazw dla kolorów, a następnie wybierz kolor.

5. W oknie **Właściwości** kliknij przycisk strzałki obok właściwości <xref:System.Windows.Forms.Control.BackgroundImage%2A>.

6. W oknie dialogowym **Otwórz** wybierz plik, który chcesz wyświetlić.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Control.BackColor%2A>
- <xref:System.Windows.Forms.Control.BackgroundImage%2A>
- [Panel, kontrolka](panel-control-windows-forms.md)
- [Panel, kontrolka — omówienie](panel-control-overview-windows-forms.md)
- [Instrukcje: grupowanie kontrolek za pomocą kontrolki Panel formularzy Windows Forms przy użyciu narzędzia Projektant](group-controls-with-wf-panel-control-using-the-designer.md)
