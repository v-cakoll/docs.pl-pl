---
title: SaveFileDialog, składnik — omówienie
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 7609c29b7e932ecee7dc8a289617094bd8d480e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743100"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>SaveFileDialog — Informacje o składniku (Formularze systemu Windows)

Składnik <xref:System.Windows.Forms.SaveFileDialog> Windows Forms jest wstępnie skonfigurowanym oknem dialogowym. Jest to takie samo, jak okno dialogowe **plik zapisywania** standardowego używany przez system Windows. Dziedziczy z klasy <xref:System.Windows.Forms.CommonDialog>.

## <a name="working-with-the-savefiledialog-component"></a>Praca ze składnikiem SaveFileDialog

Użyj jej jako prostego rozwiązania umożliwiającego użytkownikom zapisywanie plików zamiast konfigurować własne okno dialogowe. Opierając się na standardowych oknach dialogowych systemu Windows, podstawowe funkcje aplikacji tworzonych przez Ciebie są od razu znane użytkownikom. Należy jednak pamiętać, że w przypadku korzystania ze składnika <xref:System.Windows.Forms.SaveFileDialog> należy napisać własną logikę zapisywania plików.

Możesz użyć metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>, aby wyświetlić okno dialogowe w czasie wykonywania. Plik można otworzyć w trybie odczytu/zapisu przy użyciu metody <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>.

Po dodaniu do formularza składnik <xref:System.Windows.Forms.SaveFileDialog> pojawia się w zasobniku u dołu Projektant formularzy systemu Windows w programie Visual Studio.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.SaveFileDialog>
- [SaveFileDialog, składnik](savefiledialog-component-windows-forms.md)
