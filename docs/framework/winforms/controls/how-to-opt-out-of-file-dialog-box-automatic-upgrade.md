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
ms.openlocfilehash: a4be35617e8be1c6c83ac6f2d06e03b6cbb2977f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59301103"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="706f4-102">Instrukcje: jak nie zgadzać się na uczestnictwo dotyczące automatycznego uaktualniania okna dialogowego obsługi pliku</span><span class="sxs-lookup"><span data-stu-id="706f4-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="706f4-103">Gdy <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> klasy są używane w aplikacji, ich wyglądu i działania zależą od wersji systemu Windows, w której działa aplikacja na.</span><span class="sxs-lookup"><span data-stu-id="706f4-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="706f4-104">Gdy aplikacja, która została utworzona na [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] lub wcześniej, jest wyświetlany na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> są automatycznie wyświetlane przy użyciu [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] wygląd i zachowanie.</span><span class="sxs-lookup"><span data-stu-id="706f4-104">When an application that was created on the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] or earlier is displayed on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] appearance and behavior.</span></span> <span data-ttu-id="706f4-105">Począwszy od [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], użytkownik może zrezygnować z automatycznego uaktualniania, aby wyświetlić <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> z [!INCLUDE[winxp](../../../../includes/winxp-md.md)]— styl wyglądu i zachowania.</span><span class="sxs-lookup"><span data-stu-id="706f4-105">Starting in the [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="706f4-106">Aby zrezygnować z automatycznego uaktualniania okno dialogowe pliku</span><span class="sxs-lookup"><span data-stu-id="706f4-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1. <span data-ttu-id="706f4-107">Ustaw <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> właściwość <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog> do `false` przed wyświetleniem okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="706f4-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="706f4-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="706f4-108">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
