---
title: "FontDialog — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1e00fc074148ddd53885bafbb490a3e3868fc0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="fontdialog-component-overview-windows-forms"></a><span data-ttu-id="0a838-102">FontDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="0a838-102">FontDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="0a838-103">Formularze systemu Windows <xref:System.Windows.Forms.FontDialog> składnik jest wstępnie skonfigurowane okno dialogowe, które jest standard Windows **czcionki** okno dialogowe używany do udostępnienia czcionek, które są aktualnie zainstalowane w systemie.</span><span class="sxs-lookup"><span data-stu-id="0a838-103">The Windows Forms <xref:System.Windows.Forms.FontDialog> component is a pre-configured dialog box, which is the standard Windows **Font** dialog box used to expose the fonts that are currently installed on the system.</span></span> <span data-ttu-id="0a838-104">Używać go w aplikacji systemu Windows jako prostym rozwiązaniem wybór czcionki zamiast własne okno dialogowe Konfigurowanie.</span><span class="sxs-lookup"><span data-stu-id="0a838-104">Use it within your Windows-based application as a simple solution for font selection in lieu of configuring your own dialog box.</span></span>  
  
 <span data-ttu-id="0a838-105">Domyślnie okno dialogowe zawiera pola listy czcionki, styl czcionki i rozmiar. pola wyboru dla efekty, takie jak przekreślenia i podkreślenie; listy rozwijanej dla skryptu; i przykładowe wygląd czcionki.</span><span class="sxs-lookup"><span data-stu-id="0a838-105">By default, the dialog box shows list boxes for Font, Font style, and Size; check boxes for effects like Strikeout and Underline; a drop-down list for Script; and a sample of how the font will appear.</span></span> <span data-ttu-id="0a838-106">(Skryptu lub odwołuje się do innego znaku skryptów, które są dostępne dla danej czcionki, na przykład hebrajski japoński.) Aby wyświetlić okno dialogowe czcionki, należy wywołać <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="0a838-106">(Script refers to different character scripts that are available for a given font, for example, Hebrew or Japanese.) To display the font dialog box, call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="0a838-107">Właściwości klucza</span><span class="sxs-lookup"><span data-stu-id="0a838-107">Key Properties</span></span>  
 <span data-ttu-id="0a838-108">Składnik ma wiele właściwości, które skonfigurować jego wyglądu.</span><span class="sxs-lookup"><span data-stu-id="0a838-108">The component has a number of properties that configure its appearance.</span></span> <span data-ttu-id="0a838-109">Ustawione opcje Okno dialogowe właściwości są <xref:System.Windows.Forms.FontDialog.Font%2A> i <xref:System.Windows.Forms.FontDialog.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="0a838-109">The properties that set the dialog-box selections are <xref:System.Windows.Forms.FontDialog.Font%2A> and <xref:System.Windows.Forms.FontDialog.Color%2A>.</span></span> <span data-ttu-id="0a838-110"><xref:System.Windows.Forms.FontDialog.Font%2A> Ustawia właściwość czcionki, style, rozmiar, skrypt i skutki; na przykład `Arial, 10pt, style=Italic, Strikeout`.</span><span class="sxs-lookup"><span data-stu-id="0a838-110">The <xref:System.Windows.Forms.FontDialog.Font%2A> property sets the font, style, size, script, and effects; for example, `Arial, 10pt, style=Italic, Strikeout`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a838-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a838-111">See Also</span></span>  
 <xref:System.Windows.Forms.FontDialog>  
 [<span data-ttu-id="0a838-112">Fontdialog — składnik</span><span class="sxs-lookup"><span data-stu-id="0a838-112">FontDialog Component</span></span>](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
