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
ms.openlocfilehash: 380f8abe502c37e57207c43696158c1e3bdc7697
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532490"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="8efda-102">Porady: jak nie zgadzać się na uczestnictwo dotyczące automatycznego uaktualniania okna dialogowego obsługi pliku</span><span class="sxs-lookup"><span data-stu-id="8efda-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="8efda-103">Gdy <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> klasy są używane w aplikacji, ich wyglądu i działania są zależne od wersji systemu Windows, aplikacja jest uruchomiona na.</span><span class="sxs-lookup"><span data-stu-id="8efda-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="8efda-104">Gdy aplikacja, która została utworzona na [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] lub wcześniej jest wyświetlany na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> są automatycznie wyświetlane z [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] wygląd i zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8efda-104">When an application that was created on the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] or earlier is displayed on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] appearance and behavior.</span></span> <span data-ttu-id="8efda-105">Począwszy od [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], można zrezygnować z automatycznego uaktualniania, aby wyświetlić <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> z [!INCLUDE[winxp](../../../../includes/winxp-md.md)]— styl wyglądu i zachowania.</span><span class="sxs-lookup"><span data-stu-id="8efda-105">Starting in the [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="8efda-106">Aby zrezygnować z automatycznej aktualizacji okno dialogowe pliku</span><span class="sxs-lookup"><span data-stu-id="8efda-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1.  <span data-ttu-id="8efda-107">Ustaw <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> właściwość <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog> do `false` przed wyświetleniem okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="8efda-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8efda-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8efda-108">See Also</span></span>  
 <xref:System.Windows.Forms.FileDialog>
