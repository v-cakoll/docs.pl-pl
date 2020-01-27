---
title: OpenFileDialog — Informacje o składniku
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: c519b373150a49ee41dbb0c503f7d5a4862477d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728440"
---
# <a name="openfiledialog-component-overview-windows-forms"></a>OpenFileDialog — Informacje o składniku (Formularze systemu Windows)

Składnik <xref:System.Windows.Forms.OpenFileDialog> Windows Forms jest wstępnie skonfigurowanym oknem dialogowym. Jest to to samo okno dialogowe **Otwórz plik** uwidocznione przez system operacyjny Windows. Dziedziczy z klasy <xref:System.Windows.Forms.CommonDialog>.

## <a name="use-this-component"></a>Użyj tego składnika

Użyj tego składnika w aplikacji opartej na systemie Windows jako prostego rozwiązania do wyboru plików zamiast konfigurowania własnego okna dialogowego. Polegając na standardowych oknach dialogowych systemu Windows, można tworzyć aplikacje, których podstawowe funkcje są bezpośrednio znane użytkownikom. Należy jednak pamiętać, że w przypadku korzystania ze składnika <xref:System.Windows.Forms.OpenFileDialog> należy napisać własną logikę otwierania plików.

Użyj metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>, aby wyświetlić okno dialogowe w czasie wykonywania. Możesz zezwolić użytkownikom na otwieranie plików z możliwością wyboru przy użyciu właściwości <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>. Ponadto można użyć właściwości <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A>, aby określić, czy w oknie dialogowym pojawi się pole wyboru tylko do odczytu. Właściwość <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> wskazuje, czy jest zaznaczone pole wyboru tylko do odczytu. Na koniec Właściwość <xref:System.Windows.Forms.FileDialog.Filter%2A> ustawia bieżący ciąg filtru nazwy pliku, który określa opcje, które pojawiają się w polu "Pliki typu" w oknie dialogowym.

Po dodaniu do formularza składnik <xref:System.Windows.Forms.OpenFileDialog> pojawia się w zasobniku u dołu Projektant formularzy systemu Windows w programie Visual Studio.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog, składnik](openfiledialog-component-windows-forms.md)
