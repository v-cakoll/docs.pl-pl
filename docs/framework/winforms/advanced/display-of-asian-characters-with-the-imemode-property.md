---
title: Wyświetlanie znaków azjatyckich za pomocą właściwości ImeMode
ms.date: 03/30/2017
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
ms.openlocfilehash: 25602e1a878443bd54411dfd6481581abebda5c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500528"
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a><span data-ttu-id="1a826-102">Wyświetlanie znaków azjatyckich za pomocą właściwości ImeMode</span><span class="sxs-lookup"><span data-stu-id="1a826-102">Display of Asian Characters with the ImeMode Property</span></span>
<span data-ttu-id="1a826-103"><xref:System.Windows.Forms.Control.ImeMode%2A> Właściwość jest używana przez formularze i formanty, aby wymusić określony tryb na edytor input method editor (IME).</span><span class="sxs-lookup"><span data-stu-id="1a826-103">The <xref:System.Windows.Forms.Control.ImeMode%2A> property is used by forms and controls to force a specific mode for an input method editor (IME).</span></span> <span data-ttu-id="1a826-104">Edytora IME jest istotnym elementem do pisania skryptów języka chińskiego, japońskiego i koreańskiego, ponieważ te systemy pisania mieć więcej znaków niż może być zakodowany na potrzeby regularnego klawiatury.</span><span class="sxs-lookup"><span data-stu-id="1a826-104">The IME is an essential component for writing Chinese, Japanese, and Korean scripts, since these writing systems have more characters than can be encoded for a regular keyboard.</span></span> <span data-ttu-id="1a826-105">Na przykład można zezwolić tylko znaki ASCII w określonym polu.</span><span class="sxs-lookup"><span data-stu-id="1a826-105">For example, you may want to allow only ASCII characters in a particular text box.</span></span> <span data-ttu-id="1a826-106">W takim przypadku można ustawić <xref:System.Windows.Forms.Control.ImeMode%2A> właściwość <xref:System.Windows.Forms.ImeMode> i użytkowników tylko wtedy będzie można wprowadzić znaki ASCII określonego pola.</span><span class="sxs-lookup"><span data-stu-id="1a826-106">In such a case you can set the <xref:System.Windows.Forms.Control.ImeMode%2A> property to <xref:System.Windows.Forms.ImeMode> and users will only be able to enter ASCII characters for that particular text box.</span></span> <span data-ttu-id="1a826-107">Wartość domyślna <xref:System.Windows.Forms.Control.ImeMode%2A> właściwość <xref:System.Windows.Forms.ImeMode>, więc jeśli ustawisz właściwość formularza, wszystkie formanty w formularzu będą dziedziczyć tego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="1a826-107">The default value of the <xref:System.Windows.Forms.Control.ImeMode%2A> property is <xref:System.Windows.Forms.ImeMode>, so if you set the property for a form, all controls on the form will inherit that setting.</span></span> <span data-ttu-id="1a826-108">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.Control.ImeMode%2A> ) i <xref:System.Windows.Forms.ImeMode>.</span><span class="sxs-lookup"><span data-stu-id="1a826-108">For more information, see <xref:System.Windows.Forms.Control.ImeMode%2A> ) and <xref:System.Windows.Forms.ImeMode>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a826-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a826-109">See also</span></span>

- [<span data-ttu-id="1a826-110">Globalizowanie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1a826-110">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
