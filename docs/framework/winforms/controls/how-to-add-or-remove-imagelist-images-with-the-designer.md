---
title: 'Instrukcje: dodawanie lub usuwanie obrazów ImageList przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: be17d5e6a12824c1c9edc867c99e77a6a1437a36
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658583"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a><span data-ttu-id="cdde4-102">Instrukcje: dodawanie lub usuwanie obrazów ImageList przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="cdde4-102">How to: Add or Remove ImageList Images with the Designer</span></span>

<span data-ttu-id="cdde4-103">Możesz dodawać obrazy do <xref:System.Windows.Forms.ImageList> składnika kilka różnych sposobów.</span><span class="sxs-lookup"><span data-stu-id="cdde4-103">You can add images to an <xref:System.Windows.Forms.ImageList> component several different ways.</span></span> <span data-ttu-id="cdde4-104">Możesz szybko dodawać obrazy przy użyciu tagu inteligentnego skojarzonego z <xref:System.Windows.Forms.ImageList>lub, jeśli ustawiasz kilka innych właściwości <xref:System.Windows.Forms.ImageList>w, może okazać się wygodniejsze, aby dodać obrazy z okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="cdde4-104">You can add images very quickly by using the smart tag associated with the <xref:System.Windows.Forms.ImageList>, or if you are setting several other properties on the <xref:System.Windows.Forms.ImageList>, you may find it more convenient to add images with the Properties window.</span></span> <span data-ttu-id="cdde4-105">Możesz również dodawać obrazy za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="cdde4-105">You can also add images by using code.</span></span> <span data-ttu-id="cdde4-106">Aby uzyskać więcej informacji na temat dodawania obrazów przy użyciu kodu, [zobacz How to: Dodawanie lub usuwanie obrazów za pomocą składnika](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)ImageList Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="cdde4-106">For more information about how to add images with code, see [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span> <span data-ttu-id="cdde4-107">Zwykle wypełniasz <xref:System.Windows.Forms.ImageList> składnik obrazami, zanim zostanie on skojarzony z kontrolką, ale nie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="cdde4-107">Typically you populate the <xref:System.Windows.Forms.ImageList> component with images before it is associated with a control, but this is not required.</span></span>

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a><span data-ttu-id="cdde4-108">Aby dodać lub usunąć obrazy przy użyciu okno Właściwości</span><span class="sxs-lookup"><span data-stu-id="cdde4-108">To add or remove images by using the Properties window</span></span>

1. <span data-ttu-id="cdde4-109"><xref:System.Windows.Forms.ImageList> Wybierz składnik lub Dodaj go do formularza.</span><span class="sxs-lookup"><span data-stu-id="cdde4-109">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="cdde4-110">W okno właściwości kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok <xref:System.Windows.Forms.ImageList.Images%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="cdde4-110">In the Properties window, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) next to the <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>

3. <span data-ttu-id="cdde4-111">W **edytorze kolekcji obrazów**kliknij pozycję **Dodaj** lub **Usuń** , aby dodać lub usunąć obrazy z listy.</span><span class="sxs-lookup"><span data-stu-id="cdde4-111">In the **Image Collection Editor**, click **Add** or **Remove** to add or remove images from the list.</span></span>

### <a name="to-add-or-remove-images-using-the-smart-tag"></a><span data-ttu-id="cdde4-112">Aby dodać lub usunąć obrazy przy użyciu tagu inteligentnego</span><span class="sxs-lookup"><span data-stu-id="cdde4-112">To add or remove images using the smart tag</span></span>

1. <span data-ttu-id="cdde4-113"><xref:System.Windows.Forms.ImageList> Wybierz składnik lub Dodaj go do formularza.</span><span class="sxs-lookup"><span data-stu-id="cdde4-113">Select the <xref:System.Windows.Forms.ImageList> component, or add one to the form.</span></span>

2. <span data-ttu-id="cdde4-114">Kliknij symbol tagu inteligentnego (![inteligentny symbol znacznika](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span><span class="sxs-lookup"><span data-stu-id="cdde4-114">Click the smart tag glyph (![Smart Tag Glyph](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))</span></span>

3. <span data-ttu-id="cdde4-115">W oknie dialogowym **ImageList Tasks (zadania** ) wybierz pozycję **Wybierz obrazy**.</span><span class="sxs-lookup"><span data-stu-id="cdde4-115">In the **ImageList Tasks** dialog box, select **Choose Images**.</span></span>

4. <span data-ttu-id="cdde4-116">W **edytorze kolekcji obrazów** kliknij pozycję **Dodaj** lub **Usuń** , aby dodać lub usunąć obrazy z listy.</span><span class="sxs-lookup"><span data-stu-id="cdde4-116">In the **Images Collection Editor** click **Add** or **Remove** to add or remove images from the list.</span></span>

## <a name="see-also"></a><span data-ttu-id="cdde4-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdde4-117">See also</span></span>

- [<span data-ttu-id="cdde4-118">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="cdde4-118">Images, Bitmaps, and Metafiles</span></span>](../advanced/images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="cdde4-119">Przewodnik: Wykonywanie typowych zadań przy użyciu tagów inteligentnych w kontrolkach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cdde4-119">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)
- [<span data-ttu-id="cdde4-120">ImageList, składnik</span><span class="sxs-lookup"><span data-stu-id="cdde4-120">ImageList Component</span></span>](imagelist-component-windows-forms.md)
