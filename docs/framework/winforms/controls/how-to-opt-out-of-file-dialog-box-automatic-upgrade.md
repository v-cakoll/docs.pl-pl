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
ms.openlocfilehash: 154953680426f98a9506feb0b8f4de25c873b795
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959685"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="8e6b6-102">Porady: jak nie zgadzać się na uczestnictwo dotyczące automatycznego uaktualniania okna dialogowego obsługi pliku</span><span class="sxs-lookup"><span data-stu-id="8e6b6-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="8e6b6-103">Gdy klasy <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> są używane w aplikacji, ich wygląd i zachowanie są zależne od wersji systemu Windows, na którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="8e6b6-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="8e6b6-104">Gdy aplikacja utworzona w .NET Framework 2,0 lub wcześniejszej jest wyświetlana w systemie Windows Vista, <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> są automatycznie wyświetlane z zachowaniem wyglądu i zachowania systemu Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="8e6b6-104">When an application that was created on the .NET Framework 2.0 or earlier is displayed on Windows Vista, <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the Windows Vista appearance and behavior.</span></span> <span data-ttu-id="8e6b6-105">Począwszy od .NET Framework 3,0, można zrezygnować z automatycznego uaktualnienia, aby wyświetlić <xref:System.Windows.Forms.OpenFileDialog> i <xref:System.Windows.Forms.SaveFileDialog> z wyglądem i zachowaniem stylu systemu Windows XP.</span><span class="sxs-lookup"><span data-stu-id="8e6b6-105">Starting in the .NET Framework 3.0, you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a Windows XP-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="8e6b6-106">Aby zrezygnować z automatycznej aktualizacji okna dialogowego</span><span class="sxs-lookup"><span data-stu-id="8e6b6-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1. <span data-ttu-id="8e6b6-107">Przed wyświetleniem okna dialogowego Ustaw właściwość <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog> na `false`.</span><span class="sxs-lookup"><span data-stu-id="8e6b6-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e6b6-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e6b6-108">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
