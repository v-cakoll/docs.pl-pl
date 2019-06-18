---
title: 'Instrukcje: jak nie zgadzać się na uczestnictwo dotyczące automatycznego uaktualniania okna dialogowego obsługi pliku'
ms.date: 03/30/2017
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
ms.openlocfilehash: 0753873ac37f26d6503397290ef4603702737a86
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170615"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Instrukcje: jak nie zgadzać się na uczestnictwo dotyczące automatycznego uaktualniania okna dialogowego obsługi pliku
Gdy <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> klasy są używane w aplikacji, ich wyglądu i działania zależą od wersji systemu Windows, w której działa aplikacja na. Gdy aplikacja, która została utworzona w .NET Framework 2.0 lub starszej, zostanie wyświetlona na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> są automatycznie wyświetlane przy użyciu [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] wygląd i zachowanie. Począwszy od programu .NET Framework 3.0 można zrezygnować z automatycznego uaktualniania, aby wyświetlić <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> z [!INCLUDE[winxp](../../../../includes/winxp-md.md)]— styl wyglądu i zachowania.  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Aby zrezygnować z automatycznego uaktualniania okno dialogowe pliku  
  
1. Ustaw <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> właściwość <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog> do `false` przed wyświetleniem okna dialogowego.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FileDialog>
