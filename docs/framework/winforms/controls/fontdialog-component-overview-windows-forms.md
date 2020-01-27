---
title: FontDialog — Informacje o składniku
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 664b756dc068ca283e4f43edbdd0f3266f5d1142
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745707"
---
# <a name="fontdialog-component-overview-windows-forms"></a><span data-ttu-id="6efe7-102">FontDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="6efe7-102">FontDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="6efe7-103">Składnik <xref:System.Windows.Forms.FontDialog> Windows Forms jest wstępnie skonfigurowanym oknem dialogowym, które jest oknem dialogowym standardowe **czcionki** systemu Windows, które służy do udostępnienia czcionek aktualnie zainstalowanych w systemie.</span><span class="sxs-lookup"><span data-stu-id="6efe7-103">The Windows Forms <xref:System.Windows.Forms.FontDialog> component is a pre-configured dialog box, which is the standard Windows **Font** dialog box used to expose the fonts that are currently installed on the system.</span></span> <span data-ttu-id="6efe7-104">Użyj go w aplikacji opartej na systemie Windows jako proste rozwiązanie do wyboru czcionki zamiast konfigurowania własnego okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="6efe7-104">Use it within your Windows-based application as a simple solution for font selection in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="6efe7-105">Domyślnie okno dialogowe zawiera pola listy dla czcionki, stylu i rozmiaru czcionki; pola wyboru dla efektów takich jak przekreolenie i podkreolenie; Lista rozwijana dla skryptu; i przykład sposobu wyświetlania czcionki.</span><span class="sxs-lookup"><span data-stu-id="6efe7-105">By default, the dialog box shows list boxes for Font, Font style, and Size; check boxes for effects like Strikeout and Underline; a drop-down list for Script; and a sample of how the font will appear.</span></span> <span data-ttu-id="6efe7-106">(Skrypt odnosi się do różnych skryptów znaków, które są dostępne dla danej czcionki, na przykład hebrajski lub japoński). Aby wyświetlić okno dialogowe Czcionka, wywołaj metodę <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="6efe7-106">(Script refers to different character scripts that are available for a given font, for example, Hebrew or Japanese.) To display the font dialog box, call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="6efe7-107">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="6efe7-107">Key Properties</span></span>  
 <span data-ttu-id="6efe7-108">Składnik ma wiele właściwości, które konfigurują jego wygląd.</span><span class="sxs-lookup"><span data-stu-id="6efe7-108">The component has a number of properties that configure its appearance.</span></span> <span data-ttu-id="6efe7-109">Właściwości ustawiające wybory okna dialogowego są <xref:System.Windows.Forms.FontDialog.Font%2A> i <xref:System.Windows.Forms.FontDialog.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="6efe7-109">The properties that set the dialog-box selections are <xref:System.Windows.Forms.FontDialog.Font%2A> and <xref:System.Windows.Forms.FontDialog.Color%2A>.</span></span> <span data-ttu-id="6efe7-110">Właściwość <xref:System.Windows.Forms.FontDialog.Font%2A> ustawia czcionkę, styl, rozmiar, skrypt i efekty; na przykład `Arial, 10pt, style=Italic, Strikeout`.</span><span class="sxs-lookup"><span data-stu-id="6efe7-110">The <xref:System.Windows.Forms.FontDialog.Font%2A> property sets the font, style, size, script, and effects; for example, `Arial, 10pt, style=Italic, Strikeout`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6efe7-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6efe7-111">See also</span></span>

- <xref:System.Windows.Forms.FontDialog>
- [<span data-ttu-id="6efe7-112">FontDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="6efe7-112">FontDialog Component</span></span>](fontdialog-component-windows-forms.md)
