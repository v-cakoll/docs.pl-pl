---
title: SaveFileDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: be5f70e2e8b0d5143ef387819689ce95564a72d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537450"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>SaveFileDialog — Informacje o składniku (Formularze systemu Windows)
Formularze systemu Windows <xref:System.Windows.Forms.SaveFileDialog> składnik jest okno dialogowe wstępnie skonfigurowane. Jest to standardowy **Zapisz plik** okno dialogowe używane przez system Windows. Dziedziczy on z <xref:System.Windows.Forms.CommonDialog> klasy.  
  
## <a name="working-with-the-savefiledialog-component"></a>Praca ze składnikiem SaveFileDialog  
 Używać go jako proste rozwiązanie umożliwiający użytkownikom zapisywanie plików zamiast konfigurować własne okno dialogowe. Polegając na standardowe okno dialogowe systemu Windows, podstawowe funkcje tworzenia aplikacji jest znane użytkowników. Należy jednak pamiętać, że w przypadku przy użyciu <xref:System.Windows.Forms.SaveFileDialog> składnika, należy napisać logiki zapisywania plików.  
  
 Można użyć <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe w czasie wykonywania. Plik można otworzyć w trybie odczytu/zapisu z użyciem <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody.  
  
 Gdy jest ona dodawana do formularza, <xref:System.Windows.Forms.SaveFileDialog> składnika jest wyświetlana na pasku w dolnej części Projektant formularzy systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [SaveFileDialog, składnik](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
