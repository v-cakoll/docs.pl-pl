---
title: 'Instrukcje: Wyliczanie zainstalowanych czcionek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
ms.openlocfilehash: e56f06d6f7a762a1ef1ff85fa30751ea64f9f14b
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653746"
---
# <a name="how-to-enumerate-installed-fonts"></a><span data-ttu-id="6c0e6-102">Instrukcje: Wyliczanie zainstalowanych czcionek</span><span class="sxs-lookup"><span data-stu-id="6c0e6-102">How to: Enumerate Installed Fonts</span></span>
<span data-ttu-id="6c0e6-103"><xref:System.Drawing.Text.InstalledFontCollection> Klasa dziedziczy <xref:System.Drawing.Text.FontCollection> abstrakcyjna klasa bazowa.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-103">The <xref:System.Drawing.Text.InstalledFontCollection> class inherits from the <xref:System.Drawing.Text.FontCollection> abstract base class.</span></span> <span data-ttu-id="6c0e6-104">Możesz użyć <xref:System.Drawing.Text.InstalledFontCollection> obiektów do wyliczenia czcionki zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-104">You can use an <xref:System.Drawing.Text.InstalledFontCollection> object to enumerate the fonts installed on the computer.</span></span> <span data-ttu-id="6c0e6-105"><xref:System.Drawing.Text.FontCollection.Families%2A> Właściwość <xref:System.Drawing.Text.InstalledFontCollection> obiekt jest tablicą <xref:System.Drawing.FontFamily> obiektów.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-105">The <xref:System.Drawing.Text.FontCollection.Families%2A> property of an <xref:System.Drawing.Text.InstalledFontCollection> object is an array of <xref:System.Drawing.FontFamily> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c0e6-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c0e6-106">Example</span></span>  
 <span data-ttu-id="6c0e6-107">Poniższy przykład wyświetla listę nazw rodzin czcionek zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-107">The following example lists the names of all the font families installed on the computer.</span></span> <span data-ttu-id="6c0e6-108">Pobiera kod <xref:System.Drawing.FontFamily.Name%2A> właściwości każdego <xref:System.Drawing.FontFamily> obiektów w tablicy zwracanej przez <xref:System.Drawing.Text.FontCollection.Families%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-108">The code retrieves the <xref:System.Drawing.FontFamily.Name%2A> property of each <xref:System.Drawing.FontFamily> object in the array returned by the <xref:System.Drawing.Text.FontCollection.Families%2A> property.</span></span> <span data-ttu-id="6c0e6-109">Jako nazwy rodziny są pobierane, są łączone w do listy formularzy rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-109">As the family names are retrieved, they are concatenated to form a comma-separated list.</span></span> <span data-ttu-id="6c0e6-110">A następnie <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy rysuje rozdzielana przecinkami lista w prostokącie.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-110">Then the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class draws the comma-separated list in a rectangle.</span></span>  
  
 <span data-ttu-id="6c0e6-111">Jeśli uruchamiasz przykładowy kod, dane wyjściowe będą podobne do przedstawionego na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="6c0e6-111">If you run the example code, the output will be similar to that shown in the following illustration:</span></span>  
  
 ![Zrzut ekranu pokazujący rodzin czcionek zainstalowane.](./media/how-to-enumerate-installed-fonts/list-installed-font-families.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6c0e6-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6c0e6-113">Compiling the Code</span></span>  
 <span data-ttu-id="6c0e6-114">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span> <span data-ttu-id="6c0e6-115">Ponadto należy zaimportować <xref:System.Drawing.Text> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6c0e6-115">In addition, you should import the <xref:System.Drawing.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c0e6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c0e6-116">See also</span></span>
- [<span data-ttu-id="6c0e6-117">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="6c0e6-117">Using Fonts and Text</span></span>](using-fonts-and-text.md)
