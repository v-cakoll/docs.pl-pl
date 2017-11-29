---
title: "Porady: jak nie zgadzać się na uczestnictwo dotyczące automatycznego uaktualniania okna dialogowego obsługi pliku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 01be9e29c00f39125c8ee645242e986fac178ba2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Porady: jak nie zgadzać się na uczestnictwo dotyczące automatycznego uaktualniania okna dialogowego obsługi pliku
Gdy <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> klasy są używane w aplikacji, ich wyglądu i działania są zależne od wersji systemu Windows, aplikacja jest uruchomiona na. Gdy aplikacja, która została utworzona na [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] lub wcześniej jest wyświetlany na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> są automatycznie wyświetlane z [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] wygląd i zachowanie. Począwszy od [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], można zrezygnować z automatycznego uaktualniania, aby wyświetlić <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> z [!INCLUDE[winxp](../../../../includes/winxp-md.md)]— styl wyglądu i zachowania.  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Aby zrezygnować z automatycznej aktualizacji okno dialogowe pliku  
  
1.  Ustaw <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> właściwość <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog> do `false` przed wyświetleniem okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.FileDialog>
