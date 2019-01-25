---
title: SaveFileDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: ab8eb5409d017c6ea73a44e4e57ccec9cece4824
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631064"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>SaveFileDialog — Informacje o składniku (Formularze systemu Windows)
Formularze Windows <xref:System.Windows.Forms.SaveFileDialog> składnik to wstępnie skonfigurowane okno dialogowe. Jest taka sama jak standardowy **Zapisz plik** okno dialogowe używane przez Windows. Dziedziczy <xref:System.Windows.Forms.CommonDialog> klasy.  
  
## <a name="working-with-the-savefiledialog-component"></a>Praca ze składnikiem SaveFileDialog  
 Używać go jako proste rozwiązanie umożliwiające użytkownikom zapisywanie plików, zamiast konfigurować własne okno dialogowe. Opierając się na standardowych okien dialogowych Windows, natychmiast dobrze znanym użytkownikom jest podstawową funkcjonalność aplikacji, które tworzysz. Należy jednak pamiętać, że w przypadku przy użyciu <xref:System.Windows.Forms.SaveFileDialog> składnik, należy napisać własną logiką zapisywania pliku.  
  
 Możesz użyć <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe w czasie wykonywania. Możesz otworzyć plik w trybie odczytu i zapisu za pomocą <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody.  
  
 Gdy zostanie dodany do formularza, <xref:System.Windows.Forms.SaveFileDialog> składnika, który pojawia się na pasku w dolnej części projektanta Windows Forms.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.SaveFileDialog>
- [SaveFileDialog, składnik](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
