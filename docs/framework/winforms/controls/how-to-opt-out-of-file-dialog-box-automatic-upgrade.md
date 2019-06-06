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
ms.openlocfilehash: e12134768d41589dedbeb5a00cab4244c7324f97
ms.sourcegitcommit: 90f0bee0e8a416e45c78fa3ad4c91ef00e5228d5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66722613"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Instrukcje: jak nie zgadzać się na uczestnictwo dotyczące automatycznego uaktualniania okna dialogowego obsługi pliku
Gdy <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> klasy są używane w aplikacji, ich wyglądu i działania zależą od wersji systemu Windows, w której działa aplikacja na. Gdy aplikacja, która została utworzona na [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] lub wcześniej, jest wyświetlany na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> są automatycznie wyświetlane przy użyciu [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] wygląd i zachowanie. Począwszy od programu .NET Framework 3.0 można zrezygnować z automatycznego uaktualniania, aby wyświetlić <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> z [!INCLUDE[winxp](../../../../includes/winxp-md.md)]— styl wyglądu i zachowania.  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Aby zrezygnować z automatycznego uaktualniania okno dialogowe pliku  
  
1. Ustaw <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> właściwość <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog> do `false` przed wyświetleniem okna dialogowego.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FileDialog>
