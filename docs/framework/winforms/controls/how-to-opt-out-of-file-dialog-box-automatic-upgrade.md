---
title: 'Porady: jak nie zgadzać się na uczestnictwo dotyczące automatycznego uaktualniania okna dialogowego obsługi pliku'
ms.date: 03/30/2017
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
ms.openlocfilehash: bbde260cc7f05226c9b06325b45708e1cde3cf8c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976883"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Porady: jak nie zgadzać się na uczestnictwo dotyczące automatycznego uaktualniania okna dialogowego obsługi pliku
Gdy klasy <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> są używane w aplikacji, ich wygląd i zachowanie są zależne od wersji systemu Windows, na którym działa aplikacja. Gdy aplikacja utworzona w .NET Framework 2,0 lub wcześniejszej jest wyświetlana w systemie Windows Vista, <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> są automatycznie wyświetlane z zachowaniem wyglądu i zachowania systemu Windows Vista. Począwszy od .NET Framework 3,0, możesz zrezygnować z automatycznego uaktualnienia, aby wyświetlić <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> z zachowaniem stylu [!INCLUDE[winxp](../../../../includes/winxp-md.md)].  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Aby zrezygnować z automatycznej aktualizacji okna dialogowego  
  
1. Przed wyświetleniem okna dialogowego Ustaw właściwość <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog> na `false`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FileDialog>
