---
title: "Wyświetlanie znaków azjatyckich za pomocą właściwości ImeMode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Asian languages [Windows Forms], displaying with ImeMode
- Chinese characters [Windows Forms], displaying with ImeMode
- IME mode
- Japanese characters [Windows Forms], displaying with ImeMode
- international applications [Windows Forms], character display
- international characters
- Korean characters
- Asian languages
- Input Method Editor (IME), mode
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: c60ae399-0dab-4f07-9dea-6dbfb15ec0ae
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5971fd9a75f936d2ec63eea6a086c681ec996652
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a><span data-ttu-id="fca1c-102">Wyświetlanie znaków azjatyckich za pomocą właściwości ImeMode</span><span class="sxs-lookup"><span data-stu-id="fca1c-102">Display of Asian Characters with the ImeMode Property</span></span>
<span data-ttu-id="fca1c-103"><xref:System.Windows.Forms.Control.ImeMode%2A> Właściwość jest używana przez formularzy i kontrolek, aby wymusić określony tryb edytora metody wprowadzania (IME).</span><span class="sxs-lookup"><span data-stu-id="fca1c-103">The <xref:System.Windows.Forms.Control.ImeMode%2A> property is used by forms and controls to force a specific mode for an input method editor (IME).</span></span> <span data-ttu-id="fca1c-104">Edytora IME jest istotnym elementem do pisania skryptów chińskich, japońskich i koreańskich, ponieważ te systemy zapisu mają więcej znaków niż mogą być kodowane w regularnych klawiatury.</span><span class="sxs-lookup"><span data-stu-id="fca1c-104">The IME is an essential component for writing Chinese, Japanese, and Korean scripts, since these writing systems have more characters than can be encoded for a regular keyboard.</span></span> <span data-ttu-id="fca1c-105">Na przykład można zezwolić tylko znaki ASCII w określonym polu.</span><span class="sxs-lookup"><span data-stu-id="fca1c-105">For example, you may want to allow only ASCII characters in a particular text box.</span></span> <span data-ttu-id="fca1c-106">W takim przypadku można ustawić <xref:System.Windows.Forms.Control.ImeMode%2A> właściwości <xref:System.Windows.Forms.ImeMode> i użytkownicy będą mogli tylko do wprowadzania znaków ASCII określonego pola.</span><span class="sxs-lookup"><span data-stu-id="fca1c-106">In such a case you can set the <xref:System.Windows.Forms.Control.ImeMode%2A> property to <xref:System.Windows.Forms.ImeMode> and users will only be able to enter ASCII characters for that particular text box.</span></span> <span data-ttu-id="fca1c-107">Wartość domyślna <xref:System.Windows.Forms.Control.ImeMode%2A> właściwość jest <xref:System.Windows.Forms.ImeMode>, więc po ustawieniu właściwości formularza wszystkich kontrolek w formularzu będzie dziedziczyć tego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="fca1c-107">The default value of the <xref:System.Windows.Forms.Control.ImeMode%2A> property is <xref:System.Windows.Forms.ImeMode>, so if you set the property for a form, all controls on the form will inherit that setting.</span></span> <span data-ttu-id="fca1c-108">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.Control.ImeMode%2A> ) i <xref:System.Windows.Forms.ImeMode>.</span><span class="sxs-lookup"><span data-stu-id="fca1c-108">For more information, see <xref:System.Windows.Forms.Control.ImeMode%2A> ) and <xref:System.Windows.Forms.ImeMode>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fca1c-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fca1c-109">See Also</span></span>  
 [<span data-ttu-id="fca1c-110">Globalizacja formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fca1c-110">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)
